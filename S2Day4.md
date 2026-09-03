# 🎭 Social Engineering (Human Hacking)

> **Social Engineering = Hacking humans instead of systems.**

* 🎯 Trick someone to gain access to their **sensitive information**.
* 🧠 Use **manipulation** to influence the victim.

---

# 🔄 Social Engineering Life Cycle

```text id="m6j2fd"
🔎 Research
     ↓
🎣 Hook
(Contact / Talk with Victim)
     ↓
🎭 Play
(Gain Access)
     ↓
🚪 Exit
```

### 1️⃣ Research 🔎

Collect information about the target.

### 2️⃣ Hook 🎣

Contact or communicate with the victim.

### 3️⃣ Play 🎭

Manipulate the victim and gain access to the desired information or system.

### 4️⃣ Exit 🚪

Finish the interaction and leave without raising suspicion.

---

# 🎭 Types of Social Engineering

## 1️⃣ Phishing 🎣📧

An attacker tricks someone by using a **malicious website, message, or link** to steal sensitive information such as:

* 📧 Email
* 🔑 Password
* 💳 Banking information

### Types of Phishing

#### 🔹 Normal Phishing

* Massive phishing
* Not specifically targeted
* Sent to many people

```text
Attacker
   ↓
👥👥👥👥👥
Many victims
```

#### 🎯 Spear Phishing

* Targeted phishing
* Focuses on **one specific individual or organization**
* Usually more personalized

```text
Attacker
   ↓
🎯 One Specific Victim
```

---

# 2️⃣ Vishing 📞

**Vishing = Voice + Phishing**

Phishing performed through **voice communication**, usually by phone.

> 📞 Example: A scammer calls and pretends to be from a bank or another trusted organization.

---

# 3️⃣ Shoulder Surfing 👀

Watching someone's screen, keyboard, or phone to see sensitive information **without their knowledge**.

For example:

```text
👤 Victim
   ↓
⌨️ Typing Password
   ↑
👀 Attacker Watching
```

---

# 4️⃣ Dumpster Diving 🗑️

Finding useful information by searching through **physical garbage/trash**.

Examples:

* 📄 Documents
* 📝 Notes
* 📦 Labels
* 📑 Printed information

---

# 5️⃣ Digital Dumpster Diving 💻🗑️

Finding information from **old digital equipment or storage devices**.

> 💡 Simply formatting a storage device may not always securely erase the data.

Examples:

* 💽 Old hard drives
* 💻 Old computers
* 📱 Old phones
* 💾 USB drives

> ⚠️ For sensitive data, use proper **secure data-erasure methods** or physically destroy the storage device when appropriate.

---

# 6️⃣ Pretexting 🎭

Creating a **fake story or situation (pretext)** to convince someone to give information or perform an action.

### Common Examples

#### ❤️ Romance Scam

An attacker creates a fake romantic relationship to manipulate the victim.

#### 👵 Grandparent Scam

An attacker pretends to be a grandchild or another family member who urgently needs help.

#### 💰 Cryptocurrency Scam

An attacker uses fake investment opportunities or cryptocurrency-related promises to trick victims.

#### 🐋 Whaling Attack

A highly targeted attack against **high-value individuals**, such as:

* 👔 CEOs
* 💼 Executives
* 🏛️ Senior leaders
* 💰 People with access to valuable information

#### 👤 Impersonation

The attacker **pretends to be someone else**, such as:

* A friend
* Coworker
* Manager
* Company representative

---

# 7️⃣ Baiting 🪤

Uses a **false promise or attractive offer** to trick someone into taking an action.

> 🎁 The attacker provides something that looks interesting or valuable to make the victim take the bait.

---

# 8️⃣ Scareware 🚨

Uses **fear** to manipulate the victim.

It may show:

* 🚨 False security alerts
* ⚠️ Fake warnings
* 💻 Fake virus notifications
* ❌ Fictitious problems

The goal is to make the victim panic and perform an action.

---

# 9️⃣ Tailgating / Piggybacking 🚪

Following an **authorized person** into a restricted area without authorization.

```text
👤 Authorized Person
        ↓
🚪 Restricted Area
        ↑
👤 Attacker follows
```

Another technique is **asking or begging to enter**, making it seem like there is a legitimate reason.

> 💡 Example: "I forgot my access card. Can you hold the door for me?"

---

# 🔟 Eavesdropping 👂

Listening to someone's conversation **without their knowledge or permission**.

Examples:

* 👂 Listening to a private conversation
* 📞 Listening to phone calls
* 🗣️ Listening to sensitive discussions

---

# 🛡️ Prevention Methods

## 1️⃣ Awareness 🧠

Learn how social engineering attacks work.

> **Think before you trust.**

---

## 2️⃣ Multi-Step Verification 🔐

Use **MFA (Multi-Factor Authentication)** to add another layer of security.

Even if an attacker gets your password, they may still be unable to access the account.

---

## 3️⃣ Use a Password Manager 🔑

Use a trusted **password manager** to:

* Generate strong passwords
* Store passwords securely
* Avoid reusing the same password

---

# 📱 Social Media Hacking

> 🎯 **Main idea:** Attack the **user**, not necessarily the social media platform itself.

* 🧠 Use **social engineering** to trick the user.
* 🔐 The target can be sensitive information such as passwords, OTPs, or session information.

---

# 🧰 Social Engineering Toolkit (SEToolkit)

**SEToolkit** is a built-in security testing tool in **Kali Linux**.

