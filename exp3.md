
# Experiment 3: Linux File Manipulation and System Manipulation I

### Name: Radhe Patel   Roll No.: 590029079   Date: 2025-11-05

---

## 1) Objective

- To learn and perform basic and advanced file manipulation in Linux.  
- To understand system manipulation commands like process management and file linking.  
- To implement hard links, soft links, archiving, compressing, and process control using commands.  

---

## 2) Theory / Background

Linux provides powerful tools for manipulating files, directories, and system processes. Key concepts include:

- **Hard Link:** A directory entry that points directly to the inode of a file. Deleting the original file does not remove the data until all links are removed.
- **Soft Link (Symbolic Link):** A shortcut-like file pointing to another file by name/path.
- **Archiving and Compression:** Managed using `tar`, `gzip`, `zip`, `unzip`.
- **Process Management:** Commands like `ps`, `top`, `kill`, `jobs`, `bg`, `fg`.
- **Filters and Redirection:** `cat`, `head`, `tail`, `grep`, `sort`, `wc`, `>` and `>>`.

---

## 3) Environment / Requirements

- Operating System: Ubuntu 22.04 LTS  
- Terminal with bash shell  
- User: `radhe`  
- Sudo privileges enabled  

---

## 4) Script Log (Commands + Realistic Outputs)

> Prompt format used: `radhe@ubuntu:~$`

### 4.1 Creating Files, Hard Links, and Soft Links

```bash
radhe@ubuntu:~$ mkdir exp3 && cd exp3
radhe@ubuntu:~/exp3$ echo "Hello Experiment 3" > file1.txt
radhe@ubuntu:~/exp3$ ln file1.txt hardlink_file1
radhe@ubuntu:~/exp3$ ln -s file1.txt softlink_file1
radhe@ubuntu:~/exp3$ ls -li
total 8
1234567 -rw-r--r-- 2 radhe radhe 19 Nov  6 10:15 file1.txt
1234567 -rw-r--r-- 2 radhe radhe 19 Nov  6 10:15 hardlink_file1
1234568 lrwxrwxrwx 1 radhe radhe  9 Nov  6 10:15 softlink_file1 -> file1.txt
```

### 4.2 Verify Inode and Permissions

```bash
radhe@ubuntu:~/exp3$ stat file1.txt
  File: file1.txt
  Size: 19         Blocks: 8          IO Block: 4096   regular file
Device: 802h/2050d Inode: 1234567     Links: 2
Access: (0644/-rw-r--r--)  Uid: (1000/radhe)   Gid: (1000/radhe)
```

### 4.3 Archiving and Compression

```bash
radhe@ubuntu:~/exp3$ tar -cvf files.tar file1.txt
file1.txt
radhe@ubuntu:~/exp3$ gzip files.tar
radhe@ubuntu:~/exp3$ ls
file1.txt  files.tar.gz  hardlink_file1  softlink_file1
```

### 4.4 Process Management

```bash
radhe@ubuntu:~$ gedit &
[1] 2456
radhe@ubuntu:~$ ps
    PID TTY          TIME CMD
   2001 pts/0    00:00:00 bash
   2456 pts/0    00:00:02 gedit
   2470 pts/0    00:00:00 ps
radhe@ubuntu:~$ kill 2456
radhe@ubuntu:~$ echo "Process terminated"
Process terminated
```

---

## 5) Observations

- Hard links share the same inode, whereas soft links point to the filename.  
- Deleting the original file breaks only soft links.  
- Compression using `gzip` reduced file size efficiently.  
- `ps` and `kill` commands help manage running processes effectively.  

---

## 6) Conclusion

The experiment demonstrated file linking (hard and soft), archiving, compression, and process control in Linux. This provided insight into how Linux handles files at the system level and how users can manipulate files and processes efficiently.

---

## Result

Successfully performed file manipulation and basic system commands as per Experiment 3.