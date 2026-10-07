# 🖥️ System Security / Hacking

## 🔹 What is a System?

A **system** is one or more devices/components working together for a specific objective.

So, when we work with a system, we should understand:

> 🎯 **What is the objective of the system?**

We should study different parts of the system, such as:

* 🖥️ Operating System (OS)
* 🌐 Network
* 🔌 Protocols
* 🌐 Applications
* 🔐 Security controls
* ⚠️ Vulnerabilities
* 👤 Users and access controls

---

# 🧠 System Hacking

For system hacking, we need to:

### 1. Understand how things work

We should first understand the normal behavior of the system.

```text
How does the system work?
        ↓
What services does it provide?
        ↓
What protocols does it use?
        ↓
What OS/software does it use?
        ↓
What security controls exist?
```

### 2. Identify how the system may behave under different conditions

We can make assumptions about how a system might behave based on:

* System architecture
* OS
* Network configuration
* Applications
* Protocols
* User behavior
* Security controls

### 🌐 System Hacking Uses Different Fields

System security is not only about one area.

It can involve:

```text
Network Security
       +
OSINT
       +
Web Security
       +
Operating Systems
       +
Social Engineering
       ↓
System Security
```

### 🔎 OSINT / Social Engineering

Sometimes technical scanning tools cannot discover everything.

For example:

```text
Nmap
  ↓
Cannot directly discover information
about an isolated/internal system
```

In an authorized assessment, **OSINT and other information-gathering techniques** may provide additional information that network scanning cannot.

> ⭐ **Nmap shows what is exposed to the network. OSINT can reveal information that is publicly available outside the target system.**

---

# 💥 Exploitation Phase

**Exploitation** is the phase where an attacker attempts to take advantage of an identified vulnerability to gain unauthorized access or perform an unauthorized action.

The basic idea is:

```text
Vulnerability
      ↓
Exploit
      ↓
Unauthorized access/action
```

In a penetration test:

```text
Identify vulnerability
        ↓
Validate vulnerability
        ↓
Safely exploit it
        ↓
Measure impact
        ↓
Report + recommend fix
```

---

# 🧨 Types of Exploitation Techniques

## 1. 🆕 New Finding / 0-Day Vulnerability

A **zero-day vulnerability** is a vulnerability that is unknown to the vendor or for which there is no available fix at the time it is discovered/exploited.

It is called **zero-day** because defenders have had zero days to prepare a fix after the vulnerability becomes known/exploitable.

### Why don't we usually find 0-days?

Finding a new vulnerability can be difficult because it may require:

* Deep understanding of the software
* Source-code analysis
* Reverse engineering
* Fuzzing
* Debugging
* Understanding the underlying architecture

> ⚠️ A newly discovered vulnerability does **not automatically have a CVE immediately**. A CVE can be assigned later through the CVE process.

### Example

```text
New vulnerability discovered
          ↓
Research / disclosure
          ↓
CVE may be assigned
          ↓
Vendor develops a fix
```

---

## 2. 🔄 Exploiting Existing Vulnerabilities

This means using a vulnerability that is already known and documented.

We can research:

* Existing CVEs
* Vendor security advisories
* Known vulnerabilities
* Exploit databases
* Security research

Examples of common vulnerability classes:

```text
SQL Injection
XSS
Command Injection
Authentication vulnerabilities
Path Traversal
Remote Code Execution
```

> ⚠️ A CVE identifies a specific vulnerability; it does not mean that every vulnerability automatically has a working public exploit.

---

# 🛠️ Exploitation Methods

## 1. 🌐 Protocol Exploitation

This can involve weaknesses in network services or protocols.

Examples:

* Open ports exposing unnecessary services
* Misconfigured services
* Weak authentication
* Insecure protocols

### Example: FTP Anonymous Login

An FTP server may be configured to allow **anonymous login**.

```text
FTP Server
    ↓
Anonymous access enabled
    ↓
Unauthorized access risk
```

---

# 2. 🌐 Web Security Exploitation

This involves exploiting vulnerabilities in web applications.

Examples include:

* Input validation flaws
* SQL Injection
* XSS
* Command Injection
* Authentication flaws
* File upload vulnerabilities

For example, a vulnerable web application may improperly process user input and allow unintended commands to be executed on the server.

---

# 3. 🖥️ System Exploitation

This involves exploiting weaknesses in the operating system or installed software.

Examples:

* Weak passwords
* Outdated software
* Unpatched vulnerabilities
* Misconfigured permissions
* Privilege escalation vulnerabilities

---

# 4. 👤 Social Engineering

Social engineering attacks target **people rather than only technical systems**.

Examples:

* Phishing
* Vishing
* Pretexting
* Baiting
* Impersonation

The attacker attempts to manipulate a person into performing an action that benefits the attacker.

---

# 🆔 Common Vulnerabilities and Exposures — CVE

**CVE** stands for:

> **Common Vulnerabilities and Exposures**

CVE is a system for giving publicly known cybersecurity vulnerabilities **unique identifiers**.

Example format:

```text
CVE-YYYY-NNNNN
```

For example:

```text
CVE-2026-12345
```

---

# 📊 CVE vs CVSS

These are different:

```text
CVE
 ↓
Identifies the vulnerability

CVSS
 ↓
Scores the severity of the vulnerability
```

Example:

```text
CVE-2026-12345
        ↓
Vulnerability identifier

CVSS Score: 8.8
        ↓
Severity score
```

---

# 📈 Common Vulnerability Scoring System — CVSS

**CVSS** stands for:

> **Common Vulnerability Scoring System**

It is used to calculate the **severity** of a vulnerability.

The score ranges from:

```text
0.0 → 10.0
```

A higher score generally means a more severe vulnerability.

---

## 🔹 CVSS v2

| Severity  |      Score |
| --------- | ---------: |
| 🟢 Low    |  0.0 – 3.9 |
| 🟡 Medium |  4.0 – 6.9 |
| 🔴 High   | 7.0 – 10.0 |

---

## 🔹 CVSS v3

| Severity    |      Score |
| ----------- | ---------: |
| 🟢 Low      |  0.1 – 3.9 |
| 🟡 Medium   |  4.0 – 6.9 |
| 🔴 High     |  7.0 – 8.9 |
| 🔴 Critical | 9.0 – 10.0 |

> 💡 The exact scoring methodology depends on the CVSS version. CVSS measures severity, not simply "how dangerous" a vulnerability is in every real-world environment.

---

# 🏢 MITRE

**MITRE** is a nonprofit organization that develops and maintains important cybersecurity resources.

One of its most important cybersecurity resources is:

> **MITRE ATT&CK**

MITRE also operates the CVE Program together with other organizations and partners.

---

# ⚔️ MITRE ATT&CK Framework

**MITRE ATT&CK** is a knowledge base/framework describing **adversary tactics and techniques** based on real-world observations.

It helps security teams understand:

* How attackers operate
* What techniques attackers use
* How to detect attacker behavior
* How to defend against attacks
* How to map an attack to specific techniques

---

# 🛡️ MITRE ATT&CK — Main Tactics

The Enterprise ATT&CK framework includes tactics such as:

```text
Initial Access
Execution
Persistence
Privilege Escalation
Defense Evasion
Credential Access
Discovery
Lateral Movement
Collection
Command and Control
Exfiltration
Impact
```

### 🧠 Important

Your original list combined **Collection and Exfiltration**.

They are separate ATT&CK tactics:

```text
Collection
    ↓
Gather valuable data

Exfiltration
    ↓
Steal/move data out of the environment
```

Also, **Impact** is an important Enterprise ATT&CK tactic.

---

# ⛓️ Lockheed Martin Cyber Kill Chain

The **Cyber Kill Chain** was developed by **Lockheed Martin**.

It describes a traditional attack lifecycle using seven stages.

```text
1. Reconnaissance
       ↓
2. Weaponization
       ↓
3. Delivery
       ↓
4. Exploitation
       ↓
5. Installation
       ↓
6. Command & Control
       ↓
7. Actions on Objectives
```

---

## 1. 🔎 Reconnaissance

The attacker gathers information about the target.

Examples:

* IP addresses
* Domains
* Employees
* Technologies
* Public information

---

## 2. 🛠️ Weaponization

The attacker prepares a malicious payload or other capability to use against the target.

---

## 3. 📦 Delivery

The attacker delivers the malicious payload/capability to the target.

Examples:

* Phishing email
* Malicious attachment
* Malicious link
* Compromised website

---

## 4. 💥 Exploitation

The attacker exploits a vulnerability or weakness to execute code or gain access.

---

## 5. 📥 Installation

The attacker establishes malware or another mechanism on the compromised system to maintain access.

---

## 6. 📡 Command and Control — C2

The compromised system communicates with attacker-controlled infrastructure.

