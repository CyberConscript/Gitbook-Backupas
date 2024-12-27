# Identity and access management (IAM)

## IAM

**Identity Management** -  Onboarding Process, Identity repository, Authentication mechanisms

**Access management** (Authorization) - granting  permission assignments, controls, requests and approvals

**Authentication** - Verify, validate, prove the identity (What: I know, I am, I have) (SSO, MFA, Federated authentication)

**Auditing** - Activity Logs:, Anomaly Detection, Periodic Review, retention of logs (regulatory, business needs, legal, incident response).

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

## **Key Concepts**

1. **Subject**
   * A **subject** is an active entity, usually a user, process, or system, requesting access to a resource.
   * Example: A user named "Alice" trying to open a file.
2. **Object**
   * An **object** is a passive entity that the subject wants to access.
   * Example: A file, database record, or printer.
3. **Owner**
   * The **owner** is an entity (usually a subject) responsible for or associated with the creation and management of the object.
   * Example: If Alice creates a file, she is typically the owner of that file.
4. **Access Rules**
   * **Access rules** define the permissions or restrictions for interactions between the subject and the object.
   * Example: Alice can "read" the file, but not "write" to it.
5. **Enforcement Point**
   * The **enforcement point** is the mechanism or system component that checks and enforces the access rules.
   * Example: An operating system or firewall enforcing file permissions or access policies.

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

## Secure access at the server edge



