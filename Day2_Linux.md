# 🐧 Intro to Linux

- Linux is a **kernel**.
- Linux has OS properties because OS means the combination of kernel and software.
- The **kernel** is the bridge between software and hardware — it connects/communicates software and hardware and allocates resources.

---

## 📜 History of Linux

- In 1969, **Ken Thompson** and **Dennis Ritchie** created **Unix**. Unix is not open source, meaning you have to pay to use it.
- Then the **Linux kernel** was discovered by **Linus Torvalds**. He made it open source, and it was written using the **C language**.
- As mentioned before, Linux is just a kernel, so to turn it into a full OS system, **Richard Stallman** announced the **GNU Project** in 1983 and created free software in 1985. It is open source too — so now there are 2 free things that together create an OS system:

> **GNU + Linux = GNU/Linux OS**

---

## 🐚 Shell

The **shell** is the mediator between the user and the kernel — the user uses the shell to communicate with the kernel. We can say the shell is a **command line interpreter**.

### Types of Shell

- There are 500+ shells, but we'll look at only a few of them.
- Shells differ based on: **piping** (where the text starts), **coloring**, and **command completion** (some shells finish the command automatically when you start typing, e.g. by pressing the Tab key).

**1. sh**
- Piping: there is no Tab completion, the text starts at the corner.
- Color: uses a black background with white text.

**2. bash**
- It is colorful.
- It is installed by default when you install any Linux system.

> ⚡ **bash** and **zsh** look similar because of their color and piping, but they differ in command completion.

- 🔎 To know which shell you're using, run: `echo $SHELL`
- 🖥️ The Linux shell is also called the **terminal**.
- 🪟 The Windows shell is also called **CMD**, but nowadays it's called **PowerShell**.

---

## 💻 OS (Operating System)

The **OS** is the mediator between the user and the hardware at the top level, and at the low level, it is a good resource allocator.

It contains:
- **Kernel** — the core part of the OS, as mentioned before, the bridge between HW and SW
- **Software (SW)** — different software applications like PDF readers, browsers like Chrome, etc., that instruct the HW how to perform
- **Desktop Environment (Desk Env)** — the graphical user interface that helps the user interact with the OS, like the login page, taskbar, background, and everything you see when the OS boots

### Types of Desktop Environment

Choice depends on your PC's performance, quality, graphics, animation, and personal preference.

1. **Mate**
2. **GNOME** — the most beautiful one, uses animation
3. **KDE Plasma**
4. **XFCE**

- **File extension**
- **Window manager**

**i3 window manager** — when you use this, you do everything without a mouse, using only the keyboard, so you must know the shortcuts to use it. It's usually used if your PC's performance is low.

### Why Linux?

1. It's one of the most used systems because Linux gives you a choice — if your PC is low performance, use a lightweight option, otherwise use a heavier one.
2. It has the most hacking tools.
3. It's the most secure because it's not controlled by a central power, and even more malware is developed for Windows, not Linux.

---

## 📦 Linux Distributions (Distro)

Distros mean modified Linux kernels — types of OS with different:

1. Linux kernel
2. Packages (GNU)
3. Package manager
4. Desktop UI

There are 600+ distros, but we'll look at a few of them.

**1. Debian** — the first modification of Linux. From Debian, other distros were also created:
- Kali Linux
- Parrot OS
- Ubuntu

All of these are beginner-friendly distros.
> Debian uses the **apt** package manager.

**2. Arch**
- BlackArch
- Garuda

These are harder for beginners.
> Arch uses the **pacman** package manager.

**3. Red Hat**
**4. Gentoo**
**5. Android**

> 🎯 Kali Linux, Parrot, Garuda, BlackArch, etc. are the best distros for hackers.

### Kali Linux
- Designed for **digital forensics** (used by the blue team to investigate cyber attacks) and **penetration testing**.
- Maintained and funded by **Offensive Security**.
- Desktop Env: **XFCE** (default)
- Package Manager: **apt** (default)
- Shell: **zsh** (default)
- Used by hackers

### Parrot OS
- Focused on security, privacy, and development.
- Used by both hackers and developers.
- Desktop Env: **MATE** (default)
- Package Manager: **apt** (default)
- Shell: **bash** (default)

### Garuda
- Desktop Env: **KDE Plasma**
- Package Manager: **pacman**
- Shell: **fish**

> 🪟 Windows doesn't have distros because it's not open source, so people can't modify it — it just gets updates and added features.

---

## 🛠️ How Can We Use Kali Linux or Other Hacker OS?

### 1. Main OS / Main Boot
Kali Linux installed as the sole OS on the machine.

**Advantages**
- High performance
- Security
- Simplicity

**Disadvantages**
- Only access to Kali Linux OS
- Changing from Windows or another OS to Kali causes data loss

### 2. Dual Boot / 2-in-1
Use both OS systems on one PC.

**Advantages**
- Access to multiple OS
- Data preservation (you don't need to switch from one OS to another)

**Disadvantages**
- Complexity
- Resource sharing (both OS share CPU, memory, etc.)

### 3. Live Boot
Just use a bootable device (boot USB, etc.) and use it as a computer OS system.

**Advantages**
- Privacy — only use it when you want to
- No risk of data loss

**Disadvantages**
- Resource sharing

### 4. Cloud Terminals
Just search via Google, Chrome, etc. by searching "terminal".

**Advantages**
- Simple

**Disadvantages**
- Few commands available
- Can't save what you did
- It only gives you a terminal

### 5. Virtual Machine
Computers have a technology called **virtualization**.

There are 2 types of virtualization: **Type 1** and **Type 2**.

**Type 1 (Bare-Metal Hypervisor)**
- Runs directly on physical HW
- Doesn't require a host OS, e.g. VMware ESXi, Proxmox, Xen

**Type 2 (Hosted Hypervisor)**
- Runs on top of a host OS
- Relies on the host OS, e.g. VMware Workstation, Oracle VirtualBox

**Advantages**
- Easier to set up and use
- No data loss
- Can use multiple OS

**Disadvantages**
- May lag if you open other programs — depends on PC performance
- Uses your PC's storage space

### 6. WSL
### 7. Termux
