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

# 🦈 TShark, TCPDump, ARP & Network Attacks

# 1. 🦈 TShark

**TShark** is a **command-line network protocol analyzer**.

It is basically the command-line tool from the Wireshark project, so it does not provide the normal Wireshark GUI.

### ⭐ Why use TShark?

TShark is useful when:

* Working from the terminal
* Analyzing large packet captures
* Automating packet analysis
* Using tools such as `grep` and `awk`
* Working with scripts

```text
Wireshark → GUI + packet analysis

TShark    → Command line + packet analysis
```

---

## 🔹 Capture Traffic

```bash
sudo tshark -i <interface>
```

Example:

```bash
sudo tshark -i wlan0
```

`-i` specifies the **network interface** to capture from.

---

## 🔎 Filter While Capturing

We can use `-Y` for a **display filter**.

```bash
sudo tshark -i wlan0 -Y 'ip.src == 192.168.1.10'
```

➡️ Shows packets where the source IP is `192.168.1.10`.

### 🧠 Remember

```text
-i → interface
-Y → display filter
```

---

# 📂 Read a Capture File

We can read an existing capture file using `-r`.

```bash
sudo tshark -r <filepath>
```

Example:

```bash
sudo tshark -r capture.pcap
```

### Hide error messages

```bash
tshark -r capture.pcap 2>/dev/null
```

`2>/dev/null` redirects error messages to `/dev/null`.

```text
2 → stderr
> → redirect
/dev/null → discard the output
```

---

# 💾 Write/Save a Capture

We can save captured packets into a file using `-w`.

```bash
sudo tshark -i wlan0 -w capture.pcap
```

➡️ Captured packets are saved into `capture.pcap`.

```text
Network Traffic
      ↓
    TShark
      ↓
 capture.pcap
```

---

# ⏰ Time Format

TShark can change the way packet timestamps are displayed.

```bash
tshark -i <interface> -t ad
```

`-t` controls the **time format**.

`ad` means an **absolute date and time** format.

---

# 🔢 Limit the Number of Packets

We can use `-c` to limit the number of packets processed/captured.

```bash
tshark -r capture.pcap -c 10
```

➡️ Processes only the first **10 packets** from the capture.

---

# 🔢 Using `awk`

We can pipe TShark output into `awk`.

Example:

```bash
tshark -r capture.pcap | awk '{print $1}'
```

➡️ Prints the first whitespace-separated field from each line.

This is useful when we want to extract specific information from command output.

---

# 🔗 Follow TCP Streams

We can use TShark's `-z follow` feature to follow a TCP stream.

```bash
tshark -r capture.pcap -q -z follow,tcp,ascii,<stream_number>
```

For example:

```bash
tshark -r capture.pcap -q -z follow,tcp,ascii,0
```

### What do these options mean?

```text
-r → read capture file
-q → quiet output
-z → statistics/follow feature
follow → follow a stream
tcp → TCP stream
ascii → display stream as ASCII
0 → stream number
```

---

## 🔄 Follow Multiple Streams

For example:

```bash
for i in {0..5}; do
    tshark -r capture.pcap -q -z follow,tcp,ascii,$i
done
```

➡️ Loops through TCP stream numbers `0` to `5`.

### Search the output

We can pipe the result into `grep`:

```bash
for i in {0..5}; do
    tshark -r capture.pcap -q -z follow,tcp,ascii,$i
done | grep "Password"
```

➡️ Searches the displayed stream data for the word **Password**.

> ⚠️ Only inspect traffic and credentials from captures you are authorized to analyze.

---

# 🔎 TShark + AWK + Grep

We can combine command-line tools:

```text
TShark
  ↓
Extract packet information
  ↓
awk
  ↓
Select a field
  ↓
grep
  ↓
Search for specific text
```

For example:

```bash
tshark -r capture.pcap | awk '{print $<number>}' | grep "HTTP"
```

The exact field number depends on the TShark output format, so we should inspect the output first instead of assuming a fixed field number.

---

# 2. 🐧 TCPDump

**tcpdump** is another **command-line packet capture and analysis tool**.

It is similar to TShark because both work from the terminal, but their output and filtering syntax are different.

---

## 🔹 Capture from an Interface

```bash
sudo tcpdump -i <interface>
```

Example:

```bash
sudo tcpdump -i wlan0
```

---

## 🔹 Filter by Port

```bash
sudo tcpdump -i wlan0 port <port_number>
```

Example:

```bash
sudo tcpdump -i wlan0 port 80
```

➡️ Captures traffic involving port `80`.

---

## 🔹 Filter by Protocol

```bash
sudo tcpdump -i wlan0 <protocol>
```

Example:

```bash
sudo tcpdump -i wlan0 tcp
```

➡️ Captures TCP traffic.

Other examples:

```text
tcp
udp
icmp
arp
```

---

# 3. 🔗 ARP

**ARP** stands for:

> **Address Resolution Protocol**

ARP is used in IPv4 networks to map an **IP address to a MAC address** on the local network.

### 🧠 Simple Example

Suppose our computer wants to communicate with:

```text
IP: 192.168.1.1
```

but it needs the device's MAC address.

It sends an ARP request that is essentially asking:

> **"Who has 192.168.1.1? Tell me your MAC address."**

The device that owns that IP can respond with its MAC address.

```text
Our PC
  │
  │ ARP Request:
  │ "Who has 192.168.1.1?"
  ↓
Broadcast
  │
  ├── Device A ❌
  ├── Device B ❌
  └── Gateway ✅
          │
          ↓
     "My MAC is XX:XX:XX..."
```

---

# 📋 ARP Table

Our computer keeps ARP information in an **ARP cache/table**.

We can view it with:

```bash
arp
```

On modern Linux systems, another common command is:

```bash
ip neigh
```

---

# 4. 🌊 MAC Flooding

**MAC flooding** is an attack against a network switch.

The basic idea is to send a very large number of fake MAC addresses so that the switch's **MAC address table** becomes overwhelmed.

A switch normally uses its MAC address table to know:

```text
MAC address → Switch port
```

If the table becomes full, the switch may behave differently with unknown destinations, potentially causing more traffic to be flooded.

### 🧠 Simple idea

```text
Normal:

MAC A → Port 1
MAC B → Port 2
MAC C → Port 3


MAC Flooding:

MAC A
MAC B
MAC C
MAC D
MAC E
MAC F
MAC G
...
      ↓
Many fake MAC addresses
      ↓
MAC table becomes overwhelmed
```

> ⚠️ Modern switches have protections against this attack, and behavior depends on the switch configuration.

---

## 🛠️ MAC Flooding Tool

`macof` is a tool associated with MAC flooding testing.

In an **authorized lab**, it can be used to demonstrate the behavior of a switch under a large number of generated MAC addresses.

```bash
sudo macof -i <interface>
```

> ⚠️ Do not run MAC flooding against networks you do not own or have permission to test.

---

# 🛡️ Prevention of MAC Flooding

### 🔐 Port Security

**Port security** can limit the number of MAC addresses allowed on a switch port.

```text
Switch Port
     ↓
Maximum allowed MAC addresses
     ↓
Too many MACs → Security action
```

### 🔐 MAC Filtering

MAC filtering can control which MAC addresses are allowed on a network or port.

> 💡 Port security is generally the more relevant switch-level protection against MAC-table flooding.

---

# 5. 🎭 ARP Spoofing / ARP Cache Poisoning

**ARP spoofing** is a technique where an attacker sends false ARP information to associate their MAC address with another device's IP address.

It can be used to position an attacker between two devices, creating a **Man-in-the-Middle (MITM)** situation.

### 🧠 Normal Communication

```text
Computer ───────────→ Gateway
```

### 🎭 ARP Spoofing

```text
Computer
    ↓
 Attacker
    ↓
 Gateway
```

The attacker attempts to make both sides believe that the attacker's MAC address belongs to the other device.

This can allow traffic to pass through the attacker.

---

# 🧪 ARP Spoofing — Lab Concept

In an authorized lab, the general process involves:

```text
1. Identify the target and gateway
          ↓
2. Understand their IP/MAC mappings
          ↓
3. Enable packet forwarding
          ↓
4. Perform ARP poisoning
          ↓
5. Observe traffic in the lab
```

### Packet forwarding

Linux can be configured to forward IPv4 packets:

```bash
sudo sysctl net.ipv4.ip_forward=1
```

> ⚠️ Disabling a firewall is **not inherently required** for ARP spoofing and is generally a bad security practice. In a lab, configure firewall rules deliberately rather than simply disabling the firewall.

---

# 🛠️ Bettercap

**Bettercap** is a network attack and monitoring framework that can be used in authorized security labs.

Start Bettercap on an interface:

```bash
sudo bettercap -iface <interface>
```

### Discover devices

```text
net.probe on
```

Then:

```text
net.show
```

➡️ Shows discovered network devices.

Bettercap can also perform ARP spoofing in an authorized lab using its ARP spoofing features.

> ⚠️ Use this only on networks where you have explicit permission.

---

# 🌐 HTTP vs HTTPS

### HTTP

HTTP sends web traffic without TLS encryption.

```text
Client ───── HTTP ─────→ Server
```

Traffic may be readable if it is captured.

### HTTPS

HTTPS uses **TLS** to protect HTTP communication.

```text
Client ───── HTTPS/TLS ─────→ Server
```

The contents are encrypted in transit.

---

# 🔒 HSTS

**HSTS** stands for:

> **HTTP Strict Transport Security**

It tells a browser that a website should be accessed using **HTTPS**.

This helps prevent certain downgrade attacks where an attacker tries to make a user use HTTP instead of HTTPS.

---

# 🛡️ ARP Spoofing Prevention

Some defensive techniques include:

### 1. 🔐 Static ARP Entries

Important devices can have manually configured/static ARP mappings.

### 2. 🔐 Switch Security Features

Managed switches may provide features designed to detect or prevent ARP poisoning.

Examples include:

* Dynamic ARP Inspection (DAI)
* DHCP Snooping
* Port security

---

# 6. 🌐 DNS Spoofing

**DNS** stands for:

> **Domain Name System**

DNS maps domain names to IP addresses.

For example:

```text
google.com
     ↓
IP address
```

### 🎭 DNS Spoofing

In DNS spoofing, an attacker attempts to provide a **false DNS response** so that a domain resolves to an incorrect IP address.

Example:

```text
User enters:
google.com
     ↓
Attacker-controlled DNS response
     ↓
Wrong IP address
     ↓
Malicious/fake website
```

This can be used as part of a **Man-in-the-Middle** attack.

---

# 🧪 DNS Spoofing — Lab Concept

In an authorized lab, the general flow is:

```text
Prepare a controlled test website
          ↓
ARP poisoning / traffic redirection
          ↓
DNS spoofing
          ↓
Controlled domain resolves to lab IP
          ↓
Observe the result
```

Bettercap has DNS spoofing functionality that can be used in a controlled lab.

For example, the concept is:

```text
DNS spoofing
     ↓
Specify a test domain
     ↓
Enable DNS spoofing
```

> ⚠️ Never redirect real users or real domains without explicit authorization.

---

# 🛡️ DNS Spoofing Prevention

Defensive techniques include:

* 🔒 Use HTTPS
* 🔒 Use HSTS
* 🔐 Use trusted DNS resolvers
* 🔐 Use DNSSEC where appropriate
* 🔐 Monitor suspicious DNS changes
* 🔐 Use secure network configurations

---

# 7. ⬇️ Protocol Downgrade Attack

A **protocol downgrade attack** attempts to force communication from a stronger/secure protocol to a weaker one.

For example:

```text
HTTPS
  ↓
HTTP
```

The goal is to make the victim use an insecure protocol.

### 🛡️ Prevention

* Use HTTPS
* Enable HSTS
* Avoid insecure HTTP redirects
* Keep browsers and servers updated
* Use secure TLS configurations

> ⭐ HSTS is especially important because it tells the browser to use HTTPS for the protected domain.

---

# 8. 💥 DoS / DDoS Attacks

## DoS

**DoS** stands for:

> **Denial of Service**

A DoS attack attempts to make a service unavailable by overwhelming or exhausting its resources.

---

## DDoS

**DDoS** stands for:

> **Distributed Denial of Service**

The attack traffic comes from **many systems**, rather than a single source.

```text
       Attacker
           ↓
    ┌──────┼──────┐
    ↓      ↓      ↓
  Bot 1   Bot 2   Bot 3
    ↓      ↓      ↓
    └──────┼──────┘
           ↓
        Server
```

---

# 💥 Types of DoS Attacks

## 1. SYN Flood

A SYN flood sends a large number of TCP connection requests.

```text
SYN
SYN
SYN
SYN
SYN
 ↓
Server resources
 ↓
Can become exhausted
```

---

## 2. Service Request Flood

The attacker sends a very large number of requests to a service.

The goal is to consume:

* CPU
* Memory
* Connections
* Bandwidth
* Other resources

---

## 3. Application-Level DoS

This targets the application layer and may exploit:

* Expensive operations
* Poorly designed application logic
* Resource-intensive requests
* Application vulnerabilities

---

# 🛠️ DoS/DDoS Testing Tools

Tools that may appear in security training include:

```text
LOIC
HOIC
Slowloris / RUDY
PyLoris
DDOSIM
```


---

# 🛡️ DoS/DDoS Prevention

### ☁️ Use DDoS Protection

Services such as DDoS-protection/CDN providers can absorb and filter malicious traffic.

### 🔥 Firewalls

Configure firewalls to filter unwanted traffic.

### 📡 Control Broadcast Traffic

Limit or control unnecessary broadcast traffic on the network.

### 📊 Monitor Inbound Traffic

Monitor incoming traffic for unusual:

* Traffic volume
* Connection rates
* Source patterns
* Protocol behavior

---

# 🛡️ General Network Security Prevention

## 🔥 1. Deploy a Robust Firewall

A firewall controls network traffic based on security rules.

---

## 🚨 2. IDS/IPS

**IDS** = Intrusion Detection System

➡️ Detects suspicious activity.

**IPS** = Intrusion Prevention System

➡️ Detects and can actively block suspicious activity.

```text
IDS → Detect

IPS → Detect + Prevent/Block
```

---

## 🔐 3. Strong Data Encryption

Use encryption to protect sensitive data during transmission and storage.

Examples:

```text
HTTPS/TLS
SSH
VPN
```

---

## 🔑 4. Strong Access Controls

Use:

* Strong authentication
* Least privilege
* MFA
* Proper authorization
* Account management

---

## 🔎 5. Regular Vulnerability Assessment

Regularly check systems for security weaknesses.

---

## 🧪 6. Penetration Testing

Conduct authorized penetration testing to identify and fix vulnerabilities before attackers exploit them.

---

# 🧠 QUICK MEMORY

```text
TShark
→ Command-line packet analysis

TCPDump
→ Command-line packet capture

ARP
→ IP → MAC mapping

MAC Flooding
→ Overwhelm switch MAC table

ARP Spoofing
→ Fake ARP mappings

DNS Spoofing
→ Fake DNS response

HTTPS
→ HTTP protected by TLS

HSTS
→ Force/use HTTPS for a domain

DoS
→ Deny service from one/fewer sources

DDoS
→ Distributed denial of service

IDS
→ Detect

IPS
→ Detect + Prevent
```

# ⭐ Network Attack Concepts

```text
MAC Flooding
     ↓
Targets switch MAC table

ARP Spoofing
     ↓
Targets ARP mappings

DNS Spoofing
     ↓
Targets DNS resolution

Protocol Downgrade
     ↓
Attempts to move from secure → insecure protocol

DoS
     ↓
Targets service availability

DDoS
     ↓
Targets availability from many sources
```
