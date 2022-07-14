# WEB ENUMERATION
## GOBUSTER
We can use tools such as ffuf or GoBuster to perform this directory enumeration.

### Directory/File Enumeration
GoBuster allows for performing DNS, vhost and directory brute-forcing. It has additional functionality such as enumeration of public AWS S3 buckets. Run a simple scan:

> gobuster dir -u http://<IP>/ -w /usr/share/dirb/wordlist/common.txt

### DNS Subdomain Enumeration
There also may be essential resources hosted on subdomains
Useful lists for fuzzing and exploitation:

> git clone https://github.com/danielmiessler/SecLists
> sudo apt install seclists -y

> gobuster dns -d <URL> -W /usr/share/SecLists/Discovery/DNS/namelist.txt

## WEB ENUMERATION TIPS
### Banner Grabbing / Web Server Headers
We can use cURL to retrieve server header info from the commandline.

> curl -IL <URL>

Another handly tool is EyeWitness. It can be used 4 take screenshots of target webapp, fingerprint them, and identify possible default credentials.

### Whatweb 
Extract the version of web servers, supporting frameworks and apps using whatweb.

> whatweb <IP>

### Certificates
Viewing the certificate reveals the details below.

### Robots.txt
This is a file whose purpose is to instruct search engine web crawlers such as Googlebot which resources can and cannot be accessed for indexing. 

### Source Code
