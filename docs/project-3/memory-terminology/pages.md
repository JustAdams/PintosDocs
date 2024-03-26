---
layout: default
title: Pages
parent: Memory Terminology
grand_parent: Project 3
nav_order: 1
---

### 4.1.2.1 Pages

A page, sometimes called a virtual page, is a continuous region of virtual memory 4,096 bytes (the page size) in length. A page must be page-aligned, that is, start on a virtual address evenly divisible by the page size. Thus, a 32-bit virtual address can be divided into a 20-bit page number and a 12-bit page offset (or just offset), like this:

 	
               31               12 11        0
              +-------------------+-----------+
              |    Page Number    |   Offset  |
              +-------------------+-----------+
                       Virtual Address
                    
Each process has an independent set of user (virtual) pages, which are those pages below virtual address PHYS_BASE, typically 0xc0000000 (3 GB). The set of kernel (virtual) pages, on the other hand, is global, remaining the same regardless of what thread or process is active. The kernel may access both user and kernel pages, but a user process may access only its own user pages. See section 3.1.4 Virtual Memory Layout, for more information.

Pintos provides several useful functions for working with virtual addresses. See section A.6 Virtual Addresses, for details.
