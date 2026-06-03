
## **==IP Addresses ==**
An IP address serves two principal functions: it identifies the host, or more specifically, its network interface. "Network interface controller", and it provides the location of the host in the network, and thus, the capability of establishing a path to that host. Its role has been characterized as follows: "A name indicates what we seek. An address indicates where it is. A route indicates how to get there." The header" of each IP packet "Network packet" contains the IP address of the sending host and that of the destination host.

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


## ==**Mac address:**==
A MAC address (medium access control address or media access control address) is a unique identifier assigned to a network interface controller (NIC) for use as a network address in communications within a network segment. This use is common in most IEEE 802 networking technologies, including Ethernet, Wi-Fi, and Bluetooth. Within the Open Systems Interconnection (OSI) network model, MAC addresses are used in the medium access control protocol sublayer of the data link layer. As typically represented, MAC addresses are recognizable as six groups of two hexadecimal digits, separated by hyphens, colons, or without a separator. 

A **MAC address** (Media Access Control address) is a unique, 12-character physical identifier assigned to a network interface card (NIC) by its manufacturer.

Think of an **IP address** like your mailing address (which changes if you move), while a **MAC address** is like your fingerprint or DNA—it is permanently tied to the specific hardware of your device.

## 1. Structure of a MAC Address

A MAC address consists of **48 bits**, typically represented as 12 hexadecimal digits (0-9, A-F) separated by colons, hyphens, or periods.
> **Example:** `00:1A:2B:3C:4D:5E`

it is split perfectly into two halves:
- **Organizationally Unique Identifier (OUI):** The first 6 digits (24 bits) identify the manufacturer of the device (e.g., Apple, Intel, Cisco).
- **Network Interface Controller (NIC) Specific:** The last 6 digits (24 bits) are a unique serial number assigned by the manufacturer to that specific chip.
## 2. How it Differs from an IP Address

|**Feature**|**MAC Address**|**IP Address**|
|---|---|---|
|**Layer (OSI Model)**|**Layer 2** (Data Link Layer)|**Layer 3** (Network Layer)|
|**Permanence**|**Permanent** (Burned into the hardware)|**Dynamic/Static** (Assigned by software/routers)|
|**Scope**|Used for communication **within** the local network (LAN).|Used for routing data **across** different networks (Internet).|
|**Addressing**|Physical Address|Logical Address|

## 3. Why Do We Need Both?

When data travels across the internet, it uses **IP addresses** to find the right neighborhood (network). However, once the data arrives at your local home or office router, the router uses **MAC addresses** to deliver the data packets to the exact device (your phone, laptop, or smart TV) that requested it.
This translation between IP addresses and MAC addresses on a local network is handled by a protocol called **ARP (Address Resolution Protocol)**.

## 4. MAC Randomization (Modern Security)

Because traditional MAC addresses never change, they can theoretically be used to track a device's physical movement as it connects to different public Wi-Fi networks.

To prevent this tracking, modern operating systems (like Android, iOS, Windows, and macOS) now use **MAC Randomization**. When scanning for or connecting to a network, the device generates a temporary, fake MAC address to protect your privacy.
## 5. How to Find Your MAC Address

- **Windows (Command Prompt):** Run `ipconfig /all` or `getmac` (listed as "Physical Address").
- **Linux / macOS (Terminal):** Run `ifconfig` or `ip link show` (listed next to "ether" or "HWaddr").
- **Android / iOS:** Go to **Settings** -> **About Phone/General** -> **Status/About** -> **Wi-Fi MAC Address**.


##  **==TCP vs. UDP:==**

To truly understand TCP, it helps to compare it to its sibling, **UDP** (User Datagram Protocol):

