# Snort

_Snort has three primary uses:_&#x20;

_As a packet sniffer like tcpdump;_

_As a packet logger ;_&#x20;

_As a full-blown network intrusion prevention system;_



Capabilities of Snort;\



* Live traffic analysis
* Attack and probe detection
* Packet logging
* Protocol analysis
* Real-time alerting
* Modules & plugins
* Pre-processors
* Cross-platform support! (Linux & Windows)

Snort has three main use models;\


* Sniffer Mode - Read IP packets and prompt them in the console application.
* Packet Logger Mode - Log all IP packets (inbound and outbound) that visit the network.
* NIDS (Network Intrusion Detection System)  and NIPS (Network Intrusion Prevention System) Modes - Log/drop the packets that are deemed as malicious according to the user-defined rules.



## Basics

| Parameter      | Description                                                                                            |
| -------------- | ------------------------------------------------------------------------------------------------------ |
| -V / --version | This parameter provides information about your instance version.                                       |
| -c             | Identifying the configuration file                                                                     |
| -T             | Snort's self-test parameter, you can test your setup with this parameter.                              |
| -q             | Quiet mode prevents snort from displaying the default banner and initial information about your setup. |

## Sniffer Mode

| Display parameter | Description                                                                                                                                                    |
| ----------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| -v                | Verbose. Display the TCP/IP output in the console.                                                                                                             |
| -d                | <p>Display the packet data (payload). (More data then verbose mode).<br></p>                                                                                   |
| -e                | <p>Display the link-layer (TCP/IP/UDP/ICMP) headers. <br></p>                                                                                                  |
| -X                | Display the full packet details in HEX. (All data)                                                                                                             |
| -i                | This parameter helps to define a specific network interface to listen/sniff. Once you have multiple interfaces, you can choose a specific interface to sniff.  |

Note that you can use the parameters both in combined and separated form as follows;\


* snort -v
* snort -vd
* snort -de
* snort -v -d -e
* snort -X

\
Snort parameters: -i, -v, -d, -e, -X, -i



## Packet logger

Snort will start showing the packets and log them in the target directory.

`sudo snort -dev -l .`

ASCII mode provides multiple files in human-readable format, so it is possible to read the logs easily by using a text editor.

`sudo snort -dev -K ASCII -l .`

ASCII mode provides multiple files in human-readable format, so it is possible to read the logs easily by using a text editor.



## Log reader

```shell-session
sudo snort -r snort.log.1638459842
```

Snort can read and handle the binary like output (tcpdump and Wireshark also can handle this log format). However, if you create logs with "-K ASCII" parameter, Snort will not read them. As you can see in the above output, Snort read and displayed the log file just like in the sniffer mode.



snort log reading with tcpdump:

```shell-session
sudo tcpdump -r snort.log.1638459842 -ntc 10
```

"-r" parameter also allows users to filter the binary log files. You can filter the processed log to see specific packets with the "-r" parameter and Berkeley Packet Filters (BPF).&#x20;

* `sudo snort -r logname.log -X`
* `sudo snort -r logname.log icmp`
* `sudo snort -r logname.log tcp`
* `sudo snort -r logname.log 'udp and port 53'`

