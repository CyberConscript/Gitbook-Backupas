# Emails

## Email protocols

There are 3 specific protocols involved to facilitate the outgoing and incoming email messages, and they are briefly listed below.

* SMTP (Simple Mail Transfer Protocol) - to handle the sending of emails.&#x20;
* POP3 (Post Office Protocol) - Is responsible transferring email between a client and a mail server.&#x20;
* IMAP (Internet Message Access Protocol) - Is responsible transferring email between a client and a mail server.&#x20;

You should have noticed that both POP3 and IMAP sound same by definition. But there are differences between these two.



**POP3**

* Emails are **downloaded and stored on a single device**.
* Sent messages are stored on the single device from which the email was sent.
* Emails can only be accessed from the single device the emails were downloaded to.
* If you want to keep messages on the server, make sure the setting "Keep email on server" is enabled, or all messages are deleted from the server once downloaded to the single device's app or software.

**IMAP**

* Emails are stored on the server and can be downloaded to **multiple devices**.
* Sent messages are stored on the server.
* Messages can be synced and accessed across multiple devices.



<figure><img src="../../../.gitbook/assets/image (1).png" alt=""><figcaption></figcaption></figure>

Below is an explanation of each numbered point from the above diagram:

1. Alexa composes an email to Billy (`billy@johndoe.com`) in her favorite email client. After she's done, she hits the send button.
2. The SMTP server needs to determine where to send Alexa's email. It queries DNS for information associated with `johndoe.com`.&#x20;
3. The DNS server obtains the information `johndoe.com` and sends that information to the SMTP server.&#x20;
4. The SMTP server sends Alexa's email across the Internet to Billy's mailbox at `johndoe.com`.
5. In this stage, Alexa's email passes through various SMTP servers and is finally relayed to the destination SMTP server.&#x20;
6. Alexa's email finally reached the destination SMTP server.
7. Alexa's email is forwarded and is now sitting in the local POP3/IMAP server waiting for Billy.&#x20;
8. Billy logs into his email client, which queries the local POP3/IMAP server for new emails in his mailbox.
9. Alexa's email is copied (IMAP) or downloaded (POP3) to Billy's email client.&#x20;

## Ports of email protocols



<table data-header-hidden><thead><tr><th></th><th width="240.33333333333331"></th><th></th></tr></thead><tbody><tr><td><strong>Protocol</strong></td><td><strong>Security Setting</strong></td><td><strong>Port Number(s)</strong></td></tr><tr><td><strong>SMTP (sending mail)</strong></td><td><strong>Encrypted - TLS/STARTTLS</strong></td><td><strong>465</strong></td></tr><tr><td>SMTP (sending mail)</td><td>Encrypted - SSL</td><td>465</td></tr><tr><td>SMTP (sending mail)</td><td>Unencrypted</td><td>25* (or 26)</td></tr><tr><td><strong>POP3 (receiving mail)</strong></td><td><strong>Encrypted - TLS</strong></td><td><strong>995</strong></td></tr><tr><td>POP3 (receiving mail)</td><td>Encrypted - SSL</td><td>995</td></tr><tr><td>POP3 (receiving mail)</td><td>Unencrypted</td><td>110</td></tr><tr><td><strong>IMAP (receiving mail)</strong></td><td><strong>Encrypted - TLS</strong></td><td><strong>993</strong></td></tr><tr><td>IMAP (receiving mail)</td><td>Encrypted - SSL</td><td>993</td></tr><tr><td>IMAP (receiving mail)</td><td>Unencrypted</td><td>143</td></tr></tbody></table>

\


## Email composition



Before we begin, we need to understand that there are two parts to an email:

* the email header (information about the email, such as the email servers that relayed the email)
* the email body (text and/or HTML formatted text)

