TCPDUMP
=======

Commands
--------

* Capture packets from a particular interface eth0
```
tcpdump -i eth0 
```

* Capture only 100 packets    
```
tcpdump -c 100
```

* Display captured packets in ASCII   
```
tcpdump -A
```
* Display captured packets in HEX and ASCII   
```
tcpdump -XX
```
* Capture packet data, writing it into into a file    
```
tcpdump -w saved.pcap
```
* Read back saved packet data from a file 
```
tcpdump -r saved.pcap
```

* Capture only packets longer/smaller than 1024 bytes tcpdump greater 1024
```
tcpdump less 1024  
```

* Capture only ICMP, UDP or TCP packets 
```
tcpdump ip proto \\icmp
tcpdump udp (tcpdump ip proto \\udp)
tcpdump tcp
```

* Capture only packets going to/from a particular port
```
tcpdump port 22
```

* Capture packets for a particular destination IP and port
```
tcpdump dst 54.165.81.189 and port 6666 
```

* Capture web trafic
```
tcpdump -n -s 65535 -A -p port 80
```

Links
-----

 * man tcpdump (RTFM)
 * https://sysdig.com/blog/linux-troubleshooting-cheatsheet/
 * http://rm-rf.es/tcpdump-ejemplos/
 * http://jvns.ca/blog/2016/03/16/tcpdump-is-amazing/