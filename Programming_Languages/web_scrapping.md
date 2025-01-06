# TOPICS

1. 
2. Setting up scrappy
3. 
4. First scrappy spider
5. 
6. cleaning data
7. saving data to files and databases
8. faking scrappy headers and user-agents
9. rotating proxies and proxy APIS
10. deploying and scheduling spiders using scrapyd
11. deploying and scheduling spiders with scrapeops
12.



## setting up a project
``scrapy startproject bookscraper``
``scrapy startproject ProjectName``

## 7 saving data 
- via command line  
``scrapy crawl bookspider -O bookData.csv``

appending data to a file  
``scrapy crawl bookspider -o bookData.csv``

- via Feed setting
go to setting and add the following line:

```
FEEDS = {
    'booksdata.json' : {'format': 'json'}
}
```
After this run your spider and the file will be created, booksdata.json == filename, format == specifies the format === csv, json


To overide settings in setting file:
add :
```
customer_settings = {
    'FEEDS' : {
        'books_new_data' : {'format': 'csv', 'overwrite' : True }
    }
}
```
in spiderfile.
- data into database



## setting up user for mysql:

To start mysql in kali:
```
service start mysql

sudo mysql -h localhost -u root # I had to use "sudo" since it was a new installation

mysql> USE mysql;
mysql> CREATE USER 'YOUR_SYSTEM_USER'@'localhost' IDENTIFIED BY 'YOUR_PASSWD';
mysql> GRANT ALL PRIVILEGES ON *.* TO 'YOUR_SYSTEM_USER'@'localhost';
mysql> UPDATE user SET plugin='unix_socket' WHERE User='YOUR_SYSTEM_USER';';
mysql> FLUSH PRIVILEGES;
mysql> exit;


sudo service mysql restart

```

## PART 8: user agents  
**using jake user agents**  
When scrapping somewebsites, they may block you  due to policy and data rights and ownership. However we can overcome this hurdle by using fake user agents.
To use fake useragents do the following:

1. using a single fake agent:
go to settings and add the following:
``USER_AGENTS = "Mozilla/5.0 (X11; Linux x86_64; rv:128.0) Gecko/20100101 Firefox/128.0"`` 

2. option 2:
In bookspider.py add a list of user agents:
get from [useragents](https://thepythonscrapyplaybook.com/scrapy-managing-user-agents/)    

```
user_agent_list = [
   'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/93.0.4577.82 Safari/537.36',
   'Mozilla/5.0 (iPhone; CPU iPhone OS 14_4_2 like Mac OS X) AppleWebKit/605.1.15 (KHTML, like Gecko) Version/14.0.3 Mobile/15E148 Safari/604.1',
   'Mozilla/4.0 (compatible; MSIE 9.0; Windows NT 6.1)',
   'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/87.0.4280.141 Safari/537.36 Edg/87.0.664.75',
   'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.102 Safari/537.36 Edge/18.18363',
]

// In any statement that has a response.follow() add the following code:
headers={"User-Agent": user_agent_list[random.randint(0, len(user_agent_list)-1)]}
```

**using scrapy api  fake headers or user agents**
Rather that using a list of user_agents,  we could use fake user agents or headers provided from  [api](https://scrapeops.io/app/headers)
Go to your middleware.py file and create a new class and import the following modules:


```

import urllib.parse import urlencode
import request
from random import randint

class ScrapeOpsFakeUserAgentMiddleware:

    @classmethod
    def from_crawler(cls, crawler):
        return cls(crawler.settings)

    def __init__(self, settings):
        self.scrapeops_api_key = settings.get('SCRAPEOPS_API_KEY')
        self.scrapeops_endpoint = settings.get('SCRAPEOPS_FAKE_USER_AGENT_ENDPOINT', 'http://headers.scrapeops.io/v1/user-agents?') 
        self.scrapeops_fake_user_agents_active = settings.get('SCRAPEOPS_FAKE_USER_AGENT_ENABLED', False)
        self.scrapeops_num_results = settings.get('SCRAPEOPS_NUM_RESULTS')
        self.headers_list = []
        self._get_user_agents_list()
        self._scrapeops_fake_user_agents_enabled()


    def _get_user_agents_list(self):
        payload = {'api_key': self.scrapeops_api_key}
        if self.scrapeops_num_results is not None:
            payload['num_results'] = self.scrapeops_num_results
        response = requests.get(self.scrapeops_endpoint, params=urlencode(payload))
        json_response = response.json()
        self.user_agents_list = json_response.get('result', [])


    def _get_random_user_agent(self):
        random_index = randint(0, len(self.user_agents_list) - 1)
        return self.user_agents_list[random_index]

    def _scrapeops_fake_user_agents_enabled(self):
        if self.scrapeops_api_key is None or self.scrapeops_api_key == '' or self.scrapeops_fake_user_agents_active == False:
            self.scrapeops_fake_user_agents_active = False
        else:
            self.scrapeops_fake_user_agents_active = True

    def process_request(self, request, spider):        
        random_user_agent = self._get_random_user_agent()
        request.headers['User-Agent'] = random_user_agent

        print("************ NEW HEADER ATTACHED *******")
        print(request.headers['User-Agent'])

```

in setting.py add the following:
```
SCRAPEOPS_API_KEY= "YOUR KEY"
SCRAPEOPS_FAKE_USER_AGENT_ENDPOINT = 'https://headers.scrapeops.io/v1/user-agents'
SCRAPEOPS_FAKE_USER_AGENT_ENABLED = True
SCRAPEOPS_NUM_RESULTS = 50 # SET NUMBER OF AGENTS YOU WANT
```


After this go to ``setting.py`` file, on DOWNLOADER_MIDDLEWARES and add the following line:
```
DOWNLOADER_MIDDLEWARES = [
   "bookscraper.pipelines.BookscraperPipeline": 300,
]
```

*For complex web scrapping use ``ROBOTSTXT_OBEY = False`` to scrap*