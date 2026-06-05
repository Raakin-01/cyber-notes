In Linux, security and multi-user isolation are built directly into the core of the operating system. Everything revolves around **who you are (User)** and **what you are allowed to do (Privileges)**.

## 1. Types of Users in Linux

Linux categorizes users into three distinct types to keep the system organized and secure:

- **Root User (Superuser):** This is the system administrator account (UID `0`). The root user has absolute power, can access any file, run any command, and modify any system configuration.
    
- **Regular Users:** Created for daily tasks, development, and standard human operations. By default, they only have full control over their own home directory (`/home/username`) and cannot alter system-wide files.
    
- **System Users:** Created by the OS or specific software applications (like `www-data` for Apache, `mysql`, or `ssh`). They don't have interactive login shells; they exist purely to run background services with restricted permissions so that if a service is compromised, the attacker doesn't get full system access.
    

## 2. Linux File Permissions (The Privilege Model)

In Linux, **everything is a file** (even hardware devices). Every file and directory on the system is assigned specific permissions for three distinct levels of ownership.

If you run the command `ls -l` in a terminal, you will see a permission string that looks like this:

`- rwx r-x r--`

This string breaks down into four parts:

### The Ownership Levels

1. **User (u):** The individual user who owns the file (usually the creator).
    
2. **Group (g):** A collection of users who share the same access privileges to the file.
    
3. **Others (o):** Anyone else who has access to the system (the rest of the world).
    

### The Permission Types

- **Read (r):** Allowed to view the contents of a file or list the contents of a directory. (Numeric value = `4`)
    
- **Write (w):** Allowed to modify or delete a file, or add/remove files within a directory. (Numeric value = `2`)
    
- **Execute (x):** Allowed to run a file as a program/script, or enter (`cd` into) a directory. (Numeric value = `1`)
    

## 3. Managing Users and Groups

To manage accounts, you use commands that modify system configuration files like `/etc/passwd` (user details) and `/etc/group` (group details).

- **Create a user:** `sudo adduser sam`
    
- **Delete a user:** `sudo deluser sam`
    
- **Create a group:** `sudo addgroup developers`
    
- **Add user to a group:** `sudo usermod -aG developers sam` (The `-aG` flags mean _append_ to _group_).
    

## 4. Modifying Permissions and Ownership

If you own a file, or if you have root privileges, you can change who can access it using three core commands:

### `chmod` (Change Mode)

Changes the read, write, and execute permissions. You can use symbolic (letters) or absolute (numeric) notation.

- **Symbolic:** `chmod g+w script.sh` (Adds **w**rite permission to the **g**roup)
    
- **Numeric:** `chmod 754 script.sh`
    
    - `7` ($4+2+1$) $\rightarrow$ User gets `rwx`
        
    - `5` ($4+0+1$) $\rightarrow$ Group gets `r-x`
        
    - `4` ($4+0+0$) $\rightarrow$ Others get `r--`
        

### `chown` (Change Owner)

Changes the user and/or group ownership of a file.

- `sudo chown sam report.txt` (Changes owner to user `sam`)
    
- `sudo chown sam:developers report.txt` (Changes owner to user `sam` and group to `developers`)
    

## 5. Escalating Privileges: `sudo` and `su`

Because logging in as the root user permanently is highly dangerous (a single wrong command can wipe the drive), Linux uses privilege escalation tools:

- **`su` (Switch User):** Switches your terminal session entirely to another user account (usually root). Requires the target user's password.
    
- **`sudo` (Superuser Do):** Allows a regular user to execute a single command with root privileges. It checks if the user is listed in the safe administrative list (the `/etc/sudoers` file) and asks for the _regular user's_ own password for confirmation.
    


```
                                                                             
┌──(raakin㉿raakin)-[~]
└─$ echo "hello" > hello.txt
                                                                             
┌──(raakin㉿raakin)-[~]
└─$  ls -la
total 148
drwx------ 17 raakin raakin  4096 Jun  5 16:45 .
drwxr-xr-x  3 root   root    4096 May 30 17:18 ..
-rw-r--r--  1 raakin raakin   220 May 30 17:18 .bash_logout
-rw-r--r--  1 raakin raakin  5578 May 30 17:18 .bashrc
-rw-r--r--  1 raakin raakin  3526 May 30 17:18 .bashrc.original
drwxrwxr-x 11 raakin raakin  4096 May 30 17:28 .cache
drwxr-xr-x 13 raakin raakin  4096 May 30 17:24 .config
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Desktop
-rw-r--r--  1 raakin raakin    35 May 30 17:23 .dmrc
drwxr-xr-x  2 raakin raakin  4096 Jun  5 16:34 Documents
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Downloads
-rw-r--r--  1 raakin raakin 11759 May 30 17:18 .face
lrwxrwxrwx  1 raakin raakin     5 May 30 17:18 .face.icon -> .face
drwx------  3 raakin raakin  4096 May 30 17:23 .gnupg
-rw-rw-r--  1 raakin raakin     6 Jun  5 16:45 hello.txt
-rw-------  1 raakin raakin     0 May 30 17:23 .ICEauthority
drwxr-xr-x  3 raakin raakin  4096 May 30 17:18 .java
drwxr-xr-x  5 raakin raakin  4096 May 30 17:23 .local
drwxrwxr-x  5 raakin raakin  4096 May 30 17:28 .mozilla
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Music
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Pictures
-rw-r--r--  1 raakin raakin   807 May 30 17:18 .profile
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Public
drwx------  3 raakin raakin  4096 May 30 17:23 .ssh
-rw-r--r--  1 raakin raakin     0 May 30 17:25 .sudo_as_admin_successful
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Templates
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Videos
-rw-------  1 raakin raakin    51 Jun  5 16:25 .Xauthority
-rw-------  1 raakin raakin  4532 Jun  5 16:26 .xsession-errors
-rw-------  1 raakin raakin  4532 Jun  4 15:35 .xsession-errors.old
-rw-r--r--  1 raakin raakin   336 May 30 17:18 .zprofile
-rw-------  1 raakin raakin    86 May 30 17:29 .zsh_history
-rw-r--r--  1 raakin raakin 10882 May 30 17:18 .zshrc
                                                                             
┌──(raakin㉿raakin)-[~]
└─$  chmod +rwx hello.txt
                                                                             
┌──(raakin㉿raakin)-[~]
└─$ ls -la
total 148
drwx------ 17 raakin raakin  4096 Jun  5 16:45 .
drwxr-xr-x  3 root   root    4096 May 30 17:18 ..
-rw-r--r--  1 raakin raakin   220 May 30 17:18 .bash_logout
-rw-r--r--  1 raakin raakin  5578 May 30 17:18 .bashrc
-rw-r--r--  1 raakin raakin  3526 May 30 17:18 .bashrc.original
drwxrwxr-x 11 raakin raakin  4096 May 30 17:28 .cache
drwxr-xr-x 13 raakin raakin  4096 May 30 17:24 .config
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Desktop
-rw-r--r--  1 raakin raakin    35 May 30 17:23 .dmrc
drwxr-xr-x  2 raakin raakin  4096 Jun  5 16:34 Documents
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Downloads
-rw-r--r--  1 raakin raakin 11759 May 30 17:18 .face
lrwxrwxrwx  1 raakin raakin     5 May 30 17:18 .face.icon -> .face
drwx------  3 raakin raakin  4096 May 30 17:23 .gnupg
-rwxrwxr-x  1 raakin raakin     6 Jun  5 16:45 hello.txt
-rw-------  1 raakin raakin     0 May 30 17:23 .ICEauthority
drwxr-xr-x  3 raakin raakin  4096 May 30 17:18 .java
drwxr-xr-x  5 raakin raakin  4096 May 30 17:23 .local
drwxrwxr-x  5 raakin raakin  4096 May 30 17:28 .mozilla
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Music
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Pictures
-rw-r--r--  1 raakin raakin   807 May 30 17:18 .profile
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Public
drwx------  3 raakin raakin  4096 May 30 17:23 .ssh
-rw-r--r--  1 raakin raakin     0 May 30 17:25 .sudo_as_admin_successful
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Templates
drwxr-xr-x  2 raakin raakin  4096 May 30 17:23 Videos
-rw-------  1 raakin raakin    51 Jun  5 16:25 .Xauthority
-rw-------  1 raakin raakin  4532 Jun  5 16:26 .xsession-errors
-rw-------  1 raakin raakin  4532 Jun  4 15:35 .xsession-errors.old
-rw-r--r--  1 raakin raakin   336 May 30 17:18 .zprofile
-rw-------  1 raakin raakin    86 May 30 17:29 .zsh_history
-rw-r--r--  1 raakin raakin 10882 May 30 17:18 .zshrc
```