| **Feature**       | **TCP (Transmission Control Protocol)**           | **UDP (User Datagram Protocol)**                    |
| ----------------- | ------------------------------------------------- | --------------------------------------------------- |
| **Connection**    | Connection-oriented (requires handshake)          | Connectionless (just fires and forgets)             |
| **Reliability**   | **Guaranteed.** Re-sends lost data.               | **Not guaranteed.** Packets can be lost.            |
| **Speed**         | Slower (due to overhead and error-checking)       | Faster (minimal overhead)                           |
| **Ordering**      | Delivers data in the exact order sent.            | Packets can arrive in any order.                    |
| **Best Used For** | Web browsing (HTTP/HTTPS), Email, File transfers. | Video streaming, Online gaming, VoIP (Voice calls). |

## ==**common ports and protocols:**==
In networking, **protocols** are the rules for how data is structured and sent, while **ports** are the virtual doorways on a device that route that data to the specific application or service that needs it.

An IP address gets you to the right building; the port number gets you to the right apartment.

Here is a breakdown of the most common ports and protocols, categorized by their function.

## 1. Web & Remote Access

These protocols are responsible for how you access the internet and manage servers remotely.

|**Port**|**Protocol**|**Layer 4 Transport**|**Description**|
|---|---|---|---|
|**80**|**HTTP** (Hypertext Transfer Protocol)|TCP|Unencrypted web traffic. Used for loading standard websites.|
|**443**|**HTTPS** (HTTP Secure)|TCP|Encrypted web traffic. Uses TLS/SSL to secure data between browser and server.|
|**22**|**SSH** (Secure Shell)|TCP|Secure, encrypted remote command-line access to servers.|
|**23**|**Telnet**|TCP|Legacy, _unencrypted_ remote command-line access (highly insecure).|
|**3389**|**RDP** (Remote Desktop Protocol)|TCP / UDP|Microsoft's protocol for visual remote desktop GUI access.|

## 2. Infrastructure & Core Services

Without these, the internet wouldn't function smoothly. They handle everything from translating domain names to assigning IP addresses automatically.

|**Port**|**Protocol**|**Layer 4 Transport**|**Description**|
|---|---|---|---|
|**53**|**DNS** (Domain Name System)|UDP / TCP|Translates human-readable domain names (e.g., `google.com`) into IP addresses.|
|**67 / 68**|**DHCP** (Dynamic Host Configuration Protocol)|UDP|Automatically assigns IP addresses, subnet masks, and gateways to devices on a network.|
|**123**|**NTP** (Network Time Protocol)|UDP|Synchronizes clock times between devices and servers across a network.|
|**161 / 162**|**SNMP** (Simple Network Management Protocol)|UDP|Used by network administrators to monitor and manage network devices (routers, switches).|

## 3. File Transfer

Used for moving files between clients and servers over a network.

|**Port**|**Protocol**|**Layer 4 Transport**|**Description**|
|---|---|---|---|
|**20 / 21**|**FTP** (File Transfer Protocol)|TCP|Transfers files. Port 21 is for commands/control; Port 20 is for actual data transfer. Unencrypted.|
|**69**|**TFTP** (Trivial FTP)|UDP|A stripped-down, connectionless version of FTP used for quick, simple file transfers (like booting diskless workstations).|
|**445**|**SMB** (Server Message Block)|TCP|Used by Windows for sharing files, printers, and serial ports across a local network.|

## 4. Email Services

These protocols dictate how emails are sent from clients to servers, and how they are retrieved.

|**Port**|**Protocol**|**Layer 4 Transport**|**Description**|
|---|---|---|---|
|**25**|**SMTP** (Simple Mail Transfer Protocol)|TCP|Primarily used for _sending_ routing email between mail servers.|
|**110**|**POP3** (Post Office Protocol v3)|TCP|_Retrieves_ email from a server. Downloads the mail locally and typically deletes it from the server.|
|**143**|**IMAP** (Internet Message Access Protocol)|TCP|_Retrieves_ email from a server, but keeps the messages synced across multiple devices.|
|**587**|**Secure SMTP**|TCP|Modern port for client email submission utilizing TLS encryption.|
|**993**|**IMAPS** (IMAP Secure)|TCP|Over-the-network encrypted version of IMAP.|
|**995**|**POP3S** (POP3 Secure)|TCP|Over-the-network encrypted version of POP3.|

