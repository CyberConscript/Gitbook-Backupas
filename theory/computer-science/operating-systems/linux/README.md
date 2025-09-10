# Linux

## Distributions

Popular Linux Distributions Several Linux distributions have gained popularity and are commonly used in various contexts:

1. Ubuntu: Ubuntu is a user-friendly distribution known for its ease of use and widespread adoption. It offers long-term support (LTS) releases for stability and regular releases with updated software. Debian based.
2. Red Hat Enterprise Linux (RHEL): RHEL is a commercial distribution known for its stability and support in enterprise environments. CentOS, a community-driven project, was closely related to RHEL until changes in its development.
3. Fedora: Fedora is the community-driven upstream distribution for RHEL. It features cutting-edge software and serves as a testing ground for new technologies.
4. openSUSE: openSUSE offers two main distributions: Leap, which focuses on stability, and Tumbleweed, a rolling-release distribution for the latest software.
5. 5\. Debian: Debian is known for its commitment to free and open-source software principles. It is the foundation for many other distributions, including Ubuntu and Kali Linux.
6. Arch Linux: Arch Linux is a minimalist, rolling-release distribution that allows users to build a custom system. It is favored by users who want complete control over their setup.&#x20;



Specialized Distributions Beyond general-purpose distributions, there are specialized distributions designed for specific tasks or industries:&#x20;

• Kali Linux: Kali Linux is tailored for penetration testing and ethical hacking, providing a suite of security tools. Debian based.

• Raspbian: Raspbian is designed for Raspberry Pi single-board computers, making it ideal for educational and IoT projects.

• Tails: Tails is a privacy-focused distribution that routes internet traffic through the Tor network for anonymous browsing.&#x20;

• Ubuntu Studio: Ubuntu Studio is geared toward multimedia production, offering a range of audio, video, and graphics software.



## System Updates and Security

\
Linux excels in system updates and security, thanks to its package\
management systems, such as APT and YUM. Updates are centralized,\
making it straightforward to keep the system secure and up to date. In contrast, some proprietary operating systems require users to manage updates individually for various software components.

Before performing system updates, it's essential to update the package list\
to ensure you have the latest information about available packages. Once you've updated the package list, you can perform system updates to upgrade your installed software to the latest versions:

\
• **APT** (Advanced Package Tool): Used by Debian and Debian-based\
distributions like Ubuntu, Kali.

`apt-get`

`apt update`

`apt upgrade`

`apt full-upgrade`

`apt install package-name`

`apt remove package-name`

`apt autoremove`

\
• **RPM** (Red Hat Package Manager): Used by Red Hat, CentOS, Fedora,\
and related distributions.

• **Pacman**: Used by Arch Linux and its derivatives.

pacman -Sy

\
• **YUM** and **DNF**: Used by some RPM-based distributions.\
Understanding the package management system is essential because it\
affects how you install and manage software on your system. Used by Red Hat, CentOS, Fedora, and related distributions.

yum check-update

yum install package-name

yum remove package-name

### Release Cycles

\
Distributions follow different release cycles, which dictate how often new\
versions are released and the level of stability provided:\
• **Fixed/Point Release**: These distributions have stable releases with a\
predetermined lifecycle. Examples include Ubuntu LTS (Long-Term\
Support) and CentOS.\
• **Rolling Release**: Rolling-release distributions continuously update their\
software, offering the latest features and improvements. Examples include\
Arch Linux and openSUSE Tumbleweed.\
• **Regular Release**: These distributions follow a regular release schedule,\
typically, every six months to two years. Ubuntu’s regular releases fall into\
this category.\


## Common Desktop Environments

