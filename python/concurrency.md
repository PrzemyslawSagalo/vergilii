# Concurrency in Python
| Feature | AsyncIO | Threading | Multiprocessing |
| :--- | :--- | :--- | :--- |
| **Context Switch** | **Cooperative (Code Decides)**<br>Switch happens *only* at `await`. Very fast (User-space). | **Preemptive (OS Decides)**<br>OS interrupts execution arbitrarily. Slower (Kernel-space). | **Preemptive (OS Decides)**<br>OS interrupts execution arbitrarily. Slower (Kernel-space). |
| **Best For** | **High Concurrency I/O**<br>(Websockets, APIs, 10k+ connections) | **Blocking / Legacy I/O**<br>(File systems, DB drivers without async support) | **CPU Bound**<br>(Heavy math, Image processing, ML) |
| **Memory Overhead** | **Low**<br>Single process, single thread overhead. | **Medium**<br>Shared heap, but each thread has its own stack. | **High**<br>Each process copies the entire Python interpreter/resources. |
| **Data Sharing** | **Shared (Easy)**<br>Single memory space. No locks are usually needed (atomic between awaits). | **Shared (Complex)**<br>Shared memory. **Requires Locks/Mutexes** to prevent race conditions. | **Isolated (Slow)**<br>Separate memory spaces. Data must be **copied** via IPC (Pickling). |
| **GIL Impact** | **Irrelevant**<br>Runs on a single thread. | **Significant**<br>Only one thread executes Python bytecode at a time. | **Bypassed**<br>Each process has its own GIL, allowing true parallelism. |
