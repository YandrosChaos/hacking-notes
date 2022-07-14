# SERVICE SCANNING
A service is an application running on a computer that preforms some useful functons for other users or computers. The machines which host those 'services' are the 'servers'. 

## NMAP (network mapper)
This is the most basic scan. Nmap will only scan the 1000 most common ports by default.

```bash
nmap [IP]
```

### HEADINGS
- PORT -> Info about ports. By default, will conduct a TCP scan unless specifically requested to perform UPD scan.
- STATE -> Confirms that the ports are open.
- SERVICE -> The service's name is typically mapped to the specific port number. The default scan will not tell us what is listening on that port.

### PARAMS
- -sC -> Obtain more detailed information
- -sV -> Perform version scan
- -p- -> Scan all TCP ports

### SCRIPTS
> locate scripts/citrix
> nmap --script <script name> -p <port> <host>

## ATTACKING NETWORK SERVICES
### BANNER GRABBING
Using nmap:
> namp -sV --script=banner <target>
> nmap -sV --script=banner -p21 <target>/<port>

Using nc version of Netcat:
> nc -nv <IP> <PORT>

### FTP
> nmap -sC -sV -p21 <IP>
> ftp -p <IP>

### SMB (server message block)
Prevalent protocol on Windows Machines that provides many vectors for vertical and lateral movement. Some SMB versions may be vulnerable to RCE exploits such as EternalBlue. Nmap has many scripts for enumerating SMB. such as smb-os-discovery.nse.

> nmap --script smb-os-discovery.nse -p<PORT> <IP>

### SHARES
SBM allows users and administrators to share folders and make them accessible remotely by other users. A tool that can enumerate and interact with SBM shares is smbclient.
- -L -> Flag that specifies that we want to retrieve a list of available shares on remote host
- -N -> suppressed the password prompt
- -U -> Username

> smbclient -U <username> \\\\<IP>\\<PATH>

### SNMP
Provide info and statistics about a router or device.

> snmpwalk -v 2c -c public <IP> <NUMBER>

A tool such as onesyxtyone can be used to brute force the community string names using a dictionary file of common community string.

> onesixtyone -c <DICTIONARY TXT> <IP>
