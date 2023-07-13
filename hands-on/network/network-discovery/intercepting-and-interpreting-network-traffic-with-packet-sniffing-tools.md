# Intercepting and Interpreting Network Traffic with Packet Sniffing Tools

### Scenario <a href="#scenario" id="scenario"></a>

In this activity, you will use Wireshark and tcpdump to capture network traffic and display relevant information on the local network. Interpreting the output from such captures is useful for security assessments.

### Sniff network traffic <a href="#sniff-network-traffic" id="sniff-network-traffic"></a>

Use the Kali Linux virtual machine to capture some network traffic and identify the main features of the Wireshark network analyzer. You'll assume that KALI has been able to obtain some sort of network tap, which has been simulated for you already by configuring port mirroring on the Hyper-V switch.

1. &#x20;Select the [PT1-Kali](https://labclient.labondemand.com/Instructions/a37a36cc-aba2-494b-8f4b-dd8d25cee668?rc=10) and log on with the credentials root and Pa\$$w0rd
2.  &#x20;From the desktop, select the **Wireshark** application.

    Maximize the window to make Wireshark easier to work with.
3. &#x20;Under _Capture_, select the **eth0** adapter.
4.  &#x20;In the _Capture filter_ box, type ip.

    > The ip filter captures IPv4 traffic, not IPv6 traffic.

    There are two types of filters: capture restricts which frames the sniffer records while display filters (but does not discard) what has been recorded. The syntax of capture and display filters is different, and capture filters are more basic.
5. &#x20;Start the capture by selecting the blue **Start capturing packets** button in the upper left corner of the Wireshark interface.
6. &#x20;On the [PT1-Kali](https://labclient.labondemand.com/Instructions/a37a36cc-aba2-494b-8f4b-dd8d25cee668?rc=10) VM, launch Firefox from the menu, and then connect to http://10.1.0.2 (the MS1 Windows web server).
7.  &#x20;As soon as the 515support web page is displayed in Firefox, switch back to the Wireshark application.

    In this task, you are capturing packets on the PT1-Kali VM _and_ connecting to the MS1 web server from the same PT1-Kali VM.

    > Capturing traffic on a client computer as it is attempting to connect to a destination computer might be useful in both security and network troubleshooting scenarios.
8. &#x20;Select the **Stop** button on the toolbar to end the live capture.
9.  &#x20;Select any **DNS** frame (they are color-coded as light blue) from the top panel, and then observe the frame contents displayed in the middle panel.

    Wireshark splits out the successive headers and payloads to decode each protocol:

    * Frame—this shows information about the bytes captured.
    * Ethernet II—this shows the frame type (data link layer/layer 2) and the source and destination MAC addresses. Note that the first part of the address (the OUI) is identified as belonging to Microsoft (all the VMs are using MS virtual adapters). The last piece of information is the type of network protocol contained in the frame (IPv4).
    * Internet Protocol Version 4—this is the IPv4 datagram, notably showing the source and destination IP (layer 3) addresses. Note there is usually also a GeoIP function in this section, but as these are private addresses, they cannot be resolved to a particular regional registry or ISP.
    * User Datagram Protocol—layer 4 (transport) uses either UDP or TCP. The most significant fields here are the source and destination ports. UDP port 53 is the "well known" DNS server port.
    * Domain Name System—this is the application protocol. Depending on which frame you selected, you may be looking at a query or at a response.

    > Observe how this window in Wireshark reflects the layers of the TCP/IP stack (though it is inverted). Ethernet II displays physical (MAC) address information, Layer 3 shows logical addressing (IP) and layer 4 shows application layer source and destination ports. The application layer contains protocol-specific headers and the data payload (DNS in this example).
10. &#x20;Select the **TCP** frame that opens the connection to the web server (the first frame that is colored green), and then examine the contents of the middle panel.

    Be sure to note both the source and destination port numbers.

    Use the Wireshark interface to answer the following questions.
11. In the Wireshark interface, what is the name of the layer where the MAC addresses are found (Hint: this info is in the middle pane of the interface)?

    FrameEthernet IIInternet Protocol Version 4
