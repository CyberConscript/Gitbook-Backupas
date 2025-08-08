# Processes

## System

"The System process (process ID 4) is the home for a special kind of thread that runs only in kernel mode a kernel-mode system thread. System threads have all the attributes and contexts of regular user-mode threads (such as a hardware context, priority, and so on) but are different in that they run only in kernel-mode executing code loaded in system space, whether that is in Ntoskrnl.exe or in any other loaded device driver. In addition, system threads don't have a user process address space and hence must allocate any dynamic storage from operating system memory heaps, such as a paged or nonpaged pool."

What is unusual behaviour for this process?

* A parent process (aside from System Idle Process (0))
* Multiple instances of System. (Should only be one instance)&#x20;
* A different PID. (Remember that the PID will always be PID 4)
* Not running in Session 0



## SMSS (Session Manager Subsystem)

This process, also known as the Windows Session Manager, is responsible for creating new sessions. It is the first user-mode process started by the kernel.
