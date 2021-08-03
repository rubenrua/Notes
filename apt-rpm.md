Main
==========

more:
* https://en.wikipedia.org/wiki/Package_manager
* https://wiki.archlinux.org/index.php/Pacman/Rosetta

* List file contents of a pkg file
```
dpkg -c package.deb
rpm -qlp package.rpm
```
or
```
less package.{deb|rpm}
/usr/bin/lesspipe package.{deb|rpm}
```


* Search package of a installed file
```
dpkg -S file
rpm -qf file
```

* List installed pkgs
```
dpkg -l
rpm -qa
```

* List files of an installed pkg
```
dpkg -L package
rpm -ql package
```

* Show info of a pkg
```
apt-cache show yasm
rpm -qi package
```

* Show info of a pkg file
```
dpkg -I package.deb ????
rpm -qpi package.rpm
```
or
```
less package.{deb|rpm}
```


* Build deps
```
apt-get build-dep pkg
yum-builddep pkg
```

Extract
==========
```
ar x ffmpeg_4.2.1-2_armhf.deb
rpm2cpio ./packagecloud-test-1.1-1.x86_64.rpm | cpio -idmv
```


Other
==========


apt-cache policy yasm


AR
==========
Create library "libctest.a": `ar -cvq libctest.a ctest1.o ctest2.o`
List files in library: `ar -t libctest.a`



-----

From https://askubuntu.com/questions/18654/how-to-prevent-updating-of-a-specific-package
sudo apt-mark hold <package-name>
sudo apt-mark unhold <package-name>
sudo apt-mark showhold


sudo yum install 'dnf-command(versionlock)'
sudo yum versionlock add  <package-name>
