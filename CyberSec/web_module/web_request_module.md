**curl command**

Client URL: the command is used for sending http request to a server

``curl website_url`` : this returns the address of the server== which is the server type running, and even the port
``curl inlanefreight.com``

to get more help we can use the command:
``curl --help all`` | ``curl -h category`` | man curl


https / http
https encrypts data any information accessed between the sender and receiver cannot be accessed. 


``curl -k  http://inlanefreight.com`` : use this command to enfoce Client url to get the information from the given url

there are different type of headers, namely:
- general headers: date and connection
- entity headers : content-type, media type, boundary, content-length, content-encoding
- request headers : host, user-agent, referer, accepts, cookie, authorization
- response headers: server(type,model,version), set-cookie, www-authenticate
- security headers: strict-transport-security(https), referer-policy(no disclosure of specific domain), content-security-policy(execute jsbased on same website)
 
``curl -I url`` : displays the response header(from the server)
``curl -i url`` : displays both header and html body

Client url also allows us to set request headers to our servers:
``curl url -H HEADER``
``curl url -A 'Mozilla/5.0' ``: this is used to set the User-Agent that is the browser information


if to access a page , one is required to give a password, we use ``curl -u userName:userPasswd http://ipaddress/url:portNumber``
`curl -i  -v -u userName:userPasswd http://ipaddress/url:portNumber``: 
result:
```
└─$ curl -I -v -u admin:admin http://83.136.255.180:52821
*   Trying 83.136.255.180:52821...
* Connected to 83.136.255.180 (83.136.255.180) port 52821
* using HTTP/1.x
* Server auth using Basic with user 'admin'
> HEAD / HTTP/1.1
> Host: 83.136.255.180:52821
> Authorization: Basic YWRtaW46YWRtaW4=
> User-Agent: curl/8.12.1
> Accept: */*
> 
* Request completely sent off
< HTTP/1.1 200 OK
HTTP/1.1 200 OK
< Date: Wed, 26 Feb 2025 18:02:03 GMT
Date: Wed, 26 Feb 2025 18:02:03 GMT
< Server: Apache/2.4.41 (Ubuntu)
Server: Apache/2.4.41 (Ubuntu)
< Cache-Control: no-cache, must-revalidate, max-age=0
Cache-Control: no-cache, must-revalidate, max-age=0
< Content-Type: text/html; charset=UTF-8
Content-Type: text/html; charset=UTF-8
< 

```
From the above we can see the Authorization: Basic ....
this is a base64 code,  if we were using JWT, we could see a longer authorization code in Bearer

WEB SOLUTION
```
curl -v -u admin:admin  'http://83.136.255.180:52821/search.php?search=flag' -H 'Authorization: Basic YWRtaW46YWRtaW4=' 
```

## POST
to use curl to send a post request we use:
```
curl -X POST -d "username=admin&password=admin" http://83.136.249.46:53500/index.php
```
onced login, our browsers should have received a cookie for persistent authentication(we do not need to relogin every time). To view this in ``curl`` we use the -i and -v flag
``curl -X POST -d 'username=admin&password=admin' 83.136.249.46:53500/index.php -i  `` or ``curl -X POST -d 'username=admin&password=admin' 83.136.249.46:53500/index.php -v``
Looking at this output, look at the set-cookie flag: Example:
```
Note: Unnecessary use of -X or --request, POST is already inferred.
*   Trying 83.136.249.46:53500...
* Connected to 83.136.249.46 (83.136.249.46) port 53500
* using HTTP/1.x
> POST /index.php HTTP/1.1
> Host: 83.136.249.46:53500
> User-Agent: curl/8.12.1
> Accept: */*
> Content-Length: 29
> Content-Type: application/x-www-form-urlencoded
> 
* upload completely sent off: 29 bytes
< HTTP/1.1 200 OK
< Date: Mon, 17 Mar 2025 09:13:45 GMT
< Server: Apache/2.4.41 (Ubuntu)
< Set-Cookie: PHPSESSID=720easvm66dvfcjpp393cq50ll; path=/  [THIS IS THE COOKIE]
< Expires: Thu, 19 Nov 1981 08:52:00 GMT
< Cache-Control: no-store, no-cache, must-revalidate
< Pragma: no-cache
< Vary: Accept-Encoding
< Content-Length: 1554
< Content-Type: text/html; charset=UTF-8
< 
```
With the  authenticated cookie_value, we can use this to access the web page without the need to provide our user credentials by using the ``-b`` flag of ``curl`` command.
```
curl -b "PHPSESSID=720easvm66dvfcjpp393cq50ll" 83.136.249.46:53500/index.php
```
Another option is to pass the PHP_SESSION cookie as a header when sending the request
```
culr -H "Cookie: PHPSESSID=720easvm66dvfcjpp393cq50ll" 83.136.249.46:53500/index.php
```
Also by using the storage in devtools, delete the current session of the page, add the following exactly with what you got from the ``curl -X POST -d 'username:admin&password:admin' -i or -v``
in dev tools add:
session_name=PHPSESSID
session_value=720easvm66dvfcjpp393cq50ll


new_session_cookie =  Set-Cookie: PHPSESSID=34p7eu07pk6d7i5g10ic36i0pv;

**using curl to search directly**
```
curl -X POST -d '{"search":"london"}' -b "PHPSESSID=34p7eu07pk6d7i5g10ic36i0pv"  -H "Content-type: application/json"  $htb_address/search.php
```

To get the flag: 
```
curl -X POST -d '{"search":"flag"}' -b 'PHPSESSID=34p7eu07pk6d7i5g10ic36i0pv' -H 'Content-Type: application/json'  $htb_address/search.php
```

## WORKING WITH API
api can be used to perform the following operations : put(update), post(add data), delete(remove data) and get(view data) from the database.

**GET**
```
curl -X PUT http://94.237.54.190:35912/api.php/city/london

# view data
curl -X GET http://94.237.54.190:35912/api.php/city (returns all city in city table)
```
use the ``-jq`` flag to have the data in JSON format and ``-s`` flag for any extra details to be supressed

**POST**
To add data to the database we use the POST method
```
curl -X POST http://94.237.54.190:35912/api.php/city -d'{"city_name":"HBT_City", "country_name":"HBT"}' -H 'Content-Type: application/json'
```

**UPDATE**
to update data on the database, we can either use the PUT or the PATCH http method. the difference is that the PATCH http method is used to partially update an entry in the databs while the PUT method is used to update the entire entry
```
curl -X PUT http://ip_address:port_number/api.php/city/mexico -d '{"city_name":"nairobi", "country_name":"Kenya"}' -H 'Content-Type:application/json'
```
In some apis, if the is no entry and we are updating the data is automatically added to the database(like it performs POST)

**DELETE**
the delete method is used to delete data from the table
```
curl -X DELETE http://ip_address:port_number/api.php/city/mexico 

curl -X GET http://ip_address:port_number/api.php/city/mexico return []
```
