# 🔐 Cryptography

> **Cryptography = Crypto + Graphy**
>
> * **Crypto** → Hidden / Secret
> * **Graphy** → Writing
>
> 🧠 **Cryptography = Secret/secure writing and communication**

---

# 🎯 What Is Cryptography Used For?

Cryptography is mainly used for:

* 🔒 **Encryption** → Confidentiality
* 🛡️ **Integrity** → Making sure data has not been altered
* 🔑 **Authentication** → Verifying identity
* ✍️ **Digital signatures** → Proving who signed/sent something

---

# 🔤 Cipher

A **cipher** is an algorithm used to **encrypt and decrypt messages**.

### 🔄 Basic Process

```text
📝 Plaintext
     ↓
🔐 Encryption Algorithm + Key
     ↓
🔒 Ciphertext
     ↓
🔓 Decryption Algorithm + Key
     ↓
📝 Plaintext
```

> 💡 The **key** is a value used by the cryptographic algorithm to control the encryption/decryption process.

---

# 🔑 Types of Cryptographic Keys

## 1️⃣ Symmetric Cryptography

Uses the **same key** for encryption and decryption.

```text
        🔑 Same Key
       ↙          ↘
📝 Plaintext      🔒 Ciphertext
       ↓          ↑
       └──────────┘
```

### Example

```text
AES
DES
```

---

## 2️⃣ Asymmetric Cryptography

Uses **different keys**:

* 🔓 **Public Key** → Can be shared
* 🔐 **Private Key** → Must be kept secret

```text
🔓 Public Key  → Encryption
🔐 Private Key → Decryption
```

### Examples

```text
RSA
ElGamal
```

---

# 🧩 Types of Ciphers

## 1️⃣ Block Cipher

Encrypts data in **fixed-size blocks**.

Examples:

* AES → 128-bit blocks
* DES → 64-bit blocks

---

## 2️⃣ Stream Cipher

Encrypts data **bit-by-bit or byte-by-byte** rather than processing a fixed-size block at once.

---

# 🔐 Types of Symmetric Ciphers

## 1️⃣ Caesar Cipher 🏛️

The Caesar cipher shifts the alphabet by a fixed number.

### Example: Shift by 3

```text
Normal:
A B C D E F G ... X Y Z

Shift:
D E F G H I J ... A B C
```

So:

```text
A → D
B → E
C → F
```

> 💡 **Caesar shift by 3 = ROT3**

---

# 2️⃣ Keyword Cipher 🔑

Uses a **keyword** to create a new alphabet.

### Example

```text
Key = HACK
```

First put the unique letters of the keyword:

```text
H A C K
```

Then add the remaining alphabet letters, removing duplicates:

```text
H A C K B D E F G I J L M N O P Q R S T U V W X Y Z
```

So the alphabet changes from:

```text
Normal:
A B C D E F G H I J K L M ...

Cipher:
H A C K B D E F G I J L M ...
```

> 💡 **Duplicate letters are removed** when creating the new alphabet.

---

# 3️⃣ ROT (Rotation) 🔄

ROT means **rotation**.

The alphabet is rotated by a specific number.

Examples:

```text
ROT3
ROT13
ROT47
```

### ROT13

```text
A → N
B → O
C → P
...
N → A
```

> 💡 ROT13 is commonly used for simple text obfuscation, **not secure encryption**.

---

# 4️⃣ Data Encryption Standard (DES) 🔐

### 📜 History

* Developed by **IBM** in the early 1970s.
* Became a U.S. standard through **NIST** in 1977.
* Used for data encryption/protection.
* Became an important foundation in the history of modern cryptography.

### ⚙️ DES Features

* 🔲 **Block cipher**
* 📦 Block size → **64 bits**
* 🔑 Effective key size → **56 bits**
* ➕ 8 additional bits are used for parity.

> ⚠️ DES is now considered **insecure/outdated** because its 56-bit key is too small against modern brute-force attacks.

NIST eventually withdrew DES and modern systems moved to stronger algorithms such as **AES**.

---

# ⚙️ How DES Works

The main steps are:

### 1️⃣ Initial Permutation

Uses a **P-box (Permutation Box)** to rearrange the bits.

### 2️⃣ Feistel Rounds

