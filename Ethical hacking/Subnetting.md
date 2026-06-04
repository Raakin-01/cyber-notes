Subnetting is ==the logical process of dividing a large IP network into smaller, more efficient, and secure subnetworks (subnets)==
![[Pasted image 20260604154125.png]]

![[Pasted image 20260604154308.png]]

In classful IPv4 addressing, IP addresses are divided into classes based on how many bits are used for the network ID and host ID.

- ****Class A:**** 8-bit network ID, 24-bit host ID
- ****Class B:**** 16-bit network ID, 16-bit host ID
- ****Class C:**** 24-bit network ID, 8-bit host ID

![[Pasted image 20260604154644.png]]



| ip              | subnet          | hosts | network      | broadcast     |
| --------------- | --------------- | ----- | ------------ | ------------- |
| 192.168.1.0/24  | 255.255.255.0   | 254   | 192.168.1.0  | 192.168.1.255 |
| 192.168.1.0/28  | 255.255.255.240 | 14    | 192.168.1.0  | 192.168.1.15  |
| 192.168.1.16/28 | 255.255.255.240 | 14    | 192.168.1.16 | 192.168.1.31  |
| 192.168.0.0/23  | 255.255.254.0   | 510   | 192.168.0.0  | 192.168.1.255 |
| 192.168.2.0/23  | 255.255.254.0   | 510   | 192.168.2.0  | 192.168.3.255 |
| 192.168.1.0/27  | 255.255.255.224 | 30    | 192.168.1.0  | 192.168.1.31  |

