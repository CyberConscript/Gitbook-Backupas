# Commands

## Commands and examples

* Searching with locate. The locate command is not perfect, however. Sometimes the results of  \
  locate can be overwhelming, giving you too much information. Also, locate  \
  uses a database that is usually only updated once a day, so if you just created  \
  a file a few minutes or a few hours ago, it might not appear in this list until  \
  the next day

```
locate <something>
```



* Finding Binaries with whereis. whereis returns just the binaries and man page

```
whereis <something>
```

*   Finding Binaries in the PATH Variable with which. able to find a binary file in the directories listed    \
    in the PATH variable

    ```
    which <something>
    ```
* Powerful Searches with find

```
find <directory> -type <type> -name <something>
```



* Wildcards

```
? - single char
[xyz] - chars in brackets
* - any
```



* To copy files, we use the cp command. This creates a duplicate of the file in  \
  the new location and leaves the old one in place

```
cp old_file location/copy_file
```



* Find search / location where user root and permission with sticky bit:

```
find / -user root -perm -4000
```

* To copy files, we use the cp command. This creates a duplicate of the file in  \
  the new location and leaves the old one in place

```
cp old_file location/copy_file
```

* The mv command can be used to move a file or directory to a new location or simply to give an existing file a new name.

```
mv old_file_name new_name
```

* The mv command can be used to move a file or directory to a new location or simply to give an existing file a new name.

```
mv old_file_name new_name
```

* To remove a file, you can simply use the rm command,

```
rm filename
```

* The command for removing a directory is similar to the rm command for  \
  removing files but with dir (for directory) appended

```
rmdir dirname    
rm -r newdirectory
```

* If you just want to view the beginning of a file, you can use the head command

```
head -20 /etc/snort/snort.conf
```

* If you just want to view the end of a file, you can use the tail command

```
tail-20 /etc/snort/snort.conf
```

* To display a file with line numbers, we use the nl (number lines) command.

```
nl /etc/snort/snort.conf    
```

* To display a file with line numbers, we use the nl (number lines) command.

```
nl /etc/snort/snort.conf   
```

* The sed command lets you search for occurrences of a word or a text pattern and then perform some action on it.

```
sed s/what_to_find/how_to_change/ source_file > destination_file
sed s/what_to_find/how_to_change/g source_file > destination_file
sed s/what_to_find/how_to_change/2 source_file > destination_file
```

##

## Analyzing and managing Networks

* Change IP address

<pre><code><strong>kali: 
</strong><strong>ifconfig eth0 192.168.181.115
</strong>ifconfig eth0 192.168.181.115 netmask 255.255.0.0 broadcast 192.168.1.255

kali >ifconfig eth0 down
kali >ifconfig eth0 hw ether 00:11:22:33:44:55
kali >ifconfig eth0 up

check wifi: iwconfig

DNS records /etc/hosts


ubuntu: 
sudo ip addr add 192.168.181.115/24 dev eth0
or
nano /etc/netplan/01-netcfg.yaml
sudo netplan apply


DNS resolvers config: /etc/resolv.conf

</code></pre>

* get IP from dhcp

```
dhclient eth0

The dhclient command sends a DHCPDISCOVER request from the network
interface specified (here, eth0). It then receives an offer (DHCPOFFER) from the
DHCP server (192.168.181.131 in this case) and confirms the IP assignment
to the DHCP server with a dhcp request.
```

* Examining DNS with dig

```
dig example.com
dig example.com A
dig example.com AAAA
dig example.com MX
dig example.com NS
dig example.com TXT
dig -x 8.8.8.8
dig example.com ANY
dig example.com +short
dig example.com +noall +answer
dig example.com +noall +answer +authority
dig example.com @8.8.8.8 #Use Google DNS
dig example.com +trace
dig example.com +multiline
dig example.com +stats
dig example.com +nocomments +nocmd +noquestion +noauthority +noadditional +answer
```

## Software installation



In Debian-based Linux distributions, which include Kali and Ubuntu, the\
default software manager is the Advanced Packaging Tool, or apt, whose\
primary command is apt-get. It’s worth adding a backup repository or two that your system can search through in case it doesn’t find it a\
specific software in the Kali repository via /etc/apt/sources.list.

* Searching for a Package

```
apt-cache search <keyword>
```

* Installing Package

```
apt-get install <package_name>
```

