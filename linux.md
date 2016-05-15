LINUX
=====


Tips:
-----

* Trace the Execution

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
```

http://www.thegeekstuff.com/2011/11/strace-examples/

* Exec as root without sudo
```sh
pkexec emacs /etc/sudoers
```

http://manpages.ubuntu.com/manpages/precise/en/man1/pkexec.1.html


* Flock for Cron jobs
```sh
flock -n /tmp/path.to.lockfile -c command with args
```

http://www.elevatedcode.com/2013/05/07/flock-for-cron-jobs.html

* VNC server
```sh
sudo apt-get -y install x11vnc
x11vnc -display :0
```

* Ubuntu: Recompile package from source
```
apt-get install devscripts

apt-get source XXXXX
cd XXXXXX
sudo apt-get build-dep XXXXXX
dpkg-buildpackage -b -uc
```

* SSH: Avoid disconnection timeout

```
cat ~/.ssh/config
Host *
    ServerAliveInterval 120
    ServerAliveCountMax 3
```

* Intercept stdout and stderr of a process

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

* HTTP Server easy in python

```
$ python -m SimpleHTTPServer
```
```
$ python3 -m http.server.
```


LINKS
-----

* http://wiki.openvz.org/Package_managers
* http://www.vicente-navarro.com/blog/2009/06/13/reenvio-dinamico-de-puertos-montar-un-servidor-socks-con-ssh/
* http://www.vicente-navarro.com/blog/2009/05/24/creando-tuneles-tcpip-port-forwarding-con-ssh-los-8-escenarios-posibles-usando-openssh/
