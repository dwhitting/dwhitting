## Hi there 👋

I am focusing on lower-level systems programming with a specific interest in the Georgia Tech OMSCS Computing Systems track.

### 🚀 Featured Project 1: Concurrency & IPC Performance Benchmark in C
* **Code Location**: [hl_projs/my_timer](https://github.com/dwhitting/c-practice/tree/main/hl_projs/my_timer)
* **The Tool**: Built a custom benchmarking timer (`my_timer_t`) in C to precisely measure CPU execution time of isolated code segments down to the millisecond. (Could go to nanosecond if needed)
* **Core Experiment**: Evaluated the overhead of different Inter-Process Communication (IPC) strategies by summing a dynamically allocated 2D array (**10,000 x 10,000 integers**) across multiple architectures.

#### 📊 Performance Results:
* **Baseline (Single Process):** Sequential execution on a single core. **(The file: arr_sum_single_process.c)**
* **Multi-Process via Disk (`mkstemp()`):** Work divided between a parent and child process and synchronized using a mkstemp() file with locks (`flock`). **Result: ~10ms faster than baseline.** (Multi-core parallel processing power successfully outran the Single Process, even with the physical disk I/O overhead). **(The file: arr_sum_two_process.c)**
* **Multi-Process via Kernel Pipeline (`pipe()`):** Work divided across parent and child, but data is passed back in RAM via a kernel pipe buffer. **Result: ~30ms faster than baseline / ~20ms faster than disk.** **Key Takeaways:** This project demonstrates the power of parallel processing via `fork()`, the efficiency of Linux Copy-on-Write (COW) memory management, and the large performance advantage of memory-space IPC over traditional file-system storage. **(The file: arr_sum_two_process_pipe.c)**
* **Multi-Thread (`10x threads'):** Now added file that divides work among 10x threads.  That halved the time of the Mulit-Process via Kernal Pipline. **(The file: arr_sum_threads.c)**

### 🚀 Featured Project 2: Multi-thread Proxy Server In C
* **Code Location**: [hl_projs/proxy_server](https://github.com/dwhitting/c-practice/tree/7a11c11dc1619835040ce4c2f5aeb760a20c3e1b/hl_projs/proxy_server)
* **Iterative Server Phase:** This is file: **prox_serv_iterative.c**, and it connects with a client (http://www.example.com is the primary practice page during this project), connects to the host the client is seeking, then sends the contents of the remote server page back to the client.
* **Multi-Threaded Proxy Server Phase:** This is file: **prox_serv.threaded.c**, and it spins up a thread for each client request. Terminal shows thread creations and kills to track the various phases of the proxy actions. 
