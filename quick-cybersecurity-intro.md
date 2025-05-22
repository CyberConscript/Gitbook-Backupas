# Quick cybersecurity intro

### <mark style="color:purple;background-color:yellow;">**Governance, risk & compliance**</mark>

#### So how does it begin?

Well, You need someone in an organization wanting to improve their own information security posture. That somebody takes responsibility to build everything from the ground level. This is where security starts.

**Governance** is a way of defining and distributing the responsibilities, roles, and procedures for making decisions on information security for an organization. It is used to define specific security objectives, enable the attainment of these objectives and evaluate performance.

#### How do we know how badly we need it? Answer: by doing Your homework.

**Risk management** is all about understanding the various risks that an organization will face. Risk is the probability of harm to an organization's assets. Identifying, understanding, and controlling those risks on a reasonable level, operating with or totally mitigating some risks. But the fact is that risk can not be eliminated, it can be accepted or mitigated.

#### What is our status?

**Compliance** means meeting the requirements in defined guidelines. Requirements or objectives that seek to improve an organization's information security posture. Might be defined internally by the organization or mandated by local government, trade groups, or standards bodies as a way of applying common practices. A **control framework** is a guideline that:

* Groups and organizes security controls;
* Helps to design a new security program or edit existing one;
* Audits the implementation of controls to prove that they are in compliance with frameworks or specified controls.

Control frameworks must be followed by one or more of these reasons: legislative or government regulatory purposes, industry, competitive, or just simply there are some best practices that match the company's objectives.

Evaluation of compliance is done by determining the level of conformity to a framework, identifying gaps in control implementation for possible missing or not correctly implemented controls, determining the overall effectiveness of controls.

Some standards:

* **ISO/IEC 27000 series** - standards and best practices focused on creating an information security management system.
* **NIST** - National Institute of Standards and Technology special publication 800 series on various topics.
* **CIS** - Center for Internet Security controls. Basic actions on how to counter the most common threats.

Some other compliance regulations:

* **HIPPA** - health insurance portability and accountability act (HIPAA) deals with electronic patient health information Sarbanes.
* **SOX** - Sarbanes-Oxley related to financial reporting of internal controls and disclosure. Ensure integrity of financial data.
* **GDPR** - European law to protect the private data of EU citizens regardless of the company's location.

Industry requirements:

* **PCI DSS** - payment card data and implementation of specific security controls. North American Electric reliability corporation critical infrastructure protection.
* **NERC CIP** - Electric reliability corporation critical infrastructure protection is cybersecurity and physical controls for key portions of information systems that manage the power system.

### <mark style="color:purple;background-color:yellow;">Protection of assets</mark>

#### Wait, what is an asset?

**The asset** might be an item of property owned by a person or company, regarded as having value. In information or cyber security, an asset is any data, device, or another component of the environment that supports information-related activities. Assets can include hardware, software, and confidential information. That is why assets can be divided into two types:

* Tangible assets or physical: buildings, manufacturing facilities, data centers, distribution systems, inventory, raw materials, transport. Requires big amounts of investment to obtain and maintain tangible assets.
* Intangible assets or logical assets: intellectual property, strategy or plans, financial data, business processes, internally developed methods, customer data, internal data.

If any of these assets would be disclosed or lost then the organization could suffer financial harm.

#### Meet the threats

**A threat** is an event or condition that has the potential for causing asset loss and undesirable consequences. Examples: loss of the asset, disruption, exposure of internal information.

These threats can stop an organization from conducting normal operations, limit business success or just simply bring the end of the organization.

#### Security pillars

Overall security posture is measured on how good the organization is at: **prevention**, **detection**, and **response**.

When we discuss data and information, we must consider **Information assurance**. The **CIA** triad refers to an information security model made up of the three main components where each component represents a fundamental security objective of information assurance:

