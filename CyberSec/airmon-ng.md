# Description
airmon-ng is a script that is used for brute forcing into networks. 
Official tool that is used to enable monitor mode on wireless interface. Used to kill network managers, change from monitor mode to manager mode and entering the command ``airmon-ng`` with no options will display  a list of interfaces. 
In my Example :
```
sudo airmon-ng      

PHY     Interface       Driver          Chipset

phy0    wlan0           iwlwifi         Intel Corporation Wireless 7265 (rev 59)

```

## Syntax | Usage
```
airmon-ng <start|stop> <interface> [channel] 
airmon-ng check
airmon-ng check kill 
airmon-ng start wlan0
airmon-ng stop wlan0mon
```
After exiting monitor mode, restart the network manager by using the command, 
```
service network-manager start
```

## Capturing packets
airmon-ng has a suite of packages and one which is used to capture packets is :
[[airodump-ng]]