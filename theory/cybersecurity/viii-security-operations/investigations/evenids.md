# EvenIDs

## Windows native

* **Logins/failed logins/lockouts**
  * 4624 - An account was successfully logged on:
    * 2 = Interactive (local console)
    * 3 = Network (SMB, etc.)
    * 7 = Unlock workstation
    * 10 = Remote Interactive (RDP)
    * 11 = Cached Interactive (cached credentials)
  * 4625 - An account failed to log on
  * 4740 — A user account was locked out
* **Account modifications:**
  * 4720 - A user account was created
  * 4722 - A user account was enabled
  * 4738 - A user account was changed
  * 4725 - A user account was disabled
  * 4726 - A user account was deleted
  * 4723 - An attempt was made to change an account’s password
  * 4724 - An attempt was made to reset an account’s password
* **Group modifications**
  * 4732 - A member was added to a security-enabled local group
  * 4733 - A member was removed from a security-enabled local group
  * 4728 - A member was added to a security-enabled global group
  * 4729 - A member was removed from a security-enabled global group
  * 4730 — A security-enabled global group was deleted
  * 4731 — A security-enabled global group was created
* **Kerberos:**
  * 4768 - A Kerberos authentication (TGT) was requested
  * 4769 - A Kerberos service ticket (TGS) was requested (many 4769s for different SPNs in a short time from the same user)
  * 4771 - Kerberos pre-authentication failed
  * 4772 - Kerberos service ticket request failed
* **Process**
  * 4688 - New process is launched.





## Sysmon

### Process Events

1 — Process Create (includes command line, parent, hashes, etc.)\
2 — File Creation Time Changed\
3 — Network Connection Detected (outbound TCP/UDP connections)\
4 — Sysmon Service State Changed (start/stop of Sysmon itself)\
5 — Process Terminated\
6 — Driver Loaded\
7 — Image Loaded (DLLs or EXEs mapped into processes)

### File & Registry Events

8 — CreateRemoteThread (remote code injection into another process)\
9 — RawAccessRead (low-level disk reads, e.g., by disk forensics tools or malware)\
10 — Process Access (OpenProcess calls — used in token stealing, Mimikatz)\
11 — File Create (creation of a file or overwriting an existing one)\
12 — Registry Object Added or Deleted\
13 — Registry Value Set\
14 — Registry Object Renamed

### WMI & Named Pipe Events

15 — FileCreateStreamHash (streams created on files; used for detecting alternate data streams)\
16 — Sysmon Configuration Change (config updates)\
17 — Pipe Created (named pipes, often used in C2)\
18 — Pipe Connected (client connecting to a named pipe)

### Other Notable Events

19 — WMI Event Filter activity detected\
20 — WMI Event Consumer activity detected\
21 — WMI Event Consumer-To-Filter binding\
22 — DNS Query (domain lookups by processes)\
23 — File Delete Archived (deletion of a file captured before removal, if enabled)\
24 — Clipboard Changed (monitors clipboard activity, newer Sysmon versions)\
25 — Process Tampering (e.g., process hollowing, image replacement)\
26 — FileDeleteDetected (logs file deletions in monitored folders)

