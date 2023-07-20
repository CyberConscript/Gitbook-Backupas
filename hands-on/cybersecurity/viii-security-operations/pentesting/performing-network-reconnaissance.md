# Performing Network Reconnaissance

### Scenario <a href="#scenario" id="scenario"></a>

In this activity, you will play the role of penetration tester. You will begin by investigating the network as if you were unfamiliar with it. You will use various tools to acquire and document the layout. You will then specifically investigate a web server. Next, you'll run a credentialed scan against that web server by using OpenVAS. Finally, you'll participate in a test security features as related to malware that installs a remote backdoor. You will close the backdoor at the end of the exercise.



### Discover the network <a href="#discover-the-network" id="discover-the-network"></a>

Use available tools to display information about local machines and the network.

* Linux logon credentials ([PT1-Kali](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) and [LX1](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10)):\
  root and Pa\$$w0rd
* Windows logon credentials ([DC1](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) and [MS1](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10)):\
  515support\Administrator and Pa\$$w0rd

1.  &#x20;Use any or all of the tools from the following list to discover the IP addresses for the virtual machines listed below:

    ```nocopy-nocolor
    ip addr
    ```

    ```nocopy-nocolor
    ifconfig
    ```

    ```nocopy-nocolor
    ipconfig
    ```
2. PT1-Kali (Kali Linux)

* Correct
* LX1 (CentOS Linux)
* Correct
* DC1 (Windows Server 2016)
* Correct
* MS1 (Windows Server 2016)
*   Correct

    > The purpose behind Applied Labs is to prove your ability to configure given settings and display knowledge of concepts, tools, and options. If you get a scored question incorrect, you may not repeat the question or change your answer. You do not need a correct answer to move forward through the lab.
* &#x20;On the [PT1-Kali](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) virtual machine, run an nmap scan to display the VM's own open ports:
* What port is open on PT1-Kali? (example: 23/tcp)
* Incorrect
*   What operating system is running on 10.1.0.254?

    LinuxWindows ServerUnixBSD
* Correct
*   What ports are open on the 10.1.0.254 device? (Choose two)

    22/tcp3389/tcp53/tcp123/upd389/tcp23/tcp

Correct



### Gather information on the web server <a href="#gather-information-on-the-web-server" id="gather-information-on-the-web-server"></a>

You've discovered a web server on the network by using a Nmap. You need to gather more information about the server to understand its possible vulnerabilities.

1. &#x20;On the [PT1-Kali](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) VM, if necessary, sign in as root using Pa\$$w0rd as the password.
2. &#x20;Use the nslookup command on PT1-Kali to display the FQDN for the server at **10.1.0.2**.
3. What is the FQDN for 10.1.0.2?

* Correct
*   &#x20;Run the following command to connect to the 10.1.0.2 HTTP server by using cURL:

    ```bash-notab-nocopy
    curl -s -I 10.1.0.2
    ```

    > You are disconnected automatically.
*   What web server service and version is used on the 10.1.0.2 virtual machine?

    Ngnix 1.18IIS 7IIS 10Apache 2.4Apache 1.9

Correct



### Configure the web server for authentication <a href="#configure-the-web-server-for-authentication" id="configure-the-web-server-for-authentication"></a>

You decide to recommend authentication to access the web server. To test security, you configure Basic Authentication on the IIS server. Next, you will intercept network traffic to verify the level of security.

The 515 Support written security policy states that any web authentication must not expose names and passwords to packet sniffing attacks.

1.  &#x20;Switch to the [MS1](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) VM, select [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10), and then sign in as 515support\Administrator with Pa\$$w0rd.

    You will configure the 10.1.0.2 MS1 web server to to accept basic authentication, which is not encrypted.
2. &#x20;Launch the **Internet Information Services (IIS) Manager**.
3.  &#x20;Use the **Authentication** applet in the Default Web Site Home pane to **Disable** **Anonymous Authentication** and **Enable** **Basic Authentication**.

    > You may ignore the alert about SSL.
4. &#x20;Close the **IIS Manager**.
5. &#x20;Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) VM, and then confirm that you are signed in. If necessary, log on with the credentials root and Pa\$$w0rd.
6.  &#x20;Open a **Terminal** console, and then run the following command to begin intercepting MS1 **HTTP** network traffic by using tcpdump:

    ```bash-notab-nocopy
    tcpdump -vv dst 10.1.0.2 and port www -w auth.txt
    ```
7. &#x20;From the top menu, start **Firefox**, and then connect to the web site hosted at **http://10.1.0.2**.
8.  &#x20;When prompted, enter the following name and password:

    515support\pentester\
    dr0w\$$aP

    > These credentials are not valid, and you will be prompted to authenticate again. The information gathered during the attempt will help a pentester determine what authentication is used for the web site.
