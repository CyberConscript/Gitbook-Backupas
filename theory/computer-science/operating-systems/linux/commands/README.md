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

