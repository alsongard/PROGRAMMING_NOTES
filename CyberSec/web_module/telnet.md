Telnet is an application protocol or older network protocol that Telnet enables the remote access to another machine with the use of telnet client, to connect to and execute commands on a remote machine that's hosting a telnet server. The telnet client will establish a connection with the server. The client will then become a virtual terminal- allowing you to interact with the remote host. It does not encrypt data, making it vulnerable to man-in-the-middle attacks. 

To use telnet to connect to a device:
```
telnet [ip_address | host_name] port
```

To check if a port is open on the server:
```
telnet example.com portNumber
```

``telnet google.com 23``

get banner information
```
nmap --script=banner ip_address -p portNumber
```

or you can use  netcat:
``nc -nv ip_address portNumber``


To connect using ftp(file transfer protocol)
```
ftp -p ip_address
```
Once logged in/connected you can list directories|gather information about the system

To download a file, use : ``get fileName``

## SMB(Server Message Block)
protocol used for 
in windows system. SMBv1(version1) had a software vulnerability called [eternityBlue](https://www.avast.com/c-eternalblue). Click to get more information.


Nmap has several scripts such as ``smb-os-discovery.nse`` that interact with the SMB service to identify the operating system
```
nmap --script  smb-os-discovery.nse -445 IP_ADDRESS
```


The ``smbclient`` tool can be used to access/share files.
```
smbclient -N -L \\\\ip_address
```
-L : specifies we want to retreive shared files
-N : used to supress password


: reveals non-default share users  
```
smbclient \\\\10.129.42.253\\users
```
**RESULTS**:
```
139/tcp  open  netbios-ssn Samba smbd 4
445/tcp  open  netbios-ssn Samba smbd 4
2323/tcp open  telnet      Linux telnetd
8080/tcp open  http        Apache Tomcat
|_http-title: Apache Tomcat
|_http-open-proxy: Proxy might be redirecting requests
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
| smb2-time: 
|   date: 2025-04-30T23:25:54
|_  start_date: N/A
| smb2-security-mode: 
|   3:1:1: 
|_    Message signing enabled but not required
|_nbstat: NetBIOS name: GS-SVCSCAN, NetBIOS user: <unknown>, NetBIOS MAC: <unknown> (unknown)


smbclient -N -L \\\\10.129.157.112

smbclient -U bob '\\10.129.157.112\'
```



Directory/File enumeration:
After finding web hosting services on a server/machine use gobuster||nikta||ffuf to perform directory enumeration.
