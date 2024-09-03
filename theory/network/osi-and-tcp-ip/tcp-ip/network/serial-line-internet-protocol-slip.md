# Serial Line Internet Protocol (SLIP)

The need for a data link layer protocol to allow IP to operate over serial links was identified very early on in the development of TCP/IP. Engineers working on IP needed a way to send IP datagrams over serial links. To solve the problem, they created the very simple protocol SLIP to frame IP messages for transmission across the serial line.



SLIP was designated nonstandard because it was developed as a very rudimentary, stopgap measure to provide layer 2 framing when needed. SLIP is so simple that there really isn’t much to standardize. Too, it has so many deficiencies that the Internet Engineering Task Force (IETF) apparently didn’t want to formalize it as a standard. RFC 1055 specifically mentions various problems with SLIP (as I’ll discuss later in this chapter) and the fact that work was already under way to define PPP as a more capable successor to SLIP.



SLIP performs only one function: the framing of data for transmission. Here’s how SLIP framing works. An IP datagram is passed down to SLIP, which breaks it into bytes and sends those bytes one at a time over the link. After the last byte of the datagram is sent, a special byte value is sent that tells the receiving device that the datagram has ended. This is called the SLIP END character, and it has a byte value of 192 in decimal numbers (C0 in hexadecimal and 11000000 binary). That’s basically SLIP framing in a nutshell: Take the whole datagram, send it one byte at a time, and then send the byte 192 to delimit the end of the datagram.

One minor enhancement to SLIP’s basic operation is to precede the datagram with an END character as well, thus clearly separating the start of the datagram from anything that precedes it. To see why this might be needed, you can imagine that at a particular time you have only one datagram to send: datagram 1. You send 1, and then send the END character to delimit it. Now, suppose there is a pause before the next datagram shows up. During that time, you aren’t transmitting, but if there is line noise, the other device might pick up spurious bytes here and there. If you later receive datagram 2 and just start sending it, the receiving device might think the noise bytes were part of datagram 2. Starting datagram 2 off with an END character tells the recipient that anything received between this END character and the previous one is a separate datagram. If that’s just noise, then this “noise datagram” is just gibberish that will be rejected at the IP layer.

But what if the END character is 192 in decimal numbers; what happens if the byte value 192 appears in the datagram itself? Transmitting it as is would fool the recipient into thinking that the datagram ended prematurely. To avoid this, an Escape character (ESC) is defined, which has a decimal value of 219 (DB in hex, 11011011 in binary). This symbol means that “this byte and the next are special.” When a value of 192 appears in the datagram, the sending device replaces it with the ESC character followed by the value 220 decimal. Thus, a single 192 becomes 219 220 (or DB DC in hexadecimal). The recipient translates back from 219 220 to 192.

To summarize, SLIP does the following: \
 Breaks an IP datagram into bytes \
 Sends the END character (value 192) after the last byte of the datagram; in better implementations, it sends the END character before the first byte as well \
 Replaces any byte to be sent in the datagram that is 192 with 219 220  Replaces any byte to be sent that is 219 with 219 22
