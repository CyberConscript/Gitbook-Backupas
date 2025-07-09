# User accounts

### Local User Accounts

Local user accounts are unique to a specific computer, offering access to its resources and applications. They are managed directly on the computer, allowing users to log in, adjust settings, and work independently without a network.

| **Security Risks**                                                                                                 | **Mitigation Strategies**                                                                             |
| ------------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------- |
| Local accounts often have weaker password requirements, making them more prone to brute-force attacks.             | Enforce strong password policies, including regular updates and complexity requirements.              |
| Local accounts can be unnecessarily granted administrative rights, increasing the risk of misuse.                  | Apply the principle of least privilege by limiting administrative rights strictly to essential users. |
| Lack of centralized control can lead to inconsistencies in security settings, exposing systems to vulnerabilities. | Regularly audit local accounts to ensure consistent application of security settings.                 |
| Without centralized logging, monitoring local user activities is more complicated.                                 | Implement centralized logging and monitoring solutions where possible, even for local accounts.       |

### Domain Accounts

Unlike local user accounts, domain accounts are centrally managed through a domain controller. This central management allows for easier user access administration, security policies, and resource sharing. Domain users can log into any computer within the domain using the same credentials, making accessing network resources and applications easier.

| **Security Risks**                                                                                                                                          | **Mitigation Strategies**                                                                                 |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| A compromised domain controller can provide attackers with access to all connected systems and sensitive data, enabling lateral movement and data breaches. | Harden and regularly patch domain controllers to protect against exploitation.                            |
| Domain accounts are primary targets for phishing campaigns aimed at stealing credentials, exploiting their network-wide privileges.                         | Employ multifactor authentication (MFA) to reduce reliance on passwords and limit phishing effectiveness. |
| Centralized management of domain accounts increases the impact of insider threats.                                                                          | Implement strict access control measures and maintain rigorous oversight of privileged accounts.          |

### System and Service Accounts

System and service accounts are special accounts in the Windows operating system and various apps. They automatically perform tasks and are designed to ensure software services and system processes function securely and efficiently.

System Accounts are default accounts in the operating system, like the Local System, Network Service, and Local Service accounts. They have certain rights that allow them to interact with system resources and carry out essential system tasks.

* Examples:
  * `LocalSystem`: highest privilege, local machine only.
  * `NetworkService`: minimal local privilege, accesses network as machine account.
  * `LocalService`: very restricted local and network access.
* No passwords, not AD-authenticated.

On the other hand, service accounts are used by apps or services to interact with the operating system. They can be set by the software (like SQL Server using a service account for its operations) or made by administrators for specific services.

* Standard AD user accounts used to run services (e.g., SQL Server, IIS).
* Often static passwords (bad).
* Manually assigned to services or scheduled tasks.





| **Security Risks**                                                                                                                                                                     | **Mitigation Strategies**                                                                               |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Service accounts with too many privileges can be used to gain unauthorized access or increase permissions in the system.                                                               | Regularly audit and restrict service account privileges based strictly on operational requirements.     |
| If service accounts are not configured properly, they can give attackers or harmful software the ability to run commands, access private information, or interrupt essential services. | Utilise strong, complex passwords or passphrases for service accounts, and manage credentials securely. |

### Managed Service Accounts (MSAs) & Virtual Accounts

Managed Service Accounts (MSAs) are specialized domain accounts designed for automated password management and simplified account administration. They are used to reducing administrative overhead and enhance security by automatically rotating passwords periodically without administrative intervention.

* Introduced in Windows Server 2008 R2.
* 1:1 relationship: one MSA per machine.
* AD manages password (rotates every 30 days by default).
* Can be used only by services on a **single** machine.

#### 🔹 **gMSA (Group Managed Service Account)**

* Introduced in Windows Server 2012.
* Allows **multiple machines** to share the same account (group-managed).
* Perfect for services behind load balancers (e.g., web farms, SQL clusters).
* Still no need to manage passwords (rotated by AD).

Virtual Accounts are local service accounts that provide simplified account management by using credentials managed by Windows internally. These accounts eliminate the necessity for administrators to manage passwords explicitly and offer a secure way to run services with minimal privilege.



