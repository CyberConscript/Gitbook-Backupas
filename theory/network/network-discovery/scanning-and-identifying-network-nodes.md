# Scanning and Identifying Network Nodes

### Scenario <a href="#scenario" id="scenario"></a>

In this activity, you will use common network tools, such as local commands and the Nmap network mapper, to discover other hosts on the local network. Next, you will conduct a banner grabbing exercise to identify specific services on the hosts. Finally, you will use DNS tools to gather name resolution information.

### Identify local network configuration <a href="#identify-local-network-configuration" id="identify-local-network-configuration"></a>

Determine the configuration of the local host and its subnet, using tools such as **ifconfig**, **ip**, **arp**, **netdiscover**, and **pathping**. Run the scans from the KALI Linux VM and the DC1 Windows Server.

1.  &#x20;On the PT1-Kali VM, sign in as root using Pa\$$w0rd as the password.

    > If the privacy shade has activated, click-and-drag up with the mouse to show the sign-in box.
2. &#x20;From the top bar, select the Terminal Emulator icon .
3.  &#x20;Run the ifconfig command to display the interface configuration. Note the IP address assigned to the eth0 interface.

    ```bash-notab-nocopy
    ifconfig
    ```
4.  &#x20;Run the ip a command to display the same information using the newer ip a tool:

    ```bash-notab-nocopy
    ip a
    ```
5. What is the IP address for the eth0 adapter of the PT1-Kali Linux virtual machine? (answer format: 1.2.3.4)
6. > The purpose behind Assisted Labs is to confirm your knowledge and guide you through the given configurations. If you get a scored question incorrect, you may repeat the question and achieve the correct answer. You do not need a correct answer to move forward through the lab.
7.  &#x20;Run the following command to identify the default gateway:

    ```bash-notab-nocopy
    ip route show
    ```

    Because the network uses DHCP to provide client addresses, the local machine has been configured with a default gateway address automatically.
8. What is the IP address of the router? (format 1.2.3.4)
9. Correct
10. &#x20;Run the arp -a command to check the ARP cache to display other hosts local to this subnet.

    ```bash-notab-nocopy
    arp -a
    ```
11. What is the IP address for the DC1.corp.515support.com virtual machine? (format 1.2.3.4)
12. Correct
13. &#x20;Run the ip neighbor command to display similar information using the newer ip tool.

    ```bash-notab-nocopy
    ip neighbor
    ```

    The ARP cache shows only machines that have communicated with the local host. To verify whether any other hosts are present, you can perform a "sweep" of the local network. One means of doing this is to use **ping** in a for/next loop. You can also use the **netdiscover** tool bundled with Kali.
14. &#x20;Run the following command to scan the network by using **netdiscover**. The results should discover several other hosts connected to the vLOCAL switch.

    ```bash-notab-nocopy
    netdiscover -i eth0 -r 10.1.0.0/24
    ```

    > The netdiscover may take up to two minutes to complete _after_ it reports as Finished.
15. How many hosts were found by netdiscover?
16. Correct
17. &#x20;Press q to exit the Netdiscover report and return to the command prompt.

    > Run netdiscover -h to view the help page. The tool can operate in a passive mode, but you do not need to be stealthy, so you will run an active scan.
18. &#x20;Switch to the DC1 VM, send Ctrl+Alt+Delete, and then login as 515support\Administrator using Pa\$$w0rd as the password.
19. &#x20;Right-click the **Start** menu and select **Command Prompt (Admin)**. When prompted, confirm UAC by selecting **Yes**
20. &#x20;Run the following command to display the IP address configuration for DC1:

    ```cmd-notab
    ipconfig
    ```
21. What is the IP address for the DC1 virtual machine? (answer format: 1.2.3.4)
22. Correct
23. &#x20;Run the following command to test the reliability (packet loss) and latency (delay) of the connection between the **DC1** VM and the **PT1-Kali** VM (the test takes 30-45 seconds to run):

    ```cmd-notab
    pathping 10.1.0.192
    ```
24. What percentage of packets were lost during this test? (Reply with values such as 0%, 50%, 100%, etc)



### Use nmap to discover hosts <a href="#use-nmap-to-discover-hosts" id="use-nmap-to-discover-hosts"></a>

From a penetration tester or threat actor perspective, network reconnaissance will typically aim to discover the following:

* Default gateway (the router connecting the subnet to other networks).
* DNS server (used to resolve host names on the network).
* Whether any network directory/authentication and application servers are present.
* Whether any host/client access devices are present.
* Whether any other types of devices (embedded systems or appliances) are present.

Use Nmap from the PT1-Kali VM to report this information for this network.

1. &#x20;Switch back to PT1-Kali. If necessary, log in as root using Pa\$$w0rd as the password.
2.  &#x20;Run the following command to scan the Kali VM:

    ```bash-notab-nocopy
    nmap localhost
    ```
3.  What port is open on the virtual machine?

    22/tcp53/udp161/udp80/tcp443/tcp
