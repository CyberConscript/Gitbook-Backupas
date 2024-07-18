# Emails

Email, or electronic mail, is a method of exchanging digital messages between people using electronic devices. Here’s a basic overview of how email works:

## Components of an Email System

1. **Email Clients**: These are applications used to send and receive emails. Examples include Microsoft Outlook, Gmail, Apple Mail, and Thunderbird.
2. **Mail Servers**: These servers handle the storage and forwarding of emails. There are two main types of servers involved in email communication:
   * **SMTP Server** (Simple Mail Transfer Protocol): Used to send and forward emails.
   * **IMAP Server** (Internet Message Access Protocol) or **POP3 Server** (Post Office Protocol): Used to receive and store emails.



## Mail flow

Below is an explanation of each numbered point from the above diagram:

1. Sender creates an email to Receiver. \
   The user writes an email in an email client and specifies the recipient’s email address.\
   When the user clicks "send," the email client connects to the SMTP server, which typically requires the user’s authentication.
2. The SMTP server needs to determine where to send sender's email. The sender's SMTP server checks the recipient’s domain (the part after the "@" in the email address). It queries DNS for information associated with receivers domain.
3. The DNS server obtains the information domain and sends that information to the SMTP server.&#x20;
4. The SMTP server sends senders email across the Internet to receivers mailbox.
5. In this stage, senders email passes through various SMTP servers and is finally relayed to the destination SMTP server.&#x20;
6. Sender's email finally reached the destination SMTP server. The recipient’s SMTP server stores the email and forwards it to the appropriate IMAP or POP3 server.
7. Sender's email is forwarded and is now sitting in the local POP3/IMAP server waiting for receiver.&#x20;
8. Receiver logs into his email client. The recipient’s email client periodically checks the IMAP or POP3 server for new emails. When a new email is detected, the client downloads it (for POP3) or syncs it (for IMAP) to the recipient’s device.
9. Senders email is copied (IMAP) or downloaded (POP3) to receivers email client.&#x20;

## Email protocols

There are 3 specific protocols involved to facilitate the outgoing and incoming email messages, and they are briefly listed below.

* **SMTP (Simple Mail Transfer Protocol)**:
  * Used for sending emails.
  * Works on port 25 (or port 587 for secure transmission).
  *   **Commands**: SMTP communication involves a series of commands and responses:

      * **HELO/EHLO**: Initiates the conversation with the server.
      * **MAIL FROM**: Specifies the sender's email address.
      * **RCPT TO**: Specifies the recipient's email address.
      * **DATA**: Signals the beginning of the message body.
      * **QUIT**: Ends the SMTP session.




*   **IMAP (Internet Message Access Protocol)**:

    * Used for retrieving emails.
    * Allows multiple devices to access the same mailbox and keeps emails on the server. Ideal for users who access their email from various devices (e.g., phone, tablet, computer).
    * **State Synchronization**: Changes made on one device (e.g., reading, deleting) are reflected on all other devices. Real-time synchronization of email status and folder structure.
    * **Folder Management**: Supports multiple folders/labels and server-side search.
    * Works on port 143 (or port 993 for secure transmissions).
    * **Commands**: IMAP includes commands for managing and accessing emails:
      * **LOGIN**: Authenticates the user.
      * **SELECT**: Selects a mailbox to access.
      * **FETCH**: Retrieves specific emails.
      * **STORE**: Updates flags/labels on emails.
      * **LOGOUT**: Ends the IMAP session.

    &#x20;
* **POP3 (Post Office Protocol version 3)**:
  * Used for retrieving emails.
  * Downloads emails to the recipient’s device and typically deletes them from the server.
  * Works on port 110 (or port 995 for secure transmission).
  * **Commands**: POP3 communication involves simpler commands compared to IMAP:
    * **USER**: Specifies the username.
    * **PASS**: Provides the password.
    * **STAT**: Checks the number of messages and their size.
    * **RETR**: Retrieves a specific message.
    * **DELE**: Deletes a specific message.
    * **QUIT**: Ends the POP3 session.





Comparison

| Feature           | IMAP                         | POP3                                                      |
| ----------------- | ---------------------------- | --------------------------------------------------------- |
| Storage           | Emails remain on the server  | Emails are downloaded and usually deleted from the server |
| Access            | Multi-device                 | Single-device                                             |
| Synchronization   | Full synchronization         | No synchronization                                        |
| Folder Management | Supports server-side folders | Limited or no folder support                              |
| Real-time Updates | Supports real-time updates   | Downloads emails periodically                             |
| Connection        | Persistent connection        | Connects, retrieves, and disconnects                      |
| Complexity        | More complex                 | Simpler                                                   |



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





#### Security Measures

* **Encryption**: TLS/SSL encryption is used to secure the transmission of emails.
* **Authentication**: Users must authenticate to access their email accounts, usually with a username and password.
* **Spam Filters**: These help to filter out unwanted emails.
* **Antivirus Software**: Protects against malicious attachments.
* Anti-spoofing records:

