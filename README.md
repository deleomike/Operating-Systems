# Operating Systems - CMPSC 473

My operating systems course's labs primarily focused on threading, race conditions, and how these are affected by the OS.

The book for the course was **Modern Operating Systems Fourth Edition by Andrew S. Tatenbaum**

- Labs
  - [Lab 6](./src/Lab6/)
  - [Lab 11](./src/lab11/)
- Homework
  - [HW 1](./src/HW1/)
- Algorithms
  - [Linked List](./src/LinkedList/)
  - [Sort Numbers](./src/Sort_Numbers/)
  - [Bitmap](./src/Bitmap/)
  - [Hermite Interpolation](./src/hermite/)
- Threading
  - [Race Conditions](./src/Race/)
  - [Signals](./src/Signals/)
  - [Batched Threads (w/ Mutex)](./src/Batch/)


## Final Exam Study Guide

| Term/Question                                                                                                                                                                     | Answer                                                                                                                                           |
|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|
| Memory: Base register = 120 Limit register = 360 - What is address space size?                                                                                                    | 240                                                                                                                                              |
| Memory: Base register = 120 Limit register = 360 X references relative address 50 Y references relative address 100 Z references relative address 250 - Absolute address of X Y Z | 170 220 370                                                                                                                                      |
| MM: First Fit                                                                                                                                                                     | First fit will find the first space that fits, and then break it up into what is needed, and the rest is empty space.                            |
| MM: Next Fit                                                                                                                                                                      | Picks up where fit left off. Picks next available space, like first fit                                                                          |
| MM: Best Fit                                                                                                                                                                      | Searches entire memory for the space that matches the size needed, the best                                                                      |
| MM: Worst Fit                                                                                                                                                                     | Searches entire memory for the space that is the largest                                                                                         |
| MM: Quick Fit                                                                                                                                                                     | Has a linked list of memory spaces indexed by size, and then allocates the memory to what is needed                                              |
| Paging Vs. Swapping                                                                                                                                                               | Paging is taking snippets of program memory and swapping those out when they need to be. Swapping is swapping the whole program in and out.      |
| Page Frame                                                                                                                                                                        | An indexed slice of memory the RAM                                                                                                               |
| Page                                                                                                                                                                              | An indexed slice of memory of the virtual memory                                                                                                 |
| Page Table                                                                                                                                                                        | Maps virtual addresses into physical address                                                                                                     |
| present/absent bit                                                                                                                                                                | Indicates if the memory is being stored inside the RAM or not.                                                                                   |
| What is a page fault                                                                                                                                                              | A Page Fault is the event where memory is not loaded into the Page Table, and must be retrieved from the disk                                    |
| Dirty/Clean bit                                                                                                                                                                   | Indicates if the memory has been modified or not, and if it needs to be updated from the disk                                                    |
| Translation Lookaside Buffer                                                                                                                                                      | Subset of the Page Table of the most commonly accessed memory locations (usually up to 256)                                                      |
| Page Hit vs SegFault                                                                                                                                                              | Page hit is when the indexed memory is found in the TLB. Segfault is when the memory is nowhere to be found                                      |
| Soft Miss vs Hard Miss                                                                                                                                                            | Soft Miss is when the memory Is not found in the TLB, but is in the Page Table. Hard Miss is when the memory is only found in the Disk           |
| Can the virtual memory size be larger than the RAM?                                                                                                                               | Yes                                                                                                                                              |
| What does the Memory Management Unit Do?                                                                                                                                          | Handles Memory Abstractions                                                                                                                      |
| What is a deadlock? When does it happen?                                                                                                                                          | Deadlock is when processes are waiting on a condition that will never occur. Ex: when two processes are asleep and wait for the other to wakeup. |
| Difference between Mutexes and Semaphores                                                                                                                                         | Mutexes are locks that protect the access of shared resources. Semaphores are ints that synchronize processes.                                   |
| What is the memory abstraction technique we used?                                                                                                                                 | Base and Limit Registers                                                                                                                         |
| Function to setup a specific Signal Handler                                                                                                                                       | void (*signal(int sig, void (* func) (int ))) (int);                                                                                             |
| SIG_IGN                                                                                                                                                                           | Ignores the signal                                                                                                                               |
| SIG_DFL                                                                                                                                                                           | Resets the signal handler, so the original function of the signal is used next time                                                              |
| Transient Properties of unnamed pipes in C                                                                                                                                        | Destroyed when process terminates, destroyed when ends are closed.                                                                               |
| Properties of unnamed pipes in C                                                                                                                                                  | Pipes are only accessed through the process which share same ancestors, unidirectional                                                           |
| Poperties of Named pipes in C                                                                                                                                                     | Special File Entry in UNIX, Persistent, contains no data                                                                                         |
| Size of pipe array                                                                                                                                                                | 2 Entries: read end, write end                                                                                                                   |
| Read Block                                                                                                                                                                        | Attempt to read from an empty pipe. Block until new data is inside the pipe                                                                      |
| Write Block                                                                                                                                                                       | Attemp to write to a full pipe. Block until there is room                                                                                        |
| What processes can access a pipe?                                                                                                                                                 | The process that made it, and any of its children                                                                                                |
| close()                                                                                                                                                                           | Process closes and relinquishes access to pipe. Closing it in one, does not close it in the other                                                |
| IPC: Busy Waiting                                                                                                                                                                 | Constantly checking the shared resource until it is available                                                                                    |
| IPC: Sleep and Wakeup                                                                                                                                                             | When the crit region is reached, and another process is using it. Block current until wakeup call is received                                    |
| IPC-BusyWait: Problem with Disabling Interrupts                                                                                                                                   | Might cause a system hault if current process exits without enabling. Security Concerns                                                          |
| IPC-BusyWait: Problem with Lock variables                                                                                                                                         | Does not provide mutual exclusion because there is no way to tell when OS will switch. Two processes can get into deadlock busy waiting          |
| IPC-BusyWait: Problem with strict alternation                                                                                                                                     | Violates Third rule of crit region mutual exclusion. 3. No processes outside crit region may block others                                        |
| IPC-BusyWait: Problem with Peterson's solution                                                                                                                                    | Works but cannot scale to more than two processes                                                                                                |
| IPC-BusyWait: Problem with TSL instruction                                                                                                                                        | Only useful for multi-processor architectures                                                                                                    |