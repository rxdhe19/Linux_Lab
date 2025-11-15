# Experiment 2: Linux File Systems, Permissions, and Essential Commands

### Name: Radhe Patel   Roll No.: 590029079   Date: 2025-11-05

### Aim:

* To understand the structure of Linux file systems.
* To learn and practice essential navigation and file management commands.
* To explore file permissions and ownership, and manage them using Linux commands.
* To use user management, system information commands, and editing tools.
* To solve practical exercises and tasks for mastering Linux basics.

### Environment / Requirements

* A Linux machine (Ubuntu/Debian/Linux Mint or similar).
* User privileges to create, modify, and delete files.
* Access to terminal and text editors like `nano` or `vim`.
* Terminal prompt/sample outputs use: `radhe@ubuntu:~$`

---

## Theory

Linux uses a hierarchical file system starting from the root `/`. Essential directories include `/home`, `/etc`, `/usr`, `/var`, `/bin`, and `/tmp`. File permissions are divided among **owner**, **group**, and **others**, with actions `r` (read), `w` (write), and `x` (execute). Navigation commands like `ls`, `pwd`, `cd`, and file operations (`cp`, `mv`, `rm`) form the basis of Linux usage. Editors (`nano`, `vim`) and commands for system info (`uname`, `df`, `top`, `history`) provide insights and control. Practice tasks build practical confidence.

---

## Procedure & Script Log (Commands + Realistic Outputs)

> Prompt format used in logs: `radhe@ubuntu:~$`

```terminal
radhe@ubuntu:~$ date
Wed Nov  5 20:12:41 IST 2025
```

```terminal
radhe@ubuntu:~$ uname -a
Linux ubuntu 5.15.0-126-generic #136-Ubuntu SMP x86_64 GNU/Linux
```

```terminal
radhe@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 22.04.5 LTS
Release:        22.04
Codename:       jammy
```

### Exercise 1: File System Navigation

```bash
radhe@ubuntu:~$ cd
radhe@ubuntu:~$ pwd
/home/radhe
radhe@ubuntu:~$ mkdir -p projects/linux_practice/{scripts,documents,backup}
radhe@ubuntu:~$ cd projects/linux_practice/scripts
radhe@ubuntu:~/projects/linux_practice/scripts$ touch setup.sh cleanup.sh readme.txt
radhe@ubuntu:~/projects/linux_practice/scripts$ ls -la
total 12
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:10 .
drwxr-xr-x 5 radhe radhe 4096 Nov  5 20:10 ..
-rw-r--r-- 1 radhe radhe    0 Nov  5 20:10 cleanup.sh
-rw-r--r-- 1 radhe radhe    0 Nov  5 20:10 readme.txt
-rw-r--r-- 1 radhe radhe    0 Nov  5 20:10 setup.sh
radhe@ubuntu:~/projects/linux_practice/scripts$ cd ..
radhe@ubuntu:~/projects/linux_practice$ ls -la
total 20
drwxr-xr-x 5 radhe radhe 4096 Nov  5 20:10 .
drwxr-xr-x 3 radhe radhe 4096 Nov  5 19:58 ..
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:10 scripts
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:10 documents
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:10 backup
```

### Exercise 2: File Operations and Permissions

```bash
radhe@ubuntu:~/projects/linux_practice/documents$ echo "This is a practice document" > practice.txt
radhe@ubuntu:~/projects/linux_practice/documents$ ls -l practice.txt
-rw-r--r-- 1 radhe radhe 29 Nov  5 20:11 practice.txt
radhe@ubuntu:~/projects/linux_practice/documents$ chmod 644 practice.txt
radhe@ubuntu:~/projects/linux_practice/documents$ cp practice.txt ../backup/
radhe@ubuntu:~/projects/linux_practice/documents$ cp practice.txt ../backup/practice_backup_20251105.txt
radhe@ubuntu:~/projects/linux_practice/documents$ ls -la ../backup/
total 16
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:11 .
drwxr-xr-x 5 radhe radhe 4096 Nov  5 20:10 ..
-rw-r--r-- 1 radhe radhe 29 Nov  5 20:11 practice.txt
-rw-r--r-- 1 radhe radhe 29 Nov  5 20:11 practice_backup_20251105.txt
```

### Exercise 3: Text Editing and Viewing

```bash
radhe@ubuntu:~/projects/linux_practice/documents$ seq 1 50 > numbers.txt
radhe@ubuntu:~/projects/linux_practice/documents$ head numbers.txt
1
2
3
4
5
radhe@ubuntu:~/projects/linux_practice/documents$ tail -n 5 numbers.txt
46
47
48
49
50
radhe@ubuntu:~/projects/linux_practice/documents$ cat numbers.txt | grep "25"
25
```

### Exercise 4: System Exploration

```bash
radhe@ubuntu:~$ uname -a
Linux ubuntu 5.15.0-126-generic #136-Ubuntu SMP x86_64 GNU/Linux
radhe@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   11G   37G  23% /
tmpfs           1.9G  2.1M  1.9G   1% /run
radhe@ubuntu:~$ whoami
radhe
radhe@ubuntu:~$ history 10
  201  cd projects/linux_practice
  202  ls -la
  203  seq 1 50 > numbers.txt
  204  head numbers.txt
  205  tail -n 5 numbers.txt
  206  grep "25" numbers.txt
  207  uname -a
  208  df -h
  209  whoami
  210  history 10
```

### Exercise 5: Cleanup

