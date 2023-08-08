# CMD line

IP Scanning and Nmap

Conducting network scans through tools like ping can be time-consuming, lacks stealth, and often doesn't yield detailed outcomes. To efficiently discover network topology, dedicated IP scanning tools are employed. An IP scanner undertakes host discovery and reveals the interconnections between hosts within an internetwork. For comprehensive audits, enterprise suites such as Microsoft's System Center products come into play. These suites can be furnished with credentials to carry out authorized scans, fetching comprehensive host data through management protocols like the Simple Network Management Protocol (SNMP).

Among the widely favored open-source IP scanning tools, the Nmap Security Scanner (nmap.org) stands out. Nmap employs a range of host discovery techniques, including some that operate covertly, capable of bypassing security measures such as firewalls and intrusion detection systems. This tool is open-source software, accessible through packages compatible with various Windows, Linux, and macOS versions. It can be employed through command-line interactions or a graphical user interface (GUI) known as Zenmap.

The fundamental structure of an Nmap command involves specifying the IP subnet or IP host address intended for scanning. By default, Nmap engages in pinging and dispatches TCP ACK packets to ports 80 and 443 to ascertain the presence of a host when used without additional switches. On a local network segment, Nmap extends its capabilities to include ARP and ND (Neighbor Discovery) sweeps. Upon identifying a host, Nmap proceeds to conduct a port scan on that host, discerning the services it is running.
