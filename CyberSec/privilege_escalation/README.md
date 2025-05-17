# SHELL TYPES
3 types of shell:  
- reverse shell in a reverse shell connects back to our system(attackers machine) &  provides control through reverse connectiono
- web shell : Communicates through a web server, accepts our commands through HTTP parameters, executes them, and prints back the output.
- bind shell : waits for the attacker(shell) to connect and give us control

After gaining access to a compromised host:
revesrse shell(attacker is listening & compromised host is sending request)
bind shell (attacker connects to the reverse shel)

one can use python to upgrade the terminal:
```
python -c 'import pty; pty.spawn("/bin/bash")'
```

after accessing/gaining access to a user's/compromised device, use ``echo $TERM`` or ``stty size`` : output rows and column.
copy paste the output to your reverse shell/bind shell to have full control

web shell:  
 A Web Shell is typically a web script, i.e., PHP or ASPX, that accepts our command through HTTP request parameters such as GET or POST request parameters, executes our command, and prints its output back on the web page.
 
 
 

# PRIVILEGE ESCALATION
after gaining access to a compromised machine, usually you're not given complete access but limited privileges. Privilege escalation escalates your privileges to root/admin.

To escalate attackers privilege, we enumerate the compromised host for any potential vulnerabilitiesthat can lead in achieving a higher privilege level.  
The following are checklists and cheat sheets online that have a collection of checks we can run and the commands to run these checks.
- [hackTricks](https://book.hacktricks.xyz/)
- PayLoadsAllTheThings(https://github.com/swisskyrepo/PayloadsAllTheThings)

### **Enumeration Scripts:**
a script to go through the report and look for any weaknesses. We can run many scripts to automatically enumerate the server by running common commands that return any interesting findings. 


common linux enumeration scripts:
- [LinEnum](https://github.com/rebootuser/LinEnum.git)
- [LinuxPrivChecker](https://github.com/sleventyeleven/linuxprivchecker)

common windows enumeration scripts:
- [Seatbelt](https://github.com/GhostPack/Seatbelt)
- [JAWS](https://github.com/411Hall/JAWS)

another tools is : [ Privilege Escalation Awesome Scripts SUITE (PEASS)](https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite)   
this scripts when run create a lot of 'noise' which may trigger anti-virus software or security monitoring software. 

### **Kernel Exploits**
by checking the OS(operating system) version, we could check if it has any vulnerabilities. Users/Machines running old O.S or applications which are not maintained or serviced may have vulnerabilities.   
kernel exploits can impact the entire system/cause system instability and best to try them on lab environment. 

### **vulnerable software**
another way is to check for vulnerable software in the compromised host. In linux use : ``dpkg -l`` while in windows check the ``C:\Program Files``


### **User Privileges(check)**
Another common thing is to check the user privileges of the compromised host/machine. Which commands can he/she run on the system as an admin/root. 

common ways to explot a certain user:
- Sudo
- SUID
- Windows Token Privileges

To check sudo privileges of a user:
```
sudo -l
```
Once a command has been found that can run with ``SUDO`` without a passwd, we check how can these command be exploited to give privilege escalation
if such an occurence/scenario occurs, use:  
- [GTFObins](https://gtfobins.github.io/): contains a list of commands and how they can be exploited through sudo.
- [LOLBAS](https://lolbas-project.github.io/#): a list of Windows applications which we may be able to leverage to perform certain functions, like downloading files or executing commands in the context of a privileged user.


### **Scheduled Tasks**
Another way to achieve privilege escalation is to use scheduled task(windows) or cronjobs(linux).   
Steps:  
- Add new scheduled tasks/cron jobs
- Trick them to execute a malicious software

if an attacker has write permission, we could add the cronjob in the given folders:
- /etc/crontab
- /etc/cron.d
- /var/spool/cron/crontabs/root

### **Exposed Credentials**
in exposed credentials we look into files we can read(read permissioN) that may contain exposed credantials. This is common with configuration files, log files and user history files(bash history|zsh history) and PSReadlines in Windows.
The enumeration scripts usually perform this to check for any passwords or usernames.   
if user credentails are acquired, you can check against password reuse(as some users might use the same passwords for different service/authentication)


### **SSH keys**

if we have access to the files of the user, we can read the private key for the given user on:
directory: ``/home/user/.ssh/id_rsa`` or ``/root/.ssh/id_rsa``

if any of the files are found, which contain the private key for the compromised user, you could copy this content and use : ``-i`` flag to log in with it.

in your machine
```
vim id_rsa (copy & paste content)
chmod 600 id_rsa 
ssh root@ip_address -i id_rsa
```

``ssh username@ip_address`` 

changing the permission for the user that is:   
rw- --- ---  || user group others   
make the files permission to be more restrictive. if ssh keys have lax permission(may be read by other people, the ssh server wouold prevent them from working)


At anytime we escalate our priveleges and have write permission to the .ssh directory, we can place our public key at the users ssh directory E.g /home/user/.ssh/authorized_keys

To create a new key use:
``ssh-keygen -f `` the ``-f`` flag is used to specify the output file.

this will generate 2 files a file_key and file_key.pub.
Copy the contents of key.pub to the compromised machine and use file_key with the ``ssh  user@ip_address -i flag`` to connect.
To copy the contents:   
``` reverse/compromised shell 
echo 'key.pub contents' >> /root/.ssh/authorized_keys
```
To connect: ``ssh user@ip_address -i file_key``.


hack_the_box lab: privilege escalation
explaining the following output of : 
``sudo -l``:   
(user2 : user2) NOPASSWD: /bin/bash
(targetUser:targetGroup) can run command bin/bash as sudo with no password request

```
sudo -u user /bin/bash
```


for task 2:   
**Important notes**  
while looking for directories that may contain information or files that contain information always check the permission.
After gaining access to .ssh folder which has read permission for user2, copy the file. Also check to who is the owner of the file(important when connecting to the target/compromised machine). === root 
copy the private key to your local machine and:
```
ssh root@ip_address -p portName -i file_key
```
