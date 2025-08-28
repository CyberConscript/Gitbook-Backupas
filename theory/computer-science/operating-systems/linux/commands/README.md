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







* Powerful Searches with find

```
find <directory> -type <type> <something>
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
special permissions that are slightly more complicated. These special permissions are set user ID (or SUID), set group ID (or SGID), and sticky bit.



