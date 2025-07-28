# Investigations

LESSON INTRODUCTION

Where incident response emphasizes the swift eradication of malicious activity, digital forensics requires patient capture, preservation, and analysis of evidence using verifiable methods. You may be called on to assist with an investigation into the details of a security incident and to identify threat actors. To assist these investigations, you must be able to summarize the basic concepts of collecting and processing forensic evidence that could be used in legal action or for strategic counterintelligence.

## DIGITAL FORENSICS REPORTS

A digital forensics report summarizes the significant contents of the digital data and the conclusions from the investigator's analysis. It is important to note that strong ethical principles must guide forensics analysis.

* Analysis must be performed without bias. Conclusions and opinions should be formed only from the direct evidence under analysis.
* Analysis methods must be repeatable by third parties with access to the same evidence.
* Ideally, the evidence must not be changed or manipulated. If a device used as evidence must be manipulated to facilitate analysis (disabling the lock feature of a mobile phone or preventing a remote wipe for example), the reasons for doing so must be sound and the process of doing so must be recorded.

Defense counsel may try to use any deviation of good ethical and professional behavior to have the forensics investigator's findings dismissed.

## E-DISCOVERY

A forensic examination of a device such as a fixed drive that contains Electronically Stored Information (ESI) entails a search of the whole drive (including both allocated and unallocated sectors, for instance). E-discovery is a means of filtering the relevant evidence produced from all the data gathered by a forensic examination and storing it in a database in a format such that it can be used as evidence in a trial. E-discovery software tools have been produced to assist this process. Some of the functions of e-discovery suites are:

* Identify and deduplicate files and metadata—many files on a computer system are "standard" installed files or copies of the same file. E-discovery filters these types of files, reducing the volume of data that must be analyzed.
* Search—allow investigators to locate files of interest to the case. As well as keyword search, software might support semantic search. Semantic search matches keywords if they correspond to a particular context.
* Tags—apply standardized keywords or labels to files and metadata to help organize the evidence. Tags might be used to indicate relevancy to the case or part of the case or to show confidentiality, for instance.
* Security—at all points evidence must be shown to have been stored, transmitted, and analyzed without tampering.
* Disclosure—an important part of trial procedure is that the same evidence be made available to both plaintiff and defendant. E-discovery can fulfill this requirement. Recent court cases have required parties to a court case to provide searchable ESI rather than paper records.

## VIDEO AND WITNESS INTERVIEWS

The first phase of a forensics investigation is to document the scene. The crime scene must be recorded using photographs and ideally audio and video. Investigators must capture every action they take in identifying, collecting, and handling evidence.

Remember that if the matter comes to trial, the trial could take place months or years after the event. It is vital to record impressions and actions in notes. Also consider that in-place CCTV systems or webcams might have captured valuable evidence.

If possible, evidence is gathered from the live system using forensic software tools. It is vital that these tools do as little to modify the digital data that they capture as possible.

As well as digital evidence, an investigator should interview witnesses to establish what they were doing at the scene, whether they observed any suspicious behavior or activity, and also to gather information about the computer system. An investigator might ask questions informally and record the answers as notes to gain an initial understanding of the circumstances surrounding an incident. An investigator must ask questions carefully, to ensure that the witness is giving reliable information and to avoid leading the witness to a particular conclusion. Making an audio or video recording of witness statements produces a more reliable record but may make witnesses less willing to make a statement. If a witness needs to be compelled to make a statement, there will be legal issues around employment contracts (if the witness is an employee) and right to legal representation.

## TIMELINES

A significant part of a forensic investigation will involve tying events to specific times to establish a consistent and verifiable narrative. The visual representation of events happening in chronological order is called a timeline.

Operating systems and file systems use a variety of methods to identify the time at which something occurred. The benchmark time is Coordinated Universal Time (UTC), which is essentially the time at the Greenwich meridian. Local time is the time within a particular time zone, which will be offset from UTC by several hours (or in some cases, half hours). The local time offset may also vary if a seasonal daylight saving time is in place.

NT File System (NTFS) uses UTC "internally", but many OS and file systems record time stamps as the local system time. When collecting evidence, it is vital to establish how a time stamp is calculated and note the offset between the local system time and UTC.