```text
Compromised System
       ↕
      C2
       ↕
Attacker Infrastructure
```

---

## 7. 🎯 Actions on Objectives

The attacker performs the final intended actions.

Examples:

* Stealing data
* Destroying data
* Disrupting services
* Financial theft
* Other mission objectives

---

# 🆚 Cyber Kill Chain vs MITRE ATT&CK

These two frameworks are related, but they are **not the same thing**.

| Cyber Kill Chain              | MITRE ATT&CK                    |
| ----------------------------- | ------------------------------- |
| 7-stage attack lifecycle      | Detailed knowledge base         |
| High-level                    | More detailed                   |
| Focuses on attack progression | Focuses on tactics & techniques |
| Recon → Actions on Objectives | Initial Access → Impact         |
| Lockheed Martin               | MITRE                           |

### 🧠 Easy Way to Remember

```text
Cyber Kill Chain
       ↓
"What stage of the attack?"

MITRE ATT&CK
       ↓
"What tactic and technique is the attacker using?"
```

---

# ⭐ Quick Memory

```text
SYSTEM SECURITY
      ↓
Understand the system
      ↓
Find weaknesses
      ↓
Identify vulnerabilities
      ↓
Exploit safely
      ↓
Measure impact
      ↓
Defend + Report
```

### 🔐 CVE / CVSS

```text
CVE
→ Identifies a vulnerability

CVSS
→ Scores vulnerability severity
```

### ⚔️ Attack Frameworks

```text
Cyber Kill Chain
→ Attack lifecycle

MITRE ATT&CK
→ Adversary tactics + techniques
```

### 🔥 Cyber Kill Chain

```text
Recon
 ↓
Weaponization
 ↓
Delivery
 ↓
Exploitation
 ↓
Installation
 ↓
C2
 ↓
Actions on Objectives
```

### 🛡️ ATT&CK

```text
Initial Access
 ↓
Execution
 ↓
Persistence
 ↓
Privilege Escalation
 ↓
Defense Evasion
 ↓
Credential Access
 ↓
Discovery
 ↓
Lateral Movement
 ↓
Collection
 ↓
C2
 ↓
Exfiltration
 ↓
Impact
```
# Exploit Databases, Vulnerability Assessment & Remote Shells

## 1. Exploit-DB

**Exploit Database (Exploit-DB):**
https://exploit-db.com

* Contains **publicly available exploit code and proof-of-concepts (PoCs)** for known vulnerabilities.
* It can be useful when a vulnerability already exists and we want to understand whether public exploitation research is available.
* Exploits can contain information such as:

  * Title
  * Type
  * Platform / OS
  * Author
  * Related vulnerability/CVE
* We can search by:

  * Vulnerability name
  * CVE ID
  * Software/product
  * Framework or technology, such as React
  * Platform
* Some entries allow us to download the exploit/PoC code.
* **Maintained by Offensive Security (OffSec).**

### Important

Exploit-DB is **not the same thing as the CVE database**.

* **CVE → identifies the vulnerability**
* **Exploit-DB → may contain public exploit/PoC information for that vulnerability**

---

# 2. MITRE CVE Search

**CVE Search:**
https://cve.mitre.org/cve/search_cve_list.html

We can search for vulnerabilities by:

* CVE ID
* Vulnerability/product name
* Software

It gives us detailed information about the vulnerability, such as:

* Description
* Affected software
* References
* CVE identifier

However, the CVE record itself usually **does not provide detailed step-by-step exploitation instructions**.

### Example

If we search:

```text
CVE-XXXX-XXXXX
```

we can learn:

```text
What vulnerability exists?
Which software is affected?
What versions are affected?
How severe is it?
What references are available?
```

For detailed exploit/PoC information, we may need sources such as:

* Exploit-DB
* Vendor advisories
* Security research
* GitHub
* Other trusted security sources

---

# 3. Searchsploit

**Searchsploit** is the command-line search tool for the Exploit Database.

Instead of opening Exploit-DB in a browser, we can search from the terminal.

Example:

```bash
searchsploit <keyword>
```

We can search by things such as:

* Software name
* Vulnerability name
* CVE
* Technology
* Programming language/platform

### Example

```bash
searchsploit apache
```

or:

```bash
searchsploit CVE-XXXX-XXXXX
```

### Quick memory

```text
Exploit-DB  → Web interface
Searchsploit → Terminal interface
```

---

# 4. Search Engines

We can also use search engines such as Google to find security information.

We may find:

