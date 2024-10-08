# Vulnerabilities

## Software Vulnerabilities and Patch Management

Software exploitation involves targeting vulnerabilities within software code. An application vulnerability refers to a design flaw that could bypass the security system or crash the application. While vulnerabilities typically require specific conditions to be exploited, the intricate nature of modern software and the demand for rapid releases make it difficult to have entirely vulnerability-free software. To illustrate this, consider vulnerabilities affecting Adobe's PDF document reader versus those in the foundational server software for transport security. The former might grant threat actors access to a corporate network via a workstation, while the latter could expose cryptographic keys that secure web services, leading to compromise. Both scenarios have distinct high impacts.

Many vulnerabilities are discovered by software and security researchers, who alert vendors to patch them before releasing the details. Proper patch management is crucial; failing to apply security patches to systems introduces another layer of vulnerability. Weak configuration management may result from inadequate asset documentation. While patches might be deployed on some systems, others might be left unprotected. Patches could be applied and then reversed due to performance issues

Moreover, it's crucial to recognize that software vulnerabilities extend beyond applications:

* Operating System (OS) vulnerabilities—an exploit targeting an application runs with the permissions of the user, often limited. However, a vulnerability in an OS kernel file or shared library could facilitate privilege escalation, allowing malware to execute with higher access rights, like system or root privileges. Notably, vulnerabilities like the Dirty COW vulnerability exemplify OS kernel vulnerabilities.
* Firmware vulnerabilities—BIOS/UEFI firmware controlling PC boot processes and bugs in device firmware (e.g., network cards, disk controllers) are potential weak points. Even network appliances and Internet of Things (IoT) devices operate OS code akin to firmware. Firmware exploits can be challenging to detect, as they operate with the highest privilege level. Intel AMT vulnerability is a case in point, showcasing the impact of a firmware vulnerability.

## Zero day

Despite the implementation of robust patch management protocols, malicious actors might exploit software vulnerabilities as an avenue for attacks. When a vulnerability is exploited before its discovery by the developer or before a patch can be released, it is termed a zero-day vulnerability. Such vulnerabilities can be remarkably damaging due to the time it takes for the vendor to create a patch, thus leaving systems susceptible in the interim.

## Legacy

A legacy platform refers to a technology that no longer receives security patches or support from its developer or vendor. This category encompasses various items, such as personal computers, laptops, smartphones, networking appliances, peripheral devices, Internet of Things (IoT) devices, operating systems, database and programming environments, as well as software applications. Notably, legacy platforms are incapable of receiving patches. As a result, these systems are susceptible to potential exploits and require alternative security measures beyond patching. One effective approach is to isolate them within networks inaccessible to attackers.

## Weak Host Configurations

#### Default Configurations

Relying solely on the manufacturer's default settings during the deployment of appliances or software applications is a clear example of inadequate configuration. It is not prudent to assume that vendors will ship products with secure default configurations, although many do so nowadays. Default settings may inadvertently enable insecure interfaces, providing attackers with avenues to compromise the device. This vulnerability can be especially impactful with network appliances, potentially allowing attackers to move through networks undetected and intercept traffic.

#### Unprotected Root Accounts

The root account, commonly referred to as the default Administrator account in Windows or generically known as the superuser, holds unrestricted access to system resources. This account is typically employed for operating system installations. An unsecured root account is one that attackers can gain control of, either through weak password guessing or by exploiting local boot attacks to alter or set passwords. Software vulnerabilities can also grant root access, as demonstrated in a MacOS bug (arstechnica.com/information-technology/2017/11/macos-bug-lets-you-log-in-as-admin-with-no-password-required). Such vulnerabilities are exceptionally critical, granting threat actors complete dominance over the system.

To mitigate this risk, effective user management and authorization policies should be enforced. The superuser account must be meticulously controlled, with administrative tasks carried out by accounts or roles adhering to the principle of least privilege. Normally, the default root or Administrator account is deactivated for login. Even if this account is permitted for local (interactive) login, remote access to it should be prohibited.

#### Inadequate Permissions

Open permissions arise when data files or applications are provided without appropriate differentiation of access rights among user groups. Permissions systems can be intricate, and errors, such as allowing unauthenticated guests to access confidential data files or granting write access when read access is appropriate, are easily made. This issue is particularly noticeable in cloud storage environments, where administrators accustomed to Windows and Linux directory access control lists might lack familiarity with their cloud counterparts (directdefense.com/how-to-prevent-exploitation-of-amazon-s3-buckets-with-weak-permissions).



## **Weak Network Configurations**

Vulnerabilities can stem from unnecessary services and weak encryption.

**Open Ports and Services**

Network services use TCP or UDP port numbers for client connections, and IP addresses identify clients and servers. Limit open ports to essential services for security. Steps to harden services include:

1. Restrict access to critical services by IP address or use block lists.
2. Disable unnecessary default services or block ports using firewalls.
3. Confine private network services behind firewalls or network segmentation.

**Unsecure Protocols**

Unsecure protocols transmit data as cleartext, lacking encryption and secure authentication. Attackers can exploit this weakness as a man-in-the-middle.

**Weak Encryption**

Encryption algorithms safeguard stored or transferred data, requiring correct decryption keys. Weak encryption vulnerabilities arise from:

1. Using simple passwords for encryption keys, making them guessable.
2. Utilizing algorithms with known weaknesses susceptible to brute-force attacks.
3. Distributing keys insecurely, allowing unauthorized access to encrypted data.

**Errors**

Poorly configured applications might expose unformatted error messages in certain situations. Threat actors can exploit these messages for vulnerabilities and coding errors. Secure coding practices ensure graceful failure without revealing exploitable information.



## CVE

The Common Vulnerabilities and Exposures (CVE) is a comprehensive database that catalogs vulnerabilities found in published operating systems and application software. The CVE, accessible at cve.mitre.org, provides detailed information about each vulnerability entry, including the following components:

1. **Identifier Format**: A unique identifier assigned to each vulnerability in the format CVE-YYYY-####, where YYYY represents the year of discovery and #### indicates the sequential order of discovery.
2. **Vulnerability Description**: A concise description outlining the nature of the vulnerability.
3. **Reference URLs**: A list of web addresses providing additional details and information about the vulnerability.
4. **Creation Date**: The date when the entry for the vulnerability was created.

The CVE database serves as a primary source of information for the National Vulnerability Database (NVD) maintained by the National Institute of Standards and Technology (NIST) at nvd.nist.gov. The NVD enhances CVE entries by offering supplementary analysis, a criticality assessment based on the Common Vulnerability Scoring System (CVSS), and information on available fixes.

The Common Vulnerability Scoring System (CVSS), managed by the Forum of Incident Response and Security Teams (FIRST) at first.org/cvss, is a standardized framework for evaluating vulnerabilities. CVSS metrics generate a score ranging from 0 to 10, which reflects various characteristics of the vulnerability. These characteristics include factors such as whether the vulnerability can be exploited remotely or requires local access, whether user intervention is necessary, and more. The scores are grouped into descriptive bands that provide further insight into the severity of the vulnerability.

| Score |   Description   |
| ----- | --------------- |
| 0.1+  | Low             |
| 4.0+  | Medium          |
| 7.0+  | High            |
| 9.0+  | Critical        |