DES performs **16 rounds**.

### 3️⃣ Final Permutation

Another permutation is applied at the end.

---

# 🔄 Feistel Round

The input is divided equally into:

```text
┌──────────────┬──────────────┐
│ Left Half    │ Right Half   │
└──────────────┴──────────────┘
```

Each round involves operations such as:

```text
Expansion
   ↓
Substitution
   ↓
Permutation
   ↓
XOR with Subkey
```

DES performs this process for **16 rounds**.

---

# 🚀 Advanced Encryption Standard (AES)

> 🔥 **AES is still widely used today.**

### 📌 Features

* 🔲 Block cipher
* 📦 Block size → **128 bits**
* 🔑 Key sizes:

  * AES-128
  * AES-192
  * AES-256

### 👨‍💻 Developers

AES was developed by Belgian cryptographers:

* **Vincent Rijmen**
* **Joan Daemen**

Their algorithm was originally called **Rijndael** and was selected by NIST as the AES standard in 2001.

---

# 🔢 AES Key Sizes & Rounds

| AES        | Key Size | Number of Rounds |
| ---------- | -------: | ---------------: |
| 🔐 AES-128 | 128 bits |               10 |
| 🔐 AES-192 | 192 bits |               12 |
| 🔐 AES-256 | 256 bits |               14 |

> 💡 AES-256 has the largest key size, but saying "AES-128 is weak" is too broad. **AES-128 is still considered secure for many applications.**

---

# ⚙️ AES Round Operations

A typical AES round includes:

1. 🔄 **SubBytes**
2. ↔️ **ShiftRows**
3. 🧩 **MixColumns**
4. 🔑 **AddRoundKey**

> ⚠️ The final AES round does **not** use MixColumns.

---

# 🧩 Substitution Box (S-Box)

The **S-Box** is used during the **SubBytes** step.

It replaces each byte with another byte according to a fixed lookup table.

Example from the AES S-Box:

```text
       0     1
    ┌─────┬─────┐
  0 │ 63  │ 7c  │
    ├─────┼─────┤
  1 │ ca  │ 82  │
    ├─────┼─────┤
  2 │ 67  │ fd  │
    ├─────┼─────┤
  3 │ 04  │ c7  │
    └─────┴─────┘
```

For example:

```text
Input: 31
   ↓
AES S-Box
   ↓
Output: c7
```

---

# ↔️ ShiftRows

The AES state is arranged into rows.

### Rules:

```text
1st row → No shift
2nd row → Shift 1 position to the left
3rd row → Shift 2 positions to the left
4th row → Shift 3 positions to the left
```

Example:

```text
Before:

A B C D
E F G H
I J K L
M N O P

After:

A B C D
F G H E
K L I J
P M N O
```

---

# 🔐 Uses of AES

AES is widely used for:

* 💾 **Data encryption**
* 🌐 **Secure communication**
* 🔐 **Cryptographic protocols**
* 🏛️ **Government and military applications**
* 💻 **Storage encryption**

---

# 🔑 Important Cryptography Terms

## Secret Key

A secret key is a key that must be kept secret in **symmetric cryptography**.

> 💡 Example: DES uses a **56-bit effective key**.

---

## Initialization Vector (IV)

An **IV** is an additional value used with some encryption modes.

It helps ensure that encrypting the same plaintext multiple times does not always produce the same ciphertext.

```text
Plaintext + Key + IV
          ↓
      Encryption
          ↓
      Ciphertext
```

> 💡 The IV is generally **not a secret key**. Its purpose and handling depend on the encryption mode.

---

# 🔄 Encryption Modes

## 1️⃣ ECB — Electronic Codebook

Each block is encrypted **independently**.

```text
Block 1 → Encrypt → Cipher 1
Block 2 → Encrypt → Cipher 2
Block 3 → Encrypt → Cipher 3
```

> ⚠️ ECB can reveal patterns in data and is generally **not recommended for encrypting structured data**.

---

# 2️⃣ CBC — Cipher Block Chaining

Each plaintext block is XORed with the **previous ciphertext block** before encryption.

```text
Plaintext 1 + IV
      ↓
  Encryption
      ↓
Ciphertext 1
      ↓
Plaintext 2 + Ciphertext 1
      ↓
  Encryption
      ↓
Ciphertext 2
```

