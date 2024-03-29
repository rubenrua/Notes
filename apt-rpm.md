Main
==========

more:
* https://en.wikipedia.org/wiki/Package_manager
* https://wiki.archlinux.org/index.php/Pacman/Rosetta

* List file contents of a pkg file
```
dpkg -c package.deb
rpm -qlp package.rpm
pacman -Qpl
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
pacman -Qo file
```

* List installed pkgs
```
dpkg -l
rpm -qa
pacman -Q
```

* List files of an installed pkg
```
dpkg -L package
rpm -ql package
pacman -Ql package
```

* Show info of a installe pkg
```
apt-cache show package
rpm -qi package
pacman -Qii package
```

* Show info of a remote pkg
```
apt-cache show package
dnf info package
pacman -Sii package
```

* Show info of a pkg file
```
dpkg -I package.deb ????
rpm -qpi package.rpm
pacman -Qp
```
or
```
less package.{deb|rpm}
```

* Download a package
```
apt download gstreamer1.0-tools
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
dpkg -x ffmpeg_4.2.1-2_armhf.deb

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




