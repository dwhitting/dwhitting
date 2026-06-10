## Hi there 👋

I am focusing on lower-level systems programming with a specific interest in the Georgia Tech OMSCS Computing Systems track.

### 🚀 Featured Project: Concurrency & IPC Performance Benchmark
* **Code Location**: [hl_projs/my_timer](https://github.com/dwhitting/c-practice/tree/main/hl_projs/my_timer)
* **The Tool**: Built a custom benchmarking timer (`my_timer_t`) in C to precisely measure CPU execution time of isolated code segments down to the millisecond. (Could go to nanosecond if needed)
* **Core Experiment**: Evaluated the overhead of different Inter-Process Communication (IPC) strategies by summing a dynamically allocated 2D array (**10,000 x 10,000 integers**) across multiple architectures.

#### 📊 Performance Results:
* **Baseline (Single Process):** Sequential execution on a single core.
* **Multi-Process via Disk (`mkstemp()`):** Work divided between a parent and child process and synchronized using a mkstemp() file with locks (`flock`). **Result: ~10ms faster than baseline.** (Multi-core parallel processing power successfully outran the Single Process, even with the physical disk I/O overhead).
* **Multi-Process via Kernel Pipeline (`pipe()`):** Work divided across parent and child, but data is passed back in RAM via a kernel pipe buffer. **Result: ~30ms faster than baseline / ~20ms faster than disk.** **Key Takeaways:** This project demonstrates the power of parallel processing via `fork()`, the efficiency of Linux Copy-on-Write (COW) memory management, and the large performance advantage of memory-space IPC over traditional file-system storage.