* removing software. The remove command  \
  doesn’t remove the configuration files, which means you can reinstall the  \
  same package in the future without reconfiguring.

```
apt-get remove keyword
```

* Clear out everything

```
apt-get purge keyword
```

* Software repositories will be periodically updated with new software or new  \
  versions of existing software. These updates don’t reach you automatically,  \
  so you have to request them in order to apply these updates to your own system. Updating isn’t the same as upgrading: updating simply updates the list  \
  of packages available for download from the repository, whereas upgrading  \
  will upgrade the package to the latest version in the repository.

```
apt-get update
```

* Upgrade

```
apt-get upgrade
```

The servers that hold the software for particular distributions of Linux are\
known as repositories.

Sometimes it will be that you want to install from github. Once you’ve found the software on github, you can install it from the terminal by entering the git clone command followed by its github URL.\
For instance, bluediving is located at https://www.github.com/\* To clone it into your system, enter the command git clone:

```
git clone https://www.github.com/*
```

## C o n t r o l l i n g F i l e a n d D i r e c t o r y P e r m i s s i o n s



The granting selects users permissions to read, write, or execute files - For each file and directory, we can specify the permission status for the file’s owner, for particular groups of users, and for\
all other users.

Granting Permissions\
Each and every file and directory must be allocated a particular level of permission for the different identities using it. The three levels of permission\
are as follows:\
r Permission to read. This grants permission only to open and view\
a file.\
w Permission to write. This allows users to view and edit a file.\
x Permission to execute. This allows users to execute a file (but not\
necessarily view or edit it).



* Granting Ownership to an Individual User ubob&#x20;

```
chown ubob /tmp/bobsfile
```

* Granting Ownership to a group usecurity&#x20;

```
chgrp usecurity /tmp/groupfiles
```

* Permissions table
  *

      <figure><img src="../../../../../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>
* Changing mode of file&#x20;

```
chmod 774 hashcat.hcstat

or in UGO notation

chmod u+rwx, g+rwx, o+er hashcat.hcstat

```

Linux automatically assigns base permissions—usually\
666 for files and 777 for directories. You can change the default permissions\
allocated to files and directories created by each user with the umask (or\
unmask) The umask value is not universal to all users on the system. Each user\
can set a personal default umask value for the files and directories in their\
personal .profile file.

<figure><img src="../../../../../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

In addition to the three general-purpose permissions, rwx, Linux has three\
special permissions that are slightly more complicated. These special permissions are set user ID (or SUID), set group ID (or SGID), and sticky bit.  The sticky bit is a permission bit that you can set on a directory to allow a user to delete or rename files within that directory.

Basically, the SUID bit says that any user can execute the file with the permissions of the owner but those permissions don’t extend beyond the use of\
that file.

* Setting the SUID on a file is not something a typical user would do, but if  \
  you want to do so, you’ll use the chmod command, as in&#x20;

```
chmod 4644 filename
```

SGID also grants temporary elevated permissions, but it grants the permissions\
of the file owner’s group, rather than of the file’s owner. This means that,\
with an SGID bit set, someone without execute permission can execute a file if\
the owner belongs to the group that has permission to execute that file.\
The SGID bit works slightly differently when applied to a directory: when\
the bit is set on a directory, ownership of new files created in that directory\
goes to the directory creator’s group, rather than the file creator’s group.\
This is very useful when a directory is shared by multiple users. All users in\
that group can execute the file(s), not just a single user.\


* Setting The SGID bit is represented as 2 before the regular permissions

```
chmod 2644 filename.
```

### Summary Table

| Special Bit | Symbol       | On Files                | On Directories                                |
| ----------- | ------------ | ----------------------- | --------------------------------------------- |
| **SUID**    | `s` (user)   | Run as file **owner**   | No effect                                     |
| **SGID**    | `s` (group)  | Run as file’s **group** | New files inherit group                       |
| **Sticky**  | `t` (others) | Obsolete (was caching)  | <p></p><p>Only owner can delete own files</p> |

* `ls -l` will show `s` or `t` instead of `x`.
* `chmod` numeric values:
  * `4` = SUID
  * `2` = SGID
  * `1` = Sticky



## Linux Special Permissions (Easy Version)

Normally, files and folders have **r (read), w (write), x (execute)** for _owner, group, others_.\
But there are **3 extra special permissions**:

***

#### 1. **SUID (Set User ID)**

