# IX) Threat intelligence

#### Threat Intelligence Classifications





Threat Intel is geared towards understanding the relationship between your operational environment and your adversary. With this in mind, we can break down threat intel into the following classifications:&#x20;

*   **Strategic Intel:** High-level intel that looks into the organisation’s threat landscape and maps out the risk areas based on trends, patterns and emerging threats that may impact business decisions.

    **Examples:**

    * **Nation-state threats** (e.g., Russian APTs targeting finance).
    * **Industry-specific threats** (e.g., ransomware trends in healthcare).
    * **Geopolitical risks** that may impact cybersecurity.


*   **Technical Intel:** Looks into evidence and artefacts of attack used by an adversary. Incident Response teams can use this intel to create a baseline attack surface to analyze and develop defense mechanisms.

    **Examples:**

    * **Reverse-engineered malware samples** (e.g., disassembled TrickBot malware code).
    * **Exploit code shared on dark web forums**.
    * **Detailed YARA and Sigma rules for threat detection**


*   **Tactical Intel:** Assesses adversaries’ tactics, techniques, and procedures (TTPs). This intel can strengthen security controls and address vulnerabilities through real-time investigations.

    **Examples:**

    * **MITRE ATT\&CK mappings** (e.g., using PowerShell for credential dumping).
    * **Indicators of Compromise (IoCs)** (e.g., malicious IPs, file hashes, domains).
    * **Phishing attack patterns** used by specific threat groups.


*   **Operational Intel:** Looks into an adversary’s specific motives and intent to perform an attack. Security teams may use this intel to understand the critical assets available in the organisation (people, processes and technologies) that may be targeted.

    **Examples:**

    * **Threat actor infrastructure updates** (e.g., a ransomware gang switching to new C2 domains).
    * **Zero-day vulnerabilities being exploited in the wild**.
    * **Malware command-and-control (C2) server IP addresses**.



Threat intel is obtained from a data-churning process that transforms raw data into contextualised and action-oriented insights geared towards triaging security incidents. The transformational process follows a six-phase cycle:\


### Direction

Every threat intel program requires to have objectives and goals defined, involving identifying the following parameters:

* Information assets and business processes that require defending.
* Potential impact to be experienced on losing the assets or through process interruptions.
* Sources of data and intel to be used towards protection.
* Tools and resources that are required to defend the assets.

This phase also allows security analysts to pose questions related to investigating incidents.

### Collection

Once objectives have been defined, security analysts will gather the required data to address them. Analysts will do this by using commercial, private and open-source resources available. Due to the volume of data analysts usually face, it is recommended to automate this phase to provide time for triaging incidents.

### Processing

Raw logs, vulnerability information, malware and network traffic usually come in different formats and may be disconnected when used to investigate an incident. This phase ensures that the data is extracted, sorted, organised, correlated with appropriate tags and presented visually in a usable and understandable format to the analysts. SIEMs are valuable tools for achieving this and allow quick parsing of data.

### Analysis

Once the information aggregation is complete, security analysts must derive insights. Decisions to be made may involve:

* Investigating a potential threat through uncovering indicators and attack patterns.
* Defining an action plan to avert an attack and defend the infrastructure.
* Strengthening security controls or justifying investment for additional resources.

\


### Dissemination

Different organisational stakeholders will consume the intelligence in varying languages and formats. For example, C-suite members will require a concise report covering trends in adversary activities, financial implications and strategic recommendations. At the same time, analysts will more likely inform the technical team about the threat IOCs, adversary TTPs and tactical action plans.

### Feedback

The final phase covers the most crucial part, as analysts rely on the responses provided by stakeholders to improve the threat intelligence process and implementation of security controls. Feedback should be regular interaction between teams to keep the lifecycle working.
