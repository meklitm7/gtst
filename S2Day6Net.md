# 🌐 Network Hacking  

## 🔥 What is Network Hacking?

**Network hacking** is the process of gathering information about networks and exploiting network weaknesses.

It includes:

* 🔎 Network information gathering
* 🕵️ Network sniffing
* ⚔️ Network attacks

---

# 👣 Network Footprinting

**Network footprinting** is the process of gathering information about a target network during reconnaissance.

## 🛠️ Tools for the Recon Process

Common tools include:

```text
Nmap
Ping
Traceroute
ARP
Netstat
SS
```

---

# 📡 Ping

**Ping** is used to test connectivity between two network devices by sending **ICMP Echo Request** packets.

### 🔹 Specify the Number of Pings

```bash
ping -c <number> <IP>
```

Example:

```bash
ping -c 4 192.168.1.1
```

➡️ Sends **4 ICMP requests**.

---

## 📦 Ping Packet Size

We can use `-s` to specify the **size of the ICMP data/payload** that is sent.

```bash
ping -s <number> <IP>
```

Example:

```bash
ping -s 100 192.168.1.1
```

Here:

```text
ICMP data/payload = 100 bytes
ICMP header       =   8 bytes
                    ─────
ICMP packet       = 108 bytes
```

For IPv4, there is also normally a **20-byte IP header**:

```text
ICMP data/payload = 100 bytes
ICMP header       =   8 bytes
IP header         =  20 bytes
                    ─────
IP packet         = 128 bytes
```

### 🧠 Important

`ping -s 100` means **100 bytes of ICMP data**, not 100 bytes for the entire ICMP packet.

So, if we want the **ICMP packet itself to be 100 bytes**:

```text
100 - 8 = 92
```

We use:

```bash
ping -s 92 <IP>
```

Because:

```text
92 bytes data
+ 8 bytes ICMP header
= 100 bytes ICMP packet
```

> ⭐ **Remember:** `-s` specifies the ICMP **payload/data size**.

> ⚠️ If the question asks for the **entire IPv4 packet size**, we also need to account for the IP header.

---

## 🔹 fping

**fping** can be used to ping **multiple hosts** more efficiently than running `ping` separately for every host.

---

## 🔹 nping

**Nping** is part of the Nmap suite.

It can be used for:

* Packet generation
* Packet crafting
* Connectivity testing
* Timing and response tests

Example:

```bash
nping <IP>
```

---

## 🔹 hping

**hping** is an advanced packet-generation and testing tool.

It allows us to send customized:

```text
TCP
UDP
ICMP
```

packets.

It can be useful for network testing and troubleshooting in an authorized environment.

---

# 🛣️ Traceroute

**Traceroute** is used to trace the path that packets take from a **source to a destination** across a network.

It also helps us measure the **time taken for each hop** along the way.

### 🔹 Basic Usage

```bash
traceroute <IP>
```

Example:

```bash
traceroute 8.8.8.8
```

The output shows the intermediate **hops/routers** between our machine and the destination.

### ❗ When We See `* * * *`

Sometimes we may see:

```text
* * *
```

or:

```text
* * * *
```

This can happen because:

* Some routers **block or filter ICMP/TTL-expired responses**.
* A router may be configured not to respond to traceroute probes.
* Packets or responses may be filtered or dropped.

This does **not necessarily mean the route is broken**.

### 🔄 Dynamic Traces Using MTR

When we cannot clearly figure out the network path, we can use:

```bash
mtr <IP>
```

**MTR (My Traceroute)** combines functionality similar to `ping` and `traceroute`.

It continuously checks the route and dynamically displays information such as:

* 🛣️ Network path
* ⏱️ Latency
* 📦 Packet loss
* 🔄 Changes in the route

```text
Traceroute
    ↓
Shows the path

MTR
    ↓
Continuously checks the path
    ↓
Shows latency + packet loss dynamically
```

