---
title: "Phase 1: Boot Process"
description: Overview of the Bootloader boot process
date: 2024-12-23
tags:
  - phase-1
  - draft
---
*[[Overview|Back to overview.]]*

*[[Roadmap|Back to roadmap.]]*

When a computer is turned on, the boot process has several stages to go through to prepare the system to run an operating system. This page is going to assume the system is booting in Legacy BIOS mode, not UEFI mode.

The first stage in the boot process is a power on self test. This is the process that tests the components (memory training occurs, etc.), and looks for a bootable device.

The BIOS then checks the bootable devices for the boot signature magic number. This is located in the first sector which has the byte sequence `0x55AA` at byte offsets 510 and 511. If the BIOS finds this boot sector, it loads it into memory. After its loaded, execution is then transferred to the boot record. On a floppy (which this system is intended to be run from at this current time) all 512 bytes can contain the executable code.

Once the [[Bootloader|bootloader]] is loaded, it finds and loads the kernel into memory, and passes control to it.

