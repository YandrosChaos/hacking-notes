# PRIVILEGE ESCALATION

- [Hack Tricks](https://book.hacktricks.xyz/welcome/readme)
- [Payload All The Things](https://github.com/swisskyrepo/PayloadsAllTheThings)

## Enumeration Scripts
Many of the above commands may be automatically run with a script to go through the report and look for any weaknesses. Some common Linux enumeration scripts include LinEnum and linuxprivhacker. About windows we have Seatbelt and JAWS.

Another tool is the PEASS (Privilege Escalation Awesome Scripts SUITE), which includes Linux and Windows.'

Note that these scripts run many commands known for identifying vulnerabilities and create a lot of 'noise'  that may trgger anti-virus software or security monitoring software.

## KERNEL XPLOITS
Whenever we encounter a server running an old OS, we should start by looking for potential kernel vulnerabilities that may exist.

## VULNERABLE SOFTWARE
We should look for public exploits for any installed software, especially if any older versiions are in use, containing unpatched vulnerabilities.

## USER PRIVILEGIES
- Sudo
- SUID
- Windows Token Privileges

## SCHEDULED TASKS
There are methods to have scripts run at specific intervals to carry out task. There are two ways to take advantage of scheduled tasks (Windows) or cron jobs (Linux) to escale our privilegies:
- Add new scheduled tasks/cron jobs
- Trick them to execute a malicious software

## EXPOSED CREDENTIALS
Next, we can look for files we can read and see if they contain any exposed credentials. This is very common with config files, log files and user history files ( like bash history in linux or PSReadLine in Windows ).

## SSH KEYS
If we have read access over the .ssh directory for a specific user, we may read their private ssh keys and use it to log in to the server. 
