# Concurrency Models in Python

| Feature | AsyncIO | Threading | Multiprocessing |
| :--- | :--- | :--- | :--- |
| **Context Switch** | **Cooperative (Fast)**<br>The code itself decides when to pause (using `await`). | **Preemptive (Slow)**<br>The OS forces the code to pause and switch tasks. | **Preemptive (Slow)**<br>The OS forces the code to pause and switch tasks. |
| **Best For** | **Waiting for I/O**<br>(Websockets, APIs, many connections) | **Blocking I/O**<br>(Simple file operations, legacy scripts) | **Heavy Calculation**<br>(Data processing, Machine Learning) |
| **Memory & Data** | **Shared (Efficient)**<br>Everything runs in one place. Easy access to variables. | **Shared (Careful)**<br>Threads share memory. You need **Locks** to prevent errors. | **Isolated (Expensive)**<br>Each process has its own memory. Data must be **copied** to share it. |
| **Parallelism** | **None**<br>One task runs at a time. | **None**<br>Only one thread runs at a time (due to GIL). | **True Parallelism**<br>Multiple CPUs work at the same time. |
