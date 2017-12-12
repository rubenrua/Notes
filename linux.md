# LINUX


## Tips:

### Execute xargs in parallel
```sh
find src -type f -name "*.php" -print0 | xargs -0 -n1 -P8 php -l
printf %s\\n {0..99} | xargs -n 1 -P 8 script-to-run.sh input/ output/
cat commands.sh | xargs -P4  -I "{}" sh -c "{}"
```

https://stackoverflow.com/questions/28357997/running-programs-in-parallel-using-xargs
Note: See also `parallel`.

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


### Convert addresses into file names and line numbers with addr2line
```
php-fpm[6048]: segfault at 10 ip 00007f46db77a8fb sp 00007fffa155e2d0 error 4 in xcache.so[7f46db763000+23000]
```
```sh
# 00007f46db77a8fb - 7f46db763000 = 178FB
addr2line -e /usr/lib64/20131226/xcache.so 178FB
#out /root/source/xcache-3.2.0/mod_cacher/xc_cacher.c:778
```

https://ablagoev.github.io/linux/adventures/commands/2017/02/19/adventures-in-usr-bin.html#addr2line


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
Other in GO [croncape](https://github.com/sensiocloud/croncape) [jobber](https://github.com/dshearer/jobber)


### Xephyr: Pseudo-X server
```sh
Xephyr -ac -screen 1280x1024 -br -reset -terminate 2> /dev/null :3 &
DISPLAY=:3.0 gnome-wm &
DISPLAY=:3.0 ssh -X jennie@desktop xterm
```

http://jeffskinnerbox.me/posts/2014/Apr/29/howto-using-xephyr-to-create-a-new-display-in-a-window/


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


### Debian: generate deb package.

Simple: use Effing package management (fpm)
```
fpm -s dir -t deb \
  --deb-no-default-config-files \
  --config-files "etc/galicasterpro/conf.ini" \
  -d python \
  -d python-pip \
  -d "package > 1.0" \
  --after-install $OLD_PWD"/postinst" \
  --before-install $OLD_PWD"/preinst" \
  --url "http://rubenrua.es" \
  --vendor "My Company" \
  -m "rubenrua <ruben.rua@internet.es>" \
  --description "My descriptn" \
  -n name -v $VERSION_NUMBER .
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

~C (to open the ssh command prompt) and type a command (e.g.) “-L 80:localhost:8000”
```
See: http://www.vicente-navarro.com/blog/2009/05/24/creando-tuneles-tcpip-port-forwarding-con-ssh-los-8-escenarios-posibles-usando-openssh/

See also: https://ngrok.com and [socks](https://www.linode.com/docs/networking/ssh/setting-up-an-ssh-tunnel-with-your-linode-for-safe-browsing)
## LINKS:

* https://github.com/0xAX/linux-insides
* http://wiki.openvz.org/Package_managers
* http://www.vicente-navarro.com/blog/2009/06/13/reenvio-dinamico-de-puertos-montar-un-servidor-socks-con-ssh/
*
