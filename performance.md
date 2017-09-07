PERFORMANCE
===========

![linux observability tools](imgs/linux_perf_tools_full.svg)


LINKS
-----

 * http://www.brendangregg.com/linuxperf.html
 * http://netdata.firehol.org/ ([demo](https://london.my-netdata.io/default.html))
 * https://goaccess.io/
 * https://fast.com/


TOOLS
-----

### HARDWARE

* lshw
* hwinfo


### HD

* dd
```
Comando escritura:     dd if=/dev/zero of=/dev/sdb bs=XXXX count=YYYY
Comando lectura:         dd if=/dev/sdb of=/dev/null bs=XXXX count=YYYY
```

* bonnie++
```
bonnie++ -d /mnt/test/ -n 0 -u 0 -r 2048 -s 81920 -f -b
```

* hdparam
```
hdparam -tT /dev/hda1
```

* iostat

* dstat
```
dstat -ta --top-bio
```

* pv (http://linux.die.net/man/1/pv)
```
cat file | pv -s 12345 | nc -w 1 somewhere.com 3000

cat linux-2.6.25.5.tar.bz2 | nc -q 0 ubuntu 2222
nc -lp 2222 | pv > /dev/null

tzap -r -c channels.conf "TVE-HD Pruebas(RTVE)"
cat /dev/dvb/adapter0/dvr0 | pv -r > /dev/null
```

### NET

* iperf

* ifstat

* iptraf

* lmbench:
```
./lmbench/bin/i686-pc-linux-gnu/bw_mem 256m rd 268.44 3913.68
```

* Apache HTTP server benchmarking tool (ab): https://httpd.apache.org/docs/2.4/programs/ab.html

* h2load: https://nghttp2.org/documentation/h2load.1.html

* Locus: http://locust.io/


### CPU

* geekbech: http://www.primatelabs.ca/geekbench/
* vmstat
* time
```
/usr/bin/time -v 'ffprobe 8seg.mp4'
```

* Intel® Performance Counter Monitor (PCM): https://software.intel.com/en-us/articles/intel-performance-counter-monitor


OTHER
-----

 * https://blogs.dropbox.com/tech/2017/09/optimizing-web-servers-for-high-throughput-and-low-latency/