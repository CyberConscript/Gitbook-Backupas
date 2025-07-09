# Artefacts in Group Policies

### User Artefacts in Group Policies

When Group Policy Object policies are changed or exploited, specific artefacts are left behind that can help analysts detect unauthorized changes, evaluate the security state, and comprehend policy execution.

Essential GPO enforcement artefacts include:

* **Custom User Settings:** Direct modifications to user-specific settings, such as desktop configurations, startup programs, and security configurations, leave traces in **`HKEY_CURRENT_USER`** registry keys and within user profile directories.
* **Login Scripts:** GPOs can dictate scripts to execute when a user logs in. These actions generate artefacts, including script files in the **`SYSVOL`** folder and execution logs within user profiles, found under the **`User Configuration`** settings of a GPO.
* **User Rights Assignments:** Unauthorized alterations in user rights and permissions generate detectable changes within the **`Security`** database at **`%SystemRoot%\security\database\secedit.sdb`**, offering insights into access control adjustments.
* **Security Policy Changes:** System-wide modifications to security policies by GPOs are recorded in the registry under **`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies`**, reflected in the **`Local Security Policy`**.
* **System Services Configurations:** System service adjustments, including startup type and permissions changes, are documented within the **`System`** registry hive under **`HKEY_LOCAL_MACHINE\SYSTEM`**.
* **Network Configuration Adjustments:** GPO-driven changes to network configurations manifest as modified registry settings in **`HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\NetworkList`** and alterations in configuration files located in **`%SystemRoot%\System32\drivers\etc`**.
