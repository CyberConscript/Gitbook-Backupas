# Managing Centralized Authentication

### Scenario <a href="#scenario" id="scenario"></a>

RADIUS permits centralized authentication. In this activity, you will rely on Active Directory (on DC1) as the authentication server. It will also act as the RADIUS server—the point where all authentication attempts get forwarded. The UTM1 virtual machine, running the pfSense security appliance, will be configured as a RADIUS client. It will pass authentication attempts to DC1. In this scenario, RADIUS is being used to authenticate administrative users who manage the pfSense firewall appliance itself, rather than authentication of remote access VPN or wireless users.



### Register RADIUS client <a href="#register-radius-client" id="register-radius-client"></a>

RADIUS can be used with VPN, wireless, and appliance authentication. In Windows Server, the RADIUS role is configured using Network Policy Server (NPS). Use NPS to configure the UTM1 VM as an authorized RADIUS client of DC1.

1. &#x20;Select the [DC1](https://labclient.labondemand.com/Instructions/f03ef52e-ee77-4876-96a9-55dea47a0f54?rc=10) VM, send [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/f03ef52e-ee77-4876-96a9-55dea47a0f54?rc=10), and log on with the credentials 515support\Administrator and Pa\$$w0rd
2. &#x20;In Server Manager, select **Tools > Network Policy Server**.
3.  &#x20;Expand **RADIUS Clients and Servers** to select **RADIUS Clients**. Right-click **RADIUS Clients** and select **New**.

    The RADIUS client is the network appliance accepting the user's credentials (in this case, the UTM1 VM).
4. &#x20;In the New RADIUS Client dialog box, in the Friendly name box, enter pfsense.corp.515support.com.
5. &#x20;In the Address box, type 10.1.0.254
6. &#x20;Under Shared Secret, select the **Generate** radio button, then select the **Generate** button.
7.  &#x20;Copy the shared secret string.

    > You need to keep this value on the Clipboard for a while—alternatively, you can paste it into a Notepad file.
8. &#x20;Select **OK** to close the dialog box.



### Configure network policy <a href="#configure-network-policy" id="configure-network-policy"></a>

Configure a policy that allows users in the LocalAdmin security group to authenticate with pfSense by using unencrypted authentication. Use the Class attribute to transmit the LocalGroup property from the RADIUS server to the RADIUS client when a user authenticates.

1. &#x20;In the Network Policy Server console, expand **Policies** to select **Network Policies**. Right-click **Network Policies** and select **New**.
2. &#x20;In Policy name, type pfSense Network Security Appliance Administration
3. &#x20;Select **Next**. On the Specify conditions page, select the **Add** button.
4. &#x20;Select **Windows Groups** and select **Add**.
5. &#x20;Select the **Add Groups** button then type localadmin and select **Check Names**.
6. &#x20;Select **OK** then select **OK** again to confirm the Windows Groups dialog box.
7. &#x20;Select **Next**.
8. &#x20;On the Specify Access Permission page, leave **Access granted** selected and select **Next**.
9. &#x20;On the Configure Authentication Methods page, leave the existing MS-CHAPv2 and MS-CHAP boxes selected, as shown in this screenshot.
10. &#x20;Select **Next**.

    > We are not implementing it for this lab, but because the credential is being passed using [weak MS-CHAP encryption](https://msrc-blog.microsoft.com/2012/08/20/weaknesses-in-ms-chapv2-authentication/), you must configure the management interface to use HTTPS encrypted connection security rather than plain HTTP. You would achieve this by installing a trusted root certificate to the pfSense appliance and disabling HTTP-only access.
11. &#x20;On the Configure Constraints page, select **Next**.
12. &#x20;On the Configure Settings page, with **Standard** selected, select the **Add** button.
13. &#x20;In the Add Standard RADIUS Attribute dialog box, from the Attributes box, select **Class**. Select the **Add** button.
14. &#x20;Type LocalAdmin in the box and select **OK**. Select **Close**. pfSense uses the Class attribute to communicate group membership.
15. &#x20;Select **Next** then **Finish**.



### Configure RADIUS client <a href="#configure-radius-client" id="configure-radius-client"></a>

Configure the pfSense VM as a RADIUS client by inputting the RADIUS server details. This permits pfSense to forward authentication requests to DC1.

1.  &#x20;Still on the [DC1](https://labclient.labondemand.com/Instructions/f03ef52e-ee77-4876-96a9-55dea47a0f54?rc=10) VM, open http://10.1.0.254 in the browser.

    You will be connected to the pfSense virtual machine.
2. &#x20;Log on with the credentials admin and Pa\$$w0rd. When prompted to save the password, select **Not for this site**.
3. &#x20;Maximize the browser window. Select **System > User Manager**. Select the **Authentication Servers** tab, then select the **Add** button.
4. &#x20;In the Descriptive name box, type 515support AD
5. &#x20;From the Type list, select **RADIUS**.
6. &#x20;Under RADIUS Server Settings, note that the Protocol is set to MS-CHAPv2 by default. This is the authentication protocol that determines the format for the user credential. The RADIUS server and client must be able to match at least one authentication method.
7. &#x20;In the **Hostname or IP address** box, enter 10.1.0.1
8.  &#x20;In the **Shared Secret** box, paste the Clipboard contents.

    You are pasting in the shared secret generated on DC1 in an earlier task.
9. &#x20;Select the **Save** button.
10. Which of the following best describes the reason for the shared secret configured on DC1 and pfSense?

    To authenticate pfSense to DC1.To authenticate DC1 to pfSense.To authenticate Bobby on pfSense.To authenticate Bobby on DC1.

Correct

### Configure role-based permissions <a href="#configure-role-based-permissions" id="configure-role-based-permissions"></a>

Configure a basic least permissions role for the LocalGroup security group account so that users do not have access to advanced system configuration pages.

1. &#x20;Select the **Groups** tab, then select the **Add** button.
2. &#x20;In the **Group name** box, type LocalAdmin
3. &#x20;Select the **Save** button.
4. &#x20;In the **Actions** column, select the **Edit group** pen icon to edit the **LocalAdmin** group.
5. &#x20;Under Assigned Privileges, select the **Add** button.
6.  &#x20;**SHIFT**-click to select from **WebCfg—Dashboard (all)** down to the last **WebCfg—Status: UPnP Status** item.

    This is a very long list of privilege names!
7. &#x20;Locate the item **WebCfg—pfSense wizard subsystem** and **CTRL**+click to de-select it.
8. &#x20;Select the **Save** button.
9. &#x20;Select the **Settings** tab then from the Authentication Server box, select **515support AD**. Select the **Save** button.
10. &#x20;From the upper right corner of the page, select the **Logout** button.



### Test the credentials <a href="#test-the-credentials" id="test-the-credentials"></a>

To test that pfSense is passing credentials to Active Directory, you will now log on to the pfSense device with a non-administrator account. The account is stored in AD. This allows you to exercise the privileges granted in the previous task.

1.  &#x20;Log back on with the credentials bobby and Pa\$$w0rd

    Now when you log on, the UTM1 VM passes the credentials you have submitted to the RADIUS server for validation.
2.  &#x20;Observe that you can configure most things but cannot adjust system settings to change the user accounts or root admin password.

    Ideally, you would create role-based groups with more fine-grained privileges for different tasks.
3.  Is Bobby's user account a member of the LocalAdmin group?

    YesNo

