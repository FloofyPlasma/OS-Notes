---
title: "Phase 1: Overview"
description: Overview of the Bootloader phase
date: 2024-12-23
tags:
  - phase-1
  - draft
---
*[[Roadmap|Back to roadmap.]]*

The BIOS follows a simple [[Boot Process|boot process]] when a computer is turned on. Our job is to write the boot loader for the BIOS. It's responsible for loading the OS Kernel into memory. This phase focuses on understanding x86 [[Real Mode|real mode]] and transitioning into protected mode[^1].

##### Steps for the boot loader:

- Load the kernel (and its dependencies) into memory
- Provide the kernel with information about the system
- Prepare the CPU and BIOS for the kernel
- Transfer control to the kernel

Since the bootloader is running in Real Mode, it has easy access to the BIOS. This is where steps like hardware communication (memory detection, file reading, video detection etc.), should take place. Essentially, this prepares the system for Phase 2.

[^1]: https://wiki.osdev.org/Protected_Mode