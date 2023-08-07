# Footprinting

_Topology discovery_ (or "footprinting") means scanning for hosts, IP ranges, and routes between networks to map out the structure of the target network. That can be used to build an asset database and to identify non-authorized hosts (shadow IT) or network configuration errors.&#x20;



Basic topology discovery tasks can be accomplished using the command line tools built into Windows and Linux. The following tools report the IP configuration and test connectivity on the local network segment or subnet.

* ipconfig—show the configuration assigned to network interface(s) in Windows, including the hardware or media access control (MAC) address, IPv4 and IPv6 addresses, default gateway, and whether the address is static or assigned by DHCP. If the address is DHCP-assigned, the output also shows the address of the DHCP server that provided the lease.
* ifconfig—show the configuration assigned to network interface(s) in Linux.
* ping—probe a host on a particular IP address or host name using Internet Control Message Protocol (ICMP). You can use ping with a simple script to perform a sweep of all the IP addresses in a subnet. The following example will scan the 10.1.0.0/24 subnet from a Windows machine:

for /l %i in (1,1,255) do @ping -n 1 -w 100 10.1.0.%i | find /i "reply"



arp—display the local machine's Address Resolution Protocol (ARP) cache. The ARP cache shows the MAC address of the interface associated with each IP address the local host has communicated with recently. This can be useful if you are investigating a suspected spoofing attack. For example, a sign of a man-in-the-middle attack is where the MAC address of the default gateway IP listed in the cache is not the legitimate router's MAC address.