The syntax for email messages is known as the [Internet Message Format](https://datatracker.ietf.org/doc/html/rfc5322) (IMF).

Let's look at email headers first.&#x20;

What do you look for when analyzing a potentially malicious email?\


Let's start with the following email header fields:

1. From - the sender's email address
2. Subject - the email's subject line
3. Date - the date when the email was sent
4. To - the recipient's email address

## Anti-Spoofing Records

<figure><img src="../../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>



DMARC is an anti-email phishing technology that helps organizations to safeguard themselves from malicious e-mails. With DMARC, users can set filters where incoming emails can be sent to the spam folder. By doing so, enterprises can restrict ‘no-authority’ emails that invade their inboxes.&#x20;

A survey suggests that nearly 2 million domains have embraced the DMARC standards since 2019. Though this accounts for a minority of 28% of DMARC users, the numbers are increasing rapidly.&#x20;

Furthermore, following the footsteps of the top mailbox providers including Gmail, Microsoft and Yahoo Mail, over a thousand IT CEOs and organizations plan to implement DMARC soon.&#x20;

Needless to say, the appetite for DMARC is on the rise. It uses SPF and DKIM to determine the authenticity of an email message. They work together to sort legitimate and phishing or other malicious emails. Additionally, users can set filters wherein the spoof emails can be sent to their junk inbox or restrict them completely. This framework allows companies to have complete control over their inboxes.

## **SPF Records**

A Sender Policy Framework (SPF) record is a type of DNS (TXT) record that can help prevent an email address from being forged. This record is established to identify the hostnames or IP addresses that are allowed to send emails for your custom domain.  When having an SPF record specified on your domain, helps prevent a malicious actor from spoofing your domain. The SPF TXT record contains three parts: the declaration of the record type, the IP addresses and external domains that can send on your domain’s behalf, and an enforcement rule.

**The basic syntax of the record is:**

**`v=spf1 <IP> <enforcement rule>`**

For example, **securityblue.team** has the following SPF record:

**`v=spf1 a: include:mailgun.org protection.outlook.com -all`**

We can see that the record declares that it’s an SPF record, that it allows mail to be sent from mailgun.org and protection.outlook.com, and the -all specifies that the email will show a **hard fail** if the domain is spoofed by an unauthorized sender.

## **DKIM Records**

Domain Keys Identified Mail (DKIM) is a method of email authentication that cryptographically verifies if an email has been sent by its trusted servers and hasn’t been tampered with during transmission.  The way that DKIM works is that when the mail server sends an email, an encrypted hash of the email contents is generated using a private key and then it adds this hash to the email header as a DKIM signature.  The receiving server will be able to verify whether the email contents have not been tampered with by looking up the corresponding public key in the domain's DNS records.  Once the receiving mail server decrypts the email with the public key, it calculates a new hash and verifies whether the original and the newly generated hash match to ensure email message integrity.

**The basic syntax of the record is:**

_**`V=DKIM1 <key type> <public key>`**_

## DMARC Records

Domain-based Message Authentication, Reporting & Conformance (DMARC) is an email authentication, policy, and reporting protocol.  DMARC is built largely off of concepts taken from SPF and DKIM, but it adds several improvements to those protocols.  This type of record allows the domain owner to specify what should happen if emails fail both SPF and DKIM checks.  There are three basic options that the mail server can take: none, quarantine, and reject.

**The basic syntax of the record is:**

_**`v=DMARC1 <action> <report address>`**_

For example, **securityblue.team** could have the following DMARC record:

_**`v=DMARC1; p=quarantine; rua=mailto:contact@securityblue.team`**_

We can see that the record declares that it’s a DMARC record, that it sets emails to go to the quarantine/spam folder when failing both checks, and that aggregate reports are sent to [contact@securityblue.team](mailto:contact@securityblue.team) of emails that have failed DMARC.



<figure><img src="../../../.gitbook/assets/image (2).png" alt=""><figcaption></figcaption></figure>

When organization ‘A’ sends an email, the SPF helps them determine which emails can be sent on their behalf. On the other hand, when organization ‘B’ receives an email, the DKIM checks if the email is sent from a legal source. ie. Organization ‘A’.&#x20;

Businesses that send and receive marketing e-mails must use the DMARC mechanism. By doing so, organizations can protect customer relationships and brand reputation. Also, it helps to create better transparency among new and potential clients. &#x20;

[Symantec Internet Security Threat Report](https://symantec-enterprise-blogs.security.com/blogs/threat-intelligence/istr-24-cyber-security-threat-landscape) (ISTR) 2019 suggests 48% of malicious email attachments are office files. This calls for a DMARC mechanism that guards a corporate inbox. By incorporating this system, companies get a stronger hold on their inboxes. Also, this framework helps organizations target their emails and gain maximum action from their strategies. &#x20;

**DMARC Validation System:**

Following are the steps an email undergoes through a DMARC validation system: &#x20;

1. The incoming email goes through a DMARC policy check in the DNS record.&#x20;
2. Factors like valid DKIM signature, SPF IP address and domain aliment are verified.&#x20;
3. With this information, the DMARC policy decides whether the mechanism will accept, reject or flag the email.&#x20;

**Benefits of DMARC**&#x20;

Companies have benefited tremendously by deploying DMARC as their email protection protocol. Below are a few benefits that DMARC grants its users.&#x20;

* **Access to BIMI**&#x20;

The users of the DMARC system are less likely to be sent to the recipient’s spam folder. This inculcates trust and awareness regarding the organization’s authenticity. Moreover, the users of DMARC gain access to BIMI (Brand Indicators for Message Identification), an extra layer to determine a brand’s legitimacy.&#x20;

The BIMI allows senders to stand out in the recipient inboxes by displaying their logo next to the e-mail message. A survey reveals that brands observed a [21% increase in e-mail opening rates as they used BIMI](https://www.businesswire.com/news/home/20210720005361/en/Red-Sift-and-Entrust-Survey-Showing-a-Logo-Positively-Affects-Consumer-Interaction-With-Emails-Open-Rates-Buying-Behavior-Brand-Recall-and-Confidence). Not only this but, the use of BIMI and its features improved customer confidence by 90%. This implies that receivers tend to respond to emails with a logo rather than those without.&#x20;

Consider this as a new standard focused to upsurge a brand’s credibility. Currently, only Yahoo and Gmail support the BIMI standard.

* **Email activity Reports**

The DMARC helps domain owners to be in better control of their email activity. The DMARC generates an organization’s email activity reports that give insights into data that cannot be found elsewhere.&#x20;

The reports include the following information:

1. Origin of the received email
2. Number of authorized emails&#x20;
3. Number of unauthorized emails
4. Receivers of the email

The valuable data received in these reports helps brands to make informed decisions about their e-mail marketing strategies.&#x20;

* **Increased ROI on Trust**

Investing in trust solutions pays for itself.&#x20;

With a trustworthy impact on the customer’s inbox, organizations successfully drive more customers towards themselves. On the other hand, as brands drive spoof emails away, it helps to reduce the chances of falling for a counterfeit email.&#x20;

Another astounding feature of DMARC includes the ability to set controls and policies on the ongoing email activity. Policies like p=quarantine and p=reject help to send unauthorized emails to the spam folder or stop the delivery of counterfeit emails respectively.&#x20;

* **Clean Corporate inbox**&#x20;

Corporates receive hundreds of emails daily. Just like files and important documents, emails need orderly management too.&#x20;

By incorporating DMARC, organizations set strong security policies against fraudulent emails. This modern-day email plumbing allows companies to grow their digital footprint as responsible DMARC-capable sender/receivers.&#x20;

Also, the no-spam mechanism successfully drives phishing emails away, thus keeping a corporate inbox clean.&#x20;

**Conclusion**

DMARC is a framework to help fight phishing and other malicious emails. It allows companies to have complete control over their inboxes. In fact, brands increase the security of their domains and give users peace of mind.&#x20;

&#x20;
