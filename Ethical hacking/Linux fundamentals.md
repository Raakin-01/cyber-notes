

```
                                                                             
┌──(root㉿raakin)-[~]
└─#       
```

- root is the user 
- raakin is hostname 
- ~ is the present directory
## ==**pwd(print working directory):**==

it prints the path of the current working directory.
```
┌──(raakin㉿raakin)-[~]
└─$ pwd
/home/raakin

```

## how to write echo statements directly into a file 
```
                                                                             
┌──(raakin㉿raakin)-[~]
└─$ ls 
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
                                                                             
┌──(raakin㉿raakin)-[~]
└─$ cd Documents 
                                                                             
┌──(raakin㉿raakin)-[~/Documents]
└─$ ls 
                                                                             
┌──(raakin㉿raakin)-[~/Documents]
└─$ echo "hi" > test.txt
                                                                             
┌──(raakin㉿raakin)-[~/Documents]
└─$ ls
test.txt
                                                                             
┌──(raakin㉿raakin)-[~/Documents]
└─$ cat test.txt
hi
```

## mv and cp commands in linux:

### The Core Difference
- **`cp` (Copy):** Duplicates a file or directory. The original file stays exactly where it is, and a brand-new, identical copy is created in the specified destination.
    
- **`mv` (Move):** Relocates a file or directory. It places the file in the new destination and **removes** it from the original location. `mv` is also the standard command used to **rename** files.

| **Feature**           | **cp (Copy)**                                                                 | **mv (Move / Rename)**                                                                    |
| --------------------- | ----------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------- |
| **Original File**     | Remains unchanged in its original location.                                   | Deleted from the original location (relocated).                                           |
| **Disk Space**        | Consumes additional disk space because a new file is created.                 | Generally consumes no extra space (just updates the file system pointers).                |
| **Inode Number**      | The new file gets a **new inode** number.                                     | Retains the **same inode** number (unless moved across different partitions).             |
| **Speed**             | Can be slow for large files because it has to read and write the actual data. | Instantaneous on the same drive/partition because it only changes the file path metadata. |
| **Primary Use Cases** | Backing up files, duplicating templates.                                      | Organizing files, renaming files or directories.                                          |
### Basic Syntax & Examples

#### 1. Copying Files (`cp`)

To copy a file named `report.txt` from your current folder into a folder named `backup`:

Bash

```
cp report.txt backup/
```

_If you want to copy an entire folder and everything inside it, you must use the recursive flag (`-r`):_

Bash

```
cp -r project_folder/ backup_folder/
```

#### 2. Moving and Renaming Files (`mv`)

To move `report.txt` to the `documents` folder:

Bash

```
mv report.txt documents/
```

To **rename** a file, you "move" it to a new name in the same directory:

Bash

```
mv old_name.txt new_name.txt
```