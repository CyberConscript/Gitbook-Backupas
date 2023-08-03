# III) Frameworks and standards

Cybersecurity Framework

A **cybersecurity framework (CSF)** is a list of activities and objectives undertaken to mitigate cyber security risks. Framework when used allows an organization to make an objective statement of its current cybersecurity capabilities, identify a target level of capability, and prioritize investments to achieve that target.&#x20;

Numerous frameworks exist, each slightly varying in how they categorize cybersecurity actions and controls. These frameworks are not regulatory in nature; they don't address specific industry regulations but rather represent the prevailing best practices in IT security governance at large. Most organizations historically select a particular framework, and some might even combine multiple frameworks. The majority of these frameworks possess an international scope, although some target national audiences. Many of them are tied to certification programs to showcase successful implementation by staff and consultants.



* Service Organization Control (SOC2)—evaluates the internal controls implemented by the service provider to ensure compliance with Trust Services Criteria (TSC) when storing and processing customer data. TSC refers to security, confidentiality, integrity, availability, and privacy properties. An SOC2 Type I report assesses the system design, while a Type II report assesses the ongoing effectiveness of the security architecture over a period of 6-12 months. SOC2 reports are highly detailed and designed to be restricted. They should only be shared with the auditor and regulators, and with important partners under non-disclosure agreement (NDA) terms.
* SOC3—a less detailed report certifying compliance with SOC2. SOC3 reports can be freely distributed.