Forensics also needs to consider that a host's system clock may not be properly synchronized to a valid time source or may have been tampered with. Most computers are configured to synchronize the clock to a Network Time Protocol (NTP) server. Closely synchronized time is important for authentication and audit systems to work properly. The right to modify a computer's time would normally be restricted to administrator-level accounts (on enterprise networks) and time change events should be logged.

## EVENT LOGS AND NETWORK TRAFFIC

Digital evidence is not just drawn from analysis of host system memory and data drives. An investigation may also obtain the event logs for one or more network appliances and/or server hosts. Similarly, network packet captures and traces/flows might provide valuable evidence. On a typical network, sensor and logging systems are not configured to record all network traffic, as this would generate a very considerable amount of data. On the other hand, an organization with sufficient IT resources could choose to preserve a huge amount of data. A Retrospective Network Analysis (RNA) solution provides the means to record network events at either a packet header or payload level.

For forensics, data records that are not supported by physical evidence (a data drive) must meet many tests to be admissible in court. For event logs, the drives might not be accessible or might no longer hold the original logs; for network traffic, there is no physical evidence. Where logs and network traffic are captured in a SIEM, the SIEM should demonstrate accuracy (that all relevant data was captured) and integrity (that neither party could have tampered with the data).

Digital forensics can be used for information gathering to protect against espionage and hacking. This intelligence is deployed in two different ways:

In some cases, an organization may conduct a forensics investigation without the expectation of legal action. As well as being used in a legal process, forensics has a role to play in cybersecurity. It enables the detection of past intrusions or ongoing but unknown intrusions by close examination of available digital evidence. A famous quote attributed to former Cisco CEO John Chambers illustrates the point: "There are two types of companies: those that have been hacked, and those who don't know they have been hacked."

STRATEGIC INTELLIGENCE AND COUNTERINTELLIGENCE

* Counterintelligence—identification and analysis of specific adversary tactics, techniques, and procedures (TTP) provides information about how to configure and audit active logging systems so that they are most likely to capture evidence of attempted and successful intrusions.
* Strategic intelligence—data and research that has been analyzed to produce actionable insights. These insights are used to inform risk management and security control provisioning to build mature cybersecurity capabilities.

## DATA ACQUISITION AND ORDER OF VOLATILITY

Acquisition is the process of obtaining a forensically clean copy of data from a device held as evidence. If the computer system or device is not owned by the organization, there is the question of whether search or seizure is legally valid. This impacts bring-your-own-device (BYOD) policies. For example, if an employee is accused of fraud you must verify that the employee's equipment and data can be legally seized and searched. Any mistake may make evidence gained from the search inadmissible.

Data acquisition is also complicated by the fact that it is more difficult to capture evidence from a digital crime scene than it is from a physical one. Some evidence will be lost if the computer system is powered off; on the other hand, some evidence may be unobtainable until the system is powered off. Additionally, evidence may be lost depending on whether the system is shut down or "frozen" by suddenly disconnecting the power.\\