> ⭐ **Remember:** `* * *` in traceroute does not automatically mean that the network is down.

---

# 📊 Netstat

**Netstat** stands for **Network Statistics**.

It can be used to:

* Display active network connections
* Show listening ports
* View network interface statistics
* Display routing tables
* Show associated processes (when supported)

### 🔹 Show Listening Ports

```bash
netstat -l
```

➡️ Shows sockets that are listening for connections.

### 🔹 Show Process Information

```bash
netstat -p
```

➡️ Shows the process associated with a socket when available and when you have sufficient permissions.

> 💡 On modern Linux systems, `ss` is generally preferred because `netstat` is a legacy tool.

---

# 🔌 SS — Socket Statistics

**SS** stands for **Socket Statistics**.

It gives detailed information about:

* Network connections
* Listening ports
* TCP/UDP sockets
* Socket states

### 🔹 TCP

```bash
ss -t
```

➡️ Show TCP sockets.

### 🔹 UDP

```bash
ss -u
```

➡️ Show UDP sockets.

### 🔹 Listening Ports

```bash
ss -l
```

➡️ Show listening sockets.

### 🔹 Numeric Output

```bash
ss -n
```

➡️ Show **port numbers instead of resolving service names**.

For example:

```text
:80
```

instead of:

```text
:http
```

### 🔹 All Sockets

```bash
ss -a
```

➡️ Show all sockets, including listening and non-listening sockets.

### ⭐ Useful Combination

```bash
ss -tuln
```

This is a very common command.

```text
-t → TCP
-u → UDP
-l → Listening
-n → Numeric
```

➡️ **Show listening TCP/UDP ports using numeric port numbers.**

---

# 🕵️ Network Sniffing

**Network sniffing** is the process of monitoring and capturing packets that pass through a network using sniffing tools.

It can be compared to:

> 📞 **"Tapping phone wires"**

The goal is to observe network traffic and analyze what is being transmitted.

---

# 🧩 Types of Sniffing

## 1. 👂 Passive Sniffing

In passive sniffing, the observer **only listens to network traffic** and does not modify the packets.

Historically, this was commonly associated with **hub-based networks**, because a hub forwards traffic to all connected devices.

```text
Device A ──┐
Device B ──┼── Hub ── Observer
Device C ──┘
```

The observer can potentially see traffic sent across the shared network.

---

## 2. ⚡ Active Sniffing

**Active sniffing** involves interacting with or manipulating network traffic so that traffic can potentially be observed.

It is especially relevant to **switched networks**, where simply listening to traffic is normally not enough to see another device's unicast traffic.

Examples include:

* ARP spoofing/poisoning
* MAC flooding
* Other traffic-redirection techniques

> ⚠️ These techniques should only be practiced on systems/networks you own or are explicitly authorized to test.

---

# 🛠️ Network Sniffing Tools

## 🦈 Wireshark
## 🐧 tcpdump
## 🔬 TShark
## 🖥️ Microsoft Message Analyzer
## 🔎 NetworkMiner
# 🧠 Quick Memory

| Tool                | Main Purpose                   |
| ------------------- | ------------------------------ |
| 🗺️ **Nmap**        | Network/port scanning          |
| 📡 **Ping**         | Test connectivity              |
| 🛣️ **Traceroute**  | Trace network path             |
| 📍 **MTR**          | Continuously monitor route     |
| 🔗 **ARP**          | View/manage ARP information    |
| 📊 **Netstat**      | Network connections/statistics |
| 🔌 **SS**           | Socket/connection information  |


---

# ⭐ Easy Way to Remember

```text
PING
→ "Can I reach it?"

TRACEROUTE
→ "How do I reach it?"

MTR
→ "How is the route performing?"

NETSTAT
→ "What connections/ports exist?"

SS
→ "What sockets are active?"
```

---

# 📦 Ping Size — Quick Memory

