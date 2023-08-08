# Nslookup

Found within the Windows and Linux operating systems are essential tools for carrying out fundamental service discovery tasks:

netstat—displays the status of TCP/UDP ports on the local machine. While the same command applies to both Windows and Linux, their option syntax differs. With netstat, you can examine service configurations, such as detecting instances where an unauthorized web or FTP server is running on a host. Additionally, it's possible to detect suspicious remote connections to services on the local host or originating from the host towards remote IP addresses. When investigating potential malware, the most informative netstat output reveals which process is associated with which ports.

nslookup/dig—interrogate name records of a given domain using a specific DNS resolver. On Windows (nslookup) or Linux (nslookup/dig), these tools serve a similar purpose. An attacker might employ them to test a network's DNS service for misconfigurations. A misconfigured DNS could inadvertently allow a zone transfer, granting the attacker complete records of every host within the domain. This exposure provides a wealth of insights into the network's configuration.
