# Command line windows

Here’s a list of essential Windows Command Prompt commands, organized by category for system information, network troubleshooting, file and disk management, and task/process management:

***

#### **System Information**

1. **`systeminfo`**
   * Displays detailed information about the system, including OS version, BIOS, memory, and network details.
   * Example: `systeminfo`
2. **`wmic`**
   * Windows Management Instrumentation command-line tool that can query system hardware and software details.
   * Example: `wmic cpu get name` (displays CPU name)
3. **`msinfo32`**
   * Opens the System Information window in a graphical interface.
   * Example: `msinfo32`
4. **`dxdiag`**
   * Runs the DirectX Diagnostic Tool, providing details on graphics, audio, and input devices.
   * Example: `dxdiag`

***

#### **Network Troubleshooting**

1. **`ipconfig`**
   * Displays network configuration details like IP address, subnet mask, and gateway.
   * Example: `ipconfig /all` (shows detailed network configuration)
2. **`ping`**
   * Tests connectivity to a specified IP address or domain.
   * Example: `ping google.com`
3. **`tracert`**
   * Traces the route packets take to reach a destination, showing each network hop.
   * Example: `tracert google.com`
4. **`nslookup`**
   * Queries DNS to find the IP address associated with a domain.
   * Example: `nslookup openai.com`
5. **`netstat`**
   * Displays network statistics, open connections, and listening ports.
   * Example: `netstat -an` (shows all connections and listening ports)
6. **`arp`**
   * Displays or modifies the ARP (Address Resolution Protocol) cache.
   * Example: `arp -a` (displays all ARP entries)
7. **`pathping`**
   * Combines `ping` and `tracert` to identify packet loss at each hop on the network path.
   * Example: `pathping google.com`
8. **`nbtstat`**
   * Displays NetBIOS over TCP/IP protocol information, useful for troubleshooting Windows networking.
   * Example: `nbtstat -a COMPUTERNAME`
9. **`netsh`**
   * Network configuration and troubleshooting tool with a wide range of commands.
   * Example: `netsh wlan show profiles` (lists Wi-Fi profiles)

***

#### **File and Disk Management**

1. **`dir`**
   * Lists files and directories in the specified directory.
   * Example: `dir C:\Users`
2. **`cd`**
   * Changes the current directory.
   * Example: `cd C:\Windows\System32`
3. **`copy`**
   * Copies files from one location to another.
   * Example: `copy C:\file.txt D:\`
4. **`xcopy`**
   * Copies files and directories, including subdirectories.
   * Example: `xcopy C:\source D:\destination /s`
5. **`robocopy`**
   * Robust file copy utility, often used for large data transfers with advanced options.
   * Example: `robocopy C:\source D:\destination /mir` (mirrors directories)
6. **`diskpart`**
   * Disk partition management tool for creating, deleting, and managing disk partitions.
   * Example: `diskpart` (enters disk partition tool, requires further commands)
7. **`chkdsk`**
   * Checks for and repairs disk errors.
   * Example: `chkdsk C: /f` (checks and fixes errors on C: drive)
8. **`format`**
   * Formats a specified drive.
   * Example: `format D:` (formats drive D)
9. **`sfc`**
   * System File Checker scans and repairs corrupted system files.
   * Example: `sfc /scannow`
10. **`fsutil`**
    * Manages various disk and file system properties.
    * Example: `fsutil dirty query C:` (checks if C: drive is marked as dirty)
11. **`powercfg`**
    * Manages power settings and displays power configurations.
    * Example: `powercfg /batteryreport` (creates a battery report)

***

#### **Task and Process Management**

1. **`tasklist`**
   * Lists currently running processes with details like PID and memory usage.
   * Example: `tasklist`
2. **`taskkill`**
   * Terminates a process by PID or name.
   * Example: `taskkill /PID 1234 /F` (forcefully ends the process with PID 1234)
3. **`sc`**
   * Manages Windows services (start, stop, configure).
   * Example: `sc query` (lists all services)
4. **`shutdown`**
   * Shuts down, restarts, or logs off the computer.
   * Example: `shutdown /r /t 0` (restarts immediately)
5. **`wmic process`**
   * Displays detailed information on processes, including executable paths and memory usage.
   * Example: `wmic process list brief`
6. **`net start`**
   * Starts a Windows service.
   * Example: `net start "Windows Update"`
7. **`net stop`**
   * Stops a Windows service.
   * Example: `net stop "Windows Update"`
8. **`get-process`** (PowerShell)
   * Lists all active processes (PowerShell equivalent of `tasklist`).
   * Example: `get-process`
9. **`start`**
   * Launches a program or opens a file/folder.
   * Example: `start notepad.exe` (opens Notepad)
10. **`pslist`** (part of Sysinternals Suite)
    * Lists all active processes with detailed information.
    * Example: `pslist` (provides process details like CPU time, memory use)

These commands are powerful for managing and troubleshooting a Windows system. Some of these commands, like `wmic`, `diskpart`, and `shutdown`, require administrator privileges.
