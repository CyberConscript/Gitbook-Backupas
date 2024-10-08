# Firewalls

A firewall decides which packets can enter a system and which packets can leave a system. For more information about firewalls, we recommend you check the [Firewalls](https://tryhackme.com/room/redteamfirewalls) room. Without a firewall, a client can communicate with any server without restrictions; moreover, a client can function as a server and listen for incoming connections from other clients. In other words, if an attacker manages to exploit a vulnerability on a system without a firewall in place, the attacker could use the exploit to listen on a chosen port number on the victim’s machine and connect to it without any restrictions.



A host-based firewall is a piece of software installed on a system we want to protect. Unlike a network-based firewall, the host-based firewall restricts network packets to and from a single host. The firewall has two main functions:

* What can enter? Allow or deny packets from entering a system.
* What can leave? Allow or deny packets from leaving a system.

### Linux Firewalls

The first Linux firewall was a packet filtering firewall, i.e., a stateless firewall. A stateless firewall can inspect certain fields in the IP and TCP/UDP headers to decide upon a packet but does not maintain information about ongoing TCP connections. As a result, a packet can manipulate a few TCP flags to appear as if it is part of an ongoing connection and evade certain restrictions. Current Linux firewalls are stateful firewalls; they keep track of ongoing connections and restrict packets based on specific fields in the IP and TCP/UDP headers and based on whether the packet is part of an ongoing connection.



### iptables

As a front-end, iptables provides the user-space command line tools to configure the packet filtering rule set using the netfilter hooks. For filtering the traffic, iptables has the following default chains:

* **Input**: This chain applies to the packets incoming to the firewall.
* **Output**: This chain applies to the packets outgoing from the firewall.
* **Forward** This chain applies to the packets routed through the system.



`iptables -A INPUT -p tcp --dport 22 -j ACCEPT`

* `-A INPUT` appends to the INPUT chain, i.e., packets destined for the system.
* `-p tcp --dport 22` applies to TCP protocol with destination port 22.
* `-j ACCEPT` specifies (jump to) target rule ACCEPT.



`iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT`

* `-A OUTPUT` append to the OUTPUT chain, i.e., packets leaving the system.
* `-p tcp --sport 22` applies to TCP protocol with source port 22.

Let’s say you only want to allow traffic to the local SSH server and block everything else. In this case, you need to add two more rules to set the default behaviour of your firewall:

* `iptables -A INPUT -j DROP` to block all incoming traffic not allowed in previous rules.
* `iptables -A OUTPUT -j DROP` to block all outgoing traffic not allowed in previous rules.