```text
ping -s 100
       ↓
100 bytes = ICMP DATA/PAYLOAD
       ↓
+ 8 bytes = ICMP HEADER
       ↓
108 bytes = ICMP PACKET
       ↓
+ 20 bytes = IPv4 HEADER
       ↓
128 bytes = IPv4 PACKET
```

### ⭐ Formula

```text
ICMP packet size = payload + 8

IPv4 packet size = payload + 8 + 20
```

So:

```text
Want a 100-byte ICMP packet?

100 - 8 = 92

ping -s 92 <IP>
```

---

# 🛣️ Traceroute — Quick Memory

```text
Traceroute
    ↓
Find the path
    ↓
Check each hop
    ↓
Measure response time
```

If we see:

```text
* * *
```

it may mean:

```text
Router does not respond
        OR
ICMP/response is filtered
        OR
Probe/response was dropped
```

Then:

```bash
mtr <IP>
```

➡️ Use **MTR for continuous/dynamic route checking** and to observe latency and packet loss.

# 🦈 Wireshark — Cybersecurity Notes

## 🔍 Wireshark

**Wireshark** is a **network protocol analyzer**.

It is used to capture and analyze network traffic and packets.

### 🛡️ For Red Team / Security

For security work, Wireshark can be useful for:

* 🔎 Network traffic analysis
* 🦠 Malware analysis
* 🌐 Understanding network communication
* 📦 Analyzing packets sent between systems

It can be used for **passive analysis**, where we observe traffic without modifying it.

---

# ⚙️ How Wireshark Works

Wireshark can work with:

### 🌐 Online / Real-Time Analysis

We can capture packets while network communication is happening.

```text
Network Traffic
      ↓
Wireshark
      ↓
Capture Packets
      ↓
Analyze
```

### 📁 Offline Analysis

We can also open a previously captured packet file and analyze it later.

```text
PCAP File
   ↓
Wireshark
   ↓
Analyze Packets
```

---

# 🖥️ GUI

Wireshark provides a **GUI (Graphical User Interface)**.

It is available for operating systems such as:

* 🪟 Windows
* 🐧 Linux
* 🍎 macOS

---

# 🚀 Starting Wireshark

Normally, we can start Wireshark from the application menu or terminal:

```bash
wireshark
```

If there is a permission/interface-access problem, we may sometimes use:

```bash
sudo wireshark
```

> ⚠️ Running GUI applications with `sudo` is generally not the preferred approach. It is better to configure the required packet-capture permissions when possible.

---

# ⏰ Time Display

Sometimes the packet timestamps are not displayed in the format we want.

To change the time format:

```text
View
  ↓
Time Display Format
  ↓
Choose the format
```

This changes how the packet capture time is displayed.

---

# 📋 Packet Information

Wireshark provides different columns and sections containing information about each packet.

For example:

```text
No. | Time | Source | Destination | Protocol | Length | Info
```

The **Info** column gives a summary of what is happening in the packet.

Depending on the packet/protocol, it can show information such as:

```text
Source Port → Destination Port
```

For example:

```text
12345 → 80
```

This means traffic is going from source port `12345` to destination port `80`.

> 💡 The exact information shown depends on the protocol and packet.

---

# 📦 Capture File Extensions

Common Wireshark capture files include:

```text
.pcap
.pcapng
```

### `.pcap`

A common packet-capture file format.

### `.pcapng`

The newer and more feature-rich capture format commonly used by Wireshark.

> ⭐ remember that **`.pcap` and `.pcapng`** are the important extensions you'll commonly encounter.

---

# 🔎 Wireshark Filtering

Wireshark has a powerful **display filter** system.

We can use filters to search for specific packets instead of manually looking through every packet.

---

## 🌐 Filter by Protocol

We can search for a specific protocol:

```text
http
```

➡️ Shows HTTP packets.

Other examples:

```text
dns
tcp
udp
icmp
ssh
ftp
```

---

# 🎯 Filter by IP Address

## Source IP

```text
ip.src == <IP>
```

Example:

```text
ip.src == 192.168.1.10
```

➡️ Shows packets where `192.168.1.10` is the **source IP**.

---

## Destination IP

```text
ip.dst == <IP>
```

Example:

```text
ip.dst == 192.168.1.10
```

➡️ Shows packets where `192.168.1.10` is the **destination IP**.

---

## Source OR Destination IP

```text
ip.addr == <IP>
```

Example:

```text
ip.addr == 192.168.1.10
```

➡️ Shows packets where the IP appears as either:

```text
Source IP
   OR
Destination IP
```

### 🧠 Remember

```text
ip.src  → Source only
ip.dst  → Destination only
ip.addr → Source OR destination
```

---

# 🔢 Filter by Frame Number

We can search for a specific packet/frame number:

```text
frame.number == 100
```

➡️ Shows frame/packet number `100`.

---

# ❌ Exclude a Protocol

We can use `!` to mean **NOT**.

Example:

```text
!http
```

➡️ Shows packets that are **not HTTP**.

Another example:

```text
!dns
```

➡️ Shows packets that are not DNS.

---

# 🔗 AND / OR Operators

We can combine filters.

## AND — `&&`

Both conditions must be true.

```text
ip.src == 192.168.1.10 &&(and) tcp
```

➡️ Source IP is `192.168.1.10` **AND** the packet uses TCP.

---

## OR — `||`

Either condition can be true.

```text
ip.src == 192.168.1.10 ||(or) ip.src == 192.168.1.20
```

➡️ Shows packets from either:

```text
192.168.1.10
       OR
192.168.1.20
```

### 🧠 Easy Memory

```text
&&  → AND → both conditions
||  → OR  → either condition
!   → NOT → exclude
```

---

# 🧠 How to Learn Wireshark Filters

We **don't need to memorize every Wireshark filter**.

If we don't know the filter syntax, we can use Wireshark itself.

### 🔹 Right-Click → Apply as Filter

1. Find the packet/field you are interested in.
2. **Right-click** it.
3. Select:

```text
Apply as Filter
```

4. Choose the appropriate option, such as:

```text
Selected
```

Wireshark will automatically create the filter for us.

### Example

Suppose we see:

```text
Source: 192.168.1.10
```

Instead of remembering the exact syntax, we can:

```text
Right-click
     ↓
Apply as Filter
     ↓
Selected
```

Wireshark may generate something like:

```text
ip.src == 192.168.1.10
```

### ⭐ Why this is useful

This helps us **learn the filter syntax naturally**.

```text
See packet/field
      ↓
Right-click
      ↓
Apply as Filter
      ↓
See generated filter
      ↓
Learn the syntax
```

---

# 🧠 Quick Memory

| Filter                | Meaning                  |
| --------------------- | ------------------------ |
| `http`                | Show HTTP packets        |
| `ip.src == IP`        | Source IP                |
| `ip.dst == IP`        | Destination IP           |
| `ip.addr == IP`       | Source or destination IP |
| `frame.number == 100` | Frame number 100         |
| `!http`               | Not HTTP                 |
| `A && B`              | A AND B                  |
| `A \|\| B`            | A OR B                   |

---

# ⭐ Wireshark Easy Memory

```text
Wireshark
   ↓
Capture packets
   ↓
Analyze packets
   ↓
Filter packets
   ↓
Find useful information
```

### 🔥 Most Important Filters

```text
ip.addr == IP
     ↓
Find traffic involving an IP

ip.src == IP
     ↓
Find traffic coming FROM an IP

ip.dst == IP
     ↓
Find traffic going TO an IP

http
     ↓
Find HTTP traffic

!http
     ↓
Find everything except HTTP

frame.number == N
     ↓
Find a specific packet
```

