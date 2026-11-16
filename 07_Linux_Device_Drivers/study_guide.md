# Linux Device Drivers — Complete Study Guide (Basics to Advanced)
# Read topics IN THIS ORDER

---

## STEP 1: Linux Kernel Basics
1. Linux Kernel overview — what it does
   https://www.geeksforgeeks.org/the-linux-kernel/

2. Kernel Space vs User Space
   https://www.geeksforgeeks.org/user-space-and-kernel-space/

   Must know:
   - Kernel space: privileged mode, direct hardware access
   - User space: restricted, accesses hardware only via system calls
   - Buffer copy needed between them (copy_to_user, copy_from_user)

3. System Calls — how user space talks to kernel
   https://www.geeksforgeeks.org/introduction-of-system-call/

---

## STEP 2: Loadable Kernel Modules (LKM)
4. Linux Kernel Module basics
   https://www.geeksforgeeks.org/linux-kernel-module-programming-hello-world-program/

   Minimal module structure:
   #include <linux/init.h>
   #include <linux/module.h>
   static int __init my_init(void) { printk("loaded\n"); return 0; }
   static void __exit my_exit(void) { printk("removed\n"); }
   module_init(my_init);
   module_exit(my_exit);
   MODULE_LICENSE("GPL");

5. Module commands — must memorize all 5:
   insmod module.ko   — load module
   rmmod module       — remove module
   lsmod              — list loaded modules
   modinfo module.ko  — show module info
   dmesg              — view kernel log (printk output)

6. Why printk and not printf?
   https://www.geeksforgeeks.org/printk-and-dmesg/
   Answer: Kernel cannot use libc. printk is kernel's own logging.

---

## STEP 3: Character Device Driver
7. Character Device Driver tutorial (full walkthrough)
   https://www.geeksforgeeks.org/character-device-driver/

8. file_operations structure
   https://www.geeksforgeeks.org/file-operations-structure-in-linux-device-driver/

   Must know all 5 function pointers:
   .open    — called when device file is opened
   .read    — called on read() system call
   .write   — called on write() system call
   .release — called when device file is closed
   .unlocked_ioctl — called on ioctl() system call

9. Major and Minor Numbers
   https://www.geeksforgeeks.org/major-and-minor-numbers-in-linux/

   Must know:
   - Major number → identifies the DRIVER
   - Minor number → identifies the specific DEVICE INSTANCE
   - alloc_chrdev_region() → dynamic major number allocation (preferred)
   - register_chrdev() → static allocation

---

## STEP 4: copy_to_user / copy_from_user — IMPORTANT
10. copy_to_user and copy_from_user
    https://www.geeksforgeeks.org/copy-to-user-and-copy-from-user-in-linux-kernel/

    Must know WHY they are needed:
    - User-space pointer may not be mapped
    - User pointer could be invalid or malicious
    - Protects kernel from faults caused by bad user pointers

    In read() driver function  → copy_to_user(user_buf, kernel_buf, count)
    In write() driver function → copy_from_user(kernel_buf, user_buf, count)

---

## STEP 5: /proc, /sys, /dev
11. Linux /proc filesystem
    https://www.geeksforgeeks.org/proc-file-system-linux/

12. Linux sysfs (/sys)
    https://www.geeksforgeeks.org/sysfs-file-system-in-linux/

    Must know differences:
    /dev  → device files, interface to hardware drivers
    /proc → virtual FS, process info, kernel params (read-mostly)
    /sys  → kernel objects, device attributes, driver parameters

---

## STEP 6: Interrupt Handling in Drivers
13. Interrupt handling in Linux kernel
    https://www.geeksforgeeks.org/linux-kernel-interrupt-handling/

    Must know the two functions:
    request_irq(irq, handler, flags, name, dev_id) — register handler
    free_irq(irq, dev_id)                          — unregister handler

    Must know: dev_id must match between request_irq and free_irq
    (needed to identify which handler to remove on shared IRQs)

---

## STEP 7: Tasklet vs Workqueue — IMPORTANT
14. Bottom Halves in Linux — Tasklets and Workqueues
    https://www.geeksforgeeks.org/tasklets-and-work-queues-in-linux-kernel/

    Must know this difference:
    | Feature     | Tasklet              | Workqueue               |
    |-------------|----------------------|-------------------------|
    | Context     | Atomic (softirq)     | Process context         |
    | Can sleep   | NO                   | YES                     |
    | Use when    | Fast, non-blocking   | Needs sleep/mutex/I/O   |

---

## STEP 8: ioctl
15. ioctl in Linux device drivers
    https://www.geeksforgeeks.org/ioctl-in-linux/

    Must know:
    - Used for device-specific commands not covered by read/write
    - Examples: set baud rate, get sensor calibration, set LED brightness
    - Defined in driver's file_operations as .unlocked_ioctl

---

## STEP 9: Platform Driver
16. Platform Driver in Linux
    https://www.geeksforgeeks.org/platform-devices-and-drivers/

    Must know:
    - For on-chip/hardwired devices (no auto-discovery)
    - Device info comes from Device Tree or board file
    - Contrast: PCI driver = auto-discoverable via PCI ID

---

## STEP 10: LDD3 Book (Best Free Resource)
17. Linux Device Drivers 3rd Edition — FREE online
    https://lwn.net/Kernel/LDD3/

    Chapters to focus on:
    - Chapter 2: Building and Running Modules
    - Chapter 3: Char Drivers
    - Chapter 10: Interrupt Handling

---

## Practice Links

Sanfoundry Linux Device Driver MCQs:
- https://www.sanfoundry.com/linux-device-driver-questions-answers/

The Linux Foundation free training (LFD103):
- https://training.linuxfoundation.org/training/a-beginners-guide-to-linux-kernel-development-lfd103/

---

## Study Schedule for Linux Device Drivers (5 days)

| Day | Steps  | Topics |
|-----|--------|--------|
| 1   | 1–2    | Kernel vs user space, LKM, module commands |
| 2   | 3      | Character device driver, file_operations, major/minor |
| 3   | 4–5    | copy_to_user/from_user, /dev /proc /sys |
| 4   | 6–8    | Interrupt handling, tasklet vs workqueue, ioctl |
| 5   | 9–10   | Platform driver + LDD3 chapters + Sanfoundry practice |
