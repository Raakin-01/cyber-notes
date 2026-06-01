
**==IP Addresses **==
An IP address serves two principal functions: it identifies the host, or more specifically, its network interface. "Network interface controller", and it provides the location of the host in the network, and thus, the capability of establishing a path to that host. Its role has been characterized as follows: "A name indicates what we seek. An address indicates where it is. A route indicates how to get there." The header" of each IP packet "Network packet") contains the IP address of the sending host and that of the destination host.

**IPV4:**
A 32-bit IP address is broken down into four sections of 8 bits each (called octets). 
For human convenience, these binary numbers are written in "dotted-decimal" format                    (e.g., (192.168.1.1)).
Here is how a 32-bit IP address breaks down:
- **Total Size:** \(32\) bits (or \(4\) bytes).
- **Octets:** \(4\) sections of \(8\) bits each.
- **Possible Combinations:** \(2^{32}\) (which equals exactly \(4,294,967,296\) unique addresses).
- **Usage:** Used to identify devices (like phones, computers, and servers) on a network.

**IPV6:**
Because the older **IPv4** addresses (the ones with four numbers separated by dots) are running out, newer devices use IPv6, which is 128 bits long and written in hexadecimal (e.g., `2001:0db8:85a3:0000:0000:8a2e:0370:7334`).
Here is a quick breakdown of the two types:
- **IPv4 Addresses:** **32 bits** long (composed of four \(8\)-bit "octets" like `192.168.1.1`).
- **IPv6 Addresses:** **128 bits** long (composed of eight \(16\)-bit sections).

| Name         | [CIDR](https://en.wikipedia.org/wiki/CIDR "CIDR") block | Address range                 | Number of  <br>addresses | _[Classful](https://en.wikipedia.org/wiki/Classful "Classful")_ description |
| ------------ | ------------------------------------------------------- | ----------------------------- | ------------------------ | --------------------------------------------------------------------------- |
| 24-bit block | 10.0.0.0/8                                              | 10.0.0.0 – 10.255.255.255     | 16777216                 | Single Class A                                                              |
| 20-bit block | 172.16.0.0/12                                           | 172.16.0.0 – 172.31.255.255   | 1048576                  | Contiguous range of 16 Class B blocks                                       |
| 16-bit block | 192.168.0.0/16                                          | 192.168.0.0 – 192.168.255.255 | 65536                    | Contiguous range of 256 Class C blocks                                      |

|Class|Most-significant bits|Network prefix length  <br>(bits)|Host identifier length  <br>(bits)|Address range|
|---|---|---|---|---|
|A|0|8|24|0.0.0.0–127.255.255.255|
|B|10|16|16|128.0.0.0–191.255.255.255|
|C|110|24|8|192.0.0.0–223.255.255.255|
|D(multicast)|1110|—N/a|—N/a|224.0.0.0–239.255.255.255|
|E(reserved)|1111|—N/a|—N/a|240.0.0.0–255.255.255.255|
![[Pasted image 20260601214125.png]]

