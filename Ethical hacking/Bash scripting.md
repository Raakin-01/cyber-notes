
##  Normal ping command :

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ ping  172.28.43.61
PING 172.28.43.61 (172.28.43.61) 56(84) bytes of data.
64 bytes from 172.28.43.61: icmp_seq=1 ttl=64 time=0.637 ms
64 bytes from 172.28.43.61: icmp_seq=2 ttl=64 time=0.187 ms
64 bytes from 172.28.43.61: icmp_seq=3 ttl=64 time=0.030 ms
64 bytes from 172.28.43.61: icmp_seq=4 ttl=64 time=0.038 ms
64 bytes from 172.28.43.61: icmp_seq=5 ttl=64 time=0.043 ms
^C
--- 172.28.43.61 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4066ms
rtt min/avg/max/mdev = 0.030/0.187/0.637/0.232 ms
```

## Saving ping command :

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ ping  172.28.43.61 -c 1 > ip.txt
```

**- C 1 :** 
- C is used for count operator . 
- 1 is the count of times this ping is command is running.
-> The pings out put is saved in ip.txt

## Reading the saved command :

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ cat ip.txt
PING 172.28.43.61 (172.28.43.61) 56(84) bytes of data.
64 bytes from 172.28.43.61: icmp_seq=1 ttl=64 time=0.022 ms

--- 172.28.43.61 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.022/0.022/0.022/0.000 ms
```
## using grep command :

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ cat ip.txt | grep "64 bytes"
64 bytes from 172.28.43.61: icmp_seq=1 ttl=64 time=0.022 ms
```

- the grep command is used for finding specific texts / characters from the documents .
- it's output is the entire line containing the word .  
## using cut command:

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ cat ip.txt | grep "64 bytes" | cut -d " " -f 4
172.28.43.61:
```

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ cat ip.txt | grep "64 bytes" | cut -d " " -f 3
from
```

- `cut`: The command-line utility used to remove or extract sections from each line of files or piped text.
- `-d " "`: Defines the **delimiter** (the separator) as a single space. This tells `cut` to view your text as a list of items separated by spaces.
- `-f 4`: Specifies the **field** (column) you want to keep. In this case, the 4th one.

## Translate option:

```
┌──(raakin㉿DESKTOP-0FFMSPJ)-[~]
└─$ cat ip.txt | grep "64 bytes" | cut -d " " -f 4 |tr -d ":"
172.28.43.61
```

The `tr -d ":"` command **deletes all colons (`:`)** from the text passed into it.

The `tr` command stands for **translate**. When you pair it with the `-d` flag, it switches from "replace" mode to **"delete" mode**.

