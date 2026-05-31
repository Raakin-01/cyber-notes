decimal number system uses base 10
binary number system uses base 2
other common bases:
- hexadecimal (base 16)
- octal (base 8)

==**ENCODING**==
->A translation from a number to anything ,an abstraction.

**==commands**==:
->grep:
$ egrep 'mellon' mysampledata.txt
$ egrep 'picoCTF' file
grep -r "picoCTF" big-zip-files

->FIND:
to find a file or directory specifially use:
Raakin-picoctf@webshell:~/files$ find . -name 'uber-secret.txt'

->to download stuff:
Raakin-picoctf@webshell:~$ wget https://artifacts.picoctf.net/c/504/big-zip-files.zip

**==NETCAT:**==
- `nc` This, of course, is the name of the program we are running. Netcat, or 'nc' as this system calls it. Sometimes the program name will be the full 'netcat' variety, but on the webshell, it is 'nc'.
    
- `saturn.picoctf.net` This is the name of the computer we’re connecting to. This is a challenge server that picoCTF runs.
    
- `52279` This is the number of the port we’re connecting to for the challenge. This will probably be different for your challenge.

==grep:==
   grep searches for PATTERNS in each FILE.  PwATTERNS is one or more patterns separated by newline characters, and grep prints each line that matches a pattern.  Typically PATTERNS should be quoted when grep is used in a shell command.

grep stands for global regular expression print
example:
**grep port:**
shows all lines in the file that contain port.
**grep -v port:**
shows all lines in the file that does not contain the word port.

**->Simple way to use grep command:**
grep hi file.txt

**grep -n hi file.txt**
gives line numbers for all the lines
**grep -c hi file.txt**
gives count of amount of times something appears in the file but does not actually show the lines
**grep -i file**
allows us to not care about case sensitivity


==**wget:**==
`wget` is a **command-line utility** that lets you download files from the internet — straight from your terminal, no browser needed! The name stands for **"Web Get"**, and it supports HTTP, HTTPS, and FTP protocols.
example:
wget https://example.com/file.zip 

**==to unzip a file:**==
unzip files.zip

**==Find==**
The `find` command searches for files and directories in your filesystem based on a huge variety of conditions — name, size, type, date modified, permissions, and so much more! It's one of the most **powerful and flexible** commands in Linux/Unix!
example:
    find . -name thisfile.txt
This command means: starting in the current directory (which is what `.`, dot means), look in this directory and all subdirectories for the file named 'thisfile.txt'. We can slightly modify this example to fit our needs for the challenge.

==**to gunzip files:==**
gunzip /tmp/disk.img.gz

**==The strings Command:==**
This is the golden standard tool for this exact scenario. It filters out all the unreadable machine bytes and prints _only_ sequences of printable characters.
```
strings warm | grep "picoCTF"
```