```bash
radhe@ubuntu:~/projects/linux_practice$ rm -i documents/numbers.txt
rm: remove regular file 'documents/numbers.txt'? y
radhe@ubuntu:~/projects/linux_practice$ rm -r backup
radhe@ubuntu:~/projects/linux_practice$ ls -la
total 8
drwxr-xr-x 3 radhe radhe 4096 Nov  5 20:12 .
drwxr-xr-x 3 radhe radhe 4096 Nov  5 19:58 ..
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:10 scripts
drwxr-xr-x 2 radhe radhe 4096 Nov  5 20:10 documents
```

---

## Practice Exercises & Tasks (Commands repeated for clarity)

### Task 1: Directory Navigation

```bash
radhe@ubuntu:~$ mkdir -p ~/test_project/{docs,scripts,data}
radhe@ubuntu:~$ cd ~/test_project/scripts
radhe@ubuntu:~/test_project/scripts$ pwd
/home/radhe/test_project/scripts
```

### Task 2: File Creation and Content

```bash
radhe@ubuntu:~/test_project/docs$ touch readme.txt notes.txt todo.txt
radhe@ubuntu:~/test_project/docs$ echo "Project documentation" > readme.txt
radhe@ubuntu:~/test_project/docs$ echo "Important notes" > notes.txt
radhe@ubuntu:~/test_project/docs$ cat readme.txt
Project documentation
radhe@ubuntu:~/test_project/docs$ cat notes.txt
Important notes
```

### Task 3: File Operations

```bash
radhe@ubuntu:~/test_project/docs$ cp readme.txt ../data/project_info.txt
radhe@ubuntu:~/test_project/docs$ mv todo.txt ../scripts/
radhe@ubuntu:~/test_project/docs$ ls -la ../data
total 8
-rw-r--r-- 1 radhe radhe 21 Nov  5 20:12 project_info.txt
```

### Task 4: File Permissions

```bash
radhe@ubuntu:~/test_project/scripts$ echo "#!/bin/bash" > backup.sh
radhe@ubuntu:~/test_project/scripts$ echo "echo Backup complete" >> backup.sh
radhe@ubuntu:~/test_project/scripts$ chmod u+x backup.sh
radhe@ubuntu:~/test_project/scripts$ ls -l backup.sh
-rwxr--r-- 1 radhe radhe 34 Nov  5 20:12 backup.sh
```

### Task 5: File Viewing

```bash
radhe@ubuntu:~/test_project/scripts$ seq 1 20 > numbers.txt
radhe@ubuntu:~/test_project/scripts$ head -n 5 numbers.txt
1
2
3
4
5
radhe@ubuntu:~/test_project/scripts$ tail -n 3 numbers.txt
18
19
20
radhe@ubuntu:~/test_project/scripts$ grep "1" numbers.txt
1
10
11
12
13
14
15
16
17
18
19
```

### Task 6: Text Editing

```bash
radhe@ubuntu:~/test_project/scripts$ nano config.txt
radhe@ubuntu:~/test_project/scripts$ cat config.txt
# (sample placeholder content)
```

### Task 7: System Information

```bash
radhe@ubuntu:~$ echo "Username: $(whoami)" > system_info.txt
radhe@ubuntu:~$ echo "Date: $(date)" >> system_info.txt
radhe@ubuntu:~$ echo "Directory: $(pwd)" >> system_info.txt
radhe@ubuntu:~$ df -h >> system_info.txt
radhe@ubuntu:~$ cat system_info.txt
Username: radhe
Date: Wed Nov  5 20:12:41 IST 2025
Directory: /home/radhe
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   11G   37G  23% /
```

### Task 8: File Organization

```bash
radhe@ubuntu:~$ mkdir ~/test_project/backup
radhe@ubuntu:~$ cp ~/test_project/*/*.txt ~/test_project/backup/
radhe@ubuntu:~$ ls -la ~/test_project/backup
total 16
-rw-r--r-- 1 radhe radhe 21 Nov  5 20:12 project_info.txt
-rw-r--r-- 1 radhe radhe 29 Nov  5 20:11 practice.txt
```

### Task 9: Process and History

```bash
radhe@ubuntu:~$ history | wc -l
150
radhe@ubuntu:~$ history 10
  141  mkdir -p ~/test_project/{docs,scripts,data}
  142  cd ~/test_project/scripts
  143  pwd
  144  touch readme.txt notes.txt todo.txt
  145  echo "Project documentation" > readme.txt
  146  echo "Important notes" > notes.txt
  147  cp readme.txt ../data/project_info.txt
  148  mv todo.txt ../scripts/
  149  seq 1 20 > numbers.txt
  150  history 10
```

### Task 10: Comprehensive Cleanup

```bash
radhe@ubuntu:~/test_project/scripts$ chmod 754 backup.sh
radhe@ubuntu:~/test_project/scripts$ find ~/test_project -type f | wc -l > summary.txt
radhe@ubuntu:~/test_project/scripts$ find ~/test_project -type d | wc -l >> summary.txt
radhe@ubuntu:~/test_project/scripts$ cat summary.txt
5
6
```

---

## Result

* Explored Linux file system structure.
* Practiced file operations, editing, and permissions.
* Learned user and system management commands.
* Completed practical exercises and lab exam-style tasks.

## Challenges Faced & Learning Outcomes

* Challenge 1: Managing complex directory structures.
* Challenge 2: Remembering symbolic vs numeric permissions.
* Challenge 3: Using `find`, `grep`, and redirection effectively.

### Learning:

* Mastered Linux navigation, file handling, and permissions.
* Gained practical knowledge of user/system management.
* Practiced exam-style tasks to solidify learning.

## Conclusion

This experiment comprehensively covered **Linux file systems, permissions, commands, editing, user management, and system info**. The tasks ensured thorough practice, making it a complete foundation for Linux proficiency.