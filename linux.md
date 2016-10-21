# LINUX


## Tips:

### Trace the Execution
```sh
#Trace the Execution of an Executable
strace ls
#Trace a Specific System Calls in an Executable Using Option -e
strace -e trace=open,read ls /home
#Save the Trace Execution to a File Using Option -o
strace -o output.txt ls
#Execute Strace on a Running Linux Process Using Option -p
strace -p 1725 -o firefox_trace.txt
#Print Timestamp for Each Trace Output Line Using Option -t
strace -t -e open ls /home
#Print Relative Time for System Calls Using Option -r
strace -r ls
#Generate Statistics Report of System Calls Using Option -c
strace -c ls /home
#Resolve every fd into its name, and every socket fd into its address line
strace -yy wget https://cdn0.bodas.net/usuarios/fotos/7/1/9/0/sfxb_376425.jpg
```

http://www.thegeekstuff.com/2011/11/strace-examples/

### Show info about a exec
```sh
#Shared library dependencies
ldd /bin/ls

#Disassemble
objdump -d /bin/ls

#Print the strings of printable characters in files
strings /bin/ls
```

https://www.cs.swarthmore.edu/~newhall/unixhelp/compilecycle.html


### Exec as root without sudo
```sh
pkexec emacs /etc/sudoers
```

http://manpages.ubuntu.com/manpages/precise/en/man1/pkexec.1.html


###  Flock for Cron jobs (and trap)
```sh
flock -n /tmp/path.to.lockfile -c command with args
```

http://www.elevatedcode.com/2013/05/07/flock-for-cron-jobs.html
http://www.computerhope.com/unix/utrap.htm

###  VNC server
```sh
sudo apt-get -y install x11vnc
x11vnc -display :0
```

###  Ubuntu: Recompile package from source
```
apt-get install devscripts

apt-get source XXXXX
cd XXXXXX
sudo apt-get build-dep XXXXXX
dpkg-buildpackage -b -uc
```

###  SSH: Avoid disconnection timeout

```
cat ~/.ssh/config
Host *
    ServerAliveInterval 120
    ServerAliveCountMax 3
```

###  Intercept stdout and stderr of a process

Since I'm not allowed to edit Jauco's answer, I'll give the full answer that worked for me (Russell's page relies on unguaranteed behaviour that, if you close fd 1 for stdout, the next creat call will open fd 1.

So, run a simple endless script like this:

```python
import time while True: print 'test' time.sleep(1)
```
Save it to test.py, run with

```sh
python test.py
#Get the pid:

ps auxw | grep test.py
#Now, attach gdb:

gdb -p (pid)
#and do the fd magic:

(gdb) call creat("/tmp/stdout", 0600)
$1 = 3
(gdb) call dup2(3, 1)
$2 = 1
```

Now you can tail /tmp/stdout and see the output that used to go to stdout.

http://stackoverflow.com/questions/249703/how-can-a-process-intercept-stdout-and-stderr-of-another-process-on-linux

###  HTTP Server easy in python

```
$ python -m SimpleHTTPServer
```
```
$ python3 -m http.server.
```

### Share or access to local ports

```
ssh -L MY_PORT:HOST_IN_LOCAL_NET:LOCAL_PORT  root@proxy.com.gal
# Example:
ssh -L 2222:192.168.1.38:22 -L 8080:192.168.1.38:80 root@proxy.com.gal
ssh -p 2222 localhost && wget localhost:8080
```
See: http://www.vicente-navarro.com/blog/2009/05/24/creando-tuneles-tcpip-port-forwarding-con-ssh-los-8-escenarios-posibles-usando-openssh/

See also: https://ngrok.com

## LINKS:

* https://github.com/0xAX/linux-insides
* http://wiki.openvz.org/Package_managers
* http://www.vicente-navarro.com/blog/2009/06/13/reenvio-dinamico-de-puertos-montar-un-servidor-socks-con-ssh/
* 
