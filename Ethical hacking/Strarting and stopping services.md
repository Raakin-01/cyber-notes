
## Apache server:

**==Starting of apache server:==**
```
┌──(raakin㉿raakin)-[~]
└─$ sudo service apache2 start
```

**==Stopping of apache server:==**
```
┌──(raakin㉿raakin)-[~]
└─$ sudo service apache2 stop 
```

**To view the apache server page just put the ip address of host onto the browser**.

## python server:

```
┌──(raakin㉿raakin)-[~]
└─$ python3 -m http.server 80
Serving HTTP on 0.0.0.0 port 80 (http://0.0.0.0:80/) ...
192.168.64.129 - - [07/Jun/2026 00:32:00] "GET / HTTP/1.1" 200 -
192.168.64.129 - - [07/Jun/2026 00:32:00] code 404, message File not found
192.168.64.129 - - [07/Jun/2026 00:32:00] "GET /favicon.ico HTTP/1.1" 404 -
192.168.64.129 - - [07/Jun/2026 00:32:08] "GET /.sudo_as_admin_successful HTTP/1.1" 200 -
192.168.64.129 - - [07/Jun/2026 00:32:23] "GET /Desktop/ HTTP/1.1" 200 -
192.168.64.129 - - [07/Jun/2026 00:32:29] "GET /Documents/ HTTP/1.1" 200 -
192.168.64.129 - - [07/Jun/2026 00:32:30] "GET /Documents/Downloads HTTP/1.1" 200 -
^C
Keyboard interrupt received, exiting.

```

ctrl+c to exit the server.
**To view the apache server page just put the ip address of host onto the browser.**


