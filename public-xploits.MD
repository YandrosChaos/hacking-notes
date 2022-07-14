# PUBLIC XPLOITS
## FIND PUBLIC EXPLOITS
A tool for this purpose is searchsploit. We can use online exploit database to search vulnerabilities, like Exploit DB, Rapid7 DB or Vulnerability Lab.

> sudo apt install exploitdb -y
> searchsploit openssh 7.2

## METASPLOIT PRIMER
- Built-in exploits for many public vulnerabilities
- Easy way to use these exploits
- Run reconnaissance script to enumerate remote hosts and compromised targets
- Verification scripts to test the existence of a vulnerability without actually compromising the targets
- Many post-exploitation and pivoting tools

> msfconsole
> search exploit <exploit name>
> use <fullname>

Before we can run the exploit, we need to configure its options:
> show options

Any option with Required set to YES needs to be set 4 the exploit. We can set them by the next way:
> set <OPTION NAME> <OPTION VALUE>

Before running the script, we can check to ensure the server is vulnerable:
> check

FINALLY:
> run/exploit

