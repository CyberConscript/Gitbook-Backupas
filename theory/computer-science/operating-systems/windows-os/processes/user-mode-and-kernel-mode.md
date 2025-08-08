# User mode and kernel mode

### User mode <a href="#user-mode" id="user-mode"></a>

When you launch an application in user mode, Windows creates a _process_ for it. This process provides the application with a private [_virtual address space_](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/virtual-address-spaces) and a private _handle table_. Since each application's virtual address space is private, one application can't modify another application's data. Each application runs in isolation, ensuring that if one crashes, it doesn't affect other applications or the operating system.

The virtual address space of a user-mode application is also limited. A process running in user mode can't access virtual addresses that are reserved for the operating system. Limiting the virtual address space of a user-mode application prevents the application from modifying or damaging critical operating system data.



### Kernel mode <a href="#kernel-mode" id="kernel-mode"></a>

All code running in kernel mode shares a single [virtual address space](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/virtual-address-spaces). As a result, a kernel-mode driver isn't isolated from other drivers or the operating system. If a kernel-mode driver mistakenly writes to the wrong virtual address, it could compromise data belonging to the operating system or another driver. If a kernel-mode driver crashes, it causes the entire operating system to crash.

The following diagram illustrates the communication between user-mode and kernel-mode components.

Drivers running in kernel mode must be careful when directly reading from or writing to addresses in user space. The following scenario illustrates why.

1. A user-mode program initiates a request to read some data from a device. The program provides the starting address of a buffer to receive the data.
2. A device driver routine, running in kernel mode, starts the read operation and returns control to its caller.
3. Later, the device interrupts the currently running thread to indicate that the read operation is complete. Kernel-mode driver routines handle the interrupt on this arbitrary thread, which belongs to an arbitrary process.
4. At this point, the driver must not write the data to the starting address that the user-mode program provided in Step 1. This address is in the virtual address space of the process that initiated the request, which is likely not the same as the current process.



<figure><img src="../../../../../.gitbook/assets/userandkernelmode01.png" alt=""><figcaption></figcaption></figure>

## Virtual address spaces <a href="#virtual-address-spaces" id="virtual-address-spaces"></a>

Processors use virtual addresses when reading or writing to memory locations. During these operations, the processor translates the virtual address into a physical one.

There are several benefits to accessing memory using virtual addresses:

* A program can use a contiguous range of virtual addresses to access a large, noncontiguous memory buffer in physical memory.
* A program can use a range of virtual addresses to access a memory buffer larger than the available physical memory. When physical memory is low, the memory manager saves pages of physical memory (typically 4 kilobytes in size) to a disk file. The system moves pages of data or code between physical memory and the disk as needed.
* The virtual addresses used by different processes are isolated. The code in one process can't alter the physical memory that is being used by another process or the operating system.

The range of virtual addresses that is available to a process is known as the process's _virtual address space_. Each [user-mode process](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/user-mode-and-kernel-mode) has its own private virtual address space.

* A 32-bit process typically has a virtual address space within the 2-gigabyte range 0x00000000 through 0x7FFFFFFF.
* A 64-bit process on 64-bit Windows has a virtual address space within the 128-terabyte range 0x000'00000000 through 0x7FFF'FFFFFFFF.

A range of virtual addresses is sometimes called a range of _virtual memory_. For more information, see [Memory and Address Space Limits](https://learn.microsoft.com/en-us/windows/win32/memory/memory-limits-for-windows-releases#memory-and-address-space-limits).

The following diagram illustrates some key features of virtual address spaces.

![Diagram showing the virtual address spaces for two 64-bit processes, Notepad.exe and MyApp.exe.](https://learn.microsoft.com/en-us/windows-hardware/drivers/gettingstarted/images/virtualaddressspace01.png)

The diagram shows the virtual address spaces for two 64-bit processes: Notepad.exe and MyApp.exe. Each process has its own virtual address space, ranging from 0x000'0000000 through 0x7FF'FFFFFFFF. Each shaded block represents one page (4 kilobytes in size) of virtual or physical memory. The Notepad process uses three contiguous pages of virtual addresses, starting at 0x7F7'93950000. However, these three contiguous pages of virtual addresses map to noncontiguous pages in physical memory. Also, both processes use a page of virtual memory beginning at 0x7F7'93950000, but these virtual pages map to different pages of physical memory.



