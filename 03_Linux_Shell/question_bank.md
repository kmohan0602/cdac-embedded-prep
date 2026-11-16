# Module 3: Linux & Shell Scripting — Question Bank + Study Guide

## Where to Study
| Resource | URL |
|---|---|
| Sanfoundry Linux MCQs | https://www.sanfoundry.com/linux-questions-answers/ |
| GeeksforGeeks Linux | https://www.geeksforgeeks.org/linux-unix/ |
| Jacob Sorber (YouTube) | Linux C programming, fork, exec, signals |
| TLPI Book (The Linux Programming Interface) | Deep reference — Kerrisk |

---

## Topic 1: Process Management (fork, exec, wait)

### Must Know
- `fork()` → creates child process, returns PID to parent, 0 to child
- `exec()` → replaces current process image
- `wait()` → parent waits for child to finish
- Zombie process → child exited, parent hasn't called `wait()`
- Orphan process → parent exited before child; adopted by `init` (PID 1)

### Question Bank

**Q1.** What is the output?
```c
int main() {
    fork();
    fork();
    printf("Hello\n");
    return 0;
}
```
**Answer:** `Hello` printed **4 times** (2² = 4 processes)

---

**Q2.** What is the output?
```c
int main() {
    int x = 5;
    if (fork() == 0) {
        x = 10;
        printf("Child: %d\n", x);
    } else {
        printf("Parent: %d\n", x);
    }
}
```
**Answer:**
```
Child: 10
Parent: 5
```
(Each process has its own copy — fork copies memory)

---

**Q3.** What is a zombie process? How to prevent it?
**Answer:** A process that has finished execution but its entry still exists in the process table because the parent hasn't called `wait()`. Prevent by: calling `wait()`/`waitpid()` in parent, or using `SIGCHLD` signal handler.

---

**Q4.** Difference between `fork()` and `vfork()`?
**Answer:**
- `fork()` → copies parent's address space (copy-on-write)
- `vfork()` → child shares parent's address space, parent is suspended until child calls `exec()` or `_exit()`. Faster but dangerous.

---

## Topic 2: Signals

### Must Know
- `SIGKILL` (9) — cannot be caught, blocked, or ignored
- `SIGTERM` (15) — graceful termination, can be caught
- `SIGCHLD` — sent to parent when child terminates
- `SIGSEGV` — segmentation fault
- `SIGALRM` — alarm timer expired
- `kill(pid, sig)` — send signal to process
- `signal(SIGINT, handler)` — register signal handler

### Question Bank

**Q5.** Which signal cannot be caught or ignored?
**Answer:** `SIGKILL` (9) and `SIGSTOP`

**Q6.** What happens when you press Ctrl+C in terminal?
**Answer:** `SIGINT` is sent to the foreground process group.

**Q7.** What is the difference between `kill -9` and `kill -15`?
**Answer:**
- `kill -15` (SIGTERM): asks process to terminate gracefully; can be caught/ignored
- `kill -9` (SIGKILL): forces immediate termination; cannot be caught

---

## Topic 3: IPC (Inter-Process Communication)

| Mechanism | Key Points |
|---|---|
| Pipe `pipe()` | Unidirectional, related processes (parent-child) |
| Named Pipe (FIFO) | Unidirectional, unrelated processes, exists in filesystem |
| Shared Memory | Fastest IPC, needs synchronization (semaphore/mutex) |
| Message Queue | Structured messages, FIFO order, kernel managed |
| Semaphore | Synchronization, not data transfer |
| Socket | Network or local IPC, bidirectional |

**Q8.** Which IPC mechanism is fastest and why?
**Answer:** Shared memory — data is not copied between kernel and user space; processes directly access the same memory region.

**Q9.** What is the limitation of a regular pipe?
**Answer:** Only works between related processes (parent-child, siblings from same parent). Unidirectional. Use named pipe (FIFO) for unrelated processes.

---

## Topic 4: File Permissions & Commands

**Q10.** What does `chmod 755 file.sh` mean?
**Answer:**
- Owner: `7` = read(4) + write(2) + execute(1) = rwx
- Group: `5` = read(4) + execute(1) = r-x
- Others: `5` = r-x

**Q11.** What does `ls -la` show that `ls` doesn't?
**Answer:** `-l` = long format (permissions, owner, size, date), `-a` = hidden files (starting with `.`)

**Q12.** Useful diagnostic commands:
- `ps aux` → all running processes
- `top` / `htop` → real-time process monitor
- `strace ./prog` → trace system calls made by program
- `ldd binary` → list shared libraries
- `netstat -tulnp` → open network ports
- `dmesg` → kernel ring buffer (hardware events, boot messages)

---

## Topic 5: Shell Scripting

**Q13.** Write a script to print numbers 1 to 10.
```bash
#!/bin/bash
for i in $(seq 1 10); do
    echo $i
done
```

**Q14.** What is `$?`, `$#`, `$@`, `$0`?
- `$?` → exit status of last command (0 = success)
- `$#` → number of arguments passed to script
- `$@` → all arguments as separate words
- `$0` → script name itself

**Q15.** What does this do?
```bash
find . -name "*.c" | xargs grep "malloc"
```
**Answer:** Finds all `.c` files in current directory and searches for the word "malloc" in them.

---

## Checklist Before Exam
- [ ] `fork()` output prediction (how many processes/prints)
- [ ] Zombie vs Orphan process
- [ ] SIGKILL vs SIGTERM
- [ ] 5 IPC types and when to use each
- [ ] Shared memory is fastest IPC
- [ ] `chmod` octal notation
- [ ] `$?` `$#` `$@` meanings
- [ ] `ps`, `top`, `strace`, `ldd` — what they do
- [ ] Pipe vs Named Pipe
