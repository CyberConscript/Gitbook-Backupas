# Email Forensics

## Intro

Email forensics is the branch of cyber forensics that involves the use of tools and techniques to analyze and examine the contents and components of emails. The use of proxy servers and other IP spoofing techniques make tracing the source of email a nightmare for investigators.

The various levels in email forensics are comprised of collecting data in a readable format, Data Recovery - the data to be investigated is converted into a readable format. Data Recovery provides help in restoring and filtering emails without any damage to their integrity. The various tools available for email forensics incorporate algorithms for recovery.



## Email Investigation steps



<figure><img src="../../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

Email headers consist of all the important details of the email, so this makes email header analysis a vital step in an investigation. An investigator can obtain the following information from an email header. Email header analysis gives us information about the attacker, like SMTP server detail, IP address of attacker and victim, timestamp when email was sent, and attachment file information. Tools for analysis like www.ip-adress.com, emailtracker pro, MailXmainer, MX Toolbox, etc.&#x20;

• Sender email \
• SMTP servers the mail passed \
• Network path of the mail \
• IP address of the sender \
• Timestamp \
• Client info \
• Encoding info



Steps:

1. Log on to the victim mail id.
2. Open the suspected email.
3. Obtain the header by viewing message source.&#x20;
4. It is important to know that when reading an email header every line can be forged, so only the **Received:** lines that are created by your service or computer should be completely trusted.
5.  The received is the most important part of the email header and is usually the most reliable. They form a list of all the servers/computers through which the message traveled in order to reach you.

    The received lines are best read from bottom to top. That is, the first "Received:" line is your own system or mail server. The last "Received:" line is where the mail originated. Each mail system has their own style of "Received:" line. A "Received:" line typically identifies the machine that received the mail and the machine from which the mail was received.
6. The easiest way for finding the original sender is by looking for the **X-Originating-IP** header. This header is important since it tells you the IP address of the computer that had sent the email. If you cannot find the **X-Originating-IP** header, then you will have to sift through the **Received** headers to find the sender's IP address.



## How to analyze an email header

**CAUTION:**

It is important to know that when reading an email header every line can be forged, so only the&#x20;

**Received:** lines that are created by your service or computer should be completely trusted.

**From** - This displays who the message is from, however, this can be easily forged and can be the least reliable.

**Subject** - This is what the sender placed as a topic of the email content.

**Date** - This shows the date and time the email message was composed.

**To** - This shows to whom the message was addressed, but may not contain the recipient's address.

**Return-Path** -The email address for return mail. This is the same as "Reply-To:".

**Envelope-To** - This header shows that this email was delivered to the mailbox of a subscriber whose email address is user@example.com.

**Delivery Date** - This shows the date and time at which the email was received by your (mt) service or email client.

**Received** - They form a list of all the servers/computers through which the message traveled in order to reach you.

**Dkim-Signature & Domainkey-Signature** - These are related to domain keys

**Message-id** - A unique string assigned by the mail system when the message is first created. These can easily be forged.

**Mime-Version** - Multipurpose Internet Mail Extensions (MIME) is an Internet standard that extends the format of email.&#x20;

**Content-Type** - Generally, this will tell you the format of the message, such as html or plaintext.

**X**-**Spam**-**Status** - Displays a spam score created by your service or mail client.

**X-Spam-Level** - Displays a spam score usually created by your service or mail client.

X-Sender-IP: shows senders IP

**Message Body** - This is the actual content of the email itself, written by the sender.

filename=" shows attached file name



Hashes from Win:

Get-filehash "filename' -algorithm md5



Sites to check mail headers:\
[https://toolbox.googleapps.com/apps/messageheader/analyzeheader](https://toolbox.googleapps.com/apps/messageheader/analyzeheader)\
[https://mha.azurewebsites.net/](https://mha.azurewebsites.net/)\
[https://ipinfo.io/](https://ipinfo.io/)\


## Capturing IP of attacker

Experts can set a bait to catch the culprit. Create a message and use a  tag, and the source of the picture is placed on a trusted HTTP server, then this email is sent to the spammer. When the attacker opens the mail, a log entry is created in the server’s log with the attacker’s IP. This technique fails if the mail client disables auto download and the hacker does not open the mail.



Additional Resources:

* [https://www.knowbe4.com/phishing](https://www.knowbe4.com/phishing)
* [https://www.itgovernance.co.uk/blog/5-ways-to-detect-a-phishing-email](https://www.itgovernance.co.uk/blog/5-ways-to-detect-a-phishing-email)
* [https://cheapsslsecurity.com/blog/10-phishing-email-examples-you-need-to-see/](https://cheapsslsecurity.com/blog/10-phishing-email-examples-you-need-to-see/)
* [https://phishingquiz.withgoogle.com](https://phishingquiz.withgoogle.com)
