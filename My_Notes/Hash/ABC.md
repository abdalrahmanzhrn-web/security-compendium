---
tags: [ "hashing", "cryptography", "cracking", "hash-id", "reference" ]
aliases: [ "Hash Types", "Hash Identification" ]
created: 2025-12-21
---

# 🔑 Hash Identification Cheat Sheet

> [!info] Identification First
> You cannot crack a hash if you don't know what algorithm created it. Check the **Length** and the **Prefix** ($sign) first.

## 1. Common Raw Hashes (Hex Only)
These usually look like random hexadecimal strings (0-9, A-F) with no special characters.

| Type | Length (Chars) | Charset | Signature / Notes |
| :--- | :--- | :--- | :--- |
| **MD5** | 32 | 0-9, a-f | Very common, older systems. |
| **NTLM** | 32 | 0-9, a-f | Windows Password Hash. Indistinguishable from MD5 visually; context matters. |
| **SHA-1** | 40 | 0-9, a-f | Git commits, older certs. |
| **SHA-256** | 64 | 0-9, a-f | Standard modern crypto (Bitcoin, etc.). |
| **SHA-512** | 128 | 0-9, a-f | Very long hex string. |

## 2. Salted / Linux Hashes (Look for `$`)
These are modular crypt hashes used in system password files (like `/etc/shadow`). They contain the salt and settings in the string.

| Type | Prefix | Length | Notes |
| :--- | :--- | :--- | :--- |
| **MD5-Crypt** | `$1$` | Variable | Older Linux/Unix. |
| **Bcrypt** | `$2a$`, `$2b$`, `$2y$` | 60 | Standard for many web apps. Slow to crack. |
| **SHA-256-Crypt**| `$5$` | 43 (Hash) | Modern Linux default (often). |
| **SHA-512-Crypt**| `$6$` | 86 (Hash) | Modern Linux default (stronger). |
| **Argon2** | `$argon2` | Variable | Memory-hard, very resistant to GPU cracking. |

## 3. Identification Tools
If you can't tell by eye, use these tools.

- Method 1: Interactive Tool
- Save hash to file or paste into tool
- Method 2: CLI Tool (Python)
- Syntax: hashid <file> or <hash_string>

```bash title:Hash_ID_Tools
hash-identifier

hashid hash.txt
```

> [!tip] Online Alternatives "Better use generators/identifiers online."

- Sometimes online tools (like [CipherIdentifier](https://www.google.com/search?q=https://www.cipheridentifier.com/) or [Hashes.com](https://hashes.com/en/tools/hash_identifier)) are faster and more up-to-date than local CLI tools.