* **What it does:** If a program has SUID, it runs as the **owner of the file**, not the person who started it.
* **Why useful:** Lets normal users do something that normally only the owner (often root) can do.
* **Example:** The `passwd` command (used to change your password).
  * You run it as a normal user → it runs with root’s power → it can edit the password file.

***

#### 2. **SGID (Set Group ID)**

* **What it does on a file:** Program runs with the **file’s group**, not your group.
* **What it does on a folder:** All new files inside get the **same group as the folder**, not the user’s default group.
* **Why useful:** Shared project folders. Everyone in the group automatically shares new files.

***

#### 3. **Sticky Bit**

* **What it does on a folder:** Only the person who made a file can delete it (even if others have write access).
* **Why useful:** In `/tmp` (a folder everyone uses), you don’t want other users deleting your stuff.

***

## Quick Memory Trick

* **SUID = runs as User (file owner)**
* **SGID = runs as Group (file’s group)**
* **Sticky = only owner can Stick (delete own files in shared folder)**



## Process management

* Checking processes for all users

```
ps aux
```



* Changing Process Priority with nice. A high nice value translates to a low priority, and a  \
  low nice value translates to a high priority (when you’re not being so nice  \
  to other users and processes). When a process is started, it inherits the nice  \
  value of its parent process. The owner of the process can lower the priority  \
  of the process but cannot increase its priority. This command would increment the nice value by -10, increasing its priority and allocating it more resources.

```
nice -n -10 /bin/slowprocess
renice 20 6996
```

So, if slowprocess is using an inordinate amount of resources on your system and you want to give it\
a lower priority, thus allowing other processes a higher priority and more resources, you could renice the slowprocess (which has a PID of 6996) and give it a much higher nice value.



* Commonly Used Kill Signals
*

    <figure><img src="../../../../../.gitbook/assets/image.png" alt=""><figcaption></figcaption></figure>
* ```
  kill -9 6996
  killall -9 zombieprocess
  ```
* Runnning in background. Running a process in the background simply means that it will continue to run without needing the terminal. In this way, the terminal is freed up for other duties

```
script_to_run_in_background_name &
```

* To return from background to foreground run fg:

```
fg 1234
```

## Scheduling

In Linux, schedulling can be accomplishedin at least two ways: with at and crond.

The at command is a daemon—a background process—useful for scheduling a job to run once at some point in the future. The crond is more suited for scheduling tasks to occur every day, week, or month.



* When you enter the at daemon with the specified time, at goes into  \
  interactive mode and you are greeted with an at> prompt. Here is where  \
  you enter the command you want executed at the specified time:

```
#> at 7:20am
at >/root/myscanningscript
```



* cron

```
at 7:20am
at >/root/myscanningscript
```

## Enviromental variables

Most commands are located in the sbin or bin subdirectory, like /usr/local/sbin or usr/local/bin. If the bash shell doesn’t find the command in one of the directories in your PATH variable, it will\
return the error command not found, even if that command does exist in a directory not in your PATH.

Environment variables are system-wide variables built into your system and\
interface that control the way your system looks, acts, and “feels” to the\
user, and they are inherited by any child shells or processes. Shell variables,\
on the other hand, are typically listed in lowercase and are only valid in the\
shell they are set in.&#x20;



### When to use `$`?

* Use `$` **when you want to get (read) the value** of the variable.
* No `$` when **setting** a variable.



* to view default

```
env    
```

* to view all enviroment

```
set
```

* to set permenantly

```
variable=value
export variable
```



* to append to PATH

```
export PATH=$PATH:/opt/myapp/bin
```



## Archives



* Create archive

```
tar -cvf new_archive_name file1 file2 file2    
```



* Extract archive

```
tar -xvf HackersArise.tar  
```



* Review archive

```
tar -tvf new_archive_name
```





Compress

Linux has several commands capable of creating compressed files. We will\
look at these:

\
• gzip, which uses the extension .tar.gz or .tgz

• bzip2, which uses the extension .tar.bz2\
• compress, which uses the extension .tar.z

```
gzip HackersArise.*
gunzip HackersArise.*
```

```
bzip2 HackersArise.*
bunzip2 HackersArise.*
```

```
compress HackersArise.*
uncompress HackersArise.*
```



Bit level copy

```
dd if=/dev/sdb of=/root/flashcopy
```



