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

### 🧠 Important

CVE is **not a glossary**.

It is a standardized identification system/catalog for publicly disclosed cybersecurity vulnerabilities.

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
