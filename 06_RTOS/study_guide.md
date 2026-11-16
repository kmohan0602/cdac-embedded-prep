# RTOS — Complete Study Guide (Basics to Advanced)
# Read topics IN THIS ORDER

---

## STEP 1: What is an RTOS
1. Introduction to RTOS — Hard, Soft, Firm real-time
   https://www.geeksforgeeks.org/real-time-operating-system-rtos/

2. RTOS vs General Purpose OS differences
   https://www.geeksforgeeks.org/difference-between-rtos-and-gpos/

   Must know:
   - RTOS has deterministic, bounded response time
   - GPOS (Linux, Windows) prioritizes throughput, not deadlines
   - Embedded systems use RTOS for predictability

---

## STEP 2: Tasks and States
3. Task / Thread concept in RTOS
   https://www.geeksforgeeks.org/task-management-in-rtos/

   Must know all 4 states:
   - Ready    → waiting for CPU, all resources available
   - Running  → currently executing on CPU
   - Blocked  → waiting for event (delay, semaphore, queue)
   - Suspended → explicitly suspended, will not run until resumed

---

## STEP 3: Scheduling
4. CPU Scheduling basics
   https://www.geeksforgeeks.org/operating-systems/cpu-scheduling-in-operating-systems/

5. Preemptive vs Non-preemptive (Cooperative) Scheduling
   https://www.geeksforgeeks.org/preemptive-and-non-preemptive-scheduling/

6. Priority-Based Scheduling
   https://www.geeksforgeeks.org/priority-scheduling-in-operating-system/

7. Round Robin Scheduling
   https://www.geeksforgeeks.org/program-for-round-robin-scheduling-for-the-same-arrival-time/

   Must know:
   - Preemptive: higher priority task immediately takes CPU
   - Cooperative: task must yield voluntarily
   - Round-robin: equal priority tasks share CPU in time slices

---

## STEP 4: Semaphore and Mutex — MOST IMPORTANT TOPIC
8. Semaphore in OS
   https://www.geeksforgeeks.org/semaphores-in-process-synchronization/

9. Mutex vs Semaphore — exact differences
   https://www.geeksforgeeks.org/operating-systems/mutex-vs-semaphore/

   Must know this table:
   | Feature       | Semaphore                  | Mutex                        |
   |---------------|----------------------------|------------------------------|
   | Ownership     | No owner                   | Has owner (task that locked) |
   | Release by    | Any task or ISR            | Only owner task              |
   | Use case      | Signaling, resource count  | Mutual exclusion             |
   | Types         | Binary, Counting           | Recursive mutex              |
   | Priority inh. | No                         | Yes                          |

---

## STEP 5: Priority Inversion — VERY IMPORTANT
10. Priority Inversion in OS
    https://www.geeksforgeeks.org/operating-systems/priority-inversion/

11. Priority Inheritance protocol
    https://www.geeksforgeeks.org/priority-inheritance/

    Must know scenario:
    - Task H (high) waits for mutex held by Task L (low)
    - Task M (medium) preempts Task L
    - Task H is indirectly blocked by Task M → Priority Inversion
    - Fix: L temporarily inherits H's priority → M cannot preempt L

---

## STEP 6: Deadlock
12. Introduction to Deadlock
    https://www.geeksforgeeks.org/operating-systems/introduction-of-deadlock-in-operating-system/

13. Deadlock Prevention
    https://www.geeksforgeeks.org/deadlock-prevention/

    Must know 4 Coffman conditions (all must be true for deadlock):
    1. Mutual Exclusion — resource not shareable
    2. Hold and Wait — holding one, waiting for another
    3. No Preemption — resource cannot be forcibly taken
    4. Circular Wait — circular chain of waiting

    Prevention: always acquire mutexes in the same fixed order (breaks circular wait)

---

## STEP 7: Message Queues
14. Message Queue in OS
    https://www.geeksforgeeks.org/ipc-using-message-queues/

15. Producer-Consumer problem
    https://www.geeksforgeeks.org/producer-consumer-problem-using-semaphores-set-1/

    Must know:
    - Queue transfers actual data (unlike semaphore which just signals)
    - FIFO order
    - Used for ISR → task data handoff

---

## STEP 8: FreeRTOS (Most popular RTOS for embedded)
16. FreeRTOS official book (FREE PDF — best resource)
    https://www.freertos.org/Documentation/RTOS_book.html

17. FreeRTOS task creation and management
    https://www.freertos.org/a00019.html

18. FreeRTOS semaphore/mutex API
    https://www.freertos.org/a00113.html

19. FreeRTOS queue API
    https://www.freertos.org/a00018.html

    Key APIs to memorize:
    xTaskCreate()          — create a task
    vTaskDelay(ticks)      — block for N ticks
    xSemaphoreCreateMutex() — create mutex
    xSemaphoreTake()       — lock/wait
    xSemaphoreGive()       — release
    xQueueCreate()         — create queue
    xQueueSend()           — send to queue
    xQueueReceive()        — receive from queue

---

## STEP 9: Stack Overflow Detection
20. Stack overflow in embedded/RTOS
    https://www.geeksforgeeks.org/stack-overflow-in-os/

    FreeRTOS methods:
    - Method 1: Check SP at context switch
    - Method 2: Fill stack with pattern (0xA5), check if corrupted

---

## Practice Links

Sanfoundry RTOS MCQs (1000 questions):
- https://www.sanfoundry.com/rtos-questions-answers/

Fastbit EBA FreeRTOS on STM32 (YouTube):
- https://www.youtube.com/c/FastbitEBA/playlists

FreeRTOS official getting started:
- https://www.freertos.org/FreeRTOS-quick-start-guide.html

---

## Study Schedule for RTOS (6 days)

| Day | Steps  | Topics |
|-----|--------|--------|
| 1   | 1–2    | RTOS intro, task states |
| 2   | 3      | Scheduling — preemptive, cooperative, round-robin |
| 3   | 4      | Semaphore vs Mutex — study the difference table deeply |
| 4   | 5–6    | Priority inversion + deadlock (4 conditions) |
| 5   | 7–8    | Message queues + FreeRTOS APIs |
| 6   | 9 + practice | Stack overflow + full Sanfoundry MCQ practice |
