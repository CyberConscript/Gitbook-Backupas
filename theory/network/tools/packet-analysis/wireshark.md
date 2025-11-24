# Wireshark

## Content

Introduction

## Introduction

Wireshark is a popular open-source packet analysis tool used for network troubleshooting, analysis, and protocol development. It allows users to capture and analyze network traffic in real-time and provides detailed insights into network protocols, packet behavior, and network performance. Here are some key features and functionalities of Wireshark:

1. Packet Capture: Wireshark can capture network packets from various network interfaces, such as Ethernet, Wi-Fi, or loopback, enabling real-time monitoring of network traffic.
2. Protocol Analysis: Wireshark provides extensive protocol support, allowing users to dissect and analyze a wide range of network protocols, including TCP/IP, UDP, HTTP, DNS, FTP, SSL/TLS, and many more.
3. Live Packet Capture: It allows users to capture and analyze network packets in real-time, providing instant visibility into network behavior and troubleshooting capabilities.
4. Offline Analysis: Wireshark also supports the analysis of previously captured packet capture files (PCAP or PCAPNG), allowing users to analyze captured traffic at a later time.
5. Packet Filtering: Wireshark offers powerful filtering capabilities to focus on specific network traffic of interest. Users can create complex display filters based on various criteria, such as source/destination IP addresses, ports, protocols, or packet contents.
6. Protocol Decoding and Dissection: Wireshark decodes network packets and presents detailed information about each packet, including protocol headers, source/destination addresses, timestamps, packet lengths, and payload data. It provides a hierarchical view of the dissected protocol layers for deep analysis.
7. Statistical Analysis: Wireshark provides statistical information, such as packet counts, round-trip times, packet size distributions, flow statistics, and protocol usage statistics. This data helps in identifying network performance issues, bottlenecks, or anomalies.
8. Packet Reconstruction: Wireshark allows users to reconstruct and view the content of captured packets, including text-based protocols, images, documents, or multimedia files.
9. Export and Reporting: Wireshark enables the export of captured packets or analysis results in various formats, such as plain text, CSV, XML, or JSON. It also supports generating customized reports for sharing analysis findings.

Wireshark is a versatile tool used by network administrators, security professionals, developers, and researchers for network troubleshooting, network security analysis, performance optimization, and protocol analysis. Its extensive features and community support make it a valuable tool in the field of network analysis and diagnostics.



