# 🐧 Linux File Hierarchy, Text Editors & User Management

---

## 🗂️ Linux File System Hierarchy

> Linux/UNIX has a **special file system** different from Windows.
> A **file system** is a directory structure that the OS uses to organize files.
> **system files** are files that used by os

| OS | System Files Location |
|----|-----------------------|
| 🪟 Windows | `Local Disk C:\` |
| 🐧 Linux | Root directory `/` |

---

### 📁 Directory Structure

---

#### 1. `/` — Root Directory
> Every file and folder in Linux starts from here — the top of everything.

```
/
├── root/
├── bin/
├── boot/
├── dev/
├── etc/
├── home/
├── lib/
├── media/
├── mnt/
├── opt/
├── sbin/
├── tmp/
└── usr/
```

> ⚠️ **`/root` and `/` are NOT the same thing:**
> - `/` → the root of the entire file system (everyone's starting point)
> - `/root` → the home directory of the **root user only** (appears *inside* `/`)

---

#### 2. `/bin` — Binary Executables
> Stores essential commands usable by **both normal and root users.**

```bash
# Commands stored here:
ls, cat, cp, mkdir, touch, echo ...
```

---

#### 3. `/boot` — Boot Loader Files
> Files needed to **start the OS** when the system powers on.
> Accessible by both normal and root users.

```
grub, vmlinuz, kernel, initrd
```

---

#### 4. `/dev` — Essential Device Files
> **All devices are represented as files** here.
> Any device attached to the system (USB, hard drive, etc.) appears as a file in this directory.

```
/dev/sda   → Hard drive
/dev/usb   → USB device
```

---

#### 5. `/etc` — Et Cetera (Configuration Files)
> Contains **all configuration files** for the system and installed programs.
> Also contains **start/stop shell scripts** used to control individual programs.

```
/etc/passwd   → User account information
/etc/hosts    → Hostname to IP mappings
```

> 💡 When you install a program → its config file is stored in `/etc`

---

#### 6. `/home` — Home Directory
> Stores **normal user information and personal files.**
> Users **cannot access each other's** home directories.

```
/home/meklit/     → meklit's personal files
/home/tito/       → tito's personal files
```

> 💡 Home directory is represented by the `~` symbol.

---

#### 7. `/lib` — Libraries
> Contains **essential libraries** needed for commands in `/bin` and `/sbin` to work correctly.

```
# File names follow this pattern:
ld-2.11.1.so
libncurses.so.5.7
```

---

#### 8. `/media` — Removable Media Mount Points
> **Temporary mount directory** for removable devices like CD-ROMs, USB drives, etc.

---

#### 9. `/mnt` — Temporarily Mounted Files
> Used by **root/sysadmin** to temporarily mount file systems.

---

#### 10. `/opt` — Optional Application Software
> Stores **third-party/personal software** — not default Linux software.
> Software is stored in packages.

```
# Examples:
Google Chrome, Microsoft Office (via Wine), etc.
```

---

#### 11. `/sbin` — Essential System Binaries
> Holds commands **not in `/bin`** — only accessible by the **root user.**

```bash
# Normal user accessing /sbin commands:
sudo useradd username    # use sudo in front
```

---

#### 12. `/tmp` — Temporary Files
> Stores **temporary files created by users.**
> ⚠️ These files **disappear when the system reboots or shuts down.**

> 🔵 **Blue team note:** Files placed here are harder to trace — they vanish on reboot.

---

#### 13. `/usr` — User Utilities
> The **parent/storage folder** of `bin`, `sbin`, `lib`, and `src`.
> Stores most user applications and their files.

> 💡 **Why does `/usr` exist?**
> If ALL commands were put into `/bin` and `/sbin`, those directories would become huge.
> Linux organizes it like this:
> - Essential commands → `/bin`
> - Most other programs → `/usr/bin`

```
/usr/bin/awk        → awk command
/usr/sbin/useradd   → useradd command
/usr/lib/awk        → awk libraries
```

---

## ✏️ Text Editors in Linux

> There are **2 types** of text editors in Linux:

| Type | Examples |
|------|----------|
| 💻 **Command-based** | VIM, Nano, Emacs, Neovim |
| 🖥️ **Graphical** | VS Code, Sublime Text |

---

## 🟢 VIM — VI Improved

> Previously called **vi** — which only let users see/edit **one line at a time.**
> VIM (**VI iMproved**) was created to fix that limitation.
> VIM uses **modes** — this is what makes it a powerful but complex editor.

---

### 🔄 VIM's 4 Modes

---

#### 1. 👁️ Normal Mode — View Only
> Default mode when you open a file — you can only read, not write.

```bash
vim filename        # Opens file in Normal Mode
```

---

#### 2. ✍️ Insert Mode — Edit / Write
> Press `i` to enter Insert Mode — you'll see `-- INSERT --` at the bottom.

```
i → enter Insert Mode → type anything → Esc to go back
```

---

#### 3. ⌨️ Command Mode — Save, Quit & Execute
> Press `Esc` to enter Command Mode, then type commands:

| Command         | Action                               |
| --------------- | ------------------------------------ |
| `:w` + Enter    | 💾 Save                              |
| `:q` + Enter    | 🚪 Quit                              |
| `:wq` + Enter   | 💾🚪 Save & Quit                     |
| `:wq!` + Enter  | ⚠️ Force Save & Quit                 |
| `:u` + Enter    | ↩️ Undo                              |
| `:%!ls` + Enter | 🖥️ Execute bash command (e.g. `ls`) |

---

#### 4. 🔷 Visual Mode — Select & Manipulate Text
> Used to **select blocks of text** and perform actions on them.

| Shortcut | Mode | Selects |
|----------|------|---------|
| `v` | Character-wise | Character by character |
| `Shift + V` | Line-wise | Entire lines |
| `Ctrl + V` or `Ctrl + Q` | Block-wise | Rectangular block of text |

**After selecting text in Visual Mode:**

| Key | Action |
|-----|--------|
| `:d` | ✂️ Delete selected text |
| `:y` | 📋 Yank (copy) selected text |
| `:p` | 📌 Paste yanked text after cursor |

---

## 🔵 Nano — Simple Terminal Editor

> Usually comes **pre-installed** on modern Linux systems.
> Much simpler than VIM — great for beginners.

| Shortcut | Action |
|----------|--------|
| `Alt + U` | ↩️ Undo |
| `Alt + E` | ↪️ Redo |
| `Ctrl + T` | 🖥️ Execute a command |
| `Alt + 6` | 📋 Copy |
| `Ctrl + K` | ✂️ Cut |
| `Ctrl + U` | 📌 Paste |
| `Ctrl + R` | 📂 Insert another file's content at cursor position (enter file path after pressing) |
| `Shift + Arrow` | 🔷 Select text |

---

## 👥 Linux User Management

> The **person who uses the computer** is called a **user.**
> Every user has a **group** with the same ID as the user.
> Users have their **own files and applications.**

```bash
whoami        # Find out which user is currently logged in
```

---

### 🔐 Types of Users

| Type | User ID | Description |
|------|---------|-------------|
| 👑 **Root User** | `0` | Full system access — superuser |
| 👤 **Normal User** | `1 – 999` | Limited access — personal files only |

> 💡 Privileges and power depend on the type of user.

---

### 🔑 Key Concepts About User Management

- By default, the **root user is created** when the OS is installed.
- The **first user** created has **more privileges** than users created after.
- Normal users can run root-level commands using **`sudo`** in front of the command.

> 💡 **SUDO** = **S**uper**u**ser **Do** — used to bypass permission denied errors.

```bash
sudo command        # Run a command as root/superuser
sudo su             # Switch to root user session
```

---

### ➕ Creating Users

#### `useradd` — Simple (No Details Asked)

```bash
sudo useradd username
```

| Feature | Detail |
|---------|--------|
| Shell | `sh` |
| Home directory | ❌ Not created by default (use `-m` flag) |
| Password | ❌ Not set automatically |
| Updates | `/etc/passwd` and `/etc/shadow` |

```bash
sudo useradd -m username    # Create user WITH home directory
```

---

#### `adduser` — Interactive (Asks for Details)

```bash
sudo adduser username
```

| Feature | Detail |
|---------|--------|
| Shell | `bash` |
| Home directory | ✅ Automatically created |
| Password | ✅ Asked during setup (stored encrypted) |
| Updates | `/etc/passwd` and `/etc/shadow` |

---

### 📂 Important User-Related Files

| File | Purpose |
|------|---------|
| `/etc/passwd` | Stores user account information |
| `/etc/shadow` | Stores **encrypted** password information |
| `/etc/group` | Stores group information |

---

### 💡 Key Concepts — Users

- When you **create a user**, Linux automatically creates a **group with the same name.**
- To **switch to root user:**
  ```bash
  sudo su
  ```
- Every user's data lives in `/home/username/`

---

*🐧 "On a Linux system, everything is a file — even your users."*
