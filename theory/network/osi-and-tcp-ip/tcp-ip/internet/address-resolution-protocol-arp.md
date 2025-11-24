# Address Resolution Protocol (ARP)

When you consider the seven layers of the OSI Reference Model, there are two that deal with addressing: the data link layer and the network layer. The physical layer is not strictly concerned with addressing at all, but rather, only with sending at the bit level. The layers above the network layer all work with network layer addresses.

But why is addressing done at two different layers? The answer is that they are very different types of addresses that are used for different purposes. The layer 2 addresses (such as IEEE 802 MAC addresses) are used for local transmissions between hardware devices that can communicate directly. They are used to implement basic local area network (LAN), wireless LAN (WLAN), and wide area network (WAN) technologies. In contrast, layer 3 addresses (most commonly, IP addresses) are used in internetworking to create the equivalent of a massive virtual network at the network layer.

The most important distinction between these types of addresses is between layers 2 and 3: Layer 2 deals with directly connected devices (on the same network), while layer 3 deals with indirectly connected devices (as well as directly connectedAddress Resolution and he TCP/IP Address Resolution Protocol (ARP) 205 ones).&#x20;

Say, for example, you want to connect to the web server at http:// www.tcpipguide.com. This is a website that runs on a server that has an Ethernet card in it that’s used for connecting it to its Internet service provider site. However, even if you know its MAC address, you cannot use it to talk directly to this server using the Ethernet card in your home PC, because the devices are on different networks—in fact, they may be on different continents! Instead, you communicate at layer 3, using the IP and higher-layer protocols such as the Transmission Control Protocol (TCP) and Hypertext Transfer Protocol (HTTP). Your request is routed from your home machine, through a sequence of routers to the server at The TCP/IP Guide, and the response is routed back to you. The communication is, logically, at layers 3 and above; you send the request not to the MAC address of the server’s network card, but rather to the server’s IP address



## Address Resolution Through Direct Mapping&#x20;

Network layer addresses must be resolved into data link layer addresses numerous times during the travel of each datagram across an internetwork. You therefore want the process to be as simple and efficient as possible. The easiest method of accomplishing this is to do direct mapping between the two types of addresses



## Dynamic Address Resolution&#x20;

You just saw that direct mapping provides a simple and highly efficient means of resolving network layer addresses into data link layer addresses. Unfortunately, it is a technique that you either cannot or should not use in a majority of cases. You cannot use it when the size of the data link layer address is larger than that of the network layer address. You shouldn’t use it when you need flexibility, because direct mapping requires you to make layer 3 and layer 2 addresses correspond. The alternative to direct mapping is a technique called dynamic address resolution. This uses a special protocol that allows a device with only an IP address to determine the corresponding data link layer address, even if the two address types take completely different forms. This is normally done by interrogating one or more other devices on a local network to determine what data link layer address corresponds to a given IP address. This is more complex and less efficient than direct mapping, but it’s more flexible. How Dynamic Addressing Works To understand how dynamic addressing works, you can consider a simple analogy. I’m sure you’ve seen a limousine driver who is waiting to pick up a person at the airport. (Well, you’ve seen it in a movie, haven’t you?) This is similar to the problem here: The driver knows the name of the person who will be transported, but not the person’s face (a type of “local address” in a manner of speaking!). To find the person, the driver holds up a card bearing that person’s name. Everyone other than that person ignores the card, but the named individual should recognize it and approach the driver. You do the same thing with dynamic address resolution in a network. Let’s say that Device A wants to send to Device B but knows only Device B’s network layer address (its “name”) and not its data link layer address (its “face”). It broadcasts a layer 2 frame containing the layer 3 address of Device B—this is like holding up the card with someone’s name on it. The devices other than Device B don’t recognize this layer 3 address and ignore it. Device B, however, knows its own network layer address. It recognizes this in the broadcast frame and sends a direct response back to Device A. This tells Device A what Device B’s layer 2 address is, and the resolution is complete. Figure 13-4 illustrates the process.



<figure><img src="../../../../../.gitbook/assets/image (17).png" alt=""><figcaption></figcaption></figure>



Direct mapping is very simple, but as you can see, dynamic resolution isn’t exactly rocket science either! It’s a simple technique that is easily implemented. Furthermore, it removes the restrictions associated with direct mapping. There is no need for any specific relationship between the network layer address and the data link layer address; they can have a completely different structure and size. There is one nagging issue though: the efficiency problem. Where direct mapping involves a quick calculation, dynamic resolution requires you to use a protocol to send a message over the network. Fortunately, there are techniques that you can employ to remove some of the sting of this cost through careful implementation.

Consider that most devices on a local network send to only a small handful of other physical devices and tend to do so over and over again. This is a phenomenon known as locality of reference, which is observed in a variety of different areas in the computing field. If you send a request to an Internet website from your office PC, it will need to go first to your company network’s local router, so you will need to resolve the router’s layer 2 address. If you later click a link on that site, that request will also need to go to the router. In fact, almost everything you do off your local network probably goes first to that same router (commonly called a default gateway). Having to do a fresh resolution each time would be, well, stupid. It would be like having to look up the phone number of your best friend every time you want to call to say hello. <br>

To avoid being accused of making address resolution protocols that are, well, stupid, designers always include a caching mechanism. After a device’s network layer address is resolved to a data link layer address, the link between the two is kept in the memory of the device for a period of time. When it needs the layer 2 address the next time, the device just does a quick lookup in its cache. This means that instead of doing a broadcast on every datagram, you do it only once for a whole sequence of datagrams



**Caching** is by far the most important performance-enhancing tool in dynamic resolution. It transforms what would otherwise be a very wasteful process into one that, most of the time, is no less efficient than direct mapping. It does, however, add complexity. The cache table entries must be maintained. There is also the problem that the information in the table may become stale over time. What happens if you change the network layer address or the data link layer address of a device? For this reason, cache entries must be set to expire periodically. The discussion of caching in TCP/IP’s ARP later in this chapter shows some of the particulars of how these issues are handled.

Other **enhancements** are also possible to the basic dynamic resolution scheme. Let’s consider again our example of sending a request to the Internet. You send a request that needs to go to the local router, so you resolve its address and send it the request. A moment later, the reply comes back to the router to be sent to you, so the router needs your address. Thus, it would have to do a dynamic resolution on you, even though you just exchanged frames. Again, this is stupid. Instead, you can improve efficiency through **cross-resolution**; **when Device A resolves the address of Device B, Device B also adds the entry for Device A to its cache**.



## TCP/IP Address Resolution Protocol (ARP)&#x20;

ARP is a full-featured, dynamic resolution protocol used to match IP addresses to underlying data link layer addresses. Originally developed for Ethernet, it has now been generalized to allow IP to operate over a wide variety of layer 2 technologies.

NOTE The Address Resolution Protocol described here is used for resolving unicast addresses in version 4 of the Internet Protocol (IPv4). Multicast addresses under IPv4 use a direct mapping method, and IPv6 uses the new Neighbor Discovery (ND) Protocol instead of ARP

Physical networks function at layers 1 and 2 of the OSI Reference Model and use data link layer addresses. In contrast, internetworking protocols function at layer 3, interconnecting these physical networks to create a possibly huge internetwork of devices specified using network layer addresses. Address resolution is the process whereby network layer addresses are resolved into data link layer addresses.

**The basic operation of ARP** involves encoding the IP address of the intended recipient in a broadcast message. It is sent on a local network to allow the intended recipient of an IP datagram to respond to the source with its data link layer address. This is done using a simple request and reply method. A special format is used for ARP messages, which are passed down to the local data link layer for transmission

## ARP Address Specification and General Operation

&#x20;An ARP transaction begins when a source device on an IP network has an IP datagram to send. It must first decide whether the destination device is on the local network or a distant network. If it’s the former, it will send directly to the destination; if it’s the latter, it will send the datagram to one of the routers on the physical network for forwarding.

## ARP Message Types and Address Designations&#x20;

In ARP (Address Resolution Protocol), the process of mapping a network layer address (like an IP address) to a data link layer address (like a MAC address) involves sending messages between devices. The terms **sender** and **target** apply differently depending on whether it's an ARP request or an ARP reply. Here’s a breakdown of how these terms are used and the role of the addresses involved:

#### **ARP Request**

* **Purpose**: The source device wants to find out the MAC address associated with an IP address on the same network.
* **Sender**: The device that is initiating the ARP request. This is the source that has an IP datagram to send and needs to know the MAC address of the destination device.
* **Target**: The destination device whose MAC address is being requested.

**Addresses involved:**

1. **Sender Hardware Address (SHA)**:
   * The MAC address of the source device sending the ARP request.
2. **Sender Protocol Address (SPA)**:
   * The IP address of the source device sending the ARP request.
3. **Target Hardware Address (THA)**:
   * This field is left empty (or filled with zeros) in the ARP request because the source device doesn't know the MAC address of the target yet.
4. **Target Protocol Address (TPA)**:
   * The IP address of the destination device whose MAC address is being sought.

#### **ARP Reply**

* **Purpose**: The target device responds to the ARP request by providing its MAC address.
* **Sender**: The destination device that received the ARP request and is now sending the ARP reply.
* **Target**: The original source device that sent the ARP request and now receives the ARP reply.

**Addresses involved:**

1. **Sender Hardware Address (SHA)**:
   * The MAC address of the destination device sending the ARP reply (which was the target in the request).
2. **Sender Protocol Address (SPA)**:
   * The IP address of the destination device sending the ARP reply.
3. **Target Hardware Address (THA)**:
   * The MAC address of the original source device (which is now the target in the reply).
4. **Target Protocol Address (TPA)**:
   * The IP address of the original source device (which is now the target in the reply).

#### **Summary of the ARP Process:**

* **Request**:
  * The **sender** (source device) sends out an ARP request asking for the MAC address of the **target** (destination device) identified by its IP address.
* **Reply**:
  * The **sender** (destination device, now replying) sends back an ARP reply with its MAC address to the **target** (the original source device).

The ARP process is crucial for devices on the same local network to communicate by converting the IP addresses used by higher layers into the MAC addresses needed for actual data transmission at the data link layer.



