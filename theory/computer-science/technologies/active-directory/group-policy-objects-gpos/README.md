# Group Policy Objects (GPOs)

Group Policy Objects (GPOs) manage settings for users and computers within a network domain. Their extensive reach and control over network resources have made them an attractive target. Forensic investigators need to understand how attackers exploit GPOs and utilise the artefacts left to uncover security incidents and prevent future attacks.

### GPO Attack Scenarios

There are a lot of scenarios in which threat actors can exploit GPOs. Here are some of the common ones with their associated forensic artefacts:

* **Privilege Escalation:** An adversary modifies a GPO to alter user rights or group memberships, granting themselves elevated privileges across the network.
* **Persistence and Lateral Movement:** Attackers embed malicious scripts or deploy malware or tools through GPO login scripts that allow for maintenance of persistent access to a system or facilitate lateral movement within a network.
* **Security Policy Modification:** Tampering with GPOs to weaken security settings, such as disabling firewall rules, antivirus software, or other security controls, making systems more vulnerable to attacks.
* **Reconnaissance:** Attackers can embed scripts in GPOs that execute malicious activities, such as reconnaissance scripts that gather sensitive network information, aiding future targeted attacks.
