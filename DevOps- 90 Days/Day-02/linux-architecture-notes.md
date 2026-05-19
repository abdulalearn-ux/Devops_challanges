* **The core components of Linux (kernel, user space, init/systemd) -** 

Linux is an open-source operating system that follows a layered architecture. It mainly consists of the following components:

&#x09;1. Hardware

This includes physical components like CPU, memory, disk, and devices. 

&#x09;2. Kernel

The kernel is the core of the Linux operating system. It acts as a bridge between hardware and software.

It is responsible for: 

&#x09;	○ Process management 

&#x09;	○ Memory management 

&#x09;	○ Device drivers 

&#x09;	○ File system handling 

&#x09;3. Shell

The shell is an interface between the user and the kernel.

It allows users to interact with the system using commands (CLI) or scripts. 

&#x09;4. Applications

These are user-level programs like browsers, editors, or any software that runs on the OS.



Init/systemd- it is the first process which is initiated whenever a Linux kernel starts this it helps to start other processes its PID is 1



* **How processes are created and managed**

Processes are created using fork and exec system calls, and the kernel manages them by scheduling, assigning PIDs, and controlling their execution.



* **What systemd does and why it matters** 

Systemd is the first process to start when Linux kernel is initiated it helps to start other process it has PID=1

