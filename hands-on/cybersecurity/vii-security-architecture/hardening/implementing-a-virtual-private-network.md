# Implementing a Virtual Private Network

### Scenario <a href="#scenario" id="scenario"></a>

You are tasked with configuring a Virtual Private Network solution for the sales team at 515 Support. You have access to two Windows servers, which will permit you to demonstrate the process. First, you will add Routing and Remote Access functionality and configure the Sales users on the DC1 server. Next, you'll configure an access policy. You will then test the VPN connection. Finally, you'll use Nmap to discover what ports are exposed on the VPN server.



### Configure the VPN server <a href="#configure-the-vpn-server" id="configure-the-vpn-server"></a>

Create a new Sales VPN group and add a Sales user. Next, configure the Routing and Remote Access and Network Policy Server roles on DC1.

> It is not recommended that you configure an Active Directory Domain Controller as a VPN server. DC1 is configured this way in the lab environment for convenience only.

1. &#x20;On the [DC1](https://labclient.labondemand.com/Instructions/f1236f24-6519-4761-9d8c-421d3d343a79?rc=10) virtual machine, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/f1236f24-6519-4761-9d8c-421d3d343a79?rc=10), and then sign on a 515support\Administrator with Pa\$$w0rd.
2. &#x20;From Server Manager, select **Tools > Active Directory Users and Computers** from **Server Manager**. Browse to the **Users** container.
3.  &#x20;Create a new global security group named Sales VPN.

    > Many of your tasks are scored by scripts. You must use the same names and other labels as the lab instructions specify or your task may be marked as incorrect. For example, if the task says to create a user account named “user01,” than “user1” would be marked as incorrect.
4. &#x20;Open the **Bobby** account, select the **Member Of** tab, and then add **Bobby** to the **Sales VPN** group.
5. &#x20;Close Active Directory Users and Computers after adding Bobby to the Sales group.
6. &#x20;From Server Manager, select **Tools > Routing and Remote Access**.
7. &#x20;Right-click **DC1 (local)** and then select **Configure and Enable Routing and Remote Access**. Select **Next** to start the wizard.
8. &#x20;Select **Remote access (dial-up or VPN)**, and then select **Next**.
9. &#x20;Check the box for **VPN**, and select **Next**,
10. &#x20;When prompted select the **INTERNET** interface as the Internet connection.
11. &#x20;Accept all remaining defaults, and then select **Finish**.
12. &#x20;Acknowledge the policy message, and accept the DHCP message when prompted.
13. &#x20;When the RRAS service has started, right-click the **DC1 (local)** node, select **Properties**. Select the **Logging** tab.
14. &#x20;Select the radio button for **Log all events**, and then select **OK** to close the properties box.
15. &#x20;Select the **Remote Access Logging & Policies** node, and then right-click it and select **Launch NPS**.
16. &#x20;In the Network Policy Server console, select the **Network Policies** node.
17. What is the purpose or effect of the default rules?

    To match all connection attempts, and then deny them.To match all connection attempts, and then permit them
18. &#x20;Right-click the **Network Policies** node, and then select **New**. Use the following settings (unless otherwise stated, accept the defaults):
    * Policy name: Enter Sales VPN access
    * Type of network access server: Select **Remote Access Server(VPN-Dial up)**
    * Conditions: Select **User Groups** and then add the Sales VPN group
    * Specify Access Permission: Select **Access Granted**
    * Configure Authentication Methods: Check the box for **Encrypted authentication (CHAP)** and leave the MS-CHAP and MS-CHAPv2 boxes at their default (checked)
    * Select **Next** multiple times until the **Finish** button is available, and then select **Finish**.
19. &#x20;Observe the new policy in the Network Policies console.
20. &#x20;In the NPS console, select **Accounting**, and then select **Configure Accounting**.
21. &#x20;Select **Log to a text file on the local computer**, accept the rest of the defaults, and then complete the configuration.
22. Which of the following answers displays the path to the log files?

    C:\Windows\VPN\LogFilesC:\Windows\System32\LogFilesC:\Windows\LogFilesC:\LogFiles



<details>

<summary>Log files.</summary>



</details>
