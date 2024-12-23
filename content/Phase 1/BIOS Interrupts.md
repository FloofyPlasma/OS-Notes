---
title: "Phase 1: BIOS Interrupts"
description: Overview of the BIOS Interrupts
date: 2024-12-23
tags:
  - phase-1
  - draft
---
*[[Overview|Back to overview.]]*

*[[Roadmap|Back to roadmap.]]*

BIOS interrupts provide essential services for hardware management and system control, especially for boot-up. BIOS interrupts are invoked using specific interrupt numbers where different registers like `AH`, `AX` or `EAX` are set to request functions. The other registers are usually used for any "arguments" the function may have, and also contain any returned data from the function.

Interrupt numbers are always passed in hex, and the `INT` opcode is used to call the BIOS. A few of the most important interrupt codes to know are the keyboard interrupt, `0x16`, the mas storage interrupt, `0x13` and the video display interrupt `0x10`.

However, when the CPU is in Protected mode, the BIOS functions are mostly unavailable. They should be used while still in [[Real Mode]] to detect hardware, manage any peripherals and setup basic tasks like memory management and display output.

You can see read more in-depth information about the specific functions on the [OSDev Wiki](https://wiki.osdev.org/BIOS#BIOS_functions).