\
Linux offers a variety of desktop environments, each with its own look,\
feel, and set of features. Some of the most popular desktop environments\
include:\
• GNOME: Known for its modern and minimalist design, GNOME is the\
default desktop environment for many distributions, including Ubuntu.• KDE Plasma: KDE Plasma provides a highly customizable and featurerich desktop experience. It’s the default desktop environment for\
distributions like KDE Neon and openSUSE.\
• Xfce: Xfce is a lightweight and resource-efficient desktop environment\
suitable for older hardware or users who prefer simplicity.\
• Cinnamon: Cinnamon offers a traditional desktop experience, making it\
a popular choice for users transitioning from other operating systems.\
• LXQt: LXQt is another lightweight desktop environment designed for\
efficiency and speed.\
• MATE: MATE is a continuation of the GNOME 2 desktop environment,\
known for its familiarity and robustness.



## Desktop Elements&#x20;

Let’s explore some common elements you’ll encounter in most Linux desktop environments:

1. Desktop Wallpaper: The background image on your desktop is called the wallpaper. You can change it to suit your preferences. To change the wallpaper, right-click on the desktop and look for a “Change Background” or similar option.2. Panel or Taskbar: The panel, often located at the bottom or top of the screen, contains various elements like the application menu, system tray, and quick launch icons for frequently used applications.
2. Application Menu: Clicking on the application menu icon opens a menu where you can access installed applications and system settings. You can typically search for applications by name or browse categories.
3. System Tray: The system tray, also known as the notification area, displays icons for system utilities, application status, and notifications. You can access settings and interact with these icons.
4. File Manager: The file manager is used for navigating your file system, managing files and folders, and launching applications. It often includes features like a sidebar for quick access to common locations, file previews, and customizable views.
5. Window Manager: The window manager handles the placement and management of open windows. You can move, resize, minimize, and maximize windows using its features.
6. Workspaces:Many desktop environments support multiple workspaces, allowing you to organize your applications across different virtual desktops. This can help keep your workflow organized.



## Keyboard Shortcuts

\
Efficiently using your desktop environment often involves learning\
keyboard shortcuts for common tasks. Here are some essential keyboard\
shortcuts that work in many Linux desktop environments:\
• Ctrl + Alt + T: Opens a terminal window.\
• Alt + Tab: Switches between open applications.\
• Alt + F2: Opens a run dialog to launch applications by typing their\
names.\
• Super/Windows key: Opens the application menu or the system\
overview (depends on the desktop environment).\
• Alt + Space: Opens the window menu for the active application.\
• Ctrl + Alt + Arrow keys: Switches between workspaces or virtual\
desktops.\
• Alt + F4: Closes the active window.





## Automation and Scripting&#x20;

The command line is essential for automation and scripting tasks. You can create shell scripts to automate repetitive tasks or perform complex operations. Shell scripts are sequences of commands saved in a file that can be executed as a single unit. For example, a simple shell script might automate the process of backing up your important files to an external drive every night.&#x20;

`#!/bin/bash`

## `Backup scriptrsync -av /home/user/documents /media/external_drive/backup`

Here are a few essential commands:\
• ls: List files and directories in the current directory.\
• cd: Change the current working directory.\
• pwd: Print the current working directory.\
• mkdir: Create a new directory.\
• touch: Create an empty file.\
• cp: Copy files and directories.\
• mv: Move or rename files and directories.\
• rm: Remove files and directories.\
• cat: Display the contents of a file.\
• grep: Search for text within files.\
• ps: List running processes.\
• top or htop: Monitor system resource usage.\
• df: Display disk space usage.\
• du: Display directory space usage.



Finding Files\
The find command is a powerful tool for locating files and directories based\
on various criteria. For example, to find all text files in the current directory\
and its subdirectories that contain the word “linux,” you can use:`$ find . -type f -name "`_`.txt" -exec grep -l "linux" {} ;`_\
_This command starts the search from the current directory (.), specifies that_\
_it should only look for regular files (-type f), searches for files with the .txt_\
_extension (-name "_.txt"), and then uses grep to search within those files for\
the specified text

## System Administration&#x20;

