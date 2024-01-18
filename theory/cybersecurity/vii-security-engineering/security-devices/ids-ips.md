# IDS/IPS

## IDS

An Intrusion Detection System (IDS) is a security tool designed to monitor and analyze network and/or system activities for signs of malicious or unauthorized activities. The primary purpose of an IDS is to identify and respond to security incidents. There are two main types of IDS: Network-based Intrusion Detection Systems (NIDS) and Host-based Intrusion Detection Systems (HIDS).

#### Network-Based Intrusion Detection Systems (NIDS):

1. **Description:**
   * NIDS monitors network traffic in real-time to detect suspicious patterns or anomalies. It analyzes packets and traffic flows to identify potential security threats or attacks.
2. **Different Versions:**
   * **Signature-Based NIDS:**
     * Uses a database of known attack signatures to identify malicious activities. It matches incoming network traffic against these signatures.
   * **Anomaly-Based NIDS:**
     * Establishes a baseline of normal network behavior and triggers alerts or alarms when deviations from this baseline are detected.
   * **Heuristic-Based NIDS:**
     * Uses predefined rules and heuristics to identify abnormal or potentially malicious behavior.
3. **Analysis Techniques:**
   * **Packet Inspection:**
     * Examines individual packets of data to identify known attack patterns or unusual activities.
   * **Traffic Flow Analysis:**
     * Analyzes patterns in network traffic, such as the volume of data, the frequency of connections, or the types of protocols used.
   * **Protocol Analysis:**
     * Monitors and analyzes the usage of network protocols to detect abnormalities or misuse.
   * **Signature Matching:**
     * Compares network traffic against a database of known attack signatures to identify malicious patterns.
   * **Behavioral Analysis:**
     * Builds a profile of normal network behavior and triggers alerts when deviations or anomalies are detected.

#### Host-Based Intrusion Detection Systems (HIDS):

1. **Description:**
   * HIDS monitors activities on individual hosts or endpoints, such as servers, workstations, or other devices. It focuses on detecting abnormal activities or security violations at the host level.
2. **Different Versions:**
   * **Signature-Based HIDS:**
     * Similar to signature-based NIDS, it uses a database of known attack signatures to identify malicious activities on individual hosts.
   * **Anomaly-Based HIDS:**
     * Establishes a baseline of normal host behavior and generates alerts when deviations from this baseline are detected.
3. **Analysis Techniques:**
   * **File Integrity Checking:**
     * Monitors changes to critical system files and alerts on unauthorized modifications.
   * **Registry Monitoring:**
     * Watches for changes to the Windows Registry or other system registries.
   * **Log Analysis:**
     * Analyzes system logs and application logs to identify security-related events.
   * **System Calls and API Monitoring:**
     * Monitors system calls and application programming interfaces (APIs) for suspicious activities.
   * **Behavioral Analysis:**
     * Profiles normal host behavior and generates alerts when deviations or anomalies are detected.



IDS plays a crucial role in network and host security by providing early detection and response capabilities to a wide range of security incidents. Organizations often deploy a combination of NIDS and HIDS, along with other security measures, to create a comprehensive defense-in-depth strategy.



