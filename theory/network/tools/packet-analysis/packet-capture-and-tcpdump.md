# Packet Capture and tcpdump

## Tcpdump

tcpdump is a command line packet capture utility for Linux ([linux.die.net/man/8/tcpdump](https://linux.die.net/man/8/tcpdump)). The basic syntax of the command is tcpdump -i eth0, where eth0 is the interface to listen on. The utility will then display captured packets until halted manually (Ctrl+C). Frames can be saved to a .pcap file using the -w option. Alternatively, you can open a pcap file using the -r option.

tcpdump is often used with some sort of filter expression to reduce the number of frames that are captured:

* Type—filter by host, net, port, or portrange.
* Direction—filter by source (src) or destination (dst) parameters (host, network, or port).
* Protocol—filter by a named protocol rather than port number (for example, arp, icmp, ip, ip6, tcp, udp, and so on).

Filter expressions can be combined by using Boolean operators:

* and (&&)
* or (||)
* not (!)

Filter syntax can be made even more detailed by using parentheses to group expressions. A complex filter expression should be enclosed by quotes. For example, the following command filters frames to those with the source IP 10.1.0.100 and destination port 53 or 80:

tcpdump -i eth0 "src host 10.1.0.100 and (dst port 53 or dst port 80)"



## Command examples

* Capture all traffic on interface eth0

```
tcpdump -i eth0
```

* Capture traffic without DNS resolution

```
tcpdump -i eth0 -nn
```

* Capture 50 packets

```
tcpdump -i eth0 -c 50
```

* Save packets to the file

```
tcpdump -i eth0 -w capture.pcap
```

* Read packets from a file

```
tcpdump -r capture.pcap
```

* Capture only TCP traffic

```
tcpdump -A -i eth0 tcp
```

* Capture traffic from a specific host

```
tcpdump -i eth0 host 192.168.1.20
```

* Capture traffic on a specific port

```
tcpdump-i eth0 port 80
```

* Capture traffic from/to a host and port

```
tcpdump -i eth0 host 192.168.1.10 and port 80
```

* Capture HTTP traffic and show in ASCII

```
tcpdump -A -i eth0 port 80
```