System administrators rely heavily on the command line for managing and configuring servers and networks. Many server-side tasks are best performed through the command line, allowing administrators to remotely manage systems and automate routine maintenance tasks.&#x20;

Additional drives and other storage devices are\
mounted upon that filesystem, leading up to the / (root) directory.\
Mounting in this context simply means attaching drives or disks to the\
filesystem to make them accessible to the operating system (OS).



Originally, Linux represented floppy drives (remember those?) as fd0\
and hard drives as hda. You will still occasionally see these drive representations on legacy Linux systems, but today most floppy drives are gone\
(thank goodness). Even so, old legacy hard drives that used an IDE or\
E-IDE interface are still represented in the form hda. Newer Serial ATA\
(SATA) interface drives and Small Computer System Interface (SCSI) hard\
drives are represented as sda. Drives are sometimes split up into sections\
known as partitions, which are represented in the labeling system with numbers, as you’ll see next.\
When systems have more than one hard drive, Linux simply names\
them serially by incrementing the last letter in alphabetical order, so the\
first drive is sda, and the second drive is sdb, the third drive is sdc, and so\
on.

At times, you may want to view the partitions on your Linux system to\
see which ones you have and how much capacity is available in each.

```
fdisk -l

```

crw------- 1 root root 10,175 May 16 12:44 agpgart\
These letters represent the two ways that devices transfer data in and\
out. The c stands for character, and these devices are known, as you might\
expect, as character devices. External devices that interact with the system\
by sending and receiving data character by character, such as mice or keyboards, are character devices.\


The b stands for the second type: block devices. They communicate in\
blocks of data (multiple bytes at a time) and include devices like hard drives\
and DVD drives. These devices require higher-speed data throughput and\
therefore send and receive data in blocks (many characters or bytes at a\
time). List Block Devices and Information with **lsblk**

#### Mounting

A storage device must be first physically connected to the filesystem and\
then logically attached to the filesystem in order for the data to be made\
available to the operating system. In other words, even if the device is physically attached to the system, it is not necessarily logically attached and available to the operating system.

As mentioned, the point in the directory tree where devices are attached\
is known as the mount point. The two main mount points in Linux are /mnt\
and /media. As a general rule, internal hard drives are mounted at /mnt, and\
external USB devices such as flash drives and external USB hard drives are\
mounted at /media, though technically any directory can be used

The filesystems that are mounted on a system are kept in a file at /etc/\
fstab (short for filesystem table).



#### Getting Information on Mounted Disks

The command df (for disk free) will provide us with basic information on\
any hard disks or mounted devices, such as CD, DVD, and flash drives,\
including how much space is being used and how much is available



### Checking for Errors

***



* `fsck` (**filesystem check**) finds and repairs filesystem errors.
* If repair is not possible, it marks bad areas as unusable.
* Always **unmount the drive before running fsck**.

***

#### Steps:

1.  Try running `fsck` on a mounted device → it fails:

    ```bash
    fsck /dev/sda1
    e2fsck: Cannot continue, aborting.
    ```
2.  Unmount the device first:

    ```bash
    umount /dev/sdb1
    ```
3.  Run `fsck` with `-p` to auto-fix problems:

    ```bash
    fsck -p /dev/sdb1
    ```

***



***

Do you want me to also make a **cheat-sheet style version** (like a mini reference card with only commands + purpose)?

### Users and Permissions: A Security Primer

\
User management and permissions are vital aspects of Linux security. Understanding how user accounts work and how permissions are assigned&#x20;\
is crucial for maintaining the integrity of your system.&#x20;

#### &#xD;User Accounts

\
In Linux, each person who uses the system has a user account. User\
accounts are used to log in, access resources, and perform actions on the\
system. Some key concepts related to user accounts include:

• Usernames: Each user has a unique username that identifies them on the\
system. Usernames are case-sensitive.\
• User IDs (UIDs): Behind the scenes, each user is assigned a numerical\
User ID (UID). The root user typically has UID 0, and other users are\
assigned UIDs starting from 1000 and increasing.\
• Groups: Users can belong to one or more groups, which provide a way to\
manage permissions more efficiently. Each group also has a Group ID\
(GID).

Sure, here’s a plain text version of common user management commands in Linux:

***

**User Management**

* `adduser [username]` — Add a new user (Debian-based systems).
* `useradd [username]` — Add a new user (generic command).
* `passwd [username]` — Set or change password for user.
* `usermod [options] [username]` — Modify an existing user.
* `userdel [username]` — Delete a user account.
* `userdel -r [username]` — Delete user and their home directory.

***

**Group Management**

* `groupadd [groupname]` — Create a new group.
* `groupdel [groupname]` — Delete a group.
* `groupmod [options] [groupname]` — Modify group.
* `gpasswd [groupname]` — Administer group settings.

***

**Add/Remove Users to/from Groups**

* `usermod -aG [group] [user]` — Add user to group (append).
* `gpasswd -a [user] [group]` — Add user to group.
* `gpasswd -d [user] [group]` — Remove user from group.

***

**Viewing Users and Groups**

* `id [username]` — Show UID, GID, and groups.
* `whoami` — Show current logged-in username.
* `groups [username]` — Show groups for user.
* `getent passwd` — List all users.
* `getent group` — List all groups.

***

**Home Directory and Shell**

* `useradd -m [user]` — Create user with home directory.
* `useradd -s /bin/bash [user]` — Set login shell.
* `usermod -d /new/home [user]` — Change home directory.
* `chsh -s /bin/zsh [user]` — Change user shell.

***

**Account Locking and Expiry**

* `passwd -l [user]` — Lock user account.
* `passwd -u [user]` — Unlock user account.
* `usermod -e YYYY-MM-DD [user]` — Set account expiration date.
* `usermod -L [user]` — Lock account.
* `usermod -U [user]` — Unlock account.
* `chage [options] [user]` — Manage password expiration.

***

**Important Files**

* `/etc/passwd` — User account information.
* `/etc/shadow` — Encrypted passwords and expiration data.
* `/etc/group` — Group information.
* `/etc/sudoers` — Sudo permissions (edit with `visudo`).

***

**View Permissions**

* `ls -l` — List files with permissions.
* `stat [file]` — Detailed file permission and ownership info.

***

**Change File/Directory Permissions**

* `chmod [permissions] [file]` — Change file/directory permissions (symbolic or numeric).
  * Example (numeric): `chmod 755 script.sh`
  * Example (symbolic): `chmod u+x file.txt`

***

**Change Ownership**

* `chown [user] [file]` — Change owner of file.
* `chown [user]:[group] [file]` — Change owner and group.
  * Example: `chown john:developers file.txt`

***

**Change Group**

* `chgrp [group] [file]` — Change group ownership only.
  * Example: `chgrp staff report.txt`

***

**Special Permission Bits**

* `chmod +s [file]` — Set SUID or SGID on file.
* `chmod +t [directory]` — Set sticky bit on directory (e.g., `/tmp`).

#### **SUID (Set User ID)**

* Applies to **executable files**.
* When a file with the SUID bit is executed, it **runs with the permissions of the file owner**, not the user running it.
* Common use: let normal users run a command with **root privileges** (safely).



#### **Sticky Bit**

* Applies to **directories**.
* Prevents users from deleting files they **don't own**, even if they have write permissions to the directory.

**Commonly used on:**

* `/tmp` directory — everyone can write, but only delete their own files.

drwxrwxrwt 10 root root 4096 /tmp

```
The t at the end indicates the sticky bit.
```

## Remote Access&#x20;

The command line is a crucial tool for remote access to Linux servers and systems. Tools like SSH (Secure Shell) enable secure remote connections, allowing you to manage a system remotely as if you were physically present. This is invaluable for server administration, remote troubleshooting, and accessing systems in various locations.
