To list cronjobs
crontab -l

Setup cronjob
``crontab -e``

A cronjob consist of 6 fields namely:

SYNTAX : **``m h dom mon dow command``**
```
m = minute
h = hour(24hr system)
dom = day of month (0 - 31 / depending on the month)
mon = month
dow = day of week
command = terminal executable command
```

``5 * * * * echo "i wish i was more than just someone you walk by" >> myFile.txt``
Asterisk means any:

``@hourly echo "helolo world" >> world.txt``
``@reboot command``
command = echo "Welcome back sir"


crontab -u userName -l  : list cronjobs for the given user
crontab -u userName -e : create crontab


sudo cat /var/log/syslogs | grep "CRON"

crontab -u root -e 
* * * * * date >> myData.txt

Example:
Runs everymorning at 3 AM:
```
0 3 * * *  /usr/local/bin/website_backup.sh
```

[crontab generator org](https://crontab-generator.org/)