* **Confidentiality** - keep it a secret from unauthorized disclosure of information. Mandated by policy and implemented through access controls, system design, encryption.
* **Availability** - reachable on-demand or ensure access to information and information systems to authorized individuals when needed. Implemented by redundancy.
* **Integrity** - no alteration, unauthorized modification, or destruction of data. Not modified by individuals that should not be able to do so. Done by implementing a file system, digital signatures, and file provenance (prove origin).

Other key security principles used in building information security:

* **Identification** - recognize who You are.
* **Authentication** - prove who You say You are.
* **Authorization** - what are You allowed or granted to do or see.
* **Non-repudiation** - ensuring undeniable proof like you received something.
* **Accountability** - ability to record activities of users on who, when, what.

**Controlling implementation of security principles**

There always will be some **security controls** that work as safeguards or countermeasures. They can be placed as procedures, logical or physical means of minimizing, detecting or avoiding, or reacting to identified security risks. Meaning, that controls can be applied before, during, or even after an event.

Security controls can be grouped into separate categories. However, there are some real-world cases when some controls can be more than in one category:

* **Detective** - identify key activities and distinguish unique characteristics about an event as it happens. (Antivirus, security officer, user roles)
* **Preventive** - stop specific actions before the event would have occurred. (Antivirus, security guard, user roles)
* **Corrective** - remediate after even has occurred. (Antivirus, security guard, user roles)

Controls can also be separated by different approach or implementation type. At this case, they fall only in one particular and can not be in couple at the same time:

* **Administrative** - procedural or process-oriented security controls, focused on personnel (mandatory training).
* **Physical** - physical or tangible objects or mechanisms that serve as barriers (security guard, doors).
* **Technical** - logical controls or systems that prevent specific actions, detect and analyze activities, correct or restore normal operations (antivirus, user roles).

**Security architecture and design**

Security architecture and design are essential foundation when we want to build a secure solution and to protect a company’s data and assets at the same time.

Security architecture and design principles:

* The economy of mechanism - small and simple.
* Fail-safe defaults - creating base configuration in which default action is to deny access. Limits impact of security breaches.
* Complete mediation - is the verification of access and authority for all objects and actions. Check the source of all requests.
* Open design - design should be open for review and scrutiny.
* Separation of privilege - a division of responsibilities.
* Least privileges - granting minimum required privileges for their job.
* The least common mechanism - related to shared functions that are depended upon by all users.
* Psychological acceptability - the design with humans interaction in mind. Easy to use without hesitations, handling human error.
* Defense in depth - building multiple layers of controls and defenses.

When implementing security controls:

* Understand business objectives - security controls do not add any limitations to provided services.
* Align with security guidance - provide required protection and be consistent.
* Cost effective - use what is already provided or do not over protect.
* Easy - simple as possible. Decrease the complexity.

**Securing network communications**

How do we provide secure communications in the presence of adversaries?

First answer to this problem - cryptography. It is often used in:

* Exchange of sensitive information - allows parties to share information with only decryption keys known to them .
* Prevent unauthorized modification of information - saving the integrity.
* Prove the identities - certificates, digital signatures.

Before implementing other network security controls there always will be things to consider. For example, network architecture challenges regarding bandwidth needs. So security in networks are implemented putting these in places:

* **Demilitarized Zone (DMZ)** - isolated network segment for external internet connections to reach companies public network services.
* **IDS/IPS** - provide network awareness of malicious and potentially anomalous activity on the network. IDS - passive, just for monitoring. IPS - active, blocks potentially bad traffic and activities.
* **Next gen firewalls** - blocks traffic based on its source, destination and network ports, stateful inspection and deep packet inspection, application aware, IPS features.
* **Web proxy** and **Cloud access security brokers** (CASB) - inspect and block web traffic.
* **SIEM** - security information and event management system collects log information from multiple sources and initiate response action automatically.
* **Log management** - log management and storage.

**Securing devices**

Now it is time to protect your endpoint. As in network, same in protecting machines. More layers of protection gives stronger security:

* **Antivirus and anti malware** - centralized management and the deployment of special malware signatures on demand are key features.
* **Storage encryption** - protect data at rest on storage media to counter loss of the device threat.
* **Application whitelisting** - limiting user to authorized software, prevents introduction of malicious software to a system.
* **Data loss prevention** - prevents accidental or intentional disclosure of sensitive and classified data in email, file transfer or posting online.
* **Intrusion detection and response** - detects and responds to intrusions on real time.

Then why corporate AD infrastructure protected by next generation security solutions might still fail? Because admin forgot to place a check-mark in configuration panel. And for that reason exist configuration guides - documents that describe various configuration options for hardware, operating systems, applications.

* **Hardening guides** - instructions on improving security of systems over their out of the box configuration. NIST National checklist program.
* **Security benchmark**s (by the center for internet security (CIS)) - which are hardening guides created by the consensus of independent security professionals

**Secure development**

Unfortunately, in most cases security is considered after deployment in production, when it is more costly to implement. Security practices should be build into the solutions development lifecycle:

* **Requirements and design phase** - during this phase the system has the right foundation to operate in hostile environments with security constraints identified, threat models developed, and security controls integrated into the system design.
* Development phase - use secure coding practices to avoid common programming errors that lead to security flaws, and manual and automated code review to catch errors in the entire code base.
* Testing phase - manual application penetration testing can be used to find vulnerabilities, and prototype environments can be documented for secure deployment of systems Security can be built into an organization's SDLC. The Building Security in Maturity Model, or BSIMM, and the Open Software Assurance Maturity Model, or OpenSAMM, are two great resources.

**Physical security**

So in real physical world security can come from:

* People - employed by the organization, including all the staff members, as well as those tasked with physical protection.
* Procedures - designed to ensure that equipment, material, and visitors entering and leaving the facility are verified, logged, and monitored.
* Equipment and construction techniques - provide facility protection

Physical security controls might be implemented via:

* Entry controls - allow only authorized individuals access to a facility or spaces inside a facility.
* Sensors and alarms - provide monitoring and alerting.
* Receptions area - locations in a facility where visitors enter and are greeted and processed by staff to determine the validity of their presence there.
* Physical barriers - serve to deter, delay, or trap attackers.
* Guards - provide some deterrence for attackers in an active response during incidents.
* Visitor escorts - Visitors that are escorted while on the premises are logged and monitored during their entire time at the facility

**Last but not least: Administrative controls**

We are dealing with people. So administrative controls are oriented to human factor. As mentioned in governance, rule set on how organization runs itself must be mandatory to follow for everybody working in that organization:

* **Policies** - documented security guidance that starts with the high-level requirements.
* **Procedures** - provide step-by-step instructions for specific actions that must occur to achieve desired results.
* **Guidelines** - describe technical implementations.
* **Standards** - also describe technical implementations but more.
* **Hiring and termination procedures** - ensure that the appropriate people are brought into the organization with the position of trust and that should they leave or be asked to leave, their departure does not add risk.
* **Training and awareness** - educate and periodically remind staff members of their responsibilities for information protection.
* **Oversight and review** - methods to verify that specific actions are executed as defined by written procedures.
* **Audit** - used as a way to determine compliance with policies and procedures and their effectiveness.

**Meet the good guys: SOC**

**Security operation center** (SOC) - centralized application of people, process and technology to manage daily security operations. The main objective - protecting information assets, ensuring continous business operations. SOC success factors:

* Mission focused - define its purpose for the organization instead of a place where all the security magic happens.
* Executive level support - is a requirement for a SOC to be successful in terms of budget, headcounts, and physical space.
* People and process driven - having the right people and the right processes in place is more valuable than having the right technology.
* Detection over protection - SOC should prioritize detection capabilities over protection because protections will fail.
* Response capabilities - SOC needs to have the right response capabilities and support.

Main SOC activities:

