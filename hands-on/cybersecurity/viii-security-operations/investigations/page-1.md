---
description: Bl
---

# Page 1

## Scenario

A phishing email was sent to the SOC for analysis. Triage it and collect useful indicators for scoping and defensive activities.



## Investigation Submission

Question 1) To help us understand which employees have received this email, we can search in our email gateway for the subject line. What is the subject line of the email? (Format: Subject Line) _(2 points)_

Solved!

Question 2) Alternatively, we can use the sending address to help scope this incident. What is the From name, and the mailbox used to send the email? (Format: From Name, mailbox@domain.tld) _(3 points)_

Solved!

Question 3) Based on the email file when viewed in a text editor, what is the value of the Date property? (Format: Date Value) _(2 points)_

Solved!

Question 4) What is the filename of the attachment? We can see if any employees have downloaded the attachment by checking our EDR (Format: filename.ext) _(2 points)_

Solved!

Question 5) Extract the Base64 from the email file and use CyberChef to decode - this allows us to see the contents of the attached file. Search for http/https. What is the URL contained within the PDF? (Format: http/s://domain/tld/something) _(3 points)_

Solved!

Question 6) Investigate the attached file (found in the Investigation Files folder on the Desktop). What is the SHA256 hash of this file? (Format: SHA256) _(2 points)_

Solved!

Question 7) Open the attached file. What company is this document imitating? (Format: Company Name) _(2 points)_

Solved!

Question 8) To identify if any users have clicked the link within the file, we could search for network connections in our EDR or SIEM. Open the web page file associated with the URL destination. What is the full URL of the call-to-action button? (Format: Full URL) _(3 points)_

Solved!

Question 9) Click the button with the malicious URL and let it (try to) load in the browser (remember, we have no internet in our analysis machine - this is fine). What is the domain name of this site? (Format: domain.tld) _(2 points)_

Solved!

Question 10) Look at the Phishing technique on MITRE ATT\&CK. Which two sub-techniques are used by this actor? (Format: TXXXX.XXX, TXXXX.XXX) _(4 points)_

Solved!
