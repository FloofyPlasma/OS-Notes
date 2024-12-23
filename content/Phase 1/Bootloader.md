---
title: "Phase 1: Bootloader"
description: Overview of the what a Bootloader is, and plans for a theoretical implementation.
date: 2024-12-23
tags:
  - phase-1
  - draft
---
*[[Overview|Back to overview.]]*

*[[Roadmap|Back to roadmap.]]*

A bootloader is a small program that is run when the computer starts. Its primary job is to load the OS kernel into memory, and start it. The bootloader is the first program executed off disk after the [[Boot Process|boot process]] is completed. The bootloader will initialize hardware, and prepare the environment for the kernel.

The bootloader has several steps before its completed:

1. Initialize Hardware: Prepares the system's hardware ensuring everything is ready for the Kernel.
2. Load the Kernel: Transfers the kernel from storage to memory.
3. Transfer Control: Hands over control to the Kernel to start its execution.

### Our Theoretical Bootloader

The bootloader process will be divided into stages, and each stage will have specific responsibilities. Here's a rough outline of my bootloader's structure:

##### **Stage 1: Master Boot Record (MBR)**

The MBR will be contained within the first 512 bytes of the disk.

- Responsibilities of the MBR:
	- The BIOS will load the first 512 bytes into memory at address `0x7C00` after the [[Boot Process|boot process]] is completed.
	- The Stage 1 bootloader's primary job is to load the second-stage bootloader from the disk into memory.
	- Basic hardware initialization will be performed using [[BIOS Interrupts|BIOS interrupts]] (putting the display into text mode).
	- A simple message will be displayed, something like "Loading Stage 1..."
	- We will then load the second stage bootloader (placed in sector 2) into memory.
	- Once we load the second stage, we will transfer control to it by executing a jump into its memory location.

To summarize, the BIOS will load our MBR into `0x7C00`. Then we will want to load Stage 2 of our bootloader from disk. A basic message will be printed to the screen, and we will jump to Stage 2.

##### **Stage 2: Main Bootloader**

The main bootloader will be located in the first sector after the MBR.

- Responsibilities of Stage 2:
	- Perform further hardware initialization (setup memory).
	- Setup the Global Descriptor Table (GDT) for Protected Mode.
	- Setup interrupt handling for other system services.
	- Load the Kernel from disk into memory using [[BIOS Interrupts|BIOS interrupts]].
	- Setup memory paging.
	- Setup Protected Mode (16-bit → 32-bit)

The second stage will get the system closer to being ready for the Kernel, and will load it into memory. It will prepare the GDT, memory pages, and transition the CPU into Protected mode.

##### **Stage 3: Kernel Loader**

This will be the final stage in the bootloader, and it will implement file system support (likely FAT). It will also initialize any system libraries or configuration programs that may be needed. It will then transfer control to the Kernel.

This plan for a multi-stage bootloader will ensure the bootloader can be broken into smaller files, which in turn can help with the debugging process incase something ever goes wrong. We can also have a more complex bootloader without having to deal with the 512 byte limitation the MBR has.