* Security advisories
* CVE information
* GitHub repositories
* Security research
* Vendor documentation
* Exploit/PoC references

We can search using:

```text
<software> <vulnerability name>
```

or:

```text
<CVE-ID>
```

### Important

Finding exploit code on GitHub does **not automatically mean it is trustworthy**.

We should check:

* Who created it?
* What vulnerability does it target?
* Is the repository legitimate?
* Is it appropriate for our authorized lab?
* What does the code actually do?

---

# 5. Exploitation Technique

### Important rule

> **Anytime you get software to test, especially software from a big organization such as Microsoft or Apple, don't immediately try to find a new bug. First check for known vulnerabilities/CVEs.**

Why?

Because large and popular software has often already been:

* Tested by security researchers
* Assigned CVEs
* Documented by vendors
* Analyzed by the security community
* Added to vulnerability databases

So our first question should be:

```text
Does this software/version already have known vulnerabilities?
```

Then:

```text
What CVEs exist?
What is the severity?
Is there a patch?
Is there public research/PoC?
```

Only after understanding known vulnerabilities would researching an unknown/new vulnerability make sense.

---

# 6. Vulnerability Assessment

**Vulnerability assessment** is like using a checklist to find possible security problems.

We:

```text
Identify possible vulnerabilities
          ↓
Check whether they exist
          ↓
Determine severity
          ↓
Recommend remediation
```

### Example

Suppose we are assessing a web server.

Our checklist might include:

```text
☐ Outdated software
☐ Weak configuration
☐ Unnecessary services
☐ Weak authentication
☐ Known CVEs
☐ Missing security headers
☐ TLS configuration problems
☐ Web application vulnerabilities
```

The goal is to **identify and evaluate weaknesses**, not automatically exploit everything.

---

# 7. Vulnerability Assessment Tools

## 1. Nessus

**Nessus** is a vulnerability scanner.

It can help identify:

* Outdated components
* Known vulnerabilities
* Misconfigurations
* Missing patches
* Weak security settings

---

## 2. Acunetix

**Acunetix** is mainly focused on **web application security testing**.

It can help identify web vulnerabilities such as:

* SQL injection
* Cross-site scripting (XSS)
* Misconfigurations
* Other web application weaknesses

---

## 3. OpenVAS

**OpenVAS** stands for:

**Open Vulnerability Assessment Scanner**

It is part of the **Greenbone Vulnerability Management (GVM)** framework.

It is used for vulnerability scanning and assessment.

---

## 4. Nuclei

**Nuclei** is a fast vulnerability scanning tool.

It is especially useful for penetration testing and security testing.

It uses simple **YAML-based templates** to describe detection logic.

Example concept:

```text
Target
  ↓
Nuclei
  ↓
Templates
  ↓
Check for known condition
  ↓
Result
```

---

# 8. False Positive vs False Negative

These are very important in vulnerability scanning.

### False Positive

The vulnerability **does NOT actually exist**, but the scanner says that it exists.

```text
Scanner → "Vulnerability exists"
Reality → "It does not exist"
```

### False Negative

The vulnerability **actually exists**, but the scanner fails to detect it.

```text
Scanner → "No vulnerability"
Reality → "Vulnerability exists"
```

### Easy memory

```text
False Positive → False alarm

False Negative → Missed problem
```

---

# 9. Remote Access / Remote Shell

Remote shell techniques are about obtaining a command-line shell on another system.

If we have a shell in an **authorized lab**, we may be able to perform actions such as:

* Run commands
* Inspect files
* Transfer files
* Enumerate the system
* Perform privilege assessment

The two common connection models are:

```text
Bind Shell
Reverse Shell
```

---

# 10. Bind Shell

There are two machines:

```text
Attacker                         Victim
   │                               │
   │                               │
   │                         Listener opens
   │                         on victim
   │                               │
   └──────── Connect ─────────────►│
```

In a **bind shell**:

* The listener is on the **victim/target machine**.
* The attacker connects to the victim.
* The attacker needs to know the victim's reachable IP address and port.
* The victim must be reachable from the attacker.

### Simple memory

> **Bind = Victim binds/listens.**

```text
Victim
  ↓
Listener

Attacker
  ↓
Connects to victim
```

---

# 11. Reverse Shell

In a **reverse shell**, the connection direction is reversed.

```text
Attacker                         Victim
   │                               │
   │  Listener                     │
   │  opens                        │
   │                               │
   │◄──────── Connection ──────────┤
   │                               │
```

The listener is on the **attacker machine**.

The victim initiates the connection back to the attacker.

### Simple memory

> **Reverse = Victim connects back.**

```text
Attacker
  ↓
Listener

Victim
  ↓
Connects back to attacker
```

### Why reverse shells can be useful

Many networks are designed to:

```text
Allow → Outbound connections
Restrict → Unsolicited inbound connections
```

Therefore, depending on the network configuration, a reverse connection may be easier to establish than an inbound connection.

**Important:** A firewall can still block a reverse shell. Reverse shells do not automatically bypass firewalls.

---

# 12. Bind Shell vs Reverse Shell

| Feature                 | Bind Shell         | Reverse Shell             |
| ----------------------- | ------------------ | ------------------------- |
| Listener                | Victim             | Attacker                  |
| Connection initiated by | Attacker           | Victim                    |
| Attacker connects to    | Victim             | Attacker                  |
| Main requirement        | Victim reachable   | Victim can reach attacker |
| Easy memory             | **Victim listens** | **Victim calls back**     |

---

# 13. Netcat / NC

**Netcat (`nc`)** is a command-line networking utility.

It can:

* Create TCP connections
* Create UDP connections
* Listen for connections
* Send/receive data
* Test network connectivity

On Kali/Parrot, it is commonly already available.

### Listener concept

For an authorized lab:

```bash
nc -lvnp <PORT>
```

This means conceptually:

```text
-l → listen
-v → verbose
-n → don't resolve DNS names
-p → specify port
```

The other side would then establish a connection to that listener.

---

# 14. Payload

A **payload** is the code or command that performs the intended action after an exploit succeeds.

Examples of possible payload goals include:

* Execute a command
* Create a shell
* Establish a remote session
* Transfer information
* Perform another authorized post-exploitation action

### Simple definition

> **Payload = What we want to happen after exploitation.**

Think:

```text
Exploit → Gets the opportunity
Payload → Performs the action
```

For example:

```text
Vulnerability
      ↓
   Exploit
      ↓
   Payload
      ↓
Remote shell
```

---

# 15. Reverse Shell Generator

A website such as:

https://www.revshells.com/

can generate reverse/bind shell command examples for different:

* Operating systems
* Shells
* Languages
* Connection types

Use these only in systems/labs where you have authorization.

---

# 16. Metasploit

**Metasploit** is a penetration-testing framework.

It is a collection of tools used for:

* Vulnerability research
* Exploitation
* Payload handling
* Post-exploitation
* Security testing

It is primarily written in **Ruby**.

Important components include:

### Msfconsole

Interactive command-line interface for Metasploit.

```text
msfconsole
```

### Msfvenom

Used to generate and encode payloads.

```text
msfvenom
```

### Msfdb

Metasploit database functionality for storing/managing information used by Metasploit.

---

# 17. Metasploit Modules

Metasploit contains different types of modules, including:

```text
Exploits
Payloads
Auxiliary
Post
Encoders
Nops
```

Payloads and exploits are important components:

```text
Exploit
   ↓
Takes advantage of vulnerability
   ↓
Payload
   ↓
Performs intended action
```

On Kali, Metasploit's files are commonly located under:

```text
/usr/share/metasploit-framework/
```

For payload modules, the exact internal path can vary by Metasploit version, so don't memorize only one directory path.

---

# 18. Payload Naming / Formatting

A common Metasploit payload naming structure looks like:

```text
OS / Architecture / Payload / Connection
```

For example:

```text
windows/meterpreter/reverse_tcp
```

Conceptually:

```text
windows
   ↓
meterpreter
   ↓
reverse_tcp
```

Other examples:

```text
linux/x86/meterpreter/reverse_tcp

osx/x86/shell_reverse_tcp

android/meterpreter/reverse_tcp

freebsd/x86/shell_reverse_tcp
```

The exact path and available payloads depend on the Metasploit version.

---

# 19. Connection Types

### Reverse TCP

```text
Victim ─────► Attacker
```

Victim initiates a TCP connection back to the listener.

---

### Bind TCP

```text
Attacker ─────► Victim
```

Victim listens and attacker connects to it.

---

### Reverse HTTPS

```text
Victim ─────► Attacker
       HTTPS/TLS
```

Uses HTTPS/TLS as the transport, providing encryption for the communication channel.

---

### Bind HTTPS

```text
Attacker ─────► Victim
       HTTPS/TLS
```

The victim listens and the attacker connects using an HTTPS/TLS-based transport.

