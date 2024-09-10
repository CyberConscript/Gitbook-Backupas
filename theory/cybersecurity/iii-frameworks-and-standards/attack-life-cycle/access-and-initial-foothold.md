# Access and initial foothold



## Gaining access to the network

During initial access, adversaries use various entry vectors to gain their initial foothold within a network. The first compromised asset is referred to as patient zero

* Exploiting public facing application
* Phishing
* External remote services
* Valid accounts
* Drive by compromise
* Supply chain
* Trusted relationships
* Removable media
* Hardware additions



## Establishing a foothold

Every mature threat actor will attempt to establish redundant (there could be multiple endpoints being compromised or multiple tools and techniques being used) and robust (stable and stealth) access to the victim’s network

At a high level, this foothold is a combination of the persistence (TA0003), defense evasion (TA0005), credential access (TA0006), and privilege escalation (TA0004) tactics from MITRE ATT\&CK (R) Enterprise Matrix.



When it comes to establishing a foothold, according to the MITRE ATT\&CK (R) Enterprise Matrix’s tactics, a huge range of options is available:&#x20;

• External Remote Services (T1133)\
&#x20;• Create Account (T1136)\
• Create or Modify System Process (T1543.003) \
• Scheduled Task/Job: Scheduled Task (T1053.005) \
• Boot or Logon Autostart Execution (T1547) \
• Boot or Logon Initialization Scripts (T1037) \
• Hijack Execution Flow (T1574) with DLL search order hijacking, DLL load order hijacking, DLL injection, spoofing, or side loading \
• Modify Authentication Process (T1556) or Server Software Component (T1505) \
• Event Triggered Execution: Component Object Model (COM) Hijacking (T1546.015) \
• Event Triggered Execution: Windows Management Instrumentation Even Subscription (T1546.003)



## Elevating access

* Operating-system-level and software vulnerabilities
* Bypass User Account Control
* Access Token Manipulation
* Process Injection
* Hijack Execution Flow
* Event Triggered Execution
* Valid accounts
* Escape to Host
* Brute force
* Credentials from Password Stores
* OS Credential Dumping
* Steal or Forge Kerberos Tickets
* Unsecured Credentials

## Defense evasion





* Impair Defenses
* Indicator Removal
* Hide Artifacts
* Masquerading
* Hijack Execution Flow
* Obfuscated Files or Information
* Modifying Registry





