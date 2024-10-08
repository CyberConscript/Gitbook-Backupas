# Evaluating

Common Vulnerability Scoring System

First introduced in 2005, the Common Vulnerability Scoring System (or CVSS) is a very popular framework for vulnerability scoring and has three major iterations. As it stands, the current version is CVSSv3.1 (with version 4.0 currently in draft) a score is essentially determined by some of the following factors (but many more):

&#x20; 1\. How easy is it to exploit the vulnerability?

&#x20; 2\. Do exploits exist for this?

&#x20; 3\. How does this vulnerability interfere with the CIA triad?

In fact, there are so many variables that you have to use a [calculator ](https://nvd.nist.gov/vuln-metrics/cvss/v3-calculator)to figure out the score using this framework. A vulnerability is given a classification (out of five) depending on the score that is has been assigned. I have put the Qualitative Severity Rating Scale and their score ranges into the table below. \


| <p>Rating<br></p> | <p>Score<br></p>     |
| ----------------- | -------------------- |
| None              | <p>0<br></p>         |
| Low               | <p>0.1 - 3.9<br></p> |
| Medium            | <p>4.0 - 6.9<br></p> |
| High              | <p>7.0 - 8.9<br></p> |
| Critical          | 9.0 - 10.0           |



| Advantages of CVSS                                                               | Disadvantages of CVSS                                                                                                                                                                          |
| -------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| CVSS has been around for a long time.                                            | CVSS was never designed to help prioritise vulnerabilities, instead, just assign a value of severity.                                                                                          |
| CVSS is popular in organisations.                                                | CVSS heavily assesses vulnerabilities on an exploit being available. However, only 20% of all vulnerabilities have an exploit available ([Tenable., 2020](https://www.tenable.com/research)) . |
| CVSS is a free framework to adopt and recommended by organisations such as NIST. | Vulnerabilities rarely change scoring after assessment despite the fact that new developments such as exploits may be found.                                                                   |





Vulnerability Priority Rating (VPR)

The VPR framework is a much more modern framework in vulnerability management - developed by Tenable, an industry solutions provider for vulnerability management. This framework is considered to be risk-driven; meaning that vulnerabilities are given a score with a heavy focus on the risk a vulnerability poses to the organisation itself, rather than factors such as impact (like with CVSS).

Unlike CVSS, VPR scoring takes into account the relevancy of a vulnerability. For example, no risk is considered regarding a vulnerability if that vulnerability does not apply to the organisation (i.e. they do not use the software that is vulnerable). VPR is also considerably dynamic in its scoring, where the risk that a vulnerability may pose can change almost daily as it ages.

VPR uses a similar scoring range as CVSS, which I have also put into the table below. However, two notable differences are that VPR does not have a _"None/Informational"_ category, and because VPR uses a different scoring method, the same vulnerability will have a different score using VPR than when using CVSS.

| <p>Rating<br></p> | <p>Score<br></p>      |
| ----------------- | --------------------- |
| Low               | 0.0 - 3.9             |
| Medium            | 4.0 - 6.9             |
| High              | <p>7.0 - 8.9<br></p>  |
| Critical          | <p>9.0 - 10.0<br></p> |

\


Let's recap some of the advantages and disadvantages of using the VPR framework in the table below.

| Advantages of VPR                                                                                                                       | Disadvantages of VPR                                                                                                                                                                                                   |
| --------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| VPR is a modern framework that is real-world.                                                                                           | VPR is not open-source like some other vulnerability management frameworks.                                                                                                                                            |
| VPR considers over 150 factors when calculating risk.                                                                                   | VPR can only be adopted apart of a commercial platform.                                                                                                                                                                |
| VPR is risk-driven and used by organisations to help prioritise patching vulnerabilities.                                               | VPR does not consider the CIA triad to the extent that CVSS does; meaning that risk to the confidentiality, integrity and availability of data does not play a large factor in scoring vulnerabilities when using VPR. |
| Scorings are not final and are very dynamic, meaning the priority a vulnerability should be given can change as the vulnerability ages. |                                                                                                                                                                                                                        |



## Vulnerability Databases



1\. [NVD (National Vulnerability Database)](https://nvd.nist.gov/vuln) The National Vulnerability Database is a website that lists all publically categorised vulnerabilities. In cybersecurity, vulnerabilities are classified under “Common Vulnerabilities and Exposures” (Or CVE for short).

2\. [Exploit-DB](http://exploit-db.com) . Exploit-DB retains exploits for software and applications stored under the name, author and version of the software or application.





| Term                   | Definition                                                                                                                          |
| ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Vulnerability          | <p>A vulnerability is defined as a weakness or flaw in the design, implementation or behaviours of a system or application.<br></p> |
| Exploit                | An exploit is something such as an action or behaviour that utilises a vulnerability on a system or application.                    |
| Proof of Concept (PoC) | A PoC is a technique or tool that often demonstrates the exploitation of a vulnerability.                                           |





