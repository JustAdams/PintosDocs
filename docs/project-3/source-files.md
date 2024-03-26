---
layout: default
title: Source Files
parent: Background
grand_parent: Project 3
nav_order: 1
---

### 4.1.1 Source Files

Since this project is built on top of project 2, you'll want to make a copy of your completed project 2 code to get started.

You will work in the vm directory for this project. The vm directory contains only Makefiles and some empty source files. The only change from userprog is that this new Makefile turns on the setting -DVM. All code you write will be in these empty files or in files introduced in earlier projects.

You might encounter these files for the first time:

"devices/block.h"
"devices/block.c"
Provides sector-based read and write access to block device. You will use this interface to access the swap partition as a block device.
