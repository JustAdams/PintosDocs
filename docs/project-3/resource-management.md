---
layout: default
title: Resource Management Overview
parent: Background
grandparent: Project 3
nav_order: 3
---

### 4.1.3 Resource Management Overview

You will need to design the following data structures:

Supplemental page table
Enables page fault handling by supplementing the page table. See section 4.1.4 Managing the Supplemental Page Table.

Frame table
Allows efficient implementation of eviction policy. See section 4.1.5 Managing the Frame Table.

Swap table
Tracks usage of swap slots. See section 4.1.6 Managing the Swap Table.

You do not necessarily need to implement three completely distinct data structures: it may be convenient to wholly or partially merge related resources into a unified data structure.

For each data structure, you need to determine what information each element should contain. You also need to decide on the data structure's scope, either local (per-process) or global (applying to the whole system), and how many instances are required within its scope.

To simplify your design, you may store these data structures in non-pageable memory. Non-pageable memory should not be evicted from the frame table. That means that you can be sure that pointers among them will remain valid.

Possible choices of data structures include arrays, lists, bitmaps, and hash tables. An array is often the simplest approach, but a sparsely populated array wastes memory. Lists are also simple, but traversing a long list to find a particular position wastes time. Both arrays and lists can be resized, but lists more efficiently support insertion and deletion in the middle.

Pintos includes a bitmap data structure in lib/kernel/bitmap.c and lib/kernel/bitmap.h. A bitmap is an array of bits, each of which can be true or false. Bitmaps are typically used to track usage in a set of (identical) resources: if resource n is in use, then bit n of the bitmap is true. Pintos bitmaps are fixed in size, although you could extend their implementation to support resizing.

Pintos also includes a hash table data structure (see section A.8 Hash Table). Pintos hash tables efficiently support insertions and deletions over a wide range of table sizes.

Although more complex data structures may yield performance or other benefits, they may also needlessly complicate your implementation. Thus, we do not recommend implementing any advanced data structure (e.g. a balanced binary tree) as part of your design.
