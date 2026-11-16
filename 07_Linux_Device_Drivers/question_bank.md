# Module 7: Linux Device Drivers — Question Bank + Study Guide

## Where to Study
| Resource | URL |
|---|---|
| Sanfoundry LDD MCQs | https://www.sanfoundry.com/linux-device-driver-questions-answers/ |
| LDD3 Book (FREE PDF) | https://lwn.net/Kernel/LDD3/ |
| The Linux Foundation (YouTube) | Linux kernel internals |
| GeeksforGeeks Linux Driver | https://www.geeksforgeeks.org/linux-device-driver-tutorial/ |

---

## Topic 1: Kernel Module Basics

**Q1.** Write a minimal Linux kernel module.
```c
#include <linux/init.h>
#include <linux/module.h>

static int __init my_init(void) {
    printk(KERN_INFO "Module loaded\n");
    return 0;
}

static void __exit my_exit(void) {
    printk(KERN_INFO "Module removed\n");
}

module_init(my_init);
module_exit(my_exit);
MODULE_LICENSE("GPL");
```

**Q2.** Commands for kernel modules:
| Command | Purpose |
|---|---|
| `insmod module.ko` | Insert (load) kernel module |
| `rmmod module` | Remove (unload) kernel module |
| `lsmod` | List currently loaded modules |
| `modinfo module.ko` | Show module information |
| `dmesg` | View kernel log (printk output) |

**Q3.** Why use `printk` instead of `printf` in kernel?
**Answer:** Kernel code cannot use C library (`libc`). `printk` is the kernel's own logging function. It supports log levels: `KERN_ERR`, `KERN_WARNING`, `KERN_INFO`, `KERN_DEBUG`.

---

## Topic 2: Character Device Driver

**Q4.** What is the `file_operations` structure?
**Answer:** Kernel structure that maps system calls (`open`, `read`, `write`, `ioctl`, `release`) to driver functions.

```c
static struct file_operations my_fops = {
    .owner   = THIS_MODULE,
    .open    = my_open,
    .read    = my_read,
    .write   = my_write,
    .release = my_release,
};
```

**Q5.** What are major and minor numbers?
**Answer:**
- **Major number:** Identifies the driver (e.g., 4 = TTY serial driver)
- **Minor number:** Identifies the specific device instance (e.g., ttyS0, ttyS1)
- `ls -l /dev/ttyS0` → `crw-rw---- 1 root 4, 64` — major=4, minor=64

**Q6.** How to register a character device?
```c
// Static allocation
register_chrdev(major, "mydev", &my_fops);

// Dynamic allocation (preferred)
alloc_chrdev_region(&dev, 0, 1, "mydev");
```

---

## Topic 3: copy_to_user / copy_from_user (IMPORTANT)

**Q7.** Why can't kernel directly access user-space pointers?
**Answer:**
1. User-space address may not be mapped (page fault would crash kernel)
2. User pointer may be invalid/malicious
3. Different virtual address spaces

**Q8.** What do `copy_to_user` and `copy_from_user` do?
```c
// In read() — sending data TO user space
copy_to_user(user_buf, kernel_buf, count);

// In write() — receiving data FROM user space
copy_from_user(kernel_buf, user_buf, count);
```
They safely copy data across the kernel/user boundary with proper validation.

---

## Topic 4: /proc, /sys, /dev

**Q9.** Difference between `/dev`, `/proc`, `/sys`:
| Directory | Purpose |
|---|---|
| `/dev` | Device files — interface to hardware drivers |
| `/proc` | Virtual filesystem — process info, kernel parameters (read-mostly) |
| `/sys` | Sysfs — kernel objects, device attributes, driver parameters |

**Q10.** How to read CPU info on Linux?
**Answer:** `cat /proc/cpuinfo`

---

## Topic 5: Interrupt Handling in Drivers

**Q11.** How to register an interrupt handler in a driver?
```c
// Register
request_irq(irq_number, my_irq_handler, IRQF_SHARED, "mydev", dev_id);

// Handler
irqreturn_t my_irq_handler(int irq, void *dev_id) {
    // Handle interrupt
    return IRQ_HANDLED;
}

// Free on exit
free_irq(irq_number, dev_id);
```

---

## Topic 6: Tasklet vs Workqueue

**Q12.** What is the difference between tasklet and workqueue?
| Feature | Tasklet | Workqueue |
|---|---|---|
| Context | Atomic (interrupt context) | Process context (can sleep) |
| Can sleep | NO | YES |
| Priority | High (softirq level) | Normal process priority |
| Use case | Fast, non-sleeping ISR bottom half | Slower work needing sleep/blocking |

**Rule:** If your deferred work needs to sleep (wait for I/O, `msleep`, mutex) → use workqueue. Otherwise → tasklet.

---

## Topic 7: ioctl

**Q13.** What is `ioctl` and why is it used?
**Answer:** `ioctl` (I/O Control) allows user-space to send device-specific commands that don't fit `read`/`write`. Examples:
- Set baud rate on serial port
- Get sensor calibration value
- Set LED brightness

```c
// User space
ioctl(fd, MY_IOCTL_SET_BAUD, 115200);

// Kernel driver
long my_ioctl(struct file *f, unsigned int cmd, unsigned long arg) {
    switch (cmd) {
        case MY_IOCTL_SET_BAUD:
            baud_rate = arg;
            break;
    }
    return 0;
}
```

---

## Topic 8: Platform Driver

**Q14.** What is a platform driver? How is it different from PCI driver?
**Answer:**
- **Platform driver:** For devices on-chip or hardwired on the board (no auto-discovery). Device info comes from Device Tree or board file.
- **PCI driver:** For devices on PCI bus — auto-discoverable via PCI ID

Embedded systems mostly use platform drivers since peripherals (UART, SPI, I2C controllers) are on-chip.

---

## Checklist Before Exam
- [ ] `module_init` / `module_exit` — lifecycle
- [ ] `insmod`, `rmmod`, `lsmod`, `dmesg`
- [ ] `file_operations` — 5 function pointers
- [ ] Major = driver, Minor = device instance
- [ ] `copy_to_user` / `copy_from_user` — why needed
- [ ] `/dev` vs `/proc` vs `/sys`
- [ ] `request_irq` / `free_irq`
- [ ] Tasklet = atomic (no sleep), Workqueue = can sleep
- [ ] `ioctl` — device-specific commands
- [ ] Platform driver = on-chip, no auto-discovery
