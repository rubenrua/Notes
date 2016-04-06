TESTBECH
========

![linux observability tools](imgs/linux_observability_tools.png)


LINKS
-----

 * http://www.brendangregg.com/linuxperf.html
 * http://www.intel.com/software/pcm
 * http://netdata.firehol.org/


TOOLS
-----

 * HARDWARE

  * lshw
  * hwinfo


 * HD

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


 * NET

  * iperf

  * ifstat

  * iptraf

  * lmbench:
```  
./lmbench/bin/i686-pc-linux-gnu/bw_mem 256m rd 268.44 3913.68
```  


 * CPU

  * geekbech: http://www.primatelabs.ca/geekbench/
  * vmstat