> 💡 CBC requires an IV for the first block.

---

# ⚠️ Limitation of Symmetric Cryptography

The main problem is **key distribution**.

Because the same secret key is used for encryption and decryption:

```text
Sender 🔑 ─────────── 🔑 Receiver
```

The sender and receiver need to securely share the secret key first.

---

# 🔓 Asymmetric Encryption

Asymmetric cryptography uses two different keys:

### 🔓 Public Key

* Anyone can access it.
* Can be shared publicly.

### 🔐 Private Key

* Must be kept secret.
* Only the owner should have access to it.

For confidentiality:

```text
Sender
  ↓
🔓 Receiver's Public Key
  ↓
🔒 Encrypted Data
  ↓
Receiver
  ↓
🔐 Receiver's Private Key
  ↓
📝 Original Data
```

---

# 🔢 Types of Asymmetric Cryptography

## 1️⃣ RSA

**RSA** was developed by:

* 👨 **Ron Rivest**
* 👨 **Adi Shamir**
* 👨 **Leonard Adleman**

### Features

* Uses a public key and private key.
* Supports different key sizes.
* Common examples include 512-bit,1024-bit and 2048-bit keys.

> 💡 RSA is widely used for digital signatures and key establishment, although modern protocols often use elliptic-curve cryptography instead.

### 🔑 SSH

SSH can generate a public/private key pair using:

```bash
ssh-keygen
```

The keys are normally stored under:

```bash
~/.ssh/
```

You can list the directory with:

```bash
ls ~/.ssh
```

> ⚠️ `known_hosts` contains **host keys for servers you have connected to**. It is not your private key.

You can view it with:

```bash
cat ~/.ssh/known_hosts
```

---

# 2️⃣ ElGamal

Developed by **Taher ElGamal**.

It is an asymmetric cryptographic algorithm based on the **discrete logarithm problem**.

> 💡 It is less commonly encountered in modern applications than RSA and newer public-key schemes.

---

# 🧠 3 Important Cryptography Concepts

These three are easy to confuse:

---

## 1️⃣ Encoding / Decoding 📝

> **No secret key is required.**

The purpose is usually to change data into another representation.

Examples:

* ROT13
* Base2
* Base64

```text
Original Data
     ↓
  Encoding
     ↓
Encoded Data
```

> ⚠️ **Encoding is NOT encryption.**

Anyone who knows the encoding method can decode it.

---

# 2️⃣ Encryption / Decryption 🔐

> **Uses a key.**

Examples:

* AES
* DES
* RSA

```text
Plaintext
   ↓
🔑 Key + Encryption
   ↓
Ciphertext
   ↓
🔑 Key + Decryption
   ↓
Plaintext
```

The goal can be **confidentiality**.

---

# 3️⃣ Hash Function #️⃣

A hash function converts data into a fixed-length value.

```text
Input Data
    ↓
 Hash Function
    ↓
Hash Value
```

Hashing is designed to be **one-way**.

> 💡 We normally don't "decrypt" a hash. Instead, we compare a newly calculated hash with the stored hash.

### Examples

* MD5
* SHA-256

### 🧂 Salt

A **salt** is a random value added when hashing passwords.

```text
Password + Salt
       ↓
   Hash Function
       ↓
     Hash
```

> 💡 Salting makes password hashes more resistant to attacks such as precomputed rainbow tables.

> ⚠️ **MD5 should not be used for password storage.** Modern password storage should use dedicated password-hashing functions such as Argon2, scrypt, or bcrypt.

---

# 🧠 Quick Memory

```text
🔐 CRYPTOGRAPHY
      │
      ├── 🔒 Symmetric
      │      ├── AES
      │      └── DES
      │
      └── 🔓 Asymmetric
             ├── RSA
             └── ElGamal


📝 Encoding
   → No key
   → Base64, ROT13

🔐 Encryption
   → Uses key
   → AES, DES, RSA

#️⃣ Hashing
   → One-way
   → SHA-256
   → MD5 (old/insecure for security use)
```

---

# 🔥 Final Revision