9. &#x20;Switch to the **Terminal** window and then select **Ctrl+C** to stop the tcpdump capture.
10. &#x20;Launch the **Wireshark** application. Use Wireshark to open the **auth.txt** file from the root user's home directory.
11. &#x20;Examine the HTTP **Get** messages to answer the following question for authentication information.
12. Which of the following options shows how the authentication information is displayed?

    Credentials: 515support\pentester:dr0w\$$aPCredentials: 515support\pentester\dr0w\$$aPCredentials: pentester:dr0w\$$aPCredentials: pentester\dr0w\$$aP



### Run OpenVAS scanner <a href="#run-openvas-scanner" id="run-openvas-scanner"></a>

OpenVAS can be managed using a web application called Greenbone Security Assistant. You will create a targeted, credentialed scan against the web server discovered above.

1.  &#x20;If necessary, sign on to the [PT1-Kali](https://labclient.labondemand.com/Instructions/ab687866-0bdf-4b6c-8a2f-2bd5c6283764?rc=10) VM, and then sign in as root using Pa\$$w0rd as the password.

    You may already be signed in.
2. &#x20;In the menu at the top of the desktop, select the **Terminal**.
3.  &#x20;In the terminal window, type openvas-start and press **ENTER**. Wait for the prompt to return.

    If you receive a timeout error, run openvas-start again.

    > It may take one to two minutes for the service to start. You must wait before proceeding to the next steps.
4. &#x20;The **Firefox** browser automatically launches when the openvas-service starts. It connects to https://127.0.0.1:9392
5. &#x20;Log on with the Username admin and Password as Pa\$$w0rd.
6.  &#x20;From the **Configuration** menu, select **Credentials** to create a credentialed scan.

    > If at any time you receive an error message from Greenbone stating "Internal error" with the reference "Could not authenticate to the manager daemon" then retry the step again.
7. &#x20;Select the blue star icon on the left to open the _New Credential_ web dialog box.
8. &#x20;Complete the dialog box with the following information:
   * Name—enter 515support
   * Allow insecure use—select **Yes**
   * Username—enter 515support\Administrator
   * Password—enter Pa\$$w0rd
9.  &#x20;Select **Create**.

    > Note that tasks are simplified for the activity. You would _NEVER_ use the domain admin credentials for this task (just as you would never use the same password across multiple accounts in multiple contexts). Create a dedicated account for vulnerability scanning.
10. &#x20;Configure a scan target. From the **Configuration** menu, select **Targets**.
11. &#x20;Select the blue star icon on the left to open the _New Target_ web dialog box.
12. &#x20;Complete the dialog box with the following information:
    * Name—enter 515support web server
    * Hosts—select **Manual** and enter 10.1.0.2 in the box.
    * Credentials—from the _SMB_ list box, select **515support**.
13. &#x20;Select **Create**.
14. &#x20;Next, configure a scan task. From the **Scans** menu, select **Tasks**.

    You may close the "Welcome to the scan task" dialog box that opens.
15. &#x20;Select the blue star icon on the left to open the _New Task_ web dialog box.
16. &#x20;Complete the dialog box with the following information:
    * Name—515support web scan
    * Scan Targets—**515support web server**
    * Scan Config—**Full and fast**
17. &#x20;Select **Create**.

    You will run the scan manually to ensure that it works as expected.
18. &#x20;Under _Name_ at the bottom of the screen, select the **515support web scan** task.
19. &#x20;Select the **Start** green arrow button to run the scan manually.

    > Now that you have begun a scan, you need to let it run for _three to four minutes_. You may continue with the next steps while the scan runs.
20. &#x20;From the _No auto-refresh_ box in the green header bar, select **Refresh every 30 seconds**. Let the scan execute while you complete the next step.
21. &#x20;Select **Scans→Reports**.

    Observe the **Scan Results** columns. Do not continue to the next task until there are results in the **High**, **Medium**, or **Low** columns.

    You can use this screen to monitor the status of tasks and preview scan results even if the task is not complete.
22. &#x20;In the **Date** column at the bottom of the Reports page, select the task with today's date to view the results.

    If there are no entries in the report yet, wait a few more minutes.
23. &#x20;From the small triangle pull down menu by the "Report:Results" title, choose **Report:Hosts** to display the discovered hosts and their related vulnerability information.
24. &#x20;In the pull-down menu at the upper left of the page, select **HTML** (the menu current reads **Anonymous XML**), and then select the green **Download filtered Report** button.
25. &#x20;When prompted, select **Save File** to download the report to the default **Downloads** folder (so it can be scored).
26. &#x20;Close the **OpenVAS** administration site in Firefox.
27. &#x20;Open the **Home** directory for the user, and then double-click the **Downloads** directory.
28. &#x20;Double-click the HTML file and view the report.

    The file name will begin with **report-** and contain a long string of characters, concluding with **.html**
29. Confirm that the report HTML file exists.

    Correct

* > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
* &#x20;Close **Firefox** to interrupt the scan.
