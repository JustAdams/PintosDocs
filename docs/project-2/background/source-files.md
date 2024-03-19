---
layout: default
title: Source Files
parent: Background
nav_order: 1
---

### 3.1.1 Source Files

You should obtain a fresh copy of Pintos from the "Files" section in Canvas.

The easiest way to get an overview of the programming you will be doing is to simply go over each part you'll be working with. In userprog, you'll find a small number of files, but here is where the bulk of your work will be:

process.c
process.h
Loads ELF binaries and starts processes.
pagedir.c
pagedir.h
A simple manager for 80x86 hardware page tables. Although you probably won't want to modify this code for this project, you may want to call some of its functions. See section 4.1.2.3 Page Tables, for more information.
syscall.c
syscall.h
Whenever a user process wants to access some kernel functionality, it invokes a system call. This is a skeleton system call handler. Currently, it just prints a message and terminates the user process. In part 2 of this project you will add code to do everything else needed by system calls.
exception.c
exception.h
When a user process performs a privileged or prohibited operation, it traps into the kernel as an "exception" or "fault."(2) These files handle exceptions. Currently all exceptions simply print a message and terminate the process. Some, but not all, solutions to project 2 require modifying page_fault() in this file.
gdt.c
gdt.h
The 80x86 is a segmented architecture. The Global Descriptor Table (GDT) is a table that describes the segments in use. These files set up the GDT. You should not need to modify these files for any of the projects. You can read the code if you're interested in how the GDT works.
tss.c
tss.h
The Task-State Segment (TSS) is used for 80x86 architectural task switching. Pintos uses the TSS only for switching stacks when a user process enters an interrupt handler, as does Linux. You should not need to modify these files for any of the projects. You can read the code if you're interested in how the TSS works.
