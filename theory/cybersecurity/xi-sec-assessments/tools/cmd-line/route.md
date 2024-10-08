# Route

Route and traceroute

The subsequent tools serve to assess routing configuration and connectivity with remote networks and hosts.

*   **Route**: This tool enables the viewing and adjustment of the local routing table on the host. Typically, most end systems utilize a default route to channel all traffic destined for remote networks through a gateway router. However, if the host is not functioning as a router, any supplementary entries within the routing table could raise suspicions.

    Output from the 'route' command on a Linux host typically resembles this example. It showcases a straightforward routing table that exhibits the default route (0.0.0.0/0) directed via the host designated as the default gateway (10.1.0.254) over the 'eth0' network interface. The second entry in the table delineates the local traffic subnet (10.1.0.0/24), which is directly connected, denoted by the gateway entry 0.0.0.0.



<figure><img src="https://s3.amazonaws.com/wmx-api-production/courses/5731/images/8872-1599771794749.png" alt=""><figcaption></figcaption></figure>

Output from the route command on a Linux host. Most endpoints have a simple routing table, similar to this. It shows the default route (0.0.0.0/0) via the host configured as the default gateway (10.1.0.254) over the network interface eth0. The second line of the table shows the subnet for local traffic (10.1.0.0/24). This network is directly connected, represented by the 0.0.0.0 gateway.



* **Tracert**: This utility employs ICMP probes to furnish round trip time (RTT) feedback for intermediary hops between the local host and a remote network host. 'Tracert' specifically pertains to the Windows version of this tool.
* **Traceroute**: Operating from a Linux host, 'traceroute' conducts route exploration. Notably, 'traceroute' employs UDP probes as the default method, distinguishing it from ICMP-based tools.
* **Pathping**: Tailored for Windows environments, 'pathping' provides comprehensive statistics concerning latency and packet loss over an extended measurement duration along a route. The equivalent utility on Linux is 'mtr'.

Within a security context, notable latency increase at the default gateway compared to a baseline might signify a potential man-in-the-middle attack. Conversely, elevated latency at other intermediary points could indicate denial of service incidents or mere network congestion.