Data acquisition usually proceeds by using a tool to make an image from the data held on the target device. An image can be acquired from either volatile or nonvolatile storage. The general principle is to capture evidence in the order of volatility, from more volatile to less volatile. The ISOC best practice guide to evidence collection and archiving, published as [tools.ietf.org/html/rfc3227](https://tools.ietf.org/html/rfc3227), sets out the general order as follows:

1. CPU registers and cache memory (including cache on disk controllers, GPUs, and so on).
2. Contents of nonpersistent system memory (RAM), including routing table, ARP cache, process table, kernel statistics.
3. Data on persistent mass storage devices (HDDs, SSDs, and flash memory devices):
   1. Partition and file system blocks, slack space, and free space.
   2. System memory caches, such as swap space/virtual memory and hibernation files.
   3. Temporary file caches, such as the browser cache.
   4. User, application, and OS files and directories.
4. Remote logging and monitoring data.
5. Physical configuration and network topology.
6. Archival media and printed documents.

## DIGITAL FORENSICS SOFTWARE

Digital forensics software is designed to assist with the acquisition, documentation, and analysis of digital evidence. Most of the commercial forensics tools are available for the Windows platform only.

* EnCase Forensic is a digital forensics case management product created by Guidance Software ([guidancesoftware.com/encase-forensic?cmpid=nav\_r](https://www.guidancesoftware.com/encase-forensic?cmpid=nav_r)). Case management is assisted by built-in pathways, or workflow templates, showing the key steps in diverse types of investigation. In addition to the core forensics suite, there are separate products for e-discovery (digital evidence management) and Endpoint Investigator (for over-the-network analysis of corporate desktops and servers).
* The Forensic Toolkit (FTK) from AccessData ([accessdata.com/products-services/forensic-toolkit-ftk](https://accessdata.com/products-services/forensic-toolkit-ftk)) is another commercial investigation suite designed to run on Windows Server (or server cluster).
* The Sleuth Kit ([sleuthkit.org](https://sleuthkit.org/)) is an open-source collection of command line tools and programming libraries for disk imaging and file analysis.
* Autopsy is a graphical front-end for these tools and acts as a case management/workflow tool. The program can be extended with plug-ins for various analysis functions. Autopsy is available for Windows and Linux systems.
* WinHex from X-Ways ([x-ways.net/winhex](https://www.x-ways.net/winhex/)) is a commercial tool for forensic recovery and analysis of binary data, with support for a range of file systems and memory dump types (depending on version).
* The Volatility Framework ([github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)) is widely used for system memory analysis.

## SYSTEM MEMORY ACQUISITION

System memory is volatile data held in Random Access Memory (RAM) modules. Volatile means that the data is lost when power is removed. A system memory dump creates an image file that can be analyzed to identify the processes that are running, the contents of temporary file systems, registry data, network connections, cryptographic keys, and more. It can also be a means of accessing data that is encrypted when stored on a mass storage device. There are various methods of collecting the contents of system memory.

#### Live Acquisition <a href="#id-83668559-0626-40d7-80ae-df362ce59c17" id="id-83668559-0626-40d7-80ae-df362ce59c17"></a>

A specialist hardware or software tool can capture the contents of memory while the host is running. Unfortunately, this type of tool needs to be preinstalled as it requires a kernel mode driver to dump any data of interest. Some examples for Windows include WinHex ([x-ways.net/winhex](https://www.x-ways.net/winhex/)), Memoryze from FireEye ([fireeye.com/services/freeware/memoryze.html](https://www.fireeye.com/services/freeware/memoryze.html)), and F-Response TACTICAL ([f-response.com/software/tac](https://www.f-response.com/software/tac)).

On Linux, a user mode tool, such as memdump ([porcupine.org/forensics/tct.html](http://www.porcupine.org/forensics/tct.html)) or dd, can be run against the /dev/mem device file. However, on most modern distributions, access to this file is blocked. The Volatility Framework ([github.com/volatilityfoundation/volatility](https://github.com/volatilityfoundation/volatility)) includes a tool to install a kernel driver (pmem). The fmem and LiME kernel utilities provide similar functionality.

#### Crash Dump <a href="#c6ce233f-4e81-4076-8260-5a50170e8bc0" id="c6ce233f-4e81-4076-8260-5a50170e8bc0"></a>

When Windows encounters an unrecoverable kernel error, it can write contents of memory to a dump file at C:\Windows\MEMORY.DMP. On modern systems, there is unlikely to be a complete dump of all the contents of memory, as these could take up a lot of disk space. However, even mini dump files, stored in C:\Windows\Minidumps, may be a valuable source of information.

#### Hibernation File and Pagefile <a href="#id-422a33ce-7a7c-4406-99cd-5f4e6275dcbc" id="id-422a33ce-7a7c-4406-99cd-5f4e6275dcbc"></a>

A hibernation file is created on disk in the root folder of the boot volume when a Windows host is put into a sleep state. If it can be recovered, the data can be decompressed and loaded into a software tool for analysis. The drawback is that network connections will have been closed, and malware may have detected the use of a sleep state and performed anti-forensics.

The pagefile/swap file/swap partition stores pages of memory in use that exceed the capacity of the host's RAM modules. The pagefile is not structured in a way that analysis tools can interpret, but it is possible to search for strings.

## DISK IMAGE ACQUISITION

Disk image acquisition refers to acquiring data from nonvolatile storage. Nonvolatile storage includes hard disk drives (HDDs), solid state drives (SSDs), firmware, other types of flash memory (USB thumb drives and memory cards), and optical media (CD, DVD, and Blu-Ray). This can also be referred to as device acquisition, meaning the SSD storage in a smartphone or media player. Disk acquisition will also capture the OS installation, if the boot volume is included.

There are three device states for persistent storage acquisition:

* Live acquisition—this means copying the data while the host is still running. This may capture more evidence or more data for analysis and reduce the impact on overall services, but the data on the actual disks will have changed, so this method may not produce legally acceptable evidence. It may also alert the adversary and allow time for them to perform anti-forensics.
* Static acquisition by shutting down the host—this runs the risk that the malware will detect the shutdown process and perform anti-forensics to try to remove traces of itself.
* Static acquisition by pulling the plug—this means disconnecting the power at the wall socket (not the hardware power-off button). This is most likely to preserve the storage devices in a forensically clean state, but there is the risk of corrupting data.

Given sufficient time at the scene, you may decide to perform both a live and static acquisition. Whichever method is used, it is imperative to document the steps taken and supply a timeline for your actions.

There are many GUI imaging utilities, including those packaged with suites such as the Forensic Toolkit and its FTK Imager. You should note that the EnCase forensics suite uses a vendor file format (.e01) compared to the raw file format used by Linux tools like dd. The file format is important when it comes to selecting a tool for analyzing the image. The .eo1 format allows image metadata (such as the checksum, drive geometry, and acquisition time) to be stored within the same file. The open-source Advanced Forensic Format (AFF) provides similar features.

If no specialist tool is available, on a Linux host you can use the dd command to make a copy of an input file (if=) to an output file (of=) and apply optional conversions to the file data. In the following sda is the fixed drive:

dd if=/dev/sda of=/mnt/usbstick/backup.img

A more recent fork of dd is dcfldd, which provides additional features like multiple output files and exact match verification.

PRESERVATION AND INTEGRITY OF EVIDENCE

It is vital that the evidence collected at the crime scene conform to a valid timeline. Digital information is susceptible to tampering, so access to the evidence must be tightly controlled. Recording the whole process establishes the provenance of the evidence as deriving directly from the crime scene.

To obtain a forensically sound image from nonvolatile storage, you need to ensure that nothing you do alters data or metadata (properties) on the source disk or file system. A write blocker assures this process by preventing any data on the disk or volume from being changed by filtering write commands at the driver and OS level. Data acquisition would normally proceed by attaching the target device to a forensics workstation or field capture device equipped with a write blocker.

#### Data Acquisition with Integrity and Non-Repudiation <a href="#id-419ffa6e-f517-4345-9223-3838862ca5db" id="id-419ffa6e-f517-4345-9223-3838862ca5db"></a>

Once the target disk has been safely attached to the forensics workstation, data acquisition proceeds as follows:

1. A cryptographic hash of the disk media is made, using either the MD5 or SHA hashing function. The output of the function can be described as a checksum.
2. A bit-by-bit copy of the media is made using the imaging utility.
3. A second hash is then made of the image, which should match the original hash of the media.
4. A copy is made of the reference image, validated again by the checksum. Analysis is performed on the copy.

This proof of integrity ensures non-repudiation. If the provenance of the evidence is certain, the threat actor identified by analysis of the evidence cannot deny their actions. The checksums prove that no modification has been made to the image.

#### Preservation of Evidence <a href="#fef65c55-5b11-438e-bbcc-c2c3b4ecc0bb" id="fef65c55-5b11-438e-bbcc-c2c3b4ecc0bb"></a>

The host devices and media taken from the crime scene should be labeled, bagged, and sealed, using tamper-evident bags. It is also appropriate to ensure that the bags have antistatic shielding to reduce the possibility that data will be damaged or corrupted on the electronic media by electrostatic discharge (ESD). Each piece of evidence should be documented by a chain of custody form which records where, when, and who collected the evidence, who subsequently handled it, and where it was stored.

The evidence should be stored in a secure facility; this not only means access control, but also environmental control, so that the electronic systems are not damaged by condensation, ESD, fire, and other hazards. Similarly, if the evidence is transported, the transport must also be secure.

ACQUISITION OF OTHER DATA

There are other potential sources of forensic data within computer systems and networks, though they can be hard to acquire or to prove as admissible.

#### Network <a href="#id-629f0a38-54ee-4f4f-8a7e-ba74b5440c42" id="id-629f0a38-54ee-4f4f-8a7e-ba74b5440c42"></a>

Packet captures and traffic flows can contain very valuable evidence, if the capture was running at the right time and in the right place to record the incident. As with memory forensics, the issue for forensics lies in establishing the integrity of the data. Most network data will come from a SIEM.

#### Cache <a href="#b238b0da-2f84-4224-a727-c013b1f61860" id="b238b0da-2f84-4224-a727-c013b1f61860"></a>

Cache can refer either to hardware components or software. Software-based cache is stored in the file system and can be acquired as part of a disk image. For example, each browser has a cache of temporary files, and each user profile has a cache of temp files. Some cache artifacts generated by the OS and applications are held in memory only, such as portions of the registry, cryptographic keys, password hashes, some types of cookies, and so on. The contents of hardware cache (CPU registers and disk controller read/write cache, for instance) is not generally recoverable.

#### Artifacts and Data Recovery <a href="#id-0d14f863-e94e-4789-b5cc-cc4a75a51a7c" id="id-0d14f863-e94e-4789-b5cc-cc4a75a51a7c"></a>

Artifacts refers to any type of data that is not part of the mainstream data structures of an operating system. For example, the Windows Alternate Data Streams (ADS) feature is often used to conceal file data, and various caches, such as prefetch and Amcache, can be used to find indicators of suspicious process behavior.

Data recovery refers to analyzing a disk (or image of a disk) for file fragments stored in slack space. These fragments might represent deleted or overwritten files. The process of recovering them is referred to as carving.

#### Snapshot <a href="#id-47376dc4-a9fb-4b87-b261-f788244b680e" id="id-47376dc4-a9fb-4b87-b261-f788244b680e"></a>

A snapshot is a live acquisition image of a persistent disk. While this may have less validity than an image taken from a device using a write blocker, it may be the only means of acquiring data from a virtual machine or cloud process.

#### Firmware <a href="#ba017909-3686-4639-8648-f489fb97a7a6" id="ba017909-3686-4639-8648-f489fb97a7a6"></a>

Firmware is usually implemented as flash memory. Some types, such as the PC firmware, can potentially be extracted from the device or from system memory using an imaging utility. It likely will be necessary to use specialist hardware to attach the device to a forensic workstation, however.

## DIGITAL FORENSICS FOR CLOUD

With an on-premises investigation, the right to seize and analyze devices is usually fairly unproblematic. There may be availability issues with taking a system out of service, and bring-your-own-device policies can be more complex, but essentially as all the equipment is the company's property, there are no third-party obstacles.

While companies can operate private clouds, forensics in a public cloud are complicated by the right to audit permitted to you by your service level agreement (SLA) with the cloud provider. Other issues with forensics investigations of cloud-hosted processing and data services are as follows:

* The on-demand nature of cloud services means that instances are often created and destroyed again, with no real opportunity for forensic recovery of any data. Cloud providers can mitigate this to some extent with extensive logging and monitoring options. A CSP might also provide an option to generate file system and memory snapshots from containers and VMs in response to an alert condition generated by a SIEM.
* Chain of custody issues are complex and might have to rely on the CSP to select and package data for you. The process should be documented and recorded as closely as is possible.
* Jurisdiction and data sovereignty may restrict what evidence the CSP is willing to release to you.
* If the CSP is a data processor, it will be bound by data breach notification laws and regulations. Coordinating the timing of notification and contact with the regulator between your organization and the CSP can be extremely complex, especially if there is an ongoing incident requiring confidentiality.
