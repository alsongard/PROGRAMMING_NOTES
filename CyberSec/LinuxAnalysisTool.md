# Linux Process Analysis Tools

# Description

# Features

* ## Top Command
* ## Cronjobs
* ## Systemctl command

## top Command
the top command is used to display the running process in the terminal and the output displayed is changing with real-time process in Linux. The top command diplays the PID(Processor Identification Number), User, C.P.U and Memory Usage , the time and command name or program name.

## systemctl command
the ``systemctl`` command is used for 
to list services that are restarted by the system use the following command
``systemctl list-unit-files | grep "enabled" | less``

## Malicious serives or processes
if a process is identified as malicious one could use the ``kill PID `` to terminate the process. If the process restart itself use the ``systemctl list-unit-files | grep "enabled" | less `` to view which service name restarts the process and then disable using the ``systemctl disable service_name``.
To ensure that the process is eradicated from the system use the command ``systemctl status service_name`` to check the process file and service file directory and remove them.

## cronjobs
cronjobs is used to automate tasks for a user. To use cronjobs use the command ``crontab -l`` which displays a a detailed explanation of how to use.