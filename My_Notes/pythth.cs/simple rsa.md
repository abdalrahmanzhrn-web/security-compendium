---
tags: [ "python", "cryptography", "rsa", "encryption", "decryption" ]
aliases: [ "RSA Workflow", "Python RSA" ]
created: 2025-12-21
---

# 🔐 RSA Encryption with Python

> [!warning] Data Type Criticality
> RSA works on **Bytes**, not Strings.
> * **Correct:** `b'secret message'`
> * **Wrong:** `'secret message'`
> * **Fix:** If you have a string, use `.encode()` before encrypting and `.decode()` after decrypting.

## 1. Generating Keys (The Setup)
First, you need to create the pair of keys. One to share (Public) and one to keep safe (Private).

- Generate a pair of keys (512 bits is fast for testing; use 2048+ for real security)
- Output: PublicKey(n, e)
- Output: PrivateKey(n, e, d, p, q)

```python title:1_Generate_Keys.py
#!/usr/bin/python3
import rsa

publicKey, privateKey = rsa.newkeys(512)

print(publicKey)

print(privateKey)
```

## 2. Encryption (Locking the Message)

You use the **Public Key** to encrypt. Anyone can lock the box, but only you can open it.

- 1. The message MUST be in bytes (note the b'...')
- 2. Define the Public Key (In a real script, you'd import this, not hardcode the huge numbers)
- Syntax: rsa.PublicKey(n, e)
- 3. Encrypt
- Output: b'\xc4d\x...\x12' (Unreadable binary garbage)

```python
#!/usr/bin/python3
import rsa

message = b'Chiiiittoooooo is tabbby gf'

PublicKey = rsa.PublicKey(10743020594262215908323...)

cipher = rsa.encrypt(message, PublicKey)

print(cipher)
```

## 3. Decryption (Unlocking the Message)

You use the **Private Key** to decrypt. This reverses the process.

- 1. The Encrypted Message (The binary garbage from step 2)
- 2. Define the Private Key
- Syntax: rsa.PrivateKey(n, e, d, p, q)
- 3. Decrypt
- Output: b'Chiiiittoooooo is tabbby gf'

```python
#!/usr/bin/python3
import rsa

cipher_text = b"'\xc4d\\t\xc4\xa1\x04\x04d\xc9..."

PrivateKey = rsa.PrivateKey(10743020594262215908323...)

decrypted_message = rsa.decrypt(cipher_text, PrivateKey)

print(decrypted_message)
```
