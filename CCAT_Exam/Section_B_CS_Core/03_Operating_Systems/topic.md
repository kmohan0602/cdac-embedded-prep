# Topic: Operating Systems — Complete CCAT Level
# Section B — CS Core

---

## Study Order (follow exactly)

---

### STEP 1: OS Basics
Read: https://www.geeksforgeeks.org/operating-systems/introduction-of-operating-system-set-1/

Must know:
- OS is resource manager + hardware abstraction layer
- Types: Batch, Time-sharing, Real-time, Distributed
- Kernel: core of OS, runs in privileged mode
- System call: interface between user program and OS

---

### STEP 2: Process and Process States
Read: https://www.geeksforgeeks.org/operating-systems/states-of-a-process-in-operating-systems/
Read: https://www.geeksforgeeks.org/operating-systems/difference-between-process-and-thread/

Must know 5 process states:
- New → Ready → Running → Waiting → Terminated

Must know Process vs Thread:
| Process | Thread |
|---------|--------|
| Independent memory | Shared memory within process |
| Expensive to create | Lightweight |
| IPC needed to communicate | Communicate via shared memory |
| Crash doesn't affect others | Crash can affect whole process |

PCB (Process Control Block): stores PID, state, PC, registers, memory info

---

### STEP 3: CPU Scheduling Algorithms
Read: https://www.geeksforgeeks.org/operating-systems/cpu-scheduling-in-operating-systems/

Must know all 6 algorithms:

| Algorithm | Type | Key Property |
|-----------|------|--------------|
| FCFS | Non-preemptive | First come first served, convoy effect |
| SJF | Non-preemptive | Shortest job first, min avg waiting time |
| SRTF | Preemptive | Shortest remaining time, preempts on arrival |
| Round Robin | Preemptive | Time quantum, fair, best for time-sharing |
| Priority | Both | Higher priority runs first, starvation possible |
| Multilevel Queue | Preemptive | Multiple queues for different process types |

Key terms:
- Turnaround time = Completion - Arrival
- Waiting time = Turnaround - Burst
- Response time = First CPU time - Arrival
- Throughput = processes completed per unit time

Practice questions: Calculate waiting time and turnaround time from Gantt chart

Read: https://www.geeksforgeeks.org/operating-systems/process-schedulers-in-operating-system/

---

### STEP 4: Memory Management
Read: https://www.geeksforgeeks.org/operating-systems/memory-management-in-operating-system/
Read: https://www.geeksforgeeks.org/operating-systems/virtual-memory-in-operating-system/
Read: https://www.geeksforgeeks.org/operating-systems/page-replacement-algorithms-in-operating-systems/

Must know:
- Paging: divide memory into fixed-size pages; eliminates external fragmentation
- Segmentation: divide into variable-size segments; eliminates internal fragmentation
- Virtual memory: allows process to use more memory than physically available
- Page fault: page not in RAM, fetched from disk (slow)

Page replacement algorithms:
| Algorithm | Key Rule |
|-----------|----------|
| FIFO | Replace page that came in earliest |
| LRU | Replace page least recently used |
| Optimal | Replace page not used for longest future time (theoretical) |

Belady's anomaly: FIFO can have MORE page faults with MORE frames (LRU doesn't have this)

---

### STEP 5: Deadlock
Read: https://www.geeksforgeeks.org/operating-systems/introduction-of-deadlock-in-operating-system/
Read: https://www.geeksforgeeks.org/operating-systems/bankers-algorithm-in-operating-system-2/

Must know 4 Coffman conditions (ALL must hold for deadlock):
1. Mutual Exclusion — resource non-shareable
2. Hold and Wait — holding one, waiting for another
3. No Preemption — resource cannot be taken forcibly
4. Circular Wait — A waits for B, B waits for A

Prevention: break any one condition
Detection: resource allocation graph
Recovery: process termination or resource preemption

Banker's Algorithm: deadlock avoidance — safe state check

---

### STEP 6: Synchronization
Read: https://www.geeksforgeeks.org/operating-systems/mutex-vs-semaphore/
Read: https://www.geeksforgeeks.org/operating-systems/g-fact-70/

Must know:
- Critical section: code accessing shared resource
- Mutual exclusion: only one process in critical section at a time
- Mutex: ownership-based lock (only owner can unlock)
- Semaphore: integer, no ownership, any process can signal
- Binary semaphore: 0 or 1, similar to mutex but no ownership
- Counting semaphore: 0 to N, for multiple resource instances

---

## Practice Links

IndiaBIX OS:
https://www.indiabix.com/operating-systems/questions-and-answers/

Neso Academy OS playlist (YouTube):
https://www.youtube.com/playlist?list=PLBlnK6fEyqRiVhbXDGLXDk_OQAeuVcp2O

GFG OS Quiz:
https://www.geeksforgeeks.org/quiz-on-operating-systems/

---

## Daily Target
- Scheduling: practice Gantt chart calculations (5 per day)
- Do 15 OS MCQs on IndiaBIX