*   ## Packet Analysis tool fundamentals&#x20;

    How it works:&#x20;

    1. Collets - packet sniffter collects raw binary data from the wire. There are few different modes of operation:
    2. Data is converted to the readable form. There are so little analysis at this step.
    3. Analysis by sniffer itself. Meaningful data is extracted.

    ## Tapping into the Wire

    There are different methods:

    Promiscuous mode - NIC does not discard packets received by it even though it was not destined for it's MAC address. &#x20;

    Sniffing - connecting to the network repeater hub or switch. It can be subdivided:

    * **5**- enable switch's port mirroring for the packet capture. It just duplicates one port's traffic to another port. Some devices allow multiple port mirroring to a single port with risk of packet loss. A similar can be done using Hub connected to a single port when the switch does not support port mirroring (Hubbin).
      * Leaves no network footprint and generates no additional packets&#x20;
      * Can be configured without taking the client offline, which is convenient when mirroring router or server ports
      * Requires processing resources from the switch and can be inconsistent at higher throughput levels&#x20;
      * Works when you are not concerned about taking the host temporarily offline&#x20;
      * Ineffective when you must capture traffic from multiple hosts, as collisions and dropped packets are likely&#x20;
      * Can result in lost packets on modern 100/1000Mbps hosts because most true hubs are only 10Mbps
    * Using network tap - placing a device in the middle of two physical network points (middle man). Can be aggregated (3 ports) and non-aggregated (4 ports). Also ARP cache poisoning can be used:&#x20;
      * Ideal when you are not concerned about taking the host temporarily offline&#x20;
      * The only option when you need to sniff traffic from a fiber-optic connection&#x20;
      * Preferred solution for enterprise packet capture and continuous monitoring because taps are reliable and can scale to high throughput links&#x20;
      * Since taps are made for the task at hand and are up to par with modern network speeds, this method is superior to hubbing out .
      * Can be expensive, especially at scale, and so may be cost prohibitive
    * ARP cache poisoning or ARP spoofing is when actor sends ARP messages to switch or router with fake MAC address information.







    ## Captured Packet tasks&#x20;

    1. **Exporting** Export captured packets to a file using the "File" menu and selecting "Export Packet Dissections" or using the keyboard shortcut Ctrl+Shift+E (Command+Shift+E on macOS).
       1. Whole pcap: File -> Save&#x20;
       2. Part of pcap: File -> Export Specific packets
    2. **Combining** Combine Captured Packet Files: Merge multiple capture files into one using the "File" menu and selecting "Merge" or using the keyboard shortcut Ctrl+Shift+M (Command+Shift+M on macOS).
       1. File -> Merge
    3. **Search** for specific packet by display filter, hex value or string
       1. Ctrl + F
    4. **Mark**
       1. Ctrl + M
    5. **Set time display**
       1. View->Time Display format
    6. **Time shift**&#x20;
       1. Edit -> Time shift or Ctrl+Shift+T
    7. **Using filters**
       1. Capture filters - capture only those packets that are specified for inclusion or exclusion.&#x20;
          1. Capture -> Options
          2.  Berkeley packet filter (BPF) syntax: host, net, port, src, dst, ip, udp, tcp, http, ftp, !\<something>

              Filter Description<br>

              | <p>tcp[13] &#x26; 32 == 32<br>tcp[13] &#x26; 16 == 16<br>tcp[13] &#x26; 8 == 8<br>tcp[13] &#x26; 4 == 4<br>tcp[13] &#x26; 2 == 2<br>tcp[13] &#x26; 1 == 1<br>tcp[13] == 18</p> | <p>TCP packets with the URG flag set<br>TCP packets with the ACK flag set<br>TCP packets with the PSH flag set<br>TCP packets with the RST flag set<br>TCP packets with the SYN flag set<br>TCP packets with the FIN flag set<br>TCP SYN-ACK packets</p> |
              | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

              <br>
       2.  **Display filters** - hide unwanted packets in the display area.&#x20;

           1. Just enter filter options on the display filter field or right click and use Expression option for the help wizard. \
              Samples: tcp.port==3389 Filter RDP traffic tcp.flags.syn==1 TCP packets with the SYN flag set tcp.flags.reset==1 TCP packets with the RST flag set !arp Clear ARP traffic http All HTTP traffic tcp.port==23 || tcp.port==21 Telnet or FTP traffic smtp || pop || imap Email traffic (SMTP, POP, or IMAP)


    8. **Viewing Endpoint Statistics**: Statistics -> Endpoints
    9. **Viewing Network Conversations**: Statistics -> Conversations
    10. **Protocol hierarchy statistics:** Statistics -> Protocol Hierarchy
    11. **Change conversation decoder**: Right click on on packet -> select Decode as
    12. **Follow Streams:** Click any of the TCP or HTTP packets in the file, right-click the packet, and choose Follow TCP Stream. Red text signifying traffic from source to destination and blue text  identifying traffic in the opposite direction, from destination to source.

    ## Packet Details

    You can double click on a packet in capture to open its details. Packets consist of 5 to 7 layers based on the OSI model. We will go over all of them in an HTTP packet from a sample capture.

    <br>

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/13.png" alt=""><figcaption></figcaption></figure>

    <br>

    Looking above we can see 7 distinct layers to the packet: frame/packet, source \[MAC], source \[IP], protocol, protocol errors, application protocol, and application data. Below we will go over the layers in more detail.

    * Frame (Layer 1) -- This will show you what frame / packet you are looking at as well as details specific to the Physical layer of the OSI model.

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/14.png" alt=""><figcaption></figcaption></figure>

    * Source \[MAC] (Layer 2) -- This will show you the source and destination MAC Addresses; from the Data Link layer of the OSI model.

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/15.png" alt=""><figcaption></figcaption></figure>

    * Source \[IP] (Layer 3) -- This will show you the source and destination IPv4 Addresses; from the Network layer of the OSI model.

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/16.png" alt=""><figcaption></figcaption></figure>

    * Protocol (Layer 4) -- This will show you details of the protocol used (UDP/TCP) along with source and destination ports; from the Transport layer of the OSI model.

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/17.png" alt=""><figcaption></figcaption></figure>

    * Protocol Errors -- This is a continuation of the 4th layer showing specific segments from TCP that needed to be reassembled.

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/18.png" alt=""><figcaption></figcaption></figure>

    * Application Protocol (Layer 5) -- This will show details specific to the protocol being used such HTTP, FTP, SMB, etc. From the Application layer of the OSI model.

    ![](https://assets.tryhackme.com/additional/wireshark101/19.png)<br>

    * Application Data -- This is an extension of layer 5 that can show the application-specific data.

    <br>

    <figure><img src="https://assets.tryhackme.com/additional/wireshark101/20.png" alt=""><figcaption></figcaption></figure>

    <br>