### Important

**HTTPS encryption does not make a payload invisible or undetectable.**

Security tools can still detect suspicious behavior.

---

# 20. Staged Payload

A **staged payload** is delivered in multiple parts.

Conceptually:

```text
Exploit
   ↓
Small first-stage loader
   ↓
Connection
   ↓
Larger second stage
   ↓
Full payload/session
```

The first stage is usually small and is responsible for obtaining/loading the larger second stage.

### Metasploit naming

Staged payloads commonly use:

```text
/
```

Example:

```text
windows/meterpreter/reverse_tcp
```

### Advantages

* Smaller initial payload
* Can provide more complex functionality
* Useful when payload size is important
* Meterpreter commonly uses staged payloads
* May not be easier to notice based on size/content

---

# 21. Non-Staged Payload

A **non-staged payload** contains the required payload functionality in one piece.

Conceptually:

```text
Exploit
   ↓
Complete payload
   ↓
Execution
```

Metasploit commonly represents these with:

```text
_
```

Example:

```text
windows/meterpreter_reverse_tcp
```

### Advantages

* Everything is delivered together
* Does not need to fetch a separate second stage
* Can be useful when additional staging communication is undesirable

### Disadvantages

* Larger payload
* May be easier to notice based on size/content
* Less suitable when payload size needs to be minimized

---

# 22. Staged vs Non-Staged

| Feature            | Staged                                   | Non-Staged                         |
| ------------------ | ---------------------------------------- | ---------------------------------- |
| Delivery           | Multiple parts                           | One piece                          |
| Initial size       | Usually smaller                          | Usually larger                     |
| Additional stage   | Yes                                      | No                                 |
| Metasploit naming  | `/`                                      | `_`                                |
| Example            | `meterpreter/reverse_tcp` staged form                | `meterpreter_reverse_tcp` non-staged form      |
| Network dependency | Usually needs second-stage communication | Doesn't need separate second stage |

### Easy memory

```text
/  → staged

_  → non-staged
```

---

# 23. Payload Example — Windows

For an **authorized lab**, a Windows payload can be generated using `msfvenom`.

Conceptually:

```bash
msfvenom -p <payload> LHOST=<LAB_IP> LPORT=<LAB_PORT> -f exe -o <filename>.exe
```

Example structure:

```text
-p      → payload
LHOST   → listener/attacker IP
LPORT   → listener port
-f exe  → Windows executable format
-o      → output file
```

---

# 24. Payload Example — Linux

For an authorized lab:

```bash
msfvenom -p <payload> LHOST=<LAB_IP> LPORT=<LAB_PORT> -f elf -o <filename>
```

### ELF

**ELF = Executable and Linkable Format**

It is a common Linux/Unix executable file format used for:

* Executable files
* Object files
* Shared libraries
* Core dumps

---

# 25. Overall Picture

These topics are connected:

```text
Vulnerability
     ↓
CVE / Security Research
     ↓
Find existing vulnerability
     ↓
Exploit / PoC
     ↓
Payload
     ↓
Connection
   ↙     ↘
Bind    Reverse
     ↓
Shell / Session
     ↓
Post-Exploitation
```

And the tools fit into different stages:

```text
CVE
 ↓
Identify known vulnerability

Exploit-DB / Searchsploit
 ↓
Find public exploit/PoC information

Nessus / OpenVAS / Nuclei
 ↓
Vulnerability assessment/scanning

Metasploit
 ↓
Authorized exploitation framework

Netcat
 ↓
Basic network connection/listener testing
```

---

# 🧠 Quick Memory

### CVE

> **What vulnerability is this?**

### Exploit-DB

> **Is there public exploit/PoC research?**

### Searchsploit

> **Search Exploit-DB from the terminal.**

### Vulnerability Assessment

> **What security problems exist?**

### Nessus / OpenVAS

> **Scan for vulnerabilities and misconfigurations.**

### Nuclei

> **Template-based security checks.**

### Bind Shell

> **Victim listens → attacker connects.**

### Reverse Shell

> **Attacker listens → victim connects back.**

### Payload

> **What action happens after exploitation?**

### Staged

> **Small first stage → larger second stage.**

### Non-Staged

> **Everything in one piece.**

### Exploit vs Payload

```text
Exploit = How we take advantage of the vulnerability

Payload = What we execute/do after exploitation
```

### CVE vs CVSS

```text
CVE  = identifies the vulnerability

CVSS = scores its severity
```