4.  &#x20;Run the following command to do a basic network scan:

    ```bash-notab-nocopy
    nmap 10.1.0.0/24
    ```
5.  &#x20;Run the following command and check the output. What services are running and what do they tell you about the host?

    ```bash-notab-nocopy
    nmap -sS 10.1.0.254
    ```

    This syntax will scan the default port range (1000 ports) on the target.
6.  What services are running on this virtual machine (the router)?

    Email and file transfer servicesSSH and DNS servicesSSH and web servicesWeb and email services
7.  &#x20;Run the following command to identify more about the host:

    ```bash-notab-nocopy
    nmap -A 10.1.0.254
    ```
8.  What operating system is running on the 10.1.0.254 host?

    LinuxWindows ServerWindows 10macOSMS-DOS
9.  &#x20;Run the following command to scan for open ports **20-200** on the network:

    ```bash-notab-nocopy
    nmap -p 20-200 10.1.0.0/24
    ```
10. Is port 80 open on MS1?
11. &#x20;Run the following command to scan for the **twenty** most common ports:

    ```bash-notab-nocopy
    nmap --top-ports 20 10.1.0.0/24
    ```
12. &#x20;Run the following command to quickly scan the network for hosts that are **up** or **down** on the network:

    ```bash-notab-nocopy
    nmap -sn 10.1.0.0/24
    ```
13. Which server is configured as an email server? (Hint: you'll need to look for the default SMTP port number in the "Ports used" field of each host)

    MS1DC1LX1PC1RT1-Internal

### Banner grab with curl and Firefox <a href="#banner-grab-with-curl-and-firefox" id="banner-grab-with-curl-and-firefox"></a>

Banner grabbing is a way of identifying service versions. This information helps attackers select potentially vulnerable machines. The information also helps administrators confirm that all services on the network are of a certain version.

Basic tools can be used to grab banners. In this activity, you will use cURL and Firefox.

1.  &#x20;Run the following command in the **Terminal** to connect to the 10.1.0.1 HTTP server by using cURL:

    ```bash-notab-nocopy
    curl -s -I 10.1.0.1
    ```
2. What web server service and version is used on the target VM?
3.  &#x20;In Kali, type firefox http://10.1.0.1 and then select **Enter**.

    ```bash-notab-nocopy
    firefox http://10.1.0.1
    ```
4. What web server service is used on the target VM?
5. &#x20;Close the Firefox web browser.

### Query DNS <a href="#query-dns" id="query-dns"></a>

DNS provides name resolution to internal networks as well as the Internet. DNS is used any time a user or application refers to a host by name. DNS queries name records to find the IP address associated with a hostname or fully qualified domain name. These name records can also reveal information about how a network is configured. In this task, you will gather DNS information by using the **dig** utility.

1.  &#x20;Run the dig command in the **Terminal** to perform a reverse lookup on the default gateway.

    ```bash-notab-nocopy
    dig -x 10.1.0.254
    ```
2. What is the IP address of the DNS server that answers the query?
3. Use dig to answer the following question: What is the fully-qualified domain name (FQDN) of the VM found at 10.1.0.2? (Hint: Check the ANSWER SECTION of the output)
4.  &#x20;Run the following command to display the authoritative DNS server for the namespace:

    ```bash-notab-nocopy
    dig soa corp.515support.com
    ```

    The query returns the FQDN of the DNS server responsible for the domain (DC1.corp.515support.com) and its host record (10.1.0.1). It's also worth noting some of the flags shown:

    * aa indicates that the answer is authoritative. The "AUTHORITY" section of the response is empty. Contents for this section are commonly omitted by name servers to reduce the size of responses.
    * ra indicates that recursion is available; that is, this router will forward queries to other servers.
5. &#x20;Close the terminal window.

### Comprehensive questions <a href="#comprehensive-questions" id="comprehensive-questions"></a>

Answer the following final comprehensive questions to ensure that you recognize the importance of the activity steps and the uses for the information you have learned.

1.  Which of the following answers correctly summarizes the steps in this activity?

    Identified the Kali Linux and Windows servers, broke the network's wireless encryption key, intercepted data packets, used banner grabbing to identify services.\
    Identified the Kali Linux and Windows servers, performed basic scans of the network, dentified hosts and services, used banner grabbing to identify services, gathered more DNS information.\
    Cracked the domain administrator's password, performed basic scans of the network, cleared log files, intercepted data packets.Used a phishing attack to gain the administrator's password, used banner grabbing to identify services, identified hosts and services, cleared log files.
2.  Which of the following answers best identifies how an administrator might use the information gathered during this activity?

    To audit passwords.\
    To configure centralized log files/SIEM information.\
    To troubleshoot Internet access.\
    \*To verify expected network and server configurations.
3.  Which of the following answers best identifies how an attacker might use the information gathered during this activity? (Select three)

    \*To decide what servers to attack\
    To crack passwords.\
    \*To check for old services that may be unpatched.\
    \*To map the network in preparation for an attack.\
    To launch a phishing attack.

