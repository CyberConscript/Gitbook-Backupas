# Point-to-Point Protocol (PPP)

PPP, which defines a complete method for robust data link connectivity between devices using serial lines or other physical layers. It includes numerous capabilities and features, including error detection, compression, authentication, and encryption.



PPP is now one of the most popular layer 2 WAN technologies in the networking world, and has replaced SLIP as the standard for serial connections on all but legacy implementations. While most often associated with dial-up modem use, PPP can run across any similar type of physical layer link. For example, it is often used to provide layer 2 functionality on Integrated Services Digital Network (ISDN).

PPP is a connection-oriented protocol that enables layer 2 links over a variety of different physical layer connections. It is supported on both synchronous and asynchronous lines and can operate in half-duplex or full-duplex mode. It was designed to carry IP traffic, but is general enough to allow any type of network layer datagram to be sent over a PPP connection. As its name implies, PPP is designed for point-to-point connections between two devices, and it assumes that frames are sent and received in the same order.



Advantages and Benefits A list of PPP’s strengths reads very much like a list of SLIP’s weaknesses, as explained earlier in this chapter. Some of PPP’s specific benefits include the following:&#x20;

 A more comprehensive framing mechanism compared to the single END character in SLIP&#x20;

 Specification of the encapsulated protocol to allow multiple layer 3 protocols to be multiplexed on a single link&#x20;

 Error detection for each transmitted frame through the use of a cyclic redundancy check (CRC) code in each frame header&#x20;

 A robust mechanism for negotiating link parameters, including the maximum frame size permitted

 A method for testing links before datagram transmission takes place and for monitoring link quality  Support for authentication of the connection using multiple authentication protocols&#x20;

 Support for additional optional features, including compression, encryption, and link aggregation (allowing two devices to use multiple physical links as if they were a single, higher-performance link)



One key advantage of PPP is that it is extensible. Over the years, new protocols have been added to the suite in order to provide additional features or capabilities. For example, PPP is designed not to use just a single authentication protocol, but to allow a choice. PPP’s success has even led to the development of derivative protocols like PPP over Ethernet (PPPoE) and PPP over ATM (PPPoA). These derivatives actually layer PPP over existing data link layer technologies, which demonstrates how valued PPP’s features are. Even when a layer 2 technology is already in use, you can apply PPP on top to provide authentication and management benefits for services like Digital Subscriber Line (DSL)



**PPP Encapsulation Method** The primary job of PPP is to take higher-layer messages, such as IP datagrams, and encapsulate them for transmission over the underlying physical layer link. To this end, PPP defines a special frame format for encapsulating data for transmission, based on the framing used in HDLC. The PPP frame was designed to be small and contain only simple fields in order to maximize bandwidth efficiency and speed in processing.&#x20;

**Link Control Protocol (LCP)** LCP is responsible for setting up, maintaining, and terminating the link between devices. It is a flexible, extensible protocol that allows many configuration parameters to be exchanged to ensure that both devices agree on how the link will be used.



1. Link Setup and Configuration Before the two devices can exchange information, they must make contact and set up a link between them. During link setup, the devices agree on all the parameters needed to manage the operation of the link. LCP begins this process and invokes the help of support protocols as needed, for options like authentication. Once the link is set up, in order to complete link setup, the appropriate NCP is called for whatever layer 3 technology is being carried on the link.
2. Link Operation The devices use the link to send datagrams. Each device transmits by encapsulating layer 3 datagrams and sending them down to layer 1 to be transmitted. Each device receives by taking PPP frames sent up from its own physical layer, stripping off the PPP header and passing the datagram up to layer 3. Where appropriate, optional protocols are used at this stage to offer features such as compression (CCP).
3. Link Termination When either device decides that it no longer wants to communicate, it terminates the link.



<figure><img src="../../../../../.gitbook/assets/image (16).png" alt=""><figcaption></figcaption></figure>