* Monitoring - involves the direct and indirect observation of security devices and systems through their activities, events, and log data. Any anomalous, suspicious, or malicious activity is recognized and an investigation is conducted.
* Response - response is needed once events are detected that indicate an incident or attack.
* Vulnerability detection - a proactive approach to defending assets. The SOC can actively manage the automated scans and manual testing needed to identify and report vulnerabilities within the organization
* Intelligence - active approach to preparing for attacks and developing defenses and responses for known and new threat actors.
* Coordination - may be needed internally to the SOC within the organization and with external parties

### <mark style="color:purple;background-color:yellow;">Auditing and monitoring, testing</mark>

**Checking effectiveness and compliance**

**Auditing** is a process conducted by a competent and independent auditor that collects evidence associated with assertions made about a system and evaluates those assertions and forms an opinion and report on whether the assertion conforms to a standard. Main features:

* Systematic process - there are specific and repeatable methods used to conduct the audit and develop consistent results.
* Independent and objective -need to maintain independence from the area or activity under review to provide an objective assessment.
* Evidence-based - the information and observations needed to determine that the business and security objectives are being met by the internal and security controls in place to protect the organization's assets.
* Assertions - claims made by an asset and supported by its set of controls. The auditors evaluate the assertions and render an opinion on the adequacy and effectiveness of controls in place.
* Opinion and reporting
* Standards - internal and external standards or frameworks with which an organization must demonstrate compliance.

**Monitoring**

Organizations that monitor their assets and the activities within their systems are more likely to detect issues and react quickly. Doing that results in:

* Reduce risk - ideally, these programs should be deployed enterprise-wide so that the coverage for the organization is complete and consistent.
* Detect issues - the purpose of monitoring is for the observation, detection, and evaluation of issues. You have to find the problems, events, and activities that are known to be or suspected to be detrimental.
* Evaluate control effectiveness - the evaluation of those controls can lead to improvements.
* Direct remediation efforts - monitoring provides data that can start the initial evaluation of a finding or enable the correlation of other data sources to provide context around an event.

There are different fields of monitoring to cover various aspects of organizations IT infrastructure:

* Network security monitoring - program for monitoring network resources to identify malicious, suspicious, and anomalous activity. This type of program assumes that prevention will fail at some point and a breach is inevitable.
* Vulnerability management - program for monitoring an organization's assets to detect vulnerabilities and to remediate them. By reducing the number of vulnerabilities available to attackers, the organization can reduce its risk
* Continuous monitoring - which is an overarching program for maintaining an accurate and real-time view of risks across the organization. Some of the elements in continuous monitoring can include vulnerability management and network security monitoring as sources of information.

**Network Security monitoring processes**

Network-based because the primary source of data used in this type of monitoring comes from the network. Focused on threats and not vulnerabilities. Establishing the network security monitoring program needs some processes in place to ensure success in detecting and mitigating threats within the environment.:

* Planning and preparation - planning and preparation for the monitoring, evaluation, escalation, and remediation of threats. Activities can include determining areas of the network that need monitoring, determining the steps needed during investigation, and reporting requirements.
* Control deployment and management - choosing the right location to monitor on the network is critically important. Network visibility is an important consideration. Depending on where this sensitive data and critical business operations occur, the placement of sensors is important in capturing the right network traffic. \*Data collection and detection - sufficient storage space is needed for the network packet captures and a mechanism for transferring those captures to the analyst for analysis is also needed. \*Response and remediation -is needed to contain and limit adversarial progress inside the network. Once the threat is contained, then the cleanup and restoration of normal services are needed.

Network security monitoring tools and approaches are selected and based on different stages of network monitoring:

* **Collection** - network taps, span ports, sensors, and packet capture devices. These tools copy, route, and filter traffic of interest and apply a set of rules looking for suspicious or malicious activity in network traffic.
* **Delivery** - events, activities, and packet captures are then collected by delivery tools. These tools take the data generated by the collection tools and moves or stores it in databases or files used by the presentation tools.
* **Presentation** - simplify and enhance the job of the analyst by adding capabilities and efficiency to the analysis process
* **Software distributions** - collection, delivery, and presentation tools are bundled into software distributions to allow quick setup and use.

**Managing weak spots**

Vulnerability management is a program to identify and reduce the number of vulnerabilities within the organization's information systems:

* Weak spot (vulnerability) focused - focused on vulnerabilities and not specific threats or threat actors.
* Organization-vide - need to reduce vulnerabilities applies across the organization. If one area is not covered by the program, then the vulnerabilities that go untreated may be used to establish a foothold by attackers and leverage that access to attack the rest of the organization.
* Risk reduction - purpose of the vulnerability management program is to reduce risk for the organization.

**Just test it...**

Testing has quite simple objective in cybersecurity operations - confirmation or validation that security controls are working as intended. Outcomes or goals we intend to achieve with testing:

* Reduce risk for the organization - testing results provide the organization with details on their current security posture which can be used to determine the next actions needed to further reduce risk.
* Evaluate the presence and effectiveness of controls - the testing process evaluates whether a security control is in place and whether that control is effective given a specific set of threats and threat actions. If the control is not present, then the test may show a lack of protection in place. Some of the tests may show the presence of a security control, but identify weaknesses in the control that allow it to be disabled, bypassed, or delayed in ways that reduce its effectiveness. Some testing can be used as an approach to evaluate the response capabilities of the organization to attack. Exercise response capabilities - exercise to simulate specific types of situations that the organization may face.

### <mark style="color:purple;"><mark style="background-color:green;"><mark style="background-color:yellow;">**Managing incidents and Security operations**<mark style="background-color:yellow;"><mark style="background-color:green;"></mark>

There's always the possibility that a weakness will be found and exploited. The organization needs to prepare for these contingencies through appropriate planning, monitoring, and execution. It is wise to be prepared for the worst with proper **Incident management**.

Incident management objectives:

* **Detect and report incident** - incident managers need to ensure that incidents are detected quickly, diagnosed accurately, and reported. There are lots of statistics that show that threat actors invade corporate networks and remain undetected for many weeks or months
* **Contain the threat** and **minimize damage** - contain and isolate the threat and limit the damage that the threat or threat actor may cause.
* **Eradicate** the threat and prevent recurrence - organizations that fail to change their environment face reinfection of malware or continued threats from persistent threat actors.
* **Restore operations** - normal operations need to be restored. Affected services need to be recovered so that business can continue to operate. Cleanup operations and further investigation may be needed to adapt the environment to prevent future incidents

There exist some other plans related to incidents which are more focused on making operations spinning during disruptions. They are **Disaster recovery** and **Business continuity** plans:

* **Business continuity plan** has goals to preserve business during a disruption, reduce impact of a disruption and speed the recovery after a disruption.
* **Disaster recovery** - restoring normal business operations after the disaster takes place.
* **Crisis management plan** - integrate the Business continuity and Disaster recovery plans in a comprehensive manner. (NIST 800-34 - The National Institute of Standards and Technology has special publication 800-34, which is guide for continuity planning)

**Security operations**

Security operations generally does the daily hands on preventive, detective and responsive activities. So they cover:

* Support IT oriented investigations - can be internal or/and external.
* Manage the security IT assets and users - focused on identifying and configuring IT assets for security purposes and identity and access management.
* Manage and utilize security technologies.
* Plan and prepare to handle contingencies the organization might face.

### **User education**

Even when technologies are constantly improving there always will remain other side - people who are using these technologies.

**Personnel security**

The skill gap between technologies and end users will wider with each day. There is need for different types of training for normal users and security personel.

**Security awareness** - help inform and periodically remind employees of their role and responsibility for protecting the organization's information and systems from attack. These programs may use visual tools, such as posters, fliers, and other printed media as reminders or informative messaging about specific attacks or threats.

**Security training** - may be required for specific compliance reasons, job function, or as a general education requirement for employees. Training can be focused on specific job functions that involve sensitive data management and use or more focused on the use of information security tools or software.