| Concept              | Main Idea                     | Example          |
| -------------------- | ----------------------------- | ---------------- |
| 📝 **Encoding**      | Change representation         | Base64, ROT13    |
| 🔐 **Encryption**    | Protect confidentiality       | AES, RSA         |
| #️⃣ **Hashing**      | One-way transformation        | SHA-256          |
| 🔑 **Symmetric**     | Same key                      | AES, DES         |
| 🔓 **Asymmetric**    | Public + private keys         | RSA              |
| 📦 **Block Cipher**  | Fixed-size blocks             | AES, DES         |
| 🌊 **Stream Cipher** | Bit/byte stream               | Stream ciphers   |
| 🔄 **IV**            | Adds uniqueness/randomization | CBC              |
| 🧂 **Salt**          | Protect password hashes       | Password storage |

> 💡 **Remember:**
>
> **Encoding → Represent**
> **Encryption → Hide**
> **Hashing → Verify**
> **Symmetric → Same key**
> **Asymmetric → Two keys**


# #️⃣ Hashing

> **Hashing** = Converting data into a fixed-length hash value using a hash function.

```text
Plain Text / File
       ↓
   Hash Function
       ↓
   Hash Value
```

---

## 🔓 Hash Cracking

Changing a hash back into the original plaintext is commonly called **hash cracking**.

> 💡 More accurately, we usually **guess possible inputs** and compare their hashes, because a cryptographic hash is designed to be one-way.

```text
Password
   ↓
  Hash
   ↓
🔍 Try possible passwords
   ↓
Compare the hashes
   ↓
Possible original password
```

---

# 🧂 Salt + Password

A **salt** is a random value added to a password before hashing.

```text
Password + Salt
       ↓
   Hash Function
       ↓
   Password Hash
```

> 💡 Salt makes cracking more difficult because the same password will produce different hashes when different salts are used.

### Without Salt

```text
password123
     ↓
   Hash A
```

### With Salt

```text
password123 + Salt1 → Hash A
password123 + Salt2 → Hash B
```

---

# 🔢 MD5

**MD5 = Message-Digest Algorithm 5**

### Features

* 📏 **128-bit** hash
* 🔢 Usually represented as **32 hexadecimal characters**
* 🔐 Produces a fixed-length hash

Example format:

```text
32 hexadecimal characters
↓
5f4dcc3b5aa765d61d8327deb882cf99
```

> ⚠️ **MD5 is not considered secure for modern cryptographic use.** It should not be used for password storage or security-sensitive integrity applications where collision resistance matters.

---

# 🎯 Purpose of Hashing

Hashing can be used for:

### 1️⃣ Password Storage 🔑

Applications can store password hashes instead of storing the actual passwords.

### 2️⃣ File Integrity 📁

A hash can help determine whether a file has been **changed or altered**.

```text
Original File → Hash A

File Later → Hash B

Hash A == Hash B
      ↓
Likely unchanged
```

> 💡 Hashing itself does **not provide confidentiality**. It is mainly useful for integrity and verification.

---

# 🔤 Encoding / Encryption

Different techniques can change the representation of data.

Examples:

```text
Base2
Base8
Base16
Base58
ROT
Base64
```

> ⚠️ **Encoding is not encryption.** Encoding normally does not use a secret key and is not intended to provide confidentiality.

---

# 🧰 Tools

## 💻 1. Terminal-Based Tools

### 🔍 `hashid`

Used to help identify the possible type of a hash.

```bash
hashid 'hash value'
```

> 💡 `hashid` does not crack the hash. It helps identify what hash algorithms the value might match.

---

## 🔤 `base64`

Base64 is an **encoding**, not encryption.

### Encode

```bash
echo "hello" | base64
```

### Decode

```bash
echo "aGVsbG8=" | base64 -d
```

```text
hello
```

> 🧠 **Remember:**
>
> `base64` → Encode
> `base64 -d` → Decode

---

# 🌐 2. Web-Based Tools

## 🧪 CyberChef

CyberChef can be used for many different encoding, decoding, encryption, and data-processing operations.

### Example

```text
Input
  ↓
CyberChef
  ↓
To Base64
  ↓
Encoded Output
```

For decoding:

```text
Encoded Input
      ↓
CyberChef
      ↓
From Base64
      ↓
Original Data
```

