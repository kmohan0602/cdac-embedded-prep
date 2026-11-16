# Linux & Shell Scripting — Complete Study Guide (Basics to Advanced)
# Read topics IN THIS ORDER

---

## STEP 1: Linux Basics
1. Introduction to Linux, file system hierarchy
   https://www.geeksforgeeks.org/linux-tutorial/

2. Basic Linux Commands (ls, cd, pwd, mkdir, rm, cp, mv, cat)
   https://www.geeksforgeeks.org/basic-linux-commands/

3. File Permissions (chmod, chown, rwx, octal notation)
   https://www.geeksforgeeks.org/linux-file-permissions/

4. Users and Groups
   https://www.geeksforgeeks.org/linux-commands-cheat-sheet/

---

## STEP 2: Processes
Read in this order:

5. Processes in Linux (PID, PPID, process states)
   https://www.geeksforgeeks.org/processes-in-linuxunix/

6. fork() system call — output prediction, process creation
   https://www.geeksforgeeks.org/fork-system-call/

7. Zombie and Orphan Processes
   https://www.geeksforgeeks.org/c/zombie-and-orphan-processes-in-c/

8. exec() family of functions
   https://www.geeksforgeeks.org/exec-family-of-functions-in-c/

9. wait() and waitpid()
   https://www.geeksforgeeks.org/wait-system-call-in-c/

10. fork() + pipe() combined example
    https://www.geeksforgeeks.org/c/c-program-demonstrate-fork-and-pipe/

---

## STEP 3: Signals
11. Signals in Linux (SIGKILL, SIGTERM, SIGCHLD, SIGSEGV)
    https://www.geeksforgeeks.org/c/signals-c-language/

12. signal() and kill() functions
    https://www.geeksforgeeks.org/signals-c-language/

    Must know:
    - SIGKILL (9)  — cannot be caught, blocked, or ignored
    - SIGTERM (15) — can be caught (graceful shutdown)
    - Ctrl+C sends SIGINT
    - Ctrl+Z sends SIGTSTP

---

## STEP 4: IPC (Inter-Process Communication)
Read in this order:

13. IPC overview — all mechanisms
    https://www.geeksforgeeks.org/operating-systems/inter-process-communication-ipc/

14. Pipes in Linux
    https://www.geeksforgeeks.org/pipe-system-call/

15. Named Pipes / FIFO
    https://www.geeksforgeeks.org/named-pipe-fifo-example-c-program/

16. Shared Memory (shmget, shmat, shmdt)
    https://www.geeksforgeeks.org/shared-memory-unixlinux/

17. Message Queues
    https://www.geeksforgeeks.org/ipc-using-message-queues/

18. Semaphores (System V)
    https://www.geeksforgeeks.org/semaphores-in-process-synchronization/

    Must know which is fastest: Shared Memory (no kernel copy)

---

## STEP 5: Shell Scripting
Read in this order:

19. Shell Scripting basics (shebang, variables, echo)
    https://www.geeksforgeeks.org/introduction-linux-shell-shell-scripting/

20. Shell Variables ($?, $#, $@, $0, $1)
    https://www.geeksforgeeks.org/shell-script-special-variables/

21. if/else, for, while in shell
    https://www.geeksforgeeks.org/conditional-statements-shell-script/

22. Functions in Shell Script
    https://www.geeksforgeeks.org/functions-in-shell-scripting/

---

## STEP 6: Useful Diagnostic Commands
23. ps, top, kill, strace, ldd — what each does
    https://www.geeksforgeeks.org/ps-command-in-linux-with-examples/
    https://www.geeksforgeeks.org/strace-command-in-linux-with-examples/
    https://www.geeksforgeeks.org/ldd-command-in-linux-with-examples/

---

## Practice Links

IndiaBIX Linux MCQs:
- https://www.indiabix.com/linux/questions-and-answers/

Jacob Sorber YouTube (Linux C programming — fork, exec, signals):
- https://www.youtube.com/@JacobSorber/videos

---

## Study Schedule for Linux (5 days)

| Day | Steps | Topics |
|-----|-------|--------|
| 1   | 1     | Linux basics, commands, file permissions |
| 2   | 2     | Processes — fork(), zombie, orphan, exec(), wait() |
| 3   | 3     | Signals — SIGKILL, SIGTERM, Ctrl+C, Ctrl+Z |
| 4   | 4     | IPC — pipes, named pipes, shared memory, message queues |
| 5   | 5–6   | Shell scripting + diagnostic commands |
