---
title: "Phase 1: Real Mode"
description: Overview of the BIOS Real Mode
date: 2024-12-23
tags:
  - phase-1
  - draft
---
*[[Overview|Back to overview.]]*

*[[Roadmap|Back to roadmap.]]*

Real Mode[^1] is the first operating mode the CPU uses after booting. While in Real Mode, the CPU is limited up to 1 MB of memory. There is also no memory protection, so faulty programs can freely overwrite any part of memory, including other programs or the OS itself. There is no separation between user-space and kernel-space memory. The main way of talking to the hardware while in Real Mode is by using [[BIOS Interrupts]].

Memory is accessed using segmentation[^2] using a segment:offset system. Real Mode does not support multitasking or virtual memory. The CPU simply executes one program at a time and lacks the mechanisms to switch between processes safely.

The BIOS provides the system with very simple device drivers. However, these devices are missing some of the advanced CPU features like hardware-level interrupts or 32-bit addressing. The CPU is limited to the 16-bit architecture of 8086 and 80286 processors.

Real Mode is essential for compatibility with older 16-bit software. However, in our OS we will want to get to Protected Mode[^3] as soon as possible to avoid these limitations.

[^1]:https://wiki.osdev.org/Real_Mode
[^2]:https://wiki.osdev.org/Segmentation
[^3]:https://wiki.osdev.org/Protected_Mode