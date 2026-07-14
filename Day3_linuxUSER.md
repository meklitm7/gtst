 # 🐉 Kali Linux — Complete Overview

> **Previously known as BackTrack Linux**
> A powerful Debian-based distribution built for penetration testing, ethical hacking, and security research.

---

## 📡 1. Information Gathering
> *Collecting data about a target before an attack — the first step in any pentest.*

| Tool | Purpose |
|------|---------|
| `nmap` | Indicates open ports and running services |
| `recon-ng` | Web reconnaissance framework |
| `maltego` | Visual link analysis and OSINT |
| `theHarvester` | Gather emails, domains, IPs |
| `whois` | Domain registration lookup |

---

## 🔍 2. Vulnerability Analysis
> *Identifying weaknesses in systems or applications.*

| Tool | Purpose |
|------|---------|
| `nikto` | Web server vulnerability scanner |
| `nmap` | Also used for vulnerability scripts |
| `OpenVAS` | Full vulnerability assessment system |
| `lynis` | Security auditing for Linux systems |

---

## 🌐 3. Web Application Analysis
> *Testing websites and web apps for security flaws.*

| Tool | Purpose |
|------|---------|
| `burpsuite` | Intercept and manipulate web traffic |
| `sqlmap` | Automated SQL injection tool |
| `OWASP ZAP` | Web app vulnerability scanner |
| `webscarab` | Used to intercept and brute force web traffic |

---

## 🗄️ 4. Database Assessment
> *Finding and exploiting vulnerabilities in databases.*

| Tool | Purpose |
|------|---------|
| `sqlmap` | Automated SQL injection and takeover |
| `jSQL Injection` | Java-based SQL injection tool |
| `oscanner` | Oracle database scanner |

---

## 🔑 5. Password Attacks
> *Cracking or brute-forcing passwords and hashes.*

| Tool | Purpose |
|------|---------|
| `wordlists` | Pre-built password lists (e.g. `rockyou.txt`) |
| `john` (John the Ripper) | Used to brute force and crack password hashes |
| `johnny` | GUI version — used to brute force (graphical interface for John) |
| `hashcat` | GPU-accelerated password cracker |

---

## 📶 6. Wireless Attacks
> *Attacking Wi-Fi networks and wireless protocols.*

| Tool | Purpose |
|------|---------|
| `wifite` | Automated wireless attack tool |
| `aircrack-ng` | WEP/WPA cracking suite |
| `kismet` | Wireless network detector |
| `reaver` | WPS brute force attack |

---

## ⚙️ 7. Reverse Engineering
> *Checking from the ground level — analyzing the material (code/binary) that built a system, without source code.*

| Tool | Purpose |
|------|---------|
| `apktool` | Decompile and rebuild Android APK files |
| `ghidra` | NSA-built open-source reverse engineering suite |
| `NASM shell` | Assembly language tool for low-level analysis |

---

## 💥 8. Exploitation Tools
> *Used to find and actively exploit vulnerabilities.*

| Tool | Purpose |
|------|---------|
| `Metasploit Framework` | The most powerful exploitation framework |
| `sqlmap` | Exploit SQL injection vulnerabilities |
| `BeEF` | Browser Exploitation Framework |

---

## 🕵️ 9. Sniffing & Spoofing
> *Hijacking networks — intercepting and manipulating network traffic.*

| Tool | Purpose |
|------|---------|
| `wireshark` | Capture and analyze network packets |
| `responder` | Capture NTLM hashes on a network |
| `ettercap` | Man-in-the-middle attack suite |

---

## 🚪 10. Post Exploitation
> *Get and maintain access after a system has been compromised.*

| Tool | Purpose |
|------|---------|
| `backdoor-factory` | Patch binaries with shellcode backdoors |
| `PowerSploit` | PowerShell-based post exploitation |
| `mimikatz` | Dump credentials from Windows memory |
| `empire` | Advanced post-exploitation agent framework |

---

## 🔬 11. Forensics
> *Investigate and research digital evidence.*

| Tool | Purpose |
|------|---------|
| `hashdeep` | Compute and audit file hashes |
| `binwalk` | Firmware and binary file analysis |
| `autopsy` | Full digital forensics GUI platform |

---

## 📝 12. Reporting Tools
> *Documenting and presenting findings from a penetration test.*

| Tool | Purpose |
|------|---------|
| `recordMyDesktop` | Screen recording for evidence |
| `maltego` | Visual reporting and data mapping |
| `dradis` | Collaborative penetration test reporting |

---

## 🎭 13. Social Engineering Tools
> *Manipulating people into granting unauthorized access.*

| Tool | Purpose |
|------|---------|
| `maltego` | OSINT and target profiling |
| `backdoor-factory` | Create malicious-looking files |
| `SET` (Social Engineering Toolkit) | Phishing, spear phishing, and more |

---

## ⚡ 14. System Services
> *Background services that run on the system — can be started and stopped.*

```bash
# BeEF (Browser Exploitation Framework)
beef-xss start        # Start BeEF service
beef-xss stop         # Stop BeEF service

# Dradis (Reporting & Collaboration)
dradis start          # Start Dradis server
dradis stop           # Stop Dradis server
```

---

## 💻 15. Usually Used Applications
> *Standard apps bundled with Kali for everyday use — as the name describes, these are the apps you usually use.*

- 🖥️ Office suite tools
- 🧑‍💻 VS Code (code editor)
- 🎵 Sound and video applications

---

## 🧩 Other Important Things

### 🖥️ Workspaces
> Help us do **multiple tasks** at once using virtual desktops — switch between different tasks without minimizing windows.

### 💤 Hibernate
> Used to **save and store** the current session to disk and power off — everything restores exactly as you left it on next boot.

### 📁 Folder Managers (File Managers)

| File Manager | Desktop Environment |
|---|---|
| `dolphin` | KDE |
| `thunar` | XFCE |
| `nautilus` | GNOME |

> 💡 **On Windows**, the built-in **File Explorer** is free.
> **Files Pro X** is a paid third-party alternative for Windows with extra features.

---

# 🐧 Linux Commands — Complete Guide

> **Linux uses a shell (terminal) to run commands.**
> Commands are small programs that do one specific task.

---

## 🖥️ Terminal Structure

Every terminal prompt has **5 parts:**

```
username@hostname:current_directory $  command_place
   1          2          3          4       5
```

| # | Part | Description |
|---|------|-------------|
| 1 | **Username** | The logged-in user |
| 2 | **Hostname** | The machine name |
| 3 | **Current Directory** | Where you are right now |
| 4 | **Privilege Symbol** | `$` = normal user &nbsp;&nbsp; `#` = root user |
| 5 | **Command Place** | Where you type your command |

---

## ⚙️ Command Structure

Every command can have **options** and **arguments:**

```bash
command  -option  argument
  ls       -a     file.txt
```

| Part | Symbol | Description | Example |
|------|--------|-------------|---------|
| **Option** | `-` or `--` | Additional flags that modify behavior | `ls -a` |
| **Argument** | — | The value or target the command works on | `cat file.txt` |

---

## 📋 Commands

---

### 1. 📂 `ls` — List Directory
> Used to list anything that can be listed: files, directories. By default lists the current directory.

```bash
ls              # List current directory
ls -l           # Full info: date, owner, permission, group
ls -a           # Display hidden files (Linux hidden files start with dot like .bashrc, .config)
ls filename     # List based on the given file name
ls -R           # Recursively list files — goes inside folder to folder
                # e.g. user/me/meklit/mm.txt, m.md → displays mm.txt, m.md
ls -Rla         # Combine multiple options together
```

---

### 2. 🌳 `tree` — Tree View
> Like `ls` but displays files and folders in a structured/hierarchy way — an organized list.

```bash
tree            # Show directory structure visually
```

---

### 3. 📁 `cd` — Change Directory
> Used to change the current working directory.

```bash
cd /            # Change to root directory
cd              # Back to user's home directory (~)
cd ..           # Go back 1 level
cd ../..        # Go back 2 levels
cd foldername   # Change to the given folder name
```

---

### 4. 📍 `pwd` — Print Working Directory
> Prints the full path of the current working directory starting from root.

```bash
pwd             # e.g. /home/username/documents
```

---

### 5. 📢 `echo` — Display Text
> Accepts text/string as an argument and displays it.

```bash
echo "Hello"              # Print text to terminal
echo "text" > filename    # Create new file and write text (overwrites if file exists ⚠️)
echo "text" >> filename   # Append text to existing file (creates if not exists ✅)
```

> 💡 **Note:** The `>` sign is called **redirecting.**
> - `>` — overwrites the file (destroys existing content!)
> - `>>` — appends to the file (safe to use on existing files)

---

### 6. 🐱 `cat` — Display File Content
> Displays the entire file content directly in the terminal.

```bash
cat filename    # Show all content of a file
```

---

### 7. 📖 `less` — Scrollable File Viewer
> Works like `cat` but opens in a text viewer — you can scroll up and down.

```bash
less filename   # Open file in scrollable viewer (press q to quit)
```

---

### 8. 🔚 `tail` — Last Lines of File
> Displays only the **last 10 lines** of a file's content.

```bash
tail filename   # Show last 10 lines
```

---

### 9. 🔝 `head` — First Lines of File
> Displays only the **first 10 lines** of a file's content.

```bash
head filename   # Show first 10 lines
```

---

### 10. ✋ `touch` — Create Empty File
> Creates a file with a given name and extension — **no content inside.**

```bash
touch file.txt                    # Create single file
touch file1 file2 file3           # Create many files at once (space between names)
```

---

### 11. 📂 `mkdir` — Make Directory
> Creates a directory with a given name.

```bash
mkdir foldername                  # Create single directory
mkdir folder1 folder2 folder3     # Create many directories at once
mkdir -p folder1/folder2/folder3  # Create nested folders (folder3 inside folder1/folder2)
```

---

### 12. 🧹 `clear` — Clear Terminal
> Clears the terminal screen — **does NOT delete anything.**

```bash
clear           # Clear the screen completely
Ctrl + L        # Shortcut — doesn't truly clear, just scrolls up to give clean space
```

---

### 13. 🗑️ `rm` — Remove / Delete
> Used to delete files and directories.

```bash
rm filename       # Delete a file
rm -r foldername  # Delete a directory (recursive)
rm -i filename    # Ask confirmation before deleting
rm -f filename    # Force delete a file (no confirmation)
rm -rf foldername # Recursive force delete a directory ⚠️ (use carefully!)
```

---

### 14. 📋 `cp` — Copy
> Copies a file — **original still exists** in the source location.

```bash
cp oldfile newfile          # Copy file in the same directory
cp oldfile ~/newfile        # Copy file to a different directory
cp -r oldfolder newfolder   # Copy a folder (recursive)
```

---

### 15. 🚚 `mv` — Move
> Moves a file or folder to a new location — also used to **rename** files.

```bash
mv oldfile newfile          # Move/rename file in the same directory
mv oldfile ~/newfile        # Move file to a different directory
mv -r oldfolder newfolder   # Move a folder
```

---

### 16. 🔎 `grep` — Search Pattern in File
> **G**lobal search for **R**egular **E**x**p**ressions — filters and searches a file for a particular pattern of characters and displays all lines that contain that pattern.

> 💡 Patterns are referred to as **regular expressions.**

```bash
grep "pattern" filename       # Search pattern (case SENSITIVE)
grep -i "pattern" filename    # Search pattern (case INSENSITIVE)
grep -c "pattern" filename    # Count total lines that contain the pattern (gives number like 1, 2, 3...)
grep -r "pattern" foldername  # Search pattern inside a folder (recursive)
grep -v "pattern" filename    # Print every line EXCEPT lines with the pattern
grep -n "pattern" filename    # Display matching lines WITH line numbers
                              # e.g.  1: you are "pattern"
                              #       2: you are "pattern"
grep -o "pattern" filename    # Display ONLY the pattern — cuts out the rest of the line
                              # (other grep commands show full line including pattern, this shows only the pattern)
grep -l "pattern" filename    # Give the file name that contains the pattern
```

> 💡 Options can be **combined:** `grep -ic`, `grep -ira`, etc.

---

### 17. 🔢 `wc` — Word Count
> Displays **number of lines, number of words, and number of bytes (characters)** — separated by spaces.

```bash
wc filename     # Show: lines  words  bytes  filename
wc -l filename  # Only number of lines
wc -w filename  # Only number of words
wc -c filename  # Only number of characters (bytes)
```

> 💡 Can be used both ways:
> ```bash
> wc filename              # Direct
> cat filename | wc        # Using pipe
> ```

---

## 🔑 Key Terms

| Symbol | Meaning |
|--------|---------|
| `~` | Home directory |
| `.` | Local (current) directory |
| `*` | All files/directories |

---

## ⚠️ Important Notes

1. **Spaces in file/folder names** — always use quotes:
   ```bash
   cd "folder name"
   ls "folder name"
   mkdir "folder name"
   ```

2. **Combining grep options** — you can stack options together:
   ```bash
   grep -ic "pattern" filename    # Case insensitive + count
   grep -ira "pattern" foldername # Case insensitive + recursive + all
   ```

3. **`grep -l` special rule:**
   - `grep -l` must know the **file path**, so only use it as:
     ```bash
     grep -l "pattern" filename   ✅  # Tells us the path/file name
     ```
   - ❌ Do **NOT** use with pipe like this:
     ```bash
     cat filename | grep -l "pattern"  ❌  # Only gives content, not the file path
     ```
   - All other grep options work with **both** methods:
     ```bash
     cat filename | grep -i "pattern"   ✅
     grep -i "pattern" filename         ✅
     ```

---

# 🐧 Linux Advanced Commands — sed, awk & Multiple Execution

---

## ⚡ Multiple Command Executions

> Run more than one command at a time using special operators.

---

### 1. 🔗 AND (`&&`) — Both Must Succeed
> **Both commands must be correct** — if one fails, neither runs.

```bash
touch me.txt && echo "hello meklit"
# ✅ Both execute if both are correct

toch me.txt && echo "hello meklit"
# ❌ Neither runs — 'toch' is wrong, so the second command is also blocked
```

---

### 2. 🔀 OR (`||`) — Either One Runs
> **If one command is true/succeeds, that command executes.**

```bash
touch me.txt || echo "hello meklit"
# ✅ If both are correct execute both of them 
# ✅ If touch fails → echo runs instead
```

---

### 3. 🔧 Pipe (`|`) — Chain Commands Together
> **Combines 2 different commands** — the output of the command **before** the pipe becomes the **input** for the command **after** the pipe.

```bash
cat file.txt | grep "pattern"
# cat reads the file → grep filters it

cat file.txt | wc -l
# cat reads the file → wc counts the lines
```

---

## ✂️ `sed` — Stream Editor

> **sed** is used for **parsing and transforming text** in Linux.
> It is efficient for large text processing tasks — the **original file never changes** (it's just a stream of text flowing through a command).

---

### 📌 Text Substitution & Replacement

```bash
sed 's/old/new/' filename        # Replace FIRST occurrence of 'old' with 'new' per line
sed 's/old/new/g' filename       # Replace ALL occurrences (use 'g' flag for global replace)
```

> 💡 **`g` flag** — use it when the word appears **more than once on the same line** and you want all replaced.

---

### 🗑️ Deleting Specific Lines

```bash
sed '/pattern/d' filename        # Delete every line that contains the pattern
```

---

### 🔄 Custom Delimiters

> You can use **any delimiter** — not just `/`. The rule is:
> 1. The **first character after `s`** becomes the delimiter
> 2. You must use the **same delimiter throughout** the command

```bash
sed 's/old/new/'  filename       # standard delimiter /
sed 's#old#new#'  filename       # using # as delimiter
sed 's|old|new|'  filename       # using | as delimiter
```

> For **delete (`/d`)** with custom delimiter — you must use an **escape character `\`** before it:

```bash
sed '\|tech|d'  file.txt         # using | as delimiter with escape
sed '\@tech@d'  file.txt         # using @ as delimiter with escape
```

---

### 💾 Permanent / In-Place Editing

> By default sed **never changes the original file.**
> Use `-i` option for **permanent (in-place) editing:**

```bash
sed -i 's/old/new/g' file.txt    # ✅ Permanently changes the file
```

> ⚠️ **Cannot use pipe with `-i`:**
> ```bash
> cat file.txt | sed -i 's/old/new/g'   # ❌ Will NOT work
> ```
> **Why?** The `-i` option needs to know **which file to open AND overwrite.**
> A pipe (`|`) only sends text — it does **not** tell sed where the text came from.

---

### 🔤 Single vs Double Quotes

| Quote Type | Behaviour | Example |
|------------|-----------|---------|
| `'single'` | Literal — **no variable expansion** | `sed 's/info/$name/'` → sed sees `$name` literally |
| `"double"` | Shell **interprets** `$`, backtick, `\` | `sed "s/info/$name/"` → shell replaces `$name` with its value first |

```bash
name=meklit

sed "s/info/$name/" file.txt
# Shell converts it to: sed 's/info/meklit/' file.txt  ✅

sed 's/info/$name/' file.txt
# sed sees literally: $name  ❌ (variable NOT expanded)
```

> 💡 Use **double quotes** when you want to use **variables** inside sed.
> Use **single quotes** when you want **literal text.**

---

## 🦅 `awk` — Pattern Scanning & Data Extraction

> Named after its creators: **A**ho, **W**einberger, and **K**ernighan.
> Ideal for **pattern scanning and data extraction** in structured text.

**Key features:**
- Processes text **line-by-line**
- Supports complex **pattern matching**
- Great for **column-based data** like CSV files
- Detects **space** as the default delimiter
- Like sed — **original file never changes** (text just flows through)

---

### 🔧 Changing the Delimiter

```bash
awk -F ',' '{statement}' filename     # Use comma as delimiter
awk -F ':' '{statement}' filename     # Use colon as delimiter
```

---

### 📦 Built-in Variables

> Using this example file (`file.txt`):
> ```
> 1, meklit mulugeta, Sales, 3500
> 2, tito dagim, IT, 4000
> 3, eliyab dagim, Marketing, 3800
> ```

---

#### `$0` — Whole Current Line

```bash
awk '{print $0}' file.txt
```
```
1, meklit mulugeta, Sales, 3500
2, tito dagim, IT, 4000
3, eliyab dagim, Marketing, 3800
```

---

#### `$1`, `$2`... — Individual Fields (Columns)

```bash
awk '{print $2}' file.txt          # default space delimiter
```
```
meklit
tito
eliyab
```

```bash
awk -F',' '{print $2}' file.txt    # comma delimiter → full name
```
```
 meklit mulugeta
 tito dagim
 eliyab dagim
```

---

#### `NR` — Number of Current Record (Line)
> *"Which line am I reading?"*

```bash
awk '{print NR, $0}' file.txt
```
```
1  1, meklit mulugeta, Sales, 3500       ← NR = 1 (first line)
2  2, tito dagim, IT, 4000               ← NR = 2 (second line)
3  3, eliyab dagim, Marketing, 3800      ← NR = 3 (third line)
```

---

#### `NF` — Number of Fields on Current Line
> *"How many fields are on this line?"*

```bash
awk '{print NF}' file.txt              # default space delimiter
```
```
5
5
5
```

```bash
awk -F',' '{print NF}' file.txt        # comma delimiter
```
```
4
4
4
```

---

### 🎯 Practical awk Examples

---

**Filter lines containing a pattern, then print a specific column:**
```bash
awk -F ',' '/m/ {print $2}' file.txt
# /m/        → process only lines that contain the character 'm' anywhere
# {print $2} → print column 2 from those matching lines
# Result: all names are displayed because each contains 'm'
```

---

**Sum a column and print the total:**
```bash
awk -F',' '{sum += $4} END {print "Total:", sum}' file.txt

# or using pipe — both work the same in awk:
cat file.txt | awk -F',' '{sum += $4} END {print "Total:", sum}'
```
```
Total: 11300
```

> 💡 Unlike `sed -i`, **awk works fine with both pipe and direct file** — no difference!

---

## 📊 Quick Comparison Table

| Feature | `&&` | `\|\|` | `\|` (pipe) | `sed` | `awk` |
|---------|------|------|------|-------|-------|
| Purpose | Both must pass | Either can pass | Chain output→input | Text transform | Data extraction |
| File changed? | — | — | — | Only with `-i` | Never |
| Works with pipe? | — | — | — | ❌ with `-i` | ✅ always |
| Default delimiter | — | — | — | `/` | space |

---

*🐧 "Text is the universal interface of Linux."*

*🐧 "In Linux, everything is a file."*

*🐉 Kali Linux — "The quieter you become, the more you are able to hear."*