12. In the Wireshark interface, what is the name of the layer where the IP addresses are found (Hint: this info is in the middle pane of the interface)?

    FrameEthernet IIInternet Protocol Version 4
13. In the Wireshark interface, what is the name of the layer where the source and destination port numbers are found (Hint: this info is in the middle pane of the interface)?

    Transmission Control Protocol (TCP)User Datagram ProtocolInternet Protocol Version 4
14. &#x20;Close or minimize **Wireshark**.



### Use tcpdump to intercept HTTP network traffic <a href="#use-tcpdump-to-intercept-http-network-traffic" id="use-tcpdump-to-intercept-http-network-traffic"></a>

The **tcpdump** program is another protocol analyzer (packet sniffer). In this activity, you will use **tcpdump** to intercept HTTP traffic.

1.  &#x20;Switch to the [MS1](https://labclient.labondemand.com/Instructions/a37a36cc-aba2-494b-8f4b-dd8d25cee668?rc=10) VM, select [Ctrl+Alt+Delete](https://labclient.labondemand.com/Instructions/a37a36cc-aba2-494b-8f4b-dd8d25cee668?rc=10), and then sign in as 515support\Administrator with Pa\$$w0rd.

    > The MS1 VM is hosting a web site that will be used as part of the packet interception activity.
2. &#x20;From **Server Manager**, select **Tools > Internet Information Services (IIS) Manager**.
3. &#x20;Expand the **MS1** and **Sites** nodes to display the **Default Web Site** node.
4. &#x20;Double-click the **Authentication** applet in the Default Web Site Home pane.
5. &#x20;Select **Anonymous Authentication**, and then from the _Actions_ pane on the right, select **Disable**.
6.  &#x20;Select **Basic Authentication**, and then from the _Actions_ pane on the right, select **Enable**.

    Note the alert about the lack of SSL and cleartext credentials, but ignore it for the purposes of this activity.
7. &#x20;Switch to the [PT1-Kali](https://labclient.labondemand.com/Instructions/a37a36cc-aba2-494b-8f4b-dd8d25cee668?rc=10) VM, and then confirm that you are signed in. If necessary, log on with the credentials root and Pa\$$w0rd.
8. &#x20;From the menu at the top of the desktop, open the **Terminal**.
9.  &#x20;Run the following command to begin intercepting MS1 **HTTP** network traffic by using tcpdump:

    ```bash-notab-nocopy
    tcpdump -vv dst 10.1.0.2 and port www -w www.pcap
    ```

    > You will not see captured frames in the Terminal output. The -w switch directs output to a capture file.
10. &#x20;From the top menu, start **Firefox**, and then connect to the web site hosted at http://10.1.0.2.
11. &#x20;You will be prompted to enter the following name and password (if not, press **F5** to refresh the page):

    515support\Administrator\
    Pa\$$w0rd
12. &#x20;Switch to the Terminal window and then select **Ctrl+C** to stop the tcpdump capture.
13. &#x20;Switch to the Wireshark application. If you closed the program, launch it again from the desktop. Select the **File** menu, and then select **Open**.
14. &#x20;Select the **www.pcap** file from the root user's home directory, and then select **Open**. If prompted, select **Continue without saving** to discard the previous Wireshark scan and open this file.

    > tcpdump files are not stored in a human-readable format. Applications such as Wireshark can be used to display their contents.
15. &#x20;Select one of the **GET** HTTP messages from the top panel in Wireshark. With the **GET** message selected, in the middle panel, expand **Hypertext Transfer Protocol**, and then expand **Authorization**.

    > If you had to refresh the page, select one of the GET frames in the second block of HTTP requests to see the authorization header.
16. Which of the following options shows how the authentication information is displayed?

    Credentials: root:Pa\$$w0rdCredentials: 515support\Administrator:Pa\$$w0rdCredentials: Admin:Pa\$$w0rdCredentials are not displayed because they are encrypted.Credentials: Administrator:Pa\$$w0rd

Correct

> HTTP packets are unencrypted and therefore vulnerable to packet sniffing.
