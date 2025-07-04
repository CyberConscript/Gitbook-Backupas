# System startup

In the Windows OS, storage partitions are represented by drive letters such as C, D, E, etc. Other operating systems may use different ways to refer to these partitions.



However, the computer still needs a map that helps guide it through these partitions, where they start and end, and what they contain. **MBR** (Master Boot Record) and **GPT** (GUID Partition Table) are different partitioning schemes that act as a map for all of the partitions used in the disk. They are like a blueprint of the building (disk) containing all the rooms (partitions). Both partitioning schemes differ in structure and properties, and choosing between them depends on multiple factors, including the disk size, hardware compatibility, and much more. The MBR/GPT is located in the very first sector of the disk and contains information about the structure and partitions of the disk. It also plays a key role during the boot process of a system. Due to this, the MBR/GPT has become an attractive target for attackers to manipulate the boot process by embedding their malware, often known as Bootkits, or tampering with them to make the system un-bootable.



### The Boot Process: Step by Step

1️⃣ **Power-On (POST)**

* Power-On Self-Test (POST) initializes hardware: CPU, RAM, GPU, storage.
* Basic hardware checks; beeps or diagnostic LEDs signal issues.

2️⃣ **Firmware (BIOS/UEFI) Initialization**

* BIOS (legacy) or UEFI (modern) firmware initializes more devices.:
  * BIOS (Basic Input/Output System) and UEFI (Unified Extensible Firmware Interface) are responsible for verifying whether all the hardware components work properly. A system can either use BIOS or UEFI firmware. The difference between them lies in their capabilities and features.
    * BIOS has been used for decades and is still used in some hardware. It runs in the basic 16-bit mode and supports only up to 2 terabytes of disks. The most important thing to note is that BIOS supports the MBR partitioning scheme.
    * UEFI came as a replacement for BIOS, offering 32-bit and 64-bit modes with up to 9 zettabytes of disks. UEFI offers a secure boot feature to ensure integrity during the system boot process. It also offers redundancy, allowing us to recover from the backup even if the boot code is corrupted. UEFI uses a GPT partitioning scheme, unlike the MBR partitioning scheme used by BIOS.
* Sets up environment for bootloader.
* Locates the configured boot device (disk, USB, network PXE).

3️⃣ **Bootloader Execution**

* BIOS: After the BIOS/UEFI has performed the POST check, it is time for the BIOS/UEFI to locate bootable devices, such as SSDs, HDDs, or USBs, with the operating system installed. Once the bootable device is located, it starts reading this device. Now, here comes the role of the MBR/GPT. The very first sector of the device would either contain the MBR (Master Boot Record) or the GPT (GUID Partition Table). The MBR/GPT would be taking control of the boot process from here.
* UEFI: Loads EFI bootloader (e.g., `bootmgfw.efi` for Windows).
* Bootloader locates bootable device and loads the OS kernel.

4️⃣ **Kernel Loading**

* OS kernel (Windows: `ntoskrnl.exe`, Linux: `vmlinuz`) is loaded into memory.
* Initializes low-level hardware drivers.

5️⃣ **Hardware Abstraction & Initialization**

* Kernel probes devices, starts device drivers.
* Initializes memory management, process scheduler.

6️⃣ **System Services & Init Processes**

* Windows: SMSS.exe → CSRSS.exe, wininit.exe, services.exe.
* Linux: init/systemd starts processes and services.
* Security and authentication subsystems initialize (e.g., LSASS).

7️⃣ **User Logon & Shell Launch**

* Login screen appears.
* After successful authentication, user shell starts (e.g., Windows Explorer, GNOME, bash).

```
+-------------------------+
|     Power-On (POST)     |
+-----------+-------------+
            |
            v
+-------------------------+
| BIOS/UEFI Initialization|
+-----------+-------------+
            |
            v
+-------------------------+
|     Bootloader (MBR/EFI)|
+-----------+-------------+
            |
            v
+-------------------------+
|      Kernel Loading     |
+-----------+-------------+
            |
            v
+-------------------------+
| Hardware & Drivers Init |
+-----------+-------------+
            |
            v
+-------------------------+
|   System Services Init  |
+-----------+-------------+
            |
            v
+-------------------------+
|  User Logon & Shell Run |
+-------------------------+
```
