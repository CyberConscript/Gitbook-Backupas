# Identity and access management (IAM)

## **Key Concepts**

* **Subject** is an active entity, usually a user, process, or system, requesting access to a resource.
  * Example: A user named "Alice" trying to open a file.
* **Object** is a passive entity that the subject wants to access.
  * Example: A file, database record, or printer.
* **Owner  -** an entity (usually a subject) responsible for or associated with the creation and management of the object.
  * Example: If Alice creates a file, she is typically the owner of that file.
* **Access Rules**
  * **Access rules** define the permissions or restrictions for interactions between the subject and the object.
  * Example: Alice can "read" the file, but not "write" to it.
* **Enforcement Point** is the mechanism or system component that checks and enforces the access rules.
  * Example: An operating system or firewall enforcing file permissions or access policies.
* **Identity Management** -  Onboarding Process, Identity repository, Authentication mechanisms
* **Identification** - claim to have a specific identity (username, account number, or e-mail address).
* **Credentials** - identification and authentication information.
* **Access management** (Authorization) - granting  permission assignments, controls, requests and approvals
* **Authentication** - Verify, validate, prove the identity (What: I know, I am, I have) (SSO, MFA, Federated authentication)  (Public + private information)
* **Auditing** - Activity Logs:, Anomaly Detection, Periodic Review, retention of logs (regulatory, business needs, legal, incident response).
* **Logical access controls** - technical tools used for identification, authentication, authorization, and accountability. They are software components that enforce access control measures for systems, programs, processes, and information. The logical access controls can be embedded within operating systems, applications, add-on security packages, or database and telecommunication management systems. It can be challenging to synchronize all access controls and ensure all vulnerabilities are covered without producing overlaps of functionality.
* **Strong authentication** contains two or all of these three methods: something a person knows, has, or is.



## Identification

#### Identification Component Requirements&#x20;

When issuing identification values to users, the following should be in place:&#x20;

• Each identifier should be unique, for user accountability.&#x20;

• A standard naming scheme should be followed.&#x20;

• The value should be nondescriptive of the user’s position or tasks.&#x20;

• The value should not be shared between users.



While most of this chapter deals with user authentication, it is important to realize system-based authentication is possible also. Computers and devices can be identified, authenticated, monitored, and controlled based upon their hardware addresses (media access control) and/or Internet Protocol (IP) addresses. Networks may have network access control (NAC) technology that authenticates systems before they are allowed access to the network. Every network device has a hardware address that is integrated into its network interface card (NIC) and a software-based address (IP) that either is assigned by a Dynamic Host Configuration Protocol (DHCP) server or locally configured.

## Authentication

Password policies

If passwords are properly generated, updated, and kept secret, they can provide effective security. Password generators can be used to create passwords for users. This ensures that a user will not be using “Bob” or “Spot” for a password, but if the generator spits out “kdjasijew284802h,” the user will surely scribble it down on a piece of paper and stick it to the monitor, which defeats the whole purpose. If a password generator is going to be used, the tools should create uncomplicated, pronounceable, nondictionary words to help users remember them so they aren’t tempted to write them down. If users can choose their own passwords, the operating system should enforce certain password requirements. The operating system can require that a password contain a certain number of characters, unrelated to the user ID, and not be easily guessable. The operating system can keep track of the passwords a specific user generates so as to ensure no passwords are reused. In March of 2020 the National Institute of Standards and Technology (NIST) updated its guidelines concerning passwords in SP 800-63B. These include the following recommendations:

• Increased password length The longer the password, the harder it is to guess. The recommended minimum password length is 8 characters for user-selected ones and 6 characters for computer-generated passwords. The maximum recommended length is 64 characters.&#x20;

• Allow special characters Users should be allowed to use any special character, and even emojis, in their passwords. Special characters, however, should not be required.&#x20;

• Disallow password hints On the surface, password hints may seem to make sense because they allow users to remember complex passwords and reduce reliance on password resetting features. However, they mostly help attackers.



## Access management lifecycle

AML:

1. **Provisioning Access**: Granting new users the necessary privileges to access required resources and systems.
2. **Manage Access**: Regularly updating and maintaining user access to ensure they have appropriate permissions.
3. **Remove Access**: Revoking access when a user's role changes or they leave the organization.
4. **Review Access Logs**: Performing periodic audits of access logs to detect and mitigate unauthorized access.

#### Identity Repository

An **identity repository** is a centralized database or directory where identity information, such as user credentials, roles, and access permissions, is stored and managed. It plays a crucial role in IAM by:

* Storing user identities and their associated attributes.
* Providing information needed for authentication and authorization processes.
* Serving as a central reference point for managing access control policies and auditing user activity.



***



## **Key Access Models**

1. **Discretionary Access Control (DAC) - access permissions set by the owner, access rights can be delegated**
   * Owners define access rules for their objects.
   * Example: A file owner grants read access to specific users.
   *

       <figure><img src="../../../.gitbook/assets/image (20).png" alt=""><figcaption></figcaption></figure>
2. **Mandatory Access Control (MAC) - high security systems, requires labels and separation of duties, access permissions are mandated by policy**
   * Access is based on security policies, often enforced by the organization, not individual owners.
   * Example: Classified documents are restricted to users with appropriate clearance levels.
   *

       <figure><img src="../../../.gitbook/assets/image (19).png" alt=""><figcaption></figcaption></figure>
3. **Role-Based Access Control (RBAC) - based on job position**
   * Permissions are assigned to roles, and subjects gain permissions by assuming roles.
   * Example: A "Manager" role can approve leave requests, while an "Employee" role cannot.
4. **Attribute-Based Access Control (ABAC) - based on attributes of subject or object**
   * Access is granted based on attributes of the subject, object, and environment.
   * Example: A rule might state, "Access is granted if the user is in the 'Finance' department and accessing during business hours."
5. Rule-based access control - based on list of rule
   1. Can be applied to groups or individuals
   2.
6. Temporal access control - time based and regulated access
7. Risk based access control - when in high risk enviroments (secondary challenge, verification of identity, restricted access)



Just in time authentication

Temporal isolation, Ephemeral (one time) accounts, Temporary elevation vs standing account access, Policy enforcement workflow process, privileged account management, removable devices.



Password-less authentication

QR, smartphone, usb key, biometrics&#x20;



MFA

Two or three authentication factors



Single sign-on&#x20;

Centralized authentication (managed by one central place). Easier to protect, single point of failure.

Example: user logs in via Radius client that call radius server to verify identity.&#x20;

Example: Kerberos based on symetric, Key Distribution center, Authentication service and ticket granting service.

## Security measures

#### Lockout

The user can be locked out for five minutes or a full day, for example, after the threshold (or clipping level) has been exceeded. It depends on how the administrator configures this mechanism.

#### Audit trail

Track password usage and both successful and unsuccessful logon attempts. This audit information should include the date, time, user ID, and workstation the user logged in from.

## Threats

#### Race condition

In software, when the authentication and authorization steps are split into two functions, there is a possibility an attacker could use a race condition to force the authorization step to be completed before the authentication step. This would be a flaw in the software that the attacker has figured out how to exploit. A race condition occurs when two or more processes use the same resource and the sequence of steps within the software can be carried out in an improper order, something that can drastically affect the output. So, an attacker can force the authorization step to take place before the authentication step and gain unauthorized access to a resource.

#### Electronic monitoring

&#x20;Listening to network traffic to capture information, especially when a user is sending her password to an authentication server. The password can be copied and reused by the attacker at another time, which is called a replay attack.&#x20;

#### Access the password file&#x20;

Usually done on the authentication server. The password file contains many users’ passwords and, if compromised, can be the source of a lot of damage. This file should be protected with access control mechanisms and encryption.&#x20;

#### Brute-force attacks&#x20;

Performed with tools that cycle through many possible character, number, and symbol combinations to uncover a password.&#x20;

#### Dictionary attacks&#x20;

Comparing files of thousands of words to the user’s password until a match is found.&#x20;

#### Social engineering

Falsely convincing an individual that she has the necessary authorization to access specific resources.&#x20;

#### Rainbow table&#x20;

Using a table that contains all possible passwords already in a hash format.