The Statements on Standards for Attestation Engagements (SSAE) are audit specifications developed by the American Institute of Certified Public Accountants (AICPA). These audits are designed to assure consumers that service providers—notably cloud providers, but including any type of hosted or third-party service—meet professional standards ([aicpa.org/interestareas/frc/assuranceadvisoryservices/serviceorganization-smanagement.html](https://www.aicpa.org/interestareas/frc/assuranceadvisoryservices/serviceorganization-smanagement.html)). Within SSAE No. 18 (the current specification), there are several levels of reporting:

#### Statements on Standards for Attestation Engagements (SSAE) Service Organization Control (SOC) <a href="#395c684c-e360-44c7-8830-17be01c9ce75" id="395c684c-e360-44c7-8830-17be01c9ce75"></a>

* Security Guidance ([cloudsecurityalliance.org/research/guidance](https://cloudsecurityalliance.org/research/guidance))—a best practice summary analyzing the unique challenges of cloud environments and how on-premises controls can be adapted to them.
* Enterprise reference architecture ([ea.cloudsecurityalliance.org](https://ea.cloudsecurityalliance.org/))—best practice methodology and tools for CSPs to use in architecting cloud solutions. The solutions are divided across a number of domains, such as risk management and infrastructure, application, and presentation services.
* Cloud controls matrix ([cloudsecurityalliance.org/research/working-groups/cloud-controls-matrix](https://cloudsecurityalliance.org/research/working-groups/cloud-controls-matrix/))—lists specific controls and assessment guidelines that should be implemented by CSPs. For cloud consumers, the matrix acts as a starting point for cloud contracts and agreements as it provides a baseline level of security competency that the CSP should meet.

The not-for-profit organization Cloud Security Alliance (CSA) produces various resources to assist cloud service providers (CSP) in setting up and delivering secure cloud platforms. These resources can also be useful for cloud consumers in evaluating and selecting cloud services.

#### Cloud Security Alliance <a href="#875b5f4d-6c5c-4f6b-af7e-6076d6a56b6f" id="875b5f4d-6c5c-4f6b-af7e-6076d6a56b6f"></a>

Where ISO 27K is a cybersecurity framework, ISO 31K ([iso.org/iso-31000-risk-management.html](https://www.iso.org/iso-31000-risk-management.html)) is an overall framework for enterprise risk management (ERM). ERM considers risks and opportunities beyond cybersecurity by including financial, customer service, competition, and legal liability factors. ISO 31K establishes best practices for performing risk assessments.

#### ISO 31K <a href="#d2c0aff4-1f5e-45a2-8c0d-0043664c920b" id="d2c0aff4-1f5e-45a2-8c0d-0043664c920b"></a>

The International Organization for Standardization (ISO) has produced a cybersecurity framework in conjunction with the International Electrotechnical Commission (IEC). The framework was established in 2005 and revised in 2013. Unlike the NIST framework, the ISO 27001 Information Security Management standard must be purchased ([iso.org/standard/54534.html](https://iso.org/standard/54534.html)). ISO 27001 is part of an overall 27000 series of information security standards, also known as 27K. Of these, 27002 classifies security controls, 27017 and 27018 reference cloud security, and 27701 focuses on personal data and privacy.

#### International Organization for Standardization (ISO) 27K <a href="#af353487-44fb-4e37-94c8-b43b02e56708" id="af353487-44fb-4e37-94c8-b43b02e56708"></a>

ISO and Cloud Frameworks

Benchmarks and Secure Configuration Guides

Although a framework gives a "high-level" view of how to plan IT services, it does not generally provide detailed implementation guidance. At a system level, the deployment of servers and applications is covered by benchmarks and secure configuration guides.

#### Center for Internet Security (CIS) <a href="#7a6184a7-7fb5-4e92-bbec-2945e5d74bcc" id="7a6184a7-7fb5-4e92-bbec-2945e5d74bcc"></a>

The Center for Internet Security ([cisecurity.org](https://cisecurity.org)) is a not-for-profit organization (founded partly by The SANS Institute). It publishes the well-known "The CIS Critical Security Controls." The CIS-RAM (Risk Assessment Method) can be used to perform an overall evaluation of security posture ([learn.cisecurity.org/cis-ram](https://learn.cisecurity.org/cis-ram)).

CIS also produces benchmarks for different aspects of cybersecurity. For example, there are benchmarks for compliance with IT frameworks and compliance programs, such as PCI DSS, NIST 800-53, SOX, and ISO 27000. There are also product-focused benchmarks, such as for Windows Desktop, Windows Server, macOS, Linux, Cisco, web browsers, web servers, database and email servers, and VMware ESXi. The CIS-CAT (Configuration Access Tool) can be used with automated vulnerability scanners to test compliance against these benchmarks ([cisecurity.org/cybersecurity-tools/cis-cat-pro/cis-cat-faq](https://www.cisecurity.org/cybersecurity-tools/cis-cat-pro/cis-cat-faq/)).

#### OS/Network Appliance Platform/Vendor-specific Guides <a href="#86691549-8cd7-4783-9a12-91b19fdfa983" id="86691549-8cd7-4783-9a12-91b19fdfa983"></a>

Operating system (OS) best practice configuration lists the settings and controls that should be applied for a computing platform to work in a defined role, such as client workstation, authentication server, network switch/router/firewall, web/application server, and so on.

Most vendors will provide guides, templates, and tools for configuring and validating the deployment of network appliances, operating systems, web servers, and application/database servers. The security configurations for each of these devices will vary not only by vendor but by device and version as well. The vendor's support portal will host the configuration guides (along with setup/install guides and software downloads and updates) or they can be easily located using a web search engine.

There is also detailed guidance available from several organizations to cover both vendor-neutral deployments and to provide third-party assessment and advice on deploying vendor products. Apart from the CIS controls, some notable sources include:

* Department of Defense Cyber Exchange provides Security Technical Implementation Guides (STIGs) with hardening guidelines for a variety of software and hardware solutions ([public.cyber.mil](https://public.cyber.mil)).
* National Checklist Program (NCP) by NIST provides checklists and benchmarks for a variety of operating systems and applications ([nvd.nist.gov/ncp/repository](https://nvd.nist.gov/ncp/repository)).

#### Application Servers <a href="#e1f13bd0-6997-48a6-b6c7-caf48f34bf4e" id="e1f13bd0-6997-48a6-b6c7-caf48f34bf4e"></a>

Most application architectures use a client/server model. This means that part of the application is a client software program, installed and run on separate hardware to the server application code. The client interacts with the server over a network. Attacks can therefore be directed at the local client code, at the server application, or at the network channel between them. As well as coding issues, the applications need to take account of platform issues. The client application might be running in a computing host alongside other, potentially malicious, software. Code that runs on the client should not be trusted. The server-side code should implement routines to verify that input conforms to what is expected.

## Web Server Applications <a href="#1dabaca3-c0fc-4e04-bc32-5e40e740cfef" id="1dabaca3-c0fc-4e04-bc32-5e40e740cfef"></a>

The Open Web Application Security Project (OWASP) is a globally recognized non-profit organization focused on improving the security of software. OWASP provides valuable resources, tools, and knowledge to help organizations build and maintain secure applications and websites. It operates as a community-driven effort involving security professionals, developers, educators, and organizations with the shared goal of enhancing web application security.

Key Aspects of OWASP:

**1. Educational Resources:** OWASP offers a wide range of educational resources, including articles, documentation, tutorials, and guides, covering various aspects of web application security. These resources are freely accessible and provide valuable insights into common vulnerabilities, attack vectors, and best practices for secure development.

**2. Top Ten Project:** One of OWASP's most well-known initiatives is the OWASP Top Ten Project. This project lists the ten most critical web application security risks, providing developers and security professionals with guidance on identifying and mitigating these risks. The list is periodically updated to reflect the evolving threat landscape.

**3. Projects and Tools:** OWASP hosts numerous open-source projects and tools that address specific security challenges. These projects cover areas such as threat modeling, security testing, secure coding, and more. Examples include the OWASP ZAP (Zed Attack Proxy) for web application security testing and the OWASP Juice Shop, a deliberately insecure web application for training and testing purposes.

**4. Conferences and Events:** OWASP organizes conferences, events, and local chapter meetings around the world. These gatherings provide opportunities for networking, knowledge sharing, and collaboration among security professionals, developers, and enthusiasts. The flagship event is the OWASP Global AppSec conference.

**5. Community Collaboration:** OWASP operates on a community-driven model, encouraging collaboration among security experts and developers. The organization emphasizes open participation, peer review, and sharing practical experiences to improve overall web application security.

**6. Secure Development Lifecycle (SDL) Integration:** OWASP promotes the integration of security practices throughout the software development lifecycle. This includes considerations for secure design, coding, testing, deployment, and maintenance of applications.

The OWASP community and its resources have had a significant impact on shaping the way organizations approach application security. By providing free and accessible knowledge, tools, and best practices, OWASP empowers developers and security practitioners to build more secure software and defend against cyber threats. It has become a central hub for professionals interested in advancing the security of web applications and technology.

\


## **Cybersecurity Regulations, Standards, and Legislation:**

Cybersecurity regulations, standards, and legislation are essential components of the global effort to secure digital systems, protect sensitive data, and mitigate cyber threats. They provide guidelines, requirements, and frameworks that organizations, governments, and industries use to establish effective cybersecurity practices and ensure a secure digital environment. Here's an overview of each:

**1. Cybersecurity Regulations:** Cybersecurity regulations are legal mandates imposed by governmental bodies that define specific requirements for organizations to follow in order to safeguard digital systems and data. These regulations vary by country and jurisdiction and often focus on industries that handle sensitive information. Non-compliance with these regulations can result in legal penalties. Examples include the General Data Protection Regulation (GDPR) in the EU, the Health Insurance Portability and Accountability Act (HIPAA) in the U.S. healthcare sector, and the New York State Department of Financial Services (NYDFS) Cybersecurity Regulation.

**2. Cybersecurity Standards:** Cybersecurity standards are voluntary guidelines and best practices developed by industry organizations, consortia, and international bodies. They provide frameworks for implementing cybersecurity controls, assessing risk, and achieving specific security goals. Standards help organizations adopt consistent and recognized cybersecurity practices. Examples include ISO/IEC 27001 for information security management, NIST SP 800-53 for federal systems in the U.S., and PCI DSS for payment card data security.

**3. Cybersecurity Legislation:** Cybersecurity legislation refers to laws enacted by governments to address cybersecurity issues. These laws can cover a wide range of topics, including data breach reporting, protection of critical infrastructure, and regulation of cybercrime. Legislation aims to empower law enforcement agencies and authorities to combat cyber threats effectively. Examples include the Cybersecurity Information Sharing Act (CISA) in the U.S., which encourages sharing of cyber threat information between private and public sectors, and the UK's Computer Misuse Act, which criminalizes unauthorized access to computer systems.

Key Benefits of Regulations, Standards, and Legislation:

* **Uniformity:** Regulations establish consistent security practices within specific industries or regions, ensuring a baseline level of cybersecurity across organizations.
* **Accountability:** Compliance with regulations holds organizations accountable for protecting sensitive data and systems.
* **Risk Management:** Standards provide guidelines for risk assessment, helping organizations identify and address vulnerabilities.
* **Interoperability:** Adhering to standards enables interoperability between systems and organizations, fostering collaboration.
* **Global Consistency:** International standards enable global organizations to adopt consistent cybersecurity practices regardless of location.
* **Legal Framework:** Legislation provides a legal framework for prosecuting cybercriminals and enforcing cybersecurity measures.

Challenges and Considerations:

* **Rapid Change:** Cyber threats evolve quickly, necessitating regular updates to regulations and standards.
* **Complexity:** Navigating a landscape of multiple regulations and standards can be complex and resource-intensive.
* **Cross-Border Compliance:** International businesses must navigate diverse regulations when operating across borders.
* **Balancing Security and Privacy:** Regulations must balance security needs with individuals' privacy rights.

In summary, cybersecurity regulations, standards, and legislation play a vital role in establishing a secure digital environment, offering guidance, legal mandates, and best practices to protect systems, data, and critical infrastructure. Organizations should stay informed about relevant regulations and standards and adopt practices that align with their specific industry and risk profile.

## **Personal Data and the General Data Protection Regulation (GDPR):** <a href="#a5cae894-40ad-4509-95ba-ba260bef0d30" id="a5cae894-40ad-4509-95ba-ba260bef0d30"></a>

Personal data refers to any information that relates to an identifiable individual, directly or indirectly. This encompasses a wide range of data, including names, addresses, email addresses, phone numbers, identification numbers, location data, online identifiers, and even factors specific to an individual's physical, physiological, genetic, mental, economic, cultural, or social identity.

The General Data Protection Regulation (GDPR) is a comprehensive data protection and privacy regulation implemented by the European Union (EU) in 2018. Its primary goal is to provide individuals with greater control over their personal data and to harmonize data protection regulations across EU member states. The GDPR applies not only to organizations within the EU but also to entities outside the EU that process personal data of EU citizens.

Key Principles of the GDPR:

1. **Lawfulness, Fairness, and Transparency:** Organizations must process personal data lawfully, fairly, and transparently. Individuals should be informed about the processing of their data.
2. **Purpose Limitation:** Personal data should be collected for specific, explicit, and legitimate purposes. It shouldn't be processed in ways incompatible with these purposes.
3. **Data Minimization:** Organizations should only collect and process the data necessary for their intended purposes. Data should be kept accurate and up to date.
4. **Accuracy:** Data should be accurate and kept up to date. Inaccurate data must be corrected or erased.
5. **Storage Limitation:** Personal data should be retained only for as long as necessary for the specified purposes.
6. **Integrity and Confidentiality:** Organizations must ensure the security and confidentiality of personal data through appropriate technical and organizational measures.
7. **Accountability:** Organizations are responsible for complying with the GDPR's principles and demonstrating their compliance.

Rights of Data Subjects:

The GDPR grants individuals various rights concerning their personal data, including:

* The right to access their data.
* The right to rectify inaccurate data.
* The right to erasure (the "right to be forgotten").
* The right to restrict processing.
* The right to data portability.
* The right to object to processing, including for direct marketing.
* Rights related to automated decision-making and profiling.

Organizational Obligations:

Organizations that collect and process personal data under the GDPR have several obligations, including obtaining clear consent before processing data, implementing data protection policies and practices, conducting data protection impact assessments for high-risk activities, and reporting data breaches within a specified timeframe.

Non-compliance with the GDPR can result in significant fines. The regulation has had a global impact, influencing data protection practices worldwide and prompting organizations to enhance their data protection measures.

It's important to note that the GDPR is a complex regulation with various nuances and intricacies. Organizations that handle personal data, particularly those dealing with EU citizens' data, need to carefully understand and implement its requirements to ensure compliance and protect individuals' privacy.them.

## Laws and Regulations at Different Levels <a href="#2c80cc8e-e016-4e87-83d2-14d62bcc651d" id="2c80cc8e-e016-4e87-83d2-14d62bcc651d"></a>

Navigating compliance matters can be intricate due to the diverse origins of laws. Laws stem from various sources, leading to a complex landscape. For instance, the General Data Protection Regulation (GDPR) isn't applicable to American data subjects; however, it does extend to American companies that gather or process personal data of individuals within EU countries. Within the United States, legal jurisdiction includes national federal laws, state laws, as well as a legal framework applicable to U.S. territories such as Puerto Rico, the U.S. Virgin Islands, Guam, and American Samoa.

Federal laws commonly center around either regulations like the Federal Information Security Management Act (FISMA) for federal departments or vertical laws impacting specific industries. Examples of vertical laws encompass the Gramm–Leach–Bliley Act (GLBA) tailored to financial services and the Health Insurance Portability and Accountability Act (HIPAA).

In a trend parallel to the GDPR, certain states have introduced "horizontal" regulations pertaining to personal data. Notably, the California Consumer Privacy Act (CCPA) stands as a prominent instance of state legislation.

Moreover, industry-specific mandates can give rise to compliance concerns. An exemplar of this is the Payment Card Industry Data Security Standard (PCI DSS), which outlines protocols for secure handling and storage of financial data.

Should you seek more comprehensive insights into U.S. privacy regulations, Varonis' blog offers a valuable overview.

It's worth noting that the landscape of laws and regulations is dynamic, often evolving to address new challenges and technologies. Staying informed and updated is crucial for maintaining compliance.\
