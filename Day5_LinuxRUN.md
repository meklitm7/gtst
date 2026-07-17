# 🐧 Linux Advanced User Commands, Sudoers & File Permissions

---

## 👤 Advanced User Commands

---

### 🔑 Password Management

```bash
sudo passwd username          # Set or change password for any user
                              # Works for both 'adduser' and 'useradd' created users
# Example:
sudo passwd meklit
```

---

### 🔧 Modifying Users & Groups

```bash
sudo usermod -u new_id username     # Change user ID
sudo groupmod -g new_id groupname   # Change group ID
sudo usermod username -s /bin/bash  # Change the shell of a user (replace bash with any shell)
```

---

### ❌ Deleting Users

```bash
sudo userdel username          # ⚠️ Deletes user BUT leaves their files behind
sudo userdel -r username       # ✅ Deletes user AND removes all their files
```

---

### 🔍 Viewing User Info

```bash
id username                    # See the user ID and group ID
whoami                         # See which user is currently logged in
groups username                # See which groups a user belongs to
```

---

### 🔄 Switching Users

```bash
su username                    # Switch to another user
                               # Root → no password required
                               # Normal user → requires that user's password
```

---

### 🏠 Home Directory Management

```bash
# Check if a user has a home directory:
ls -ld /home/username

# ✅ If home dir EXISTS — output looks like:
drwxr-xr-x 2 username groupname 4096 Jul 17 /home/username

# ❌ If home dir DOES NOT EXIST — output:
ls: cannot access '/home/username': No such file or directory

# Create home directory for a user that was created with 'useradd' (has no home dir):
sudo mkhomedir_helper username
```

---

### 👥 Group Management

```bash
sudo groupadd groupname               # Create a new group
sudo usermod -aG groupname username   # Add user to a group membership
sudo gpasswd -d username groupname    # Remove user from a group
groups username                       # Verify which groups a user is in
```

---

## 🔐 Sudoers File

> The **sudoers file** contains the list of users who are allowed to use `sudo` power.
> Not all users can use `sudo` — only those listed in this file.

| User | sudo Access |
|------|------------|
| 1st created user | ✅ Added by default |
| Other users | ❌ Must be added manually |

---

### 📋 How to Open the Sudoers File

```bash
sudo visudo        # Only the first user (who already has sudo) can run this
```

---

### ➕ Steps to Add a User to the Sudoers File

```
1. Open sudoers file:
   sudo visudo

2. Use the ↓ arrow key to scroll down until you find this comment:
   # User privilege specification

3. Below that comment you will see:
   root    ALL=(ALL:ALL) ALL

4. Copy that line and add your username:
   meklit  ALL=(ALL:ALL) ALL

5. Press Ctrl + S to save, then Ctrl + X to exit.

6. The user can now use sudo!
```

---

## 🔒 Linux File Permissions

> **Every file in Linux has its own Owner and Permissions.**
> Use `ls -l` to check permissions, owner, date, size, and filename.

```bash
ls -l filename
```

**Example output:**
```
-rwxrwxrwx  1  meklit  developers  4096  Jul 17  file.txt
 ↑ type      ↑  owner   group        size   date    name
```

> 💡 First character tells you the **type:**
> - `-` → regular **file**
> - `d` → **directory**

---

## 👑 Ownership

> Every file has **2 types of ownership:**

| Type | Description |
|------|-------------|
| **User** | The individual owner of the file |
| **Group** | The group that owns the file |

```bash
chown username:groupname filename    # Change both owner and group
chown username filename              # Change only owner
chown :groupname filename            # Change only group
```

---

## 🛡️ Permission Types

> There are **3 types of permissions**, each with a number value:

| Permission | Symbol | Number Value |
|------------|--------|-------------|
| Read | `r` | `4` |
| Write | `w` | `2` |
| Execute | `x` | `1` |

---

### 🧩 Permission Structure

```
- r w x   r w x   r w x
  ↑↑↑       ↑↑↑      ↑↑↑
  USER     GROUP    OTHER
```

```
-rwxrwxrwx
↑ ↑↑↑ ↑↑↑ ↑↑↑
│  │    │    └── Other permissions
│  │    └─────── Group permissions
│  └──────────── User permissions
└─────────────── File type (- = file, d = directory)
```

---

### ⚙️ Changing Permissions — `chmod`

#### Using Symbols

```bash
chmod a+x filename        # Add execute for ALL (user, group, other)
chmod u+x filename        # Add execute for USER only
chmod g+x filename        # Add execute for GROUP only
chmod o+x filename        # Add execute for OTHER only

chmod -x filename         # Remove execute from ALL
chmod u-r filename        # Remove read from USER only

chmod a+rwx,u-r,g-r,o-r filename   # Add rwx for all, then remove read from user, group & other
```

---

#### Using Numbers

> Add up the values for the permissions you want:
> `r=4` + `w=2` + `x=1` = `7` (full permissions)

```bash
chmod 777 filename    # ALL permissions for ALL (user=7, group=7, other=7)
chmod 521 filename    # user=5(r+x), group=2(w), other=1(x)
chmod 644 filename    # user=6(r+w), group=4(r), other=4(r)  ← common for files
chmod 755 filename    # user=7(rwx), group=5(r+x), other=5(r+x) ← common for dirs
```

**Quick reference:**

| Number | Permissions |
|--------|------------|
| `7` | read + write + execute |
| `6` | read + write |
| `5` | read + execute |
| `4` | read only |
| `2` | write only |
| `1` | execute only |
| `0` | no permissions |

---

## ⭐ Special File Permissions

> Special permissions go **beyond** normal `rwx` — they provide extra functionality.

| Permission | Numeric Value | Symbol | Purpose |
|------------|--------------|--------|---------|
| **SUID** | `4000` | `s` | Run program with the **file owner's** privileges |
| **SGID** | `2000` | `s` | New files inherit the **directory's group** |
| **Sticky Bit** | `1000` | `t` | Only file owner or root can **delete** files |

---

### 1. 🔴 SUID — Set User ID
> **Numeric value:** `4000` &nbsp;&nbsp; **Set with:** `chmod u+s filename`

> Allows a program to **run with the file owner's permissions**, not the user who ran it.

```bash
ls -l /usr/bin/passwd
# Output:
-rwsr-xr-x     ← notice the 's' instead of 'x' for user
```

**Why is it used?**
Some programs need higher privileges for specific tasks — without giving users full root access.

> 💡 **Example:** When a normal user runs `passwd` to change their password:
> - The `passwd` program **temporarily runs as root**
> - This lets it update `/etc/shadow` (which only root can write to)
> - The user does **NOT** become root — only that one program gets elevated

```bash
chmod u+s filename      # Add SUID
chmod 4755 filename     # Add SUID using numbers (4 + 755)
```

---

### 2. 🟡 SGID — Set Group ID
> **Numeric value:** `2000` &nbsp;&nbsp; **Set with:** `chmod g+s dirname`

> Makes every new file created inside a directory **inherit the directory's group.**

**Without SGID** — each file gets the creator's personal group:
```
Directory group: developers

meklit creates report.txt  →  Group: meklit   ❌
mulugeta creates code.py   →  Group: mulugeta  ❌
(different groups — hard to collaborate)
```

**With SGID** — all files inherit the directory's group:
```
Directory group: developers

meklit creates report.txt  →  Group: developers  ✅
mulugeta creates code.py   →  Group: developers  ✅
(same group — easy to collaborate!)
```

```bash
chmod g+s dirname       # Add SGID
chmod 2755 dirname      # Add SGID using numbers (2 + 755)
```

---

### 3. 🟢 Sticky Bit
> **Numeric value:** `1000` &nbsp;&nbsp; **Set with:** `chmod +t dirname`

> Prevents users from **deleting or renaming files owned by other users** in a shared directory.

```bash
ls -ld /tmp
# Output:
drwxrwxrwt     ← notice the 't' at the end
```

**Example — `/tmp` directory:**
```
meklit   creates  a.txt
mulugeta creates  b.txt

❌ meklit   CANNOT delete b.txt (belongs to mulugeta)
❌ mulugeta CANNOT delete a.txt (belongs to meklit)
✅ Each user can only delete their OWN files
✅ Root can delete ANY file
```

```bash
chmod +t dirname        # Add sticky bit
chmod 1755 dirname      # Add sticky bit using numbers (1 + 755)
```

---

## 🆚 sudo vs SUID — Key Difference

| | `sudo` | `SUID` |
|--|--------|--------|
| **Elevates** | The **user** | The **program** |
| **Requires** | User in sudoers file | `s` bit set on file |
| **Scope** | User can run many admin commands | Only that one program gets elevated |
| **Security** | Lower (broad access) | Higher (limited to one program) |
| **Use case** | Admin tasks | Specific trusted programs |

> 💡 **Easy to remember:**
> - `sudo` → Elevates the **user** 👤
> - `SUID` → Elevates the **program** ⚙️

> ✅ **SUID is safer** when only ONE specific program needs elevated privileges —
> instead of giving many users full `sudo` access.

---

# 📦 Package Management on Linux

> On Linux, to install software you use **package managers** like `apt`, `pacman`, `dpkg`, etc.
> Package managers connect to the internet to download from **repositories (repos).**

---

## 🔄 How It Works

```
Linux System  →  Package Manager  →  Repository
                                      ├── Package metadata
                                      └── Package dependencies
                                          (helper programs needed for the software to work)
```

> 💡 **Repos** are online servers where packages are uploaded and stored.
> **Debian's** package manager is called `apt` or `dpkg`.

---

## 🟢 APT — Advanced Package Tool

> The main package manager for **Debian-based** distros (Kali, Ubuntu, etc.)
> Requires internet — installs from online repositories.

---

### 📋 APT Commands

```bash
sudo apt update                  # 🔄 Fetch latest package info from repo
                                 # (system doesn't update itself automatically)

sudo apt search softwarename     # 🔍 Check if a package exists in the repo

sudo apt install softwarename    # ⬇️  Install a package

sudo apt upgrade                 # ⬆️  Update all installed software to latest version

sudo apt remove softwarename     # ⚠️  Delete the package ONLY
                                 #     (leaves behind dependencies & metadata)

sudo apt purge softwarename      # 🗑️  Delete EVERYTHING — package + dependencies + metadata

sudo apt autoremove              # 🧹 Delete leftover dependencies & metadata
```

---

### 🆚 Remove vs Purge vs Autoremove

| Command | Package | Dependencies | Metadata |
|---------|---------|-------------|---------|
| `apt remove` | ✅ Deleted | ❌ Kept | ❌ Kept |
| `apt purge` | ✅ Deleted | ✅ Deleted | ✅ Deleted |
| `apt autoremove` | ❌ Kept | ✅ Deleted | ✅ Deleted |

> 💡 **Best practice for a full clean uninstall:** use `apt purge` then `apt autoremove`

---

## 📦 Package Dependencies

> Software can be **built on top of another program** — these are called **modules.**
> Dependencies are installed automatically because they are **helper programs** needed for the software to function correctly.

```
Main Software
    └── depends on → Library A
    └── depends on → Library B  ← these are dependencies
    └── depends on → Module C
```

---

## ⚠️ Common APT Repository Errors & Fixes

---

### 1. 🔒 `Could not get lock /var/lib/apt/lists/lock`
> **Cause:** Two different `apt` processes running at the same time.

```bash
# Fix:
# ✅ Option 1: Restart your PC
# ✅ Option 2: Find and close the other running apt process
```

---

### 2. 🔒 `Could not open lock /var/lib/dpkg/lock-frontend`
> **Cause:** Running the command as a normal user without `sudo`.

```bash
# Fix:
sudo apt install softwarename    # ✅ Always use sudo
```

---

### 3. 🔍 `Unable to locate package`
> **Cause:** Package not found in repo — either wrong spelling or doesn't exist.

```bash
# Fix:
sudo apt search softwarename     # ✅ Search first to verify it exists
# Also check your spelling carefully!
```

---

### 4. 🌐 `The repository 'http://http.kali.org/kali kali-rolling Release' does not have a Release file`
> **Cause:** The repository link is **outdated.**

```bash
# Fix:
# ✅ Search for the newest and correct repo link using Google or ChatGPT
sudo apt edit-sources            # Edit repo source list manually
```

---

### 5. 🛑 Interrupted Installation (apt closed mid-install)
> **Cause:** Closing `apt` before it finishes installing.

```bash
# Fix:
sudo apt edit-sources            # Edit and fix the sources file
# 📌 More detail on this will be covered in the Footprinting module
```

---

## 🔵 DPKG — Debian Package Manager

> **Offline** package manager — does NOT need internet after you download the `.deb` file.
> Requires internet only to **download the `.deb` file** — after that it works offline.

> 💡 All Debian packages have the extension **`.deb`**

---

### 📋 DPKG Commands

```bash
sudo dpkg -i packagename.deb     # ⬇️  Install a .deb package
sudo dpkg -r packagename         # 🗑️  Remove/delete the package
sudo dpkg -p packagename         # 📦 Install/fix dependencies
```

---

## 🟠 Flatpak — Universal Package Manager

> Flatpak aims to **simplify developing, distributing, and installing apps** across any Linux distribution.
> Unlike `apt` and `dpkg`, Flatpak **works for any distro** — not just Debian-based ones.
> ⚠️ **Not built-in** — must be installed first.

---

### 📋 Flatpak Commands

```bash
# First — Install Flatpak itself:
sudo apt install flatpak

# Then use these commands:
flatpak search spotify                        # 🔍 Search for an application
flatpak install flathub com.spotify.Client   # ⬇️  Install an application
flatpak run com.spotify.Client               # ▶️  Run an application
flatpak uninstall com.spotify.Client         # 🗑️  Uninstall an application
flatpak update                               # ⬆️  Update all Flatpak applications
flatpak list                                 # 📋 List all installed Flatpak apps
flatpak --version                            # ✅ Check if Flatpak is installed & working
```

---

## 🔑 Key Points — Package Manager Rules

> Each package manager **can only manage what it installed itself:**

| Package Manager | Can Delete |
|----------------|-----------|
| `apt` | ✅ Only packages installed via `apt` |
| `flatpak` | ✅ Only packages installed via `flatpak` |
| `dpkg` | ✅ Only packages installed via `dpkg` |

> ⚠️ You **cannot** use `apt remove` to uninstall something installed with `flatpak`, and vice versa!

---

## 📊 Full Comparison — APT vs DPKG vs Flatpak

| Feature | APT | DPKG | Flatpak |
|---------|-----|------|---------|
| Needs internet? | ✅ Always | ⚠️ Only to download `.deb` | ✅ For install |
| Works offline? | ❌ | ✅ After download | ❌ |
| Distro support | Debian-based only | Debian-based only | ✅ Any distro |
| Built-in? | ✅ Yes | ✅ Yes | ❌ Must install |
| Handles dependencies? | ✅ Auto | ⚠️ Manual | ✅ Auto |
| File extension | — | `.deb` | — |

---

*🐧 "A good sysadmin knows their package manager inside out."*


*🐧 "With great permissions comes great responsibility."*
