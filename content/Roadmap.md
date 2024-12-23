---
title: Roadmap
description: The roadmap plans for my OS project.
date: 2024-12-22
tags:
  - roadmap
  - draft
---
##### **Phase 1: Bootloader**

*[[Overview|Main Page]]*
1. Learn the Basics of [[Real Mode]]:
	- Understand [BIOS interrupts](https://wiki.osdev.org/BIOS#BIOS_functions) (e.g., `int 13h` for disk I/O, `int 10h` for display).
	- Study x86 assembly for 16-bit real mode.
2. Write a Simple [Bootloader](https://wiki.osdev.org/Bootloader):
	- Write a program in assembly to display a message (e.g., "Hello, OS!").
	- Ensure it fits in a 512-byte boot sector.
	- Compile using AS and link with GCC.
3. Load a [Kernel](https://wiki.osdev.org/Kernel):
	- Extend the bootloader to load a kernel from disk into memory.
	- Use BIOS calls for disk reads.
4. Transition to [Protected Mode](https://wiki.osdev.org/Protected_Mode):
	- Switch from real mode (16-bit) to protected mode (32-bit).
	- Setup the Global Descriptor Table ([GDT](https://wiki.osdev.org/Global_Descriptor_Table)).

##### **Phase 2: Kernel Basics**

1. Set Up the Kernel Environment:
	- Write the kernel entry point in assembly.
	- Switch to C for higher-level kernel development.
	- Test printing messages from the kernel.
2. Implement Basic [Memory Management:](https://wiki.osdev.org/Memory_management)
	- Create a basic memory manager to allocate/deallocate memory.
	- Implement a simple [heap](https://wiki.osdev.org/Heap) or [stack](https://wiki.osdev.org/Stack)
3. Handle CPU Interrupts:
	- Set up the Interrupt Vector Table ([IVT](https://wiki.osdev.org/Interrupt_Vector_Table)).
	- Write interrupt handlers for keyboard input and timer.

##### **Phase 3: Device Drivers**

1. Keyboard Input:
	- Write a driver to capture [keyboard](https://wiki.osdev.org/PS/2_Keyboard) input.
	- Display typed characters on the screen.
2. Display Output:
	- Start with [VGA text mode](https://wiki.osdev.org/Text_UI) for output.
	- *Optional: Explore [graphical modes](https://wiki.osdev.org/GUI) later.*
3. *Mouse Support (Optional)*
	- Write a basic driver to read [mouse input](https://wiki.osdev.org/Mouse_Input).
	- Display mouse movements on the screen.

##### **Phase 4: Userland and File System**

1. Develop a [Simple CLI](https://wiki.osdev.org/Command_Line):
	- Allow basic user commands (e.g., "help", "reboot").
	- Handle I/O efficiently.
2. [File System](https://wiki.osdev.org/File_Systems):
	- Implement a simple file system (e.g., [FAT12/FAT16](https://wiki.osdev.org/FAT) or custom).
	- Add support for reading files from disk.

##### **Phase 5: Advanced Features**

1. [Multi-tasking](https://wiki.osdev.org/Kernel_Multitasking):
	- Learn about process management and [context switching](https://wiki.osdev.org/Context_Switching).
	- Implement a [basic scheduler](https://wiki.osdev.org/Processes_and_Threads).
2. Enhance the Kernel:
	- Add support for modules (dynamically loadable components).
	- Consider moving to a [hybrid](https://wiki.osdev.org/Hybrid_Kernel) or [microkernel](https://wiki.osdev.org/Microkernel) architecture.
3. *Networking (Optional)*
	- Implement basic [networking](https://wiki.osdev.org/Network_Stack) capabilities.
	
##### **Phase 6: Refine and Expand**

1. Polish the OS:
	- Optimize performance and memory usage.
	- Refactor code for modularity.
2. Experiment with [64-bit Mode](https://wiki.osdev.org/X86-64):
	- Transition into x86_64 for more features and modern architecture.
3. Build Userland Applications:
	- Develop small programs or utilities to showcase OS capabilities.