---

## ✨ Magic

If you don't know what type of encoding or transformation was used, **Magic** can help identify common formats automatically.

```text
Unknown Data
     ↓
   ✨ Magic
     ↓
Possible Encoding / Format
```

---

## 🔗 URL Encode / Decode

For URL-related data:

* **URL Encode** → Encode special characters for URLs
* **URL Decode** → Decode URL-encoded data

---

# 🔄 Multiple Transformations

We can apply **one or more transformations** to the same data.

For example:

```text
Plain Text
    ↓
Base64
    ↓
URL Encode
    ↓
Final Output
```

Or the reverse:

```text
Final Output
    ↓
URL Decode
    ↓
Base64 Decode
    ↓
Plain Text
```

> 💡 This is why when analyzing suspicious data, we sometimes need to identify **multiple layers**.

---

# 🔓 Tools for Hash Cracking

## 🌐 CrackStation

**CrackStation** can be used to look up/crack some common hashes using its database.

> 💡 It is more useful for hashes that are **not salted** and are already present in its database.

```text
Hash
 ↓
CrackStation
 ↓
Database Lookup
 ↓
Possible Plaintext
```

> ⚠️ A salted hash is much harder to crack using simple database lookups.

---

# 🧰 Useful Tool for Pentesting

You noted:

```text
app.pentester.com/login
```

> 💡 Keep this as a **practice/testing environment** only if it is an authorized lab provided for learning.

---

# 🧠 Quick Memory

```text
#️⃣ HASHING
One-way transformation
        ↓
Password → Hash

🧂 SALT
Password + Random Salt
        ↓
      Hash
        ↓
Harder to crack

🔢 MD5
128 bits
32 hexadecimal characters
⚠️ Not secure for modern password storage

🔤 ENCODING
No secret key
Examples:
Base64
Base16
Base58
ROT

🔐 ENCRYPTION
Uses a key
Examples:
AES
RSA

🧰 TOOLS
hashid      → Identify possible hash type
base64      → Encode
base64 -d   → Decode
CyberChef   → Many transformations
CrackStation → Hash database/cracking
```

---

# 🔥 Most Important Difference

| Technique             | Key?            | Reversible?                   | Main Purpose             |
| --------------------- | --------------- | ----------------------------- | ------------------------ |
| 🔤 **Encoding**       | ❌ No            | ✅ Yes                         | Data representation      |
| 🔐 **Encryption**     | ✅ Yes           | ✅ Yes, with key               | Confidentiality          |
| #️⃣ **Hashing**       | ❌ No            | ❌ Not designed to be reversed | Integrity / verification |
| 🧂 **Salted Hashing** | ❌ No secret key | ❌                             | Password protection      |

> **Remember:**
>
> 🔤 **Encoding → Change the format**
> 🔐 **Encryption → Hide the data**
> #️⃣ **Hashing → Verify the data**
> 🧂 **Salt → Make password hashes harder to attack**

# 📚 Wordlists & Obfuscation — Cybersecurity Notes

## 🔤 What is a Wordlist?

A **wordlist** is a set/list of words or possible strings.

**Word + List = Wordlist**

Wordlists are commonly used in security testing for things like:

* Password auditing
* Username discovery
* Directory/file discovery
* Other authorized brute-force testing

---

# 🛠️ Custom Wordlist Tools

There are different tools that can help us create custom wordlists.

## 1. 🔎 CeWL

**CeWL** works based on a **URL/website**.

It crawls a website and collects words that appear on the site to create a custom wordlist.

### 🔹 Basic usage

```bash
cewl <URL>
```

### 🔹 `-vvv`

```bash
cewl <URL> -vvv
```

`-vvv` gives **more detailed/verbose information** while CeWL is running.

### 🔹 Save the wordlist to a file

```bash
cewl <URL> | tee geez_wordlist.txt
```

This:

1. Runs CeWL on the URL.
2. Gets the words from the website.
3. Displays them in the terminal.
4. Saves them into `geez_wordlist.txt`.

### 🔹 Minimum word length

```bash
cewl <URL> -m <number>
```

`-m` specifies the **minimum word length**.

For example:

```bash
cewl <URL> -m 6
```

