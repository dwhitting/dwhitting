## Hi there 👋

I am focusing on lower-level programming with an interest in the OMSCS computing systems track.

Featured Projects:
  1. **Location**: [hl_projs/my_timer](https://github.com/dwhitting/c-practice/tree/main/hl_projs/my_timer)
    - **Aside**:This project has a custom timer I made to measure how long processes (or portions of them) take
      to execute. (The my_timer_t type in the my_timer files has and explains this.)
    - **Main Point of Project**: To measure the time it takes to sum a large dynamic memory array
      (1000x1000), first with a single process, and second with the summing done in two chunks split
      between a parent and child process (two-process sum).
    - **Results**: The two-process sum is always faster. Though only by about 10 milliseconds each time, the two-process
      has some temp- file writes (and flock()s) within the timed process that also slows it down, so I suspect
      the two-process sums much faster. Next I plan to use a Pipe to pass the data instead of a temp-file to see how
      much that speeds it up.
     