It can be started with:

```bash
sudo setoolkit
```

> 💡 SEToolkit can be used for security awareness and authorized penetration testing.

---

# 🌐 SEToolkit — Web Attack Concepts

When SEToolkit starts, it provides different menus for different types of security-testing activities.

A common path discussed in class is:

```text
Social-Engineering Attacks
          ↓
Web Attack Vectors
          ↓
Credential Harvester Attack Method
          ↓
Web Template / Site Cloner / Custom Import
```

---

## 1️⃣ Web Template

Web Template provides **pre-built web pages/templates** for security-awareness demonstrations.

The idea is:

```text
Pre-built Template
       ↓
Fake Login Page
       ↓
User Interaction
       ↓
Credentials may be captured
```

> 🚨 **Important:** A fake login page can capture credentials in plain text. 

---

## 2️⃣ Site Cloner 🌐

**Site Cloner** is used to reproduce the appearance/structure of a website for an authorized security test.
- usual use this when the web site use HTTP because in this case we can see the password in plan text

The important concept from the class is:

```text
Original Website Login Page URL
       ↓
   Clone / Fake Page
       ↓
User interacts with it
       ↓
Test how credentials are handled
```

### 🔐 HTTP vs HTTPS

* **HTTP** → Data is sent without transport encryption.
* **HTTPS** → Data is protected by TLS while being transmitted.

> 💡 HTTPS protects data **in transit**, but it does **not** make a phishing website legitimate or automatically protect credentials if the user gives them directly to an attacker-controlled page.

---

## 📁 SEToolkit Reports

SEToolkit can save information generated during testing in its report directories.

For example, the class may show a path under:

```text
/root/.set/reports/
```

---

# 3️⃣ Custom Import 🛠️

A custom page can be created using:

```text
HTML
CSS
JavaScript
```

```text
HTML + CSS + JavaScript
          ↓
    Custom Test Page
          ↓
     Security Testing
```

---

# 🖥️ LAN Testing

In a local lab, another device on the same network can access a test server using the server's local IP address.

```text
┌──────────────┐
│ Kali Linux   │
│ Test Server  │
└──────┬───────┘
       │
      LAN
       │
       ↓
┌──────────────┐
│ Test Device  │
└──────────────┘
```

> 💡 **Important:** SEToolkit itself is not simply "LAN only." Whether a test is reachable from outside the LAN depends on networking, routing, firewall/NAT configuration, and how the test service is exposed.

---

# 🌍 WAN / Internet Testing

For security testing over the internet, the test system needs to be **properly and legally exposed** to the network.

Tools such as **SocialFish** and **Zphisher** are examples commonly discussed in security-training contexts, but they can be abused for credential theft.

---

# 📱 Social Media Account Attacks

Social-media accounts can also be targeted through different techniques.

For example:

## 🔢 OTP-Based Attacks

Some attacks attempt to trick users into revealing their **OTP (One-Time Password)**.

```text
Attacker
   ↓
Social Engineering
   ↓
Victim
   ↓
OTP
```

---

## 🤖 Telegram Bot-Based Phishing

Attackers can abuse bots to communicate with victims or distribute malicious links.

```text
Attacker
   ↓
🤖 Bot
   ↓
Victim
   ↓
Malicious Link
```

---

## 🌐 API-Integrated Phishing

Attackers may combine a phishing page with APIs or backend services to automate parts of an attack.

> 💡 The security lesson is that APIs can become part of an attack chain when they are abused.

---

## 🔑 Session Hijacking

Instead of stealing the password directly, an attacker may try to obtain or abuse a user's **authenticated session**.

```text
Login
  ↓
Authenticated Session
  ↓
Session Token / Cookie
  ↓
⚠️ If stolen → Account may be compromised
```

> 🛡️ Protect session cookies, use HTTPS, enable MFA, keep software updated, and log out of sessions you don't recognize.

---


# 🧠 Quick Memory

```text
🎣 Phishing       → Malicious message/site
📞 Vishing        → Voice + Phishing
👀 Shoulder Surfing → Watch someone enter information
🗑️ Dumpster Diving → Physical trash
💻 Digital Dumpster → Old digital equipment
🎭 Pretexting     → Fake story/situation
🪤 Baiting        → False promise
🚨 Scareware      → Fear + fake warning
🚪 Tailgating     → Follow authorized person
👂 Eavesdropping  → Secretly listen
```

```text
📱 Social Media Attacks
        ↓
   🧠 Social Engineering
        ↓
   ┌────┼──────────────┐
   ↓    ↓              ↓
 OTP   Phishing    Session Attacks
   ↓    ↓              ↓
 User  Credentials   Session
```


> 🔥 **Remember:**
>
> **Social Engineering = Manipulating people to get information or access.**
>
> 🧠 **Awareness + Verification + Strong Authentication = Better Protection**


### 🧰 SEToolkit

```text
SEToolkit
    ↓
Social Engineering
    ↓
Web Attack Vectors
    ↓
Credential Harvester
    ↓
┌────────────┬──────────────┐
↓            ↓              ↓
Template   Site Cloner   Custom Import
```

> 🔥 **Main lesson:**
> **Social-media "hacking" often means attacking the human rather than breaking the social-media platform itself.**
> **Awareness + MFA + protecting OTPs + protecting sessions = strong defense.**
> **Indicator of compromise (IOC)**
**IOCs such as malware signatures or domain names provide evidence of security breaches and details about them.**