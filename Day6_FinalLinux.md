# ⚙️ Script Installation, Processes & Services — Linux Notes

---

## 📦 Script Installation

- Some scripts are not in a repository, so they get published on GitHub like open-source projects — we can download and use them.
- If the script is on GitHub, use this command to download it:
  ```
  git clone <repo-github-url>
  ```
- GitHub files often have extensions like `.py`, `.sh`. To run those files, you'd normally write the whole file path in the terminal. Instead, you can just run:
  ```
  ./filename.extension
  ```
  But before using this, you must move the file into `/usr/bin`:
  ```
  sudo cp filename.extension /usr/bin
  ```

---

## 🧩 Script Modules

- Scripts are made with scripting languages (programming languages) like: Python, Bash, Go, Ruby, etc.
- Some programming languages have dependencies, like Python and Go. Others, like Bash, usually don't.
- **To install a module (dependency):**
  - Python modules: `pip install modulename`
    - After installing a package, you can also use: `pip install -r requirements.txt`
  - Go modules: `go install modulename`
- Some tools can be installed with just `pip`, without needing `git clone`.

---

## 🐹 Go Package Installation

There are **2 installation methods**:

**a. Old version** — use `go get <repo-github-url>` without cloning.

**b. New version** — first install the package:
```
go install packageurl
```
Then move the file into `/usr/bin` (default download location is `/home/meklit/go/bin`):
```
sudo mv filename /usr/bin
```

---

## 📚 Help on Linux Commands

### 1. `man` (manual)
- Gives full info about the manual and instructions for a tool or command.
  ```
  man command
  ```
  e.g. `man adduser`
- Only works for tools installed via `apt`, not for tools installed via GitHub.
- Navigation: arrow keys · Quit: `q`

### 2. `help`
- Can use: `command -h`, `command -help`, or `command --help`

---

## 🔄 Linux Processes & Services

### Key Terms

| Term | Meaning |
|---|---|
| **Process** | A running instance of a program or executable — opened intentionally, and you can see its effect |
| **Service** | A background program that starts automatically or manually — also called a **daemon** |

### Getting Process IDs

| Command | Effect |
|---|---|
| `ps` | Processes running in my current shell |
| `ps -A` | View all running processes |
| `ps -u username` | View a user's processes |

---

## 🛑 Managing Processes (Not Real-Time)

**PID** = Process ID · **PPID** = Parent Process ID

**Stopping a process:**

| Command | Effect |
|---|---|
| `kill -19 PID` | Stop (pause) the process |
| `kill -18 PID` | Resume the paused process |
| `kill -9 PID` | Force kill — stop a process immediately |
| `killall process_name` | Kill all processes with the given name |
| `killall -u username` | Kill all processes owned by a user |

---

## 📊 Managing Processes (Real-Time)

Two tools:

**1. `top`** — shows process status. Press `q` to quit. Installed on Linux by default.

**2. `htop`** — shows process status and can also kill (stop) processes.
```
sudo apt install htop
```
- Shows a choice list at the bottom of the screen:
  - `F3` — search
  - `F9` — kill
  - `F10` — quit
- Just press the corresponding key to trigger that action.

> 🪟 **On Windows:** view processes via Task Manager → Processes tab. To view services, search "Services".

---

## 🔀 Foreground / Background

- **Foreground** — commands run at the prompt while you wait for them to complete.
- Use the `&` operator to run a program in the **background**, e.g.:
  ```
  vim file.txt &
  ```
- To bring a background process back to the foreground: `fg`
  - This works like a **stack** — if multiple processes are running in the background, `fg` brings back the **last one** you sent to the background first.
- To stop a process running in your shell: `Ctrl + C`

---

## 🛎️ Managing Services

Two tools:

### 1. `systemctl`

| Command | Effect |
|---|---|
| `sudo systemctl start servicename` | Temporarily start the service (stops when machine shuts down) |
| `sudo systemctl stop servicename` | Stop the service |
| `sudo systemctl status servicename` | Check the service's status |
| `sudo systemctl enable servicename` | Permanently start the service — it auto-starts on boot (persistent) |
| `sudo systemctl disable servicename` | Reverse of `enable` — stops it from auto-starting |

> Handles both **temporary service management** and **permanent boot configuration**.

### 2. `service`

| Command | Effect |
|---|---|
| `sudo service servicename start` | Temporarily start the service (stops when machine shuts down) |
| `sudo service servicename stop` | Stop the service |
| `sudo service servicename status` | Check the service's status |

> Handles **temporary service management** only.

---

## 🕳️ Null Device (Bit Bucket)

- `/dev/null` — redirects output to nowhere.
- If you want to ignore output (e.g. don't want to see errors), send it to the null device.
- Commonly used to hide the output of a command.

### Shell Output — 2 Streams

| Stream | Number |
|---|---|
| **STDOUT** | 1 |
| **STDERR** | 2 |

| Command | Effect |
|---|---|
| `command 2> filename` | Redirects errors into a file, and shows only error-free output. E.g. if you run `ls hello` for a non-existent folder, the error itself won't display — it'll be stored in `filename` (viewable with `cat filename`) |
| `command 1> filename` | Redirects normal output into a file. E.g. `ls 1> hello` stores the list of files/dirs into `hello` (viewable with `cat hello`) |
| `command 2> /dev/null` | Redirects errors to `/dev/null` so they disappear entirely, giving you an error-free result |

---

## 🔗 Symbolic Linking

- Symbolic linking is the same idea as a Windows shortcut.
- Used to create a shortcut-style reference to a file/program.
- Useful for creating a short path for a long file path.
- Symbolic linked files show `l` in `ls` listings, along with a `->` pointing to the original (longer) path, e.g.:
  ```
  shortcutname -> /original/longest/path
  ```
- **Create a symlink:**
  ```
  ln -s originalpath shortlinkname
  ```
- **View the original path:**
  ```
  cd -P shortcutname
  ```
  or
  ```
  pwd -P shortcutname
  ```

---

## ✍️ Alias

- A shortcut for a long command.
- **Temporary** (disappears when the system closes/restarts):
  ```
  alias aliasname="long command"
  ```
  e.g. `alias me='ls -la'` — now typing `me` runs `ls -la`

- **Permanent** — add the alias to your shell config file (`~/.bashrc`, `~/.zshrc`, `~/.fishrc`).

**Steps:**
1. Open the config file with a text editor, e.g. `~/.bashrc`:
   ```
   nano ~/.bashrc
   ```
2. Go to the end of the file and add your alias:
   ```
   alias me='ls -la'
   ```
3. Save and exit.
4. Reload the `.bashrc` file:
   ```
   source ~/.bashrc
   ```

---

## 🖇️ Tmux — Terminal Multiplexer

Used to organize/split our terminal work.

| Action | Shortcut |
|---|---|
| Split horizontally | `Ctrl+A` then `o` |
| Split vertically | `Ctrl+A` then `e` |
| Exit | `Ctrl+A` then `x`, or just type `exit` |

---

## 🌐 wget

- A tool used to download files from websites/servers.
  ```
  wget [options] [link]
  ```

---

## 🔎 find

- Used to find any pattern at any path.
  ```
  find [search path] [options] [search word]
  ```

**Common options:**

| Option | Meaning |
|---|---|
| `-name` | Search by name |
| `-perm` | Search by permission |
| `-type f` | List only files |
| `-type d` | List only directories |

**Examples:**
```
find / -name "linux"
find /home -perm 777
find -type f
find -type d
find / -type f -perm /4000
```
> `-perm /4000` finds files that have **any** of the permission bits in `4000` set — this includes permissions like `4755` or others starting with `4`.
