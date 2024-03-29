---
layout: default
title: Background
nav_order: 1
parent: Project 2
has_children: true
---

## 3.1 Background

Up to now, all of the code you have run under Pintos has been part of the operating system kernel--even the test code from the last assignment ran as part of the kernel and had full access to privileged parts of the system. However, for user programs running on top of the operating system access is restricted. This project deals with the consequences.

In Pintos (and most other OSes), we allow more than one process to run at a time but, just as in your previous programming experience, user programs are written under the illusion that they have the entire machine. This means that when you load and run multiple processes at a time, you must manage memory, scheduling, and other state correctly to maintain this illusion. In Pintos, each process has one thread (multithreaded processes are not supported).

In the previous project, we compiled our test code directly into your kernel, so we had to require certain specific function interfaces within the kernel. From now on, we will test your operating system by running user programs. This gives you much greater freedom. You must make sure that the user program interface meets the specifications described here, but given that constraint you are free to restructure or rewrite kernel code however you wish.
