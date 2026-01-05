# Concurrency Models in Python

| Feature | AsyncIO (User-Level Threads) | Threading (Kernel-Level Threads) | Multiprocessing (Processes) |
| :--- | :--- | :--- | :--- |
| **Scheduling Manager** | **Runtime Code** (Event Loop)<br>The application's runtime system manages the queue. [cite_start]Kernel is unaware of these tasks.  | [cite_start]**OS Scheduler**<br>The Operating System manages the queue and decides which thread runs.  | [cite_start]**OS Scheduler**<br>The Operating System manages the queue and distributes processes across CPU cores.  |
| **Context Switch Cost** | **Ultra Low**<br>Saves only CPU registers. No kernel trap required. | **Medium**<br>Requires kernel trap (mode switch). Saves full CPU state. | [cite_start]**High**<br>Requires kernel trap + **TLB Flush** (memory cache invalidation).  |
| **Memory Model** | **Shared Address Space**<br>All tasks share the same memory. Efficient but requires care with state. | **Shared Address Space**<br>Threads share heap memory. Requires **Locks/Mutexes** to prevent race conditions. | **Isolated Address Space**<br>Each process has its own memory map. [cite_start]Data must be copied (IPC), which is slow.  |
| **Parallelism** | **None** (Concurrent)<br>Single CPU core. Tasks run interleaved. | **None in Python** (Concurrent)<br>Limited by GIL (Global Interpreter Lock). Only one thread executes Python bytecode at a time. | **True Parallelism**<br>Bypasses GIL. Multiple processes run on separate CPU cores simultaneously. |
| **Best For** | **I/O Bound**<br>High concurrency network apps (Websockets, 10k+ connections). | **Blocking I/O**<br>Legacy libraries, file operations, or simple background tasks. | **CPU Bound**<br>Heavy computation (ML, Data Science, Image Processing). |

> **Note on TLB:** The **Translation Lookaside Buffer (TLB)** is a hardware cache for memory addresses. Switching processes (Multiprocessing) forces a TLB flush, slowing down execution as the CPU must "relearn" memory mappings. [cite_start]Switching threads or async tasks preserves the TLB, maintaining high speed.
