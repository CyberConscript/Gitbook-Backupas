# Implementing a Secure SSH Server

### Scenario <a href="#scenario" id="scenario"></a>

The Secure Shell (SSH) protocol is a common protocol for establishing remote connections to Linux, Unix, and other Unix-like systems. SSH functionality can be added to Windows, too. In this activity, you will configure several security settings on a remote destination SSH server named LX1. You'll be testing connectivity from the PT1-Kali virtual machine.



### Remotely connect by using SSH with basic password authentication <a href="#remotely-connect-by-using-ssh-with-basic-password-authentication" id="remotely-connect-by-using-ssh-with-basic-password-authentication"></a>

In this activity, the PT1-Kali Linux virtual machine will remotely connect to the LX1 VM by using the Secure Shell (SSH). In this case, the PT1-Kali VM is the SSH client, and the LX1 VM is the SSH server.

1. &#x20;Log on to the [PT1-Kali](https://labclient.labondemand.com/Instructions/d5b172f2-173d-4c1c-ae61-14b7e77356c4?rc=10) Linux workstation with the root username and the Pa\$$w0rd password.
2. &#x20;From the top bar, select the **Terminal Emulator** icon.
3.  &#x20;Run the following command to check the status of port 22 on the remote LX1 SSH server:

    ```bash-notab-nocopy
    nmap 10.1.0.10 -p 22
    ```

    > The remote LX1 server is running the CentOS 7 Linux distribution. This distribution is derived from Red Hat Enterprise Linux (RHEL).
4.  What is the status of the ssh port on the destination 10.1.0.10 LX1 server?

    ClosedUnable to determineOpen
5.  &#x20;Run the following command to test SSH connectivity to the CentOS SSH server:

    ```bash-notab-nocopy
    ssh root@10.1.0.10
    ```
6. &#x20;Enter yes when prompted to confirm the connection. This is the host key, which validates the identity of the server.
7.  &#x20;Enter Pa\$$w0rd when prompted for the password. This is the password for a user account with local logon that is authenticated by the SSH server.

    > Most Linux systems are configured to permit SSH connections through the firewall by default.
8.  &#x20;Run the following commands to verify that you are connected to the remote SSH server:

    ```bash-notab-nocopy
    hostname
    ```

    ```bash-notab-nocopy
    ip addr
    ```

    You should see a hostname of LX1 and an IP address of 10.1.0.10. Many Linux distributions also display the current user and hostname of the server in the command prompt. Observe how the prompt currently displays root@LX1.

    > The loopback address (127.0.0.1) is configured on each TCP/IP host, and the eth1 configuration represents and additional network adapter installed on the virtual machine.
9.  &#x20;Run the following command to prove you have administrative privileges on the remote server:

    ```bash-notab-nocopy
    systemctl restart rsyslog
    ```
10. &#x20;Use the touch command to create a new file named kali-ssh-test in the root user's home directory on the remote CentOS server.
11. Confirm that the /root/kali-ssh-test file exists.

    Correct
12. > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
13. &#x20;Type exit to disconnect from the remote CentOS server.



### Configure the CentOS SSH server <a href="#configure-the-centos-ssh-server" id="configure-the-centos-ssh-server"></a>

You will configure increased security settings for the SSH server.

1. &#x20;Switch to the [LX1](https://labclient.labondemand.com/Instructions/d5b172f2-173d-4c1c-ae61-14b7e77356c4?rc=10) SSH server.
2. &#x20;The VM's privacy screen is probably enabled - click anywhere on the screen with the mouse and press **ENTER**. A login prompt should appear.
3. &#x20;Sign in with the preconfigured centos account and a password of Pa\$$w0rd.
4. &#x20;Right-click the desktop, and select **Open Terminal**.
5.  &#x20;Run the following command to elevate your credentials to root:

    ```bash-notab-nocopy
    su - root
    ```

    > Note that there is a space on each side of the dash.
6. &#x20;Type Pa\$$w0rd when prompted.
7.  &#x20;Run the following commands to create a new user and set a password:

    ```bash-notab-nocopy
    useradd user01
    ```

    ```bash-notab-nocopy
    passwd user01
    ```
