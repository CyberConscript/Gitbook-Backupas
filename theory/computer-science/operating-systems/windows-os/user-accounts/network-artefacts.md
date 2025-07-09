# Network artefacts

User Artefacts via Network Traffic Analysis\



Given that authentication involves network communication, it is only natural that we can also get forensic evidence by analyzing network traffic.

Artefacts from network traffic analysis include:\


* IP Addresses and Hostnames: These identify who's involved in authentication, tracing request origin, and target.
* Authentication Protocols: These provide insights into used authentication mechanisms like Kerberos or NTLM, including fields that show the authentication type and security implications.
* Timestamps: Each packet's timestamp helps establish the sequence of events and the timing of authentication attempts.
* Success and Failure Indicators: Codes and messages in network packets state the outcome of authentication attempts, distinguishing between successful and failed attempts.
* Payload Data: Though usually encrypted, payload data can sometimes provide extra context about the request, particularly in unsecured transmissions.



### Remote Procedure Call (RPC) using NTLM authentication.

NTLM authentication relies on a 3-way handshake:

1. The first stage of this handshake is Negotiation
2. The second stage is the Challenge
3. The third stage is Authentication



We can investigate other NTLM traffic, but because these are typically encrypted, we'd need to tell Wireshark to decrypt the traffic by specifying the user's NT Password.



