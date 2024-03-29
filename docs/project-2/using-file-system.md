---
layout: default
title: Using the File System
parent: Background
grand_parent: Project 2
nav_order: 2
---

### 3.1.2 Using the File System

You will need to interface to the file system code for this project, because a) user programs are loaded from the file system and b) many of the system calls you must implement deal with the file system. However, the focus of this project is not the file system, so we have provided a simple but complete file system in the filesys directory. You will want to look over the filesys.h and file.h interfaces to understand how to use the file system and its many limitations.

There is no need to modify the file system code for this project, and so we recommend that you do not. Working on the file system is likely to distract you from this project's focus.

Proper use of the file system routines now will make life much easier for project 4, when you improve the file system implementation. Until then, you will have to tolerate the following limitations:

No internal synchronization. Concurrent accesses will interfere with one another. You should use mutual exclusion and/or synchronization to ensure that only one process at a time is executing file system code.
File size is fixed at creation time. The root directory is represented as a file, so the number of files that may be created is also limited.
File data is allocated as a single extent, that is, data in a single file must occupy a contiguous range of sectors on disk. External fragmentation can therefore become a serious problem as a file system is used over time.
No subdirectories.
File names are limited to 14 characters.
A system crash mid-operation may corrupt the disk in a way that cannot be repaired automatically. There is also no file system repair tool.
One important feature is included:

Unix-like semantics for filesys_remove() are implemented. That is, if a file is open when it is removed, its blocks are not deallocated and it may still be accessed by any threads that have it open, until the last one closes it. See Removing an Open File, for more information.
You need to be able to create a simulated disk with a file system partition. The pintos-mkdisk program provides this functionality. From the userprog/build directory, execute pintos-mkdisk filesys.dsk --filesys-size=2. This command creates a simulated disk named filesys.dsk that contains a 2 MB Pintos file system partition. Then format the file system partition by passing -f -q on the kernel's command line: pintos -f -q. The -f option causes the file system to be formatted, and -q causes Pintos to exit as soon as the format is done.

You'll need a way to copy files in and out of the simulated file system. The pintos -p ("put") and -g ("get") options do this. To copy file into the Pintos file system, use the command pintos -p file -- -q. (The -- is needed because -p is for the pintos script, not for the simulated kernel.) To copy it to the Pintos file system under the name newname, add -a newname: pintos -p file -a newname -- -q. The commands for copying files out of the Pintos file system are similar, but substitute -g for -p.

Incidentally, these commands work by passing special commands extract and append on the kernel's command line and copying to and from a special simulated "scratch" partition. If you're very curious, you can look at the pintos script as well as filesys/fsutil.c to learn the implementation details.

Here's a summary of how to create a disk with a file system partition, format the file system, copy the echo program into the new disk, and then run echo, passing argument x. (Argument passing won't work until you implemented it.) It assumes that you've already built the examples in examples and that the current directory is userprog/build:

 	
pintos-mkdisk filesys.dsk --filesys-size=2
pintos -f -q
pintos -p ../../examples/echo -a echo -- -q
pintos -q run 'echo x'
                    
The three final steps can actually be combined into a single command:

 	
pintos-mkdisk filesys.dsk --filesys-size=2
pintos -p ../../examples/echo -a echo -- -f -q run 'echo x'
                    
If you don't want to keep the file system disk around for later use or inspection, you can even combine all four steps into a single command. The --filesys-size=n option creates a temporary file system partition approximately n megabytes in size just for the duration of the pintos run. The Pintos automatic test suite makes extensive use of this syntax:

 	
pintos --filesys-size=2 -p ../../examples/echo -a echo -- -f -q run 'echo x'
                    
Note that make check uses the above command, and so any disk you have previously created will be obliterated after running make check.

You can delete a file from the Pintos file system using the rm file kernel action, e.g. pintos -q rm file. Also, ls lists the files in the file system and cat file prints a file's contents to the display.