8.  &#x20;Set the password as Pa\$$w0rd when prompted. You may ignore any warnings about the password quality.

    > Recall that Linux does not print any characters to the display when you enter a password. It may appears as though the passwd is not receiving your keystrokes, but it is.
9.  &#x20;Run the following command to back up the current **/etc/ssh/sshd\_config** configuration file:

    ```bash-notab-nocopy
    cp /etc/ssh/sshd_config ~/sshd_config_old
    ```

    > It is a good practice to back up a configuration file before making changes to it so that you can easily roll back to a known good configuration.
10. &#x20;Run the following command to open the SSH configuration file with the Vim text editor:

    ```bash-notab-nocopy
    vim /etc/ssh/sshd_config
    ```
11. &#x20;Review the following list of the required SSH configurations defined by your company's written security policy:
    * Empty passwords are not allowed for SSH authentication. **Disable the empty password** option.
    * Idle SSH connections should be disconnected after **five minutes** (300 seconds). The system should check twice before disconnecting.
    * The following banner message should be configured: "Warning! Authorized use only!" The message is set in the **/etc/issue.net** file and called with the /etc/ssh/sshd\_config file.
12. &#x20;In the text editor, edit the /etc/ssh/sshd\_config file to match the required settings. You will need to uncomment some lines and then edit them. Other lines you may simply edit.

    > The **#** hash character identifies comment lines. Comments are ignored by the system and used to provide administrators with examples, explanations, and additional information within the body of a configuration file or script.
13. &#x20;In Vim, save your changes by pressing **ESC**, and then typing :wq.
14. &#x20;Use Vim to edit the **/etc/issue.net** file. Remove all of the existing content in the file, and then add the following warning:

    ```notab-nocopy-nocolor
    Authorized use only!
    ```
15. &#x20;To save changes and quit Vim, press **ESC**, and then type :wq
16. Confirm that the banner file exists.

    Correct

* > Don’t forget to use exactly the same names as specified in the instructions.
*   &#x20;In the command prompt window, run the following command to restart the SSH service:

    ```bash-notab-nocopy
    systemctl restart sshd
    ```

    > Recall that each time you change a configuration file, you must restart the service for the change to take effect.



### SSH key-based authentication <a href="#ssh-key-based-authentication" id="ssh-key-based-authentication"></a>

Configure key-based authentication for the SSH server. Key-based authentication is more secure and it alleviates the need to remember passwords. A private key is stored on the client computer and a related public key is copied to the remote SSH server. During the authentication process, the two keys are compared instead of a password being submitted.

1.  &#x20;On the [PT1-Kali](https://labclient.labondemand.com/Instructions/d5b172f2-173d-4c1c-ae61-14b7e77356c4?rc=10) VM, confirm that the command prompt is _root@KALI_ to ensure that you do not currently have an SSH connection to the remote LX1 SSH server.

    > Type exit to disconnect an SSH session.
2.  &#x20;Run the following commands to create new user named user01 with Pa\$$w0rd as the password:

    ```bash-notab-nocopy
    adduser user01
    ```
3. &#x20;Type Pa\$$w0rd twice when prompted. Press **ENTER** for all other user account options.
4.  &#x20;Run the following command to switch to the new _user01_ user:

    ```bash-notab-nocopy
    su - user01
    ```

    You are not prompted for a password because you are de-escalating your privileges from root down to a standard user.
5.  &#x20;Run the following command to generate an SSH key pair that identifies user01:

    ```bash-notab-nocopy
    ssh-keygen
    ```
6. &#x20;Press **ENTER** three times to accept the default settings.
7.  &#x20;Run the following command to copy the public key to the SSH server:

    ```bash-notab-nocopy
    ssh-copy-id -i ~/.ssh/id_rsa.pub user01@10.1.0.10    
    ```
8. &#x20;Enter yes when prompted. Enter Pa\$$w0rd when prompted.
9.  &#x20;Run the following command to to connect to the SSH server and confirm that key-based authentication works:

    ```bash-notab-nocopy
    ssh user01@10.1.0.10
    ```
10. Were you challenged for a password?

    No, because the keys were used for authentication instead of a passwordYes, because password authentication is always enabled for SSH

*
* &#x20;Type exit to terminate the SSH connection.