In Linux, **`chmod`** stands for **"Change Mode."** It is the command used to manage and alter the access permissions (read, write, execute) of files and directories.

Understanding `chmod` requires looking at **who** gets the permissions and **how** those permissions are represented.

## 1. The Targets and the Actions

Whenever you change permissions, you are dealing with three types of users:

- **u (User):** The owner of the file.
    
- **g (Group):** Users who belong to the file's assigned group.
    
- **o (Others):** Everyone else on the system.
    
- **a (All):** Combination of all three ($u + g + o$).
    

The actions you can assign are:

- **r (Read):** Permission to view file contents or list a directory.
    
- **w (Write):** Permission to modify/delete a file or add/remove files in a directory.
    
- **x (Execute):** Permission to run a file as a program/script or `cd` into a directory.
    

There are two primary ways to use `chmod`: **Absolute (Numeric) Mode** and **Symbolic Mode**.

## 2. Absolute (Numeric) Mode

Numeric mode uses a three-digit octal number to represent permissions. Each digit corresponds to a specific owner class in this exact order: **User, Group, Others**.

The numbers are derived by adding up the values of the permissions you want to grant:

- **4** = Read ($r$)
    
- **2** = Write ($w$)
    
- **1** = Execute ($x$)
    
- **0** = No permission ($-$)
    

### Common Numeric Combinations

- **`7`** ($4 + 2 + 1$): Full permissions (`rwx`)
    
- **`6`** ($4 + 2$): Read and Write (`rw-`)
    
- **`5`** ($4 + 1$): Read and Execute (`r-x`)
    
- **`4`** ($4$): Read-only (`r--`)
    

### Examples

- **`chmod 755 script.sh`**
    
    - **7** ($u$): Owner can Read, Write, and Execute (`rwx`).
        
    - **5** ($g$): Group can Read and Execute (`r-x`).
        
    - **5** ($o$): Others can Read and Execute (`r-x`).
        
    - _Commonly used for public scripts and executable binaries._
        
- **`chmod 600 private.txt`**
    
    - **6** ($u$): Owner can Read and Write (`rw-`).
        
    - **0** ($g$): Group has no permissions (`---`).
        
    - **0** ($o$): Others have no permissions (`---`).
        
    - _Commonly used for sensitive files like private SSH keys (`id_rsa`)._
        

## 3. Symbolic Mode

Symbolic mode uses letters and mathematical operators (`+`, `-`, `=`) to modify existing permissions without recalculating the whole set.

- **`+`** Grants a permission.
    
- **`-`** Removes a permission.
    
- **`=`** Sets the exact permission (overwriting what was there).
    

### Examples

- **Make a script executable for everyone:**
    
    Bash
    
    ```
    chmod +x deploy.sh
    ```
    
- **Remove write permissions from the Group and Others:**
    
    Bash
    
    ```
    chmod go-w document.docx
    ```
    
- **Explicitly set the owner to read/write, and remove all access for everyone else:**
    
    Bash
    
    ```
    chmod u=rw,go= report.csv
    ```
    

## 4. Modifying Directories Recursively

By default, running `chmod` on a folder only changes the folder itself, not the files inside it. To apply changes to a directory and **all of its subdirectories and files**, use the recursive flag (**`-R`**):

Bash

```
chmod -R 755 /path/to/my_project
```

> ⚠️ **A Note on Execution Limits:** Be careful running a sweeping numeric command like `chmod -R 777`. This grants absolute write and execution rights to the entire system, creating massive security vulnerabilities. It is always better to grant the absolute minimum permissions required for a file or application to function.


