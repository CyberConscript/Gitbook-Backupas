# Group Policy Objects (GPOs)

Group Policy Objects (GPOs) manage settings for users and computers within a network domain. Their extensive reach and control over network resources have made them an attractive target. Forensic investigators need to understand how attackers exploit GPOs and utilise the artefacts left to uncover security incidents and prevent future attacks.

### GPO Attack Scenarios

There are a lot of scenarios in which threat actors can exploit GPOs. Here are some of the common ones with their associated forensic artefacts:

* **Privilege Escalation:** An adversary modifies a GPO to alter user rights or group memberships, granting themselves elevated privileges across the network.
* **Persistence and Lateral Movement:** Attackers embed malicious scripts or deploy malware or tools through GPO login scripts that allow for maintenance of persistent access to a system or facilitate lateral movement within a network.
* **Security Policy Modification:** Tampering with GPOs to weaken security settings, such as disabling firewall rules, antivirus software, or other security controls, making systems more vulnerable to attacks.
* **Reconnaissance:** Attackers can embed scripts in GPOs that execute malicious activities, such as reconnaissance scripts that gather sensitive network information, aiding future targeted attacks.





### User Artefacts in Group Policies

When Group Policy Object policies are changed or exploited, specific artefacts are left behind that can help analysts detect unauthorized changes, evaluate the security state, and comprehend policy execution.

Essential GPO enforcement artefacts include:

* **Custom User Settings:** Direct modifications to user-specific settings, such as desktop configurations, startup programs, and security configurations, leave traces in **`HKEY_CURRENT_USER`** registry keys and within user profile directories.
* **Login Scripts:** GPOs can dictate scripts to execute when a user logs in. These actions generate artefacts, including script files in the **`SYSVOL`** folder and execution logs within user profiles, found under the **`User Configuration`** settings of a GPO.
* **User Rights Assignments:** Unauthorized alterations in user rights and permissions generate detectable changes within the **`Security`** database at **`%SystemRoot%\security\database\secedit.sdb`**, offering insights into access control adjustments.
* **Security Policy Changes:** System-wide modifications to security policies by GPOs are recorded in the registry under **`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`**, reflected in the **`Local Security Policy`**.
* **System Services Configurations:** System service adjustments, including startup type and permissions changes, are documented within the **`System`** registry hive under **`HKEY_LOCAL_MACHINE\SYSTEM`**.
* **Network Configuration Adjustments:** GPO-driven changes to network configurations manifest as modified registry settings in **`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList`** and alterations in configuration files located in **`%SystemRoot%\System32\drivers\etc`**