## Review the SSH log file <a href="#review-the-ssh-log-file" id="review-the-ssh-log-file"></a>

You will display SSH log file entries on the LX1 SSH server to understand which users are remotely connecting to your server.

1. &#x20;Switch to the [LX1](https://labclient.labondemand.com/Instructions/d5b172f2-173d-4c1c-ae61-14b7e77356c4?rc=10) VM. If the VM's privacy screen is enabled, press **ENTER**. Sign in as the preconfigured centos user with a password of Pa\$$w0rd.
2. &#x20;If a terminal window is not already open, right-click on the desktop, and select **Open Terminal**.
3.  &#x20;Run the following command to generate an entry in the _/var/log/messages_ log file:

    ```bash-notab-nocopy-nocolor
    logger "test message"
    ```

    > Don’t forget to use exactly the same names as specified in the instructions.
4.  &#x20;Run the following commands to view the lines at the bottom of the _/var/log/secure_ log file:

    ```bash-notab-nocopy-nocolor
    tail /var/log/messages
    ```

    You should see the "test message" string near the bottom of the output.
5.  &#x20;Run the following command to view SSH events in the log file:

    ```bash-notab-nocopy-nocolor
    tail /var/log/secure | grep -i ssh
    ```
6.  Confirm that SSH entries appear in the /var/log/secure log file on the CentOS virtual machine.

    Unable to connect to machine at address 172.20.180.176. Connection refused

<details>

<summary>The tail command.</summary>

If there are no results, re-run the tail command above and ensure you have spelled everything correctly. You may also switch to the PT1-Kali VM, establish a new SSH connection, and then search the log file again. Entries may be stored in a log named secure-(today's-date).

</details>

> The most recent log file entries are written at the bottom of the files, so tail is a great tool to use to see the most current information. The head command displays the entries at the top of the file.



### Prevent root from authenticating over SSH <a href="#prevent-root-from-authenticating-over-ssh" id="prevent-root-from-authenticating-over-ssh"></a>

The final settings you will implement prevent the root user from accessing the server remotely via SSH and require key-based authentication only.

1. &#x20;Review the following list of the required SSH configurations defined by your company's written security policy:
   * Root user accounts should not be able to authenticate via SSH. **Disable root user access** over SSH.
   * Key-based authentication is required and password authentication should be explicitly denied. **Disable passwords** over SSH.
2. &#x20;On the [LX1](https://labclient.labondemand.com/Instructions/d5b172f2-173d-4c1c-ae61-14b7e77356c4?rc=10) VM, use the Vim text editor to open the /etc/ssh/sshd\_config file.
3.  &#x20;Uncomment the following line by deleting the **#** character, and the change the entry from "yes" to "no" to prevent the root user from signing in via SSH:

    ```bash-notab-nocopy-nocolor
    PermitRootLogin no    
    ```
4.  &#x20;Change the entry on the following line from "yes" to "no" to prevent password-based authentication.

    ```bash-notab-nocopy-nocolor
    PasswordAuthentication no
    ```

    > The SSH connection may be established with a standard user account, such as user01. Once the connection is made and you are "on" the remote server, you may use the su - root command to elevate your privileges, if necessary.
5. &#x20;Select **ESC**, and then type :wq to save your changes and exit Vim.
6.  &#x20;Run the following command to restart the SSH service, causing it to re-read the configuration file and apply the new settings:

    ```bash-notab-nocopy
    systemctl restart sshd
    ```
7. &#x20;Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/d5b172f2-173d-4c1c-ae61-14b7e77356c4?rc=10) virtual machine.
8.  &#x20;Attempt the SSH connection by using the root credentials.

    > This should fail with a "Permission denied" message. One of your previous configurations was to block root user authentication over an SSH connection.
9. &#x20;Attempt the SSH connection by using the user01 credentials.
10. Which TWO reasons best describe why user01 was able to establish an SSH connection but root was not?

    The wrong password was typed for the root user.The root user was explicitly denied in the LX1 sshd\_config file.The root user was not configured for key-based authentication.The user01 user was configured for key-based authentication.Port 22/tcp was closed on the LX1 virtual machine's firewall.The root user was explicitly denied in the PT1-Kali sshd\_config file.

Correct