To fully master `chmod` numbers, you don't need to memorize them. You just need to know the basic building blocks and how to add them together.
Here is the exact breakdown of how the numbers, permissions, and totals work.
### 1. The Core Values (The Blocks)

Every single digit in a `chmod` command is calculated by adding up any combination of these three baseline values:

|**Value**|**Permission**|**Letter**|**What it allows**|
|---|---|---|---|
|**4**|**Read**|`r`|Viewing file contents / Listing directory contents|
|**2**|**Write**|`w`|Modifying/Deleting files / Adding files to a directory|
|**1**|**Execute**|`x`|Running a script/program / Entering (`cd`) a directory|
|**0**|**None**|`-`|No access permitted|

### 2. Math & Permission Totals
To get a specific permission set, you add the numbers together. There are only **8 possible totals** (from 0 to 7):

| **Total** | **Math Formula** | **Resulting Permissions** | **Common Usage**                                                |
| --------- | ---------------- | ------------------------- | --------------------------------------------------------------- |
| **`7`**   | $4 + 2 + 1$      | `rwx` (Full Access)       | For scripts/programs you want to run and modify.                |
| **`6`**   | $4 + 2 + 0$      | `rw-` (Read & Write)      | Standard for regular text/data files (documents, images).       |
| **`5`**   | $4 + 0 + 1$      | `r-x` (Read & Execute)    | Standard for directories so users can see files and enter them. |
| **`4`**   | $4 + 0 + 0$      | `r--` (Read Only)         | Configuration files or logs that shouldn't be altered.          |
| **`3`**   | $0 + 2 + 1$      | `-wx` (Write & Execute)   | Rarely used (highly insecure/specialized).                      |
| **`2`**   | $0 + 2 + 0$      | `-w-` (Write Only)        | Rarely used (blind drop-boxes).                                 |
| **`1`**   | $0 + 0 + 1$      | `--x` (Execute Only)      | Extremely rare hidden binaries.                                 |
| **`0`**   | $0 + 0 + 0$      | `---` (No Access)         | Complete lockdown.                                              |

### 3. Putting it into the 3-Digit Command

When you run `chmod 754 file.txt`, you are applying those totals to three separate groups of people, in this exact order: **User (Owner) $\rightarrow$ Group $\rightarrow$ Others**.

Plaintext

```
       chmod   7       5       4   file.txt
               │       │       │
               │       │       └── Others (4 = Read-only)
               │       └────────── Group  (4+1 = Read & Execute)
               └────────────────── User   (4+2+1 = Read, Write, & Execute)
```

#### Real-World Cheat Sheet

- **`chmod 777`** ($7, 7, 7$) $\rightarrow$ `rwxrwxrwx`
    
    - _Everyone can do everything._ (Dangerous! Avoid using this unless debugging).
        
- **`chmod 755`** ($7, 5, 5$) $\rightarrow$ `rwxr-xr-x`
    
    - _Owner can modify and run it; Everyone else can read and run it._ (Standard for web servers, scripts, and public tools).
        
- **`chmod 644`** ($6, 4, 4$) $\rightarrow$ `rw-r--r--`
    
    - _Owner can read and edit; Everyone else can only read._ (Standard for general files).
        
- **`chmod 600`** ($6, 0, 0$) $\rightarrow$ `rw-------`
    
    - _Only the owner can read or edit; No one else can even look at it._ (Perfect for SSH keys, private data, or environment files containing passwords).

## creating a new user 

```
┌──(raakin㉿raakin)-[~]
└─$  sudo adduser john
[sudo] password for raakin: 
New password: 
Retype new password: 
passwd: password updated successfully
Changing the user information for john
Enter the new value, or press ENTER for the default
        Full Name []: john wick
        Room Number []: 
        Work Phone []: 
        Home Phone []: 
        Other []: 
Is the information correct? [Y/n] y   
┌──(raakin㉿raakin)-[~]
└─$ su john
Password: 
┌──(john㉿raakin)-[/home/raakin]
└─$                  
```

