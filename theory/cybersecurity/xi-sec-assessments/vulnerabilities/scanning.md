# Scanning

## **Intrusive and Non-Intrusive**

Scan intrusiveness refers to the level of interaction that a scanner has with its target during the scanning process. There are two main categories: non-intrusive (or passive) scanning and active scanning.

**Non-Intrusive (Passive) Scanning**: Non-intrusive scanning involves analyzing indirect evidence from the target, such as monitoring network traffic patterns and behaviors. This approach doesn't directly interact with the target system. A well-known example of a passive scanner is the Zeek Network Security Monitor. Passive scanners scrutinize network captures to detect any policy violations or matches with known vulnerabilities (CVEs). While passive scanning is less likely to comprehensively identify vulnerabilities, it has minimal impact on both the network and the hosts. However, it might also be used stealthily by malicious actors to scan a network. Passive scanning is particularly useful when active scanning could disrupt system stability, making it suitable for scanning devices like printers, VoIP handsets, and embedded systems networks.

**Active Scanning**: Active scanning, on the other hand, involves actively probing the target's configuration by establishing a network connection. This method is more direct and can involve sending specific requests to the target to assess its security posture. Active scanning typically requires more network bandwidth and carries a risk of causing system crashes or outages on the target. Agent-based scanning, where an agent is installed on the target, is also a form of active scanning.

The most intrusive type of vulnerability scanning goes beyond just identifying vulnerabilities. In this case, exploitation frameworks are employed. These frameworks come with default scripts designed to attempt the exploitation of vulnerabilities, aiming to execute code or gain unauthorized access to the system. This approach is highly intrusive and is more aligned with penetration testing practices than automated vulnerability scanning.

The choice between non-intrusive and active scanning depends on the organization's objectives, risk tolerance, and the nature of the target environment. While non-intrusive scanning minimizes disruption, active scanning provides more direct insights into vulnerabilities and their potential impact. It's important to consider the specific goals of the scan and the potential consequences on the target system when determining the appropriate level of intrusiveness.

## Credentialed versus Non-Credentialed Scanning

Credentialed scanning and non-credentialed scanning refer to two different approaches used in vulnerability scanning, particularly when assessing the security of systems and devices within a network.

**Credentialed Scanning**: In credentialed scanning, the vulnerability scanner is provided with valid login credentials, such as usernames and passwords, that allow it to authenticate with the target systems. Once authenticated, the scanner gains deeper access to the target's resources, files, and configurations. This enables the scanner to perform more comprehensive and accurate assessments of the system's vulnerabilities. Credentialed scanning can reveal vulnerabilities that are not accessible from an external perspective and can provide detailed insights into the configuration settings, patches, and security measures in place.

**Non-Credentialed Scanning**: Non-credentialed scanning, also known as external or remote scanning, is conducted without using any authentication credentials. The scanner interacts with the target from an external perspective, probing for vulnerabilities that can be detected without logging into the system. This approach is less intrusive and does not require access to the target's internal resources. However, it might miss certain vulnerabilities that are only visible when authenticated.

**Key Differences**:

1. **Scope**: Credentialed scanning has a broader scope as it can assess internal vulnerabilities, configurations, and patches. Non-credentialed scanning is limited to identifying externally visible vulnerabilities.
2. **Accuracy**: Credentialed scanning is generally more accurate in identifying vulnerabilities because it has access to internal information. Non-credentialed scanning might provide false positives or miss certain vulnerabilities.
3. **Complexity**: Credentialed scanning requires valid credentials, which might involve more setup and coordination. Non-credentialed scanning is simpler to execute but may lack depth in assessment.
4. **Impact**: Credentialed scanning can have a higher impact on the target system due to the deeper level of access. Non-credentialed scanning has minimal impact since it operates externally.

**Use Cases**:

* Credentialed scanning is useful for comprehensive vulnerability assessments, compliance checks, and identifying configuration issues that might not be externally visible.
* Non-credentialed scanning is suitable for quickly identifying external vulnerabilities, conducting preliminary assessments, and assessing the security posture from an external attacker's perspective.

Both approaches have their advantages and limitations. The choice between credentialed and non-credentialed scanning depends on the specific goals of the assessment, the available resources, and the level of access that can be granted to the vulnerability scanner.



## False Positives, False Negatives, and Log Review

After a scanning tool completes its execution, it typically generates a comprehensive summary report that outlines all the vulnerabilities detected during the scan. This report serves as a valuable resource for understanding the security status of the scanned systems or network. Here's what you can expect from such a report:

**1. Vulnerability Overview:** The report will provide an overview of the total number of vulnerabilities discovered, along with a breakdown based on their severity levels. Vulnerabilities are often color-coded to indicate their criticality, with red representing the most urgent vulnerabilities that require immediate attention.

**2. Criticality Levels:** Vulnerabilities are usually categorized into different criticality levels, such as high, medium, and low. The color-coded system helps quickly identify which vulnerabilities need to be addressed first.

**3. Scope Analysis:** The report might allow you to view vulnerabilities by scope, such as sorting them by the most critical issues across all hosts. This helps prioritize remediation efforts by focusing on the vulnerabilities that have the highest potential impact.

**4. Host-Level Details:** The report might also enable you to view vulnerabilities on a host-by-host basis. This breakdown provides insights into the vulnerabilities specific to each system or device within the network.

**5. Vulnerability Details:** For each identified vulnerability, the report should provide detailed information, including its description, severity level, potential impact, and how it was detected. This information helps system administrators and security teams understand the nature of each vulnerability.

**6. Remediation Guidance:** The report should offer guidance on how to remediate each vulnerability. This might include recommendations for patches, configuration changes, or updates that need to be applied to mitigate the vulnerability. Clear and actionable steps are essential for effectively addressing the issues.

**7. References:** The report might include references or links to external sources that provide more in-depth information about each vulnerability. This allows security professionals to conduct further research and gain a better understanding of the potential risks.

**8. Executive Summary:** For management or non-technical stakeholders, the report might include an executive summary that highlights the overall security posture, critical vulnerabilities, and recommendations in a concise format.

**9. Historical Data:** In some cases, the report might also include historical data, such as trends in vulnerability detection over time. This can be useful for tracking improvements in security posture over multiple scans.

Intrusive or active scanning tends to provide a broader scope of vulnerability detection within host systems and can contribute to reducing false positive results. False positives refer to instances where a scanner or assessment tool flags something as a vulnerability, even though it isn't. To illustrate, consider a scenario where a vulnerability scan highlights an open port on a firewall. Due to a history of a particular malware using this port, the tool might interpret it as a security concern and advise closing the port. However, in reality, the port isn't open on your system. Investigating such instances demands valuable time and effort. If a vulnerability scan consistently produces excessive false positives, there's a risk of undermining the credibility of the scans altogether, potentially leading to more significant issues.

Additionally, it's crucial to remain vigilant about the possibility of false negatives—potential vulnerabilities that go undetected in a scan. This risk can be partially mitigated by running regular scans and using scanning tools from multiple vendors. Furthermore, it's worth noting that automated scan plug-ins rely on pre-compiled scripts, limiting their ability to replicate the success a skilled and determined hacker might achieve. As a result, there's a risk of creating a false sense of security solely relying on automated scans.

In conclusion, while active scanning can enhance vulnerability detection, it's essential to manage false positives and negatives effectively to maintain the accuracy and reliability of security assessments.