➡️ Only words with **6 or more characters** are included.

---

# 2. ⚙️ Crunch

**Crunch** is a popular and flexible open-source wordlist generator.

It generates combinations of characters according to the rules we provide.

### 🔹 Basic syntax

```bash
crunch <min_len> <max_len>
```

* `min_len` → minimum length
* `max_len` → maximum length
* **`max_len` is included**

For example:

```bash
crunch 4 6
```

➡️ Generates strings from **4 to 6 characters**.

---

## 🔣 Crunch Pattern Symbols

Crunch has special symbols that represent different character types:

| Symbol | Meaning            |
| ------ | ------------------ |
| `@`    | lowercase letters  |
| `,`    | uppercase letters  |
| `%`    | numbers            |
| `^`    | special characters |

### Example

```bash
crunch 8 8 -t ,text@@
```

Here:

* `,` → uppercase letter
* `@` → lowercase letter
* `text` → fixed text

---

## 🔀 Permutations

The `-p` option can be used to generate **permutations** of the supplied words/strings.

```bash
crunch <min_len> <max_len> -p "text"
```

Example:

```bash
crunch 1 1 -p "cat dog"
```

The important idea is that Crunch can rearrange the supplied words into different orders.

---

## 🧩 Combining Patterns

We can combine different Crunch pattern symbols.

Example:

```bash
crunch 14 14 -t ,meklit@m%%we^
```

Here we have:

```text
, meklit @ m %% we ^
```

* `,` → uppercase letter
* `meklit` → fixed text
* `@` → lowercase letter
* `m` → fixed text
* `%%` → two numbers
* `we` → fixed text
* `^` → special character

### 📏 Counting the length

The pattern is **14 characters long**, so:

```bash
crunch 14 14 -t ,meklit@m%%we^
```

Both minimum and maximum are `14` because we want **exactly 14 characters**.

---

## 💾 Save a Wordlist

We can save the generated wordlist into a file using `-o`.

```bash
crunch <min_len> <max_len> abcd -o test.txt
```

Example:

```bash
crunch 4 4 abcd -o test.txt
```

➡️ The generated wordlist is saved in:

```text
test.txt
```

> ⚠️ Large Crunch wordlists can become extremely large very quickly. Always calculate/estimate the size before generating one.

---

# 3. 🔐 John the Ripper

**John the Ripper** is a password-auditing and password-cracking tool.

Basic syntax:

```bash
john [options] <path>
```

### 🔹 Using a wordlist with an MD5 hash

```bash
sudo john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-md5 hash_contain_file
```

Here:

| Part                               | Meaning                              |
| ---------------------------------- | ------------------------------------ |
| `sudo`                             | Run with elevated privileges         |
| `john`                             | Start John the Ripper                |
| `--wordlist=...`                   | Use the specified wordlist           |
| `/usr/share/wordlists/rockyou.txt` | Wordlist                             |
| `--format=raw-md5`                 | Tell John the hash format is raw MD5 |
| `hash_contain_file`                | File containing the hash             |

### 🧠 Important idea

John does **not decrypt the MD5 hash**.

Instead, it takes candidate passwords from the wordlist, hashes them, and compares the result with the target hash.

```text
Wordlist
   ↓
Candidate password
   ↓
      MD5
       ↓
Generated hash
       ↓
Compare with target hash
       ↓
Match? ✅
```

---

# 🕵️ Obfuscation

**Obfuscation** means making code or data **harder for humans to understand or analyze** while keeping its functionality.

For example:

```text
Normal source code
       ↓
   Obfuscation
       ↓
Harder-to-read code
```

### 🎯 Purpose

Obfuscation can be used to:

* Hide the meaning of source code
* Make reverse engineering harder
* Protect intellectual property
* Make analysis more difficult

> ⚠️ Obfuscation is **not encryption**. The original functionality is still there; it is just made harder to understand.

---

# 🧠 Quick Memory

```text
CeWL    → Website → Custom wordlist
Crunch  → Generate word combinations
John    → Password auditing/cracking
Obfuscation → Make code harder to understand
```

### ⭐ Remember

**CeWL → Collect**

**Crunch → Create**

**John → Crack/Audit**

**Obfuscation → Hide the code's meaning**