* Created dynamically by Windows per service.
* No password, not in Active Directory.
* Identifies to the system as:\
  `NT SERVICE\ServiceName`
* Appears as a security principal with limited permissions.
* Can access the network as the computer account (like `NetworkService`).

Despite their secure nature, these accounts also face security risks.

| **Security Risks**                                                                                                           | **Mitigation Strategies**                                                                                               |
| ---------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| The accounts may be granted overly broad permissions, which can lead to the exploitation of the privileges                   | Establishing clear security guidelines on assignment of roles and permissions.                                          |
| Password management and internal credential handling properties make the accounts less visible to standard monitoring tools. | Integration into centralised logging and continuous monitoring frameworks can be used to detect unusual behaviours.     |
| The reliance on automated password rotation can create a single point of failure.                                            | Implementation of disaster recovery and redundancy plans for services that rely on MSAs or virtual accounts is crucial. |
|                                                                                                                              |                                                                                                                         |

Avoid traditional service accounts with static passwords.\
Use gMSAs wherever possible for domain-based services.\
Use Virtual Accounts for local-only services with no domain requirements.\
Monitor for service account misuse, especially ones with:

* SPNs → Kerberoasting targets
* Local admin rights
* No password changes for 90+ day



### User Artefacts in the Security Account Manager (SAM)

The Security Account Manager (SAM) is a Windows database that stores the user's local account and system account info. It holds critical forensic data about account activities such as creation, alteration, and deletion. The SAM file, located at **`%SystemRoot%\\system32\\config\\SAM`**, is locked while Windows runs but can be accessed and examined from offline systems or forensic backups.

The SAM provides the following forensic data:

* The account names of local users and associated unique identifiers for each user
* Group memberships and stored hashed representations of user passwords (not in plaintext)
* Status indicators showing if accounts are active, disabled, or expired
* Records of last login timestamps

### User Artefacts in the NT Directory Services Database (NTDS.dit)

The NT Directory Services (NTDS) database, or NTDS.dit, stores detailed information about domain user accounts, groups, and other directory service data within a networked domain environment.

The NTDS can provide the following information:

* Usernames and full names of domain users
* Security Identifiers (SIDs) for each user
* Detailed group memberships, including global, domain local, and universal groups
* Hashed representations of user passwords for domain accounts
* Account activation, disablement, and expiration status
* Login timestamps and failed login attempts
* Password last set and password expiration times
* Other domain objects like computers, groups, organizational units (OUs), and security policies
* Trust relationships with other domains

Forensic examination of SAM and NTDS.dit files is crucial as they help identify unauthorized access, assess password security, and track user behaviour, which is essential for investigating security incidents and enhancing system security.



### Analyzing the NTDS.dit for User-Related Artefacts

To analyze the user-related data of a domain controller, the NTDS.dit file can be exported and examined using the DSInternals PowerShell module, a powerful tool designed for interacting with Active Directory databases and related components in a forensic context.

To start, open the VM and launch Powershell in Administrator mode.

We first need to export the NTDS.dit file along with the SYSTEM hive. Enter the following command:

PowerShell: Administrator Mode

```powershell
           C:\> ntdsutil.exe "activate instance ntds" "ifm" "create full C:\Exports" quit quit
        
```

Let's break down the command:

* **ntdsutil.exe -** The command-line tool for Active Directory database management.
* **"activate instance ntds"**- Explicitly stating that the 'ntds' instance should be activated. This typically specifies which Active Directory database instance you want to work with.
* **"ifm"** - Create a full installation media set and store it in the C:\Exports\ directory. The full option indicates that the system state data and the NTDS database will be included.
* **quit quit** - These are two quit commands issued in succession. The first quit tells ntdsutil to exit the current context (in this case, the ifm context), and the second quit exits the utility itself. It's a way to exit the tool cleanly after executing the necessary commands.

The SYSTEM hive contains the system's boot key, essential for decrypting specific data within the NTDS.dit file. Without the boot key from the SYSTEM hive, the security-related information within NTDS.dit, such as password hashes, remains encrypted and inaccessible, limiting the depth of forensic analysis that can be conducted on user account data and other domain-related information.