## 5. Directory & Database Services

Used primarily in enterprise environments to manage users, permissions, and database queries.

|**Port**|**Protocol**|**Layer 4 Transport**|**Description**|
|---|---|---|---|
|**389**|**LDAP** (Lightweight Directory Access Protocol)|TCP / UDP|Used for querying and managing directory services (like active directory users and computers).|
|**636**|**LDAPS** (LDAP Secure)|TCP|Encrypted LDAP over TLS/SSL.|
|**1433**|**MSSQL**|TCP|Default port for Microsoft SQL Server database communication.|
|**3306**|**MySQL**|TCP|Default port for MySQL database communication.|

## **==osi model==**

The **OSI (Open Systems Interconnection) Model** is a conceptual framework created by the International Organization for Standardization (ISO) in 1984. It breaks down how data moves from a physical wire or wireless signal all the way up to the software application you are using.

Instead of treating networking as one massive, complex process, the OSI model divides it into **7 distinct layers**.

## The 7 Layers of the OSI Model

A classic mnemonic to remember the layers from top (7) to bottom (1) is:

**A**ll **P**eople **S**eem **T**o **N**eed **D**ata **P**rocessing.

### 7. Application Layer

- **What it does:** The closest layer to the end user. It provides network services directly to software applications (like web browsers or email clients). It does _not_ mean the browser itself, but the protocols the browser uses.
    
- **Protocols/Tech:** HTTP, HTTPS, FTP, SMTP, DNS, SSH.
    
- **Data Unit:** Data.
    

### 6. Presentation Layer

- **What it does:** Acts as the translator for the network. It formats, structures, encrypts, and compresses data so that the application layer can understand it. It ensures that data sent from Layer 7 of one system can be read by Layer 7 of another.
    
- **Protocols/Tech:** SSL/TLS, ASCII, JPEG, GIF, MPEG, encryption/decryption algorithms.
    
- **Data Unit:** Data.
    

### 5. Session Layer

- **What it does:** Manages the dialogues (sessions) between computers. It opens, maintains, and terminates connections between applications on separate devices. It ensures that sessions stay open long enough to transfer data, and closes them to save resources when done.
    
- **Protocols/Tech:** NetBIOS, RPC, SOCKS.
    
- **Data Unit:** Data.
    

### 4. Transport Layer

- **What it does:** Responsible for end-to-end communication, flow control, and error checking. It decides how much data to send, at what speed, and tracks whether it arrives safely. This layer chops large pieces of data from the upper layers into smaller pieces (segments).
    
- **Protocols/Tech:** TCP (reliable, connection-oriented), UDP (fast, connectionless).
    
- **Data Unit:** **Segments** (TCP) or **Datagrams** (UDP).
    

### 3. Network Layer

- **What it does:** Handles the routing and forwarding of data between different networks. It looks at the logical addresses (IP addresses) of the source and destination to determine the best physical path for the data to travel.
    
- **Protocols/Tech:** IPv4, IPv6, ICMP (Ping), IPSec, Routers.
    
- **Data Unit:** **Packets**.
    

### 2. Data Link Layer

- **What it does:** Establishes a reliable link between two _directly connected_ nodes on the same network. It handles physical addressing (MAC addresses) and checks for errors that occurred at the physical layer. It is subdivided into the Logical Link Control (LLC) and Media Access Control (MAC) sublayers.
    
- **Protocols/Tech:** Ethernet, Wi-Fi (802.11), Switches, PPP.
    
- **Data Unit:** **Frames**.
    

### 1. Physical Layer

- **What it does:** The actual hardware layer. It deals with the raw electrical, optical, or radio signals that transmit unstructured digital data (bits) across physical media.
    
- **Protocols/Tech:** Cables (Cat6, Fiber optics), Hubs, Repeaters, RJ45 connectors, bitrates.
    
- **Data Unit:** **Bits**.