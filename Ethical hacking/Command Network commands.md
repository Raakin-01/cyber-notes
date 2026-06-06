## ip a:

```
┌──(raakin㉿raakin)-[~]
└─$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 00:0c:29:a8:21:8a brd ff:ff:ff:ff:ff:ff
    inet 192.168.64.129/24 brd 192.168.64.255 scope global dynamic noprefixroute eth0
       valid_lft 1533sec preferred_lft 1533sec
    inet6 fe80::20c:29ff:fea8:218a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
                                                                                                                                                            
┌──(raakin㉿raakin)-[~]
└─$ 


```

## Ifconfig:

```
┌──(raakin㉿raakin)-[~]
└─$ ifconfig
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.64.129  netmask 255.255.255.0  broadcast 192.168.64.255
        inet6 fe80::20c:29ff:fea8:218a  prefixlen 64  scopeid 0x20<link>
        ether 00:0c:29:a8:21:8a  txqueuelen 1000  (Ethernet)
        RX packets 51  bytes 3680 (3.5 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 36  bytes 4012 (3.9 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 8  bytes 480 (480.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8  bytes 480 (480.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

                                                                                                                                                            
┌──(raakin㉿raakin)-[~]
└─$ 


```

## Iwconfig:

```
                                                                                                                                                            
┌──(raakin㉿raakin)-[~]
└─$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

                                                                                                                                                            
┌──(raakin㉿raakin)-[~]
└─$ 

```
- this is used for wireless devices 

## Ip n:

```
┌──(raakin㉿raakin)-[~]
└─$  ip n
192.168.64.2 dev eth0 lladdr 00:50:56:fe:34:a5 REACHABLE 
192.168.64.254 dev eth0 lladdr 00:50:56:e5:33:6a STALE
```

## Arp -a:

```
┌──(raakin㉿raakin)-[~]
└─$ arp -a
? (192.168.64.2) at 00:50:56:fe:34:a5 [ether] on eth0
? (192.168.64.254) at 00:50:56:e5:33:6a [ether] on eth0

```

## Ip r:

```
┌──(raakin㉿raakin)-[~]
└─$ ip r    
default via 192.168.64.2 dev eth0 proto dhcp src 192.168.64.129 metric 100 
192.168.64.0/24 dev eth0 proto kernel scope link src 192.168.64.129 metric 100 

```

## Route:

```
┌──(raakin㉿raakin)-[~]
└─$ route       
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.168.64.2    0.0.0.0         UG    100    0        0 eth0
192.168.64.0    0.0.0.0         255.255.255.0   U     100    0        0 eth0
```

## Ping:

```
┌──(raakin㉿raakin)-[~]
└─$ ping 192.168.64.2
PING 192.168.64.2 (192.168.64.2) 56(84) bytes of data.
64 bytes from 192.168.64.2: icmp_seq=1 ttl=128 time=87.6 ms
64 bytes from 192.168.64.2: icmp_seq=2 ttl=128 time=0.393 ms
64 bytes from 192.168.64.2: icmp_seq=3 ttl=128 time=0.493 ms
64 bytes from 192.168.64.2: icmp_seq=4 ttl=128 time=0.395 ms
64 bytes from 192.168.64.2: icmp_seq=5 ttl=128 time=0.456 ms
 64 bytes from 192.168.64.2: icmp_seq=6 ttl=128 time=0.413 ms
64 bytes from 192.168.64.2: icmp_seq=7 ttl=128 time=1.35 ms
64 bytes from 192.168.64.2: icmp_seq=8 ttl=128 time=0.297 ms
64 bytes from 192.168.64.2: icmp_seq=9 ttl=128 time=0.498 ms
64 bytes from 192.168.64.2: icmp_seq=10 ttl=128 time=0.949 ms
64 bytes from 192.168.64.2: icmp_seq=11 ttl=128 time=0.477 ms
64 bytes from 192.168.64.2: icmp_seq=12 ttl=128 time=0.303 ms
64 bytes from 192.168.64.2: icmp_seq=13 ttl=128 time=0.464 ms
^C
--- 192.168.64.2 ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12183ms
rtt min/avg/max/mdev = 0.297/7.237/87.597/23.199 ms
```

```
┌──(raakin㉿raakin)-[~]
└─$ ping 192.168.64.3
PING 192.168.64.3 (192.168.64.3) 56(84) bytes of data.
From 192.168.64.129 icmp_seq=1 Destination Host Unreachable
From 192.168.64.129 icmp_seq=2 Destination Host Unreachable
From 192.168.64.129 icmp_seq=3 Destination Host Unreachable
From 192.168.64.129 icmp_seq=4 Destination Host Unreachable
From 192.168.64.129 icmp_seq=5 Destination Host Unreachable
From 192.168.64.129 icmp_seq=6 Destination Host Unreachable
From 192.168.64.129 icmp_seq=7 Destination Host Unreachable
From 192.168.64.129 icmp_seq=8 Destination Host Unreachable
From 192.168.64.129 icmp_seq=9 Destination Host Unreachable
^C
--- 192.168.64.3 ping statistics ---
10 packets transmitted, 0 received, +9 errors, 100% packet loss, time 9225ms
pipe 3

```

- This can happen if the icmp is disabled.
- this can also happen if the host ip is not present in the network.
