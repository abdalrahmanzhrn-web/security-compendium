---
tags: [ "python", "cryptography", "aes", "encryption", "decryption", "symmetric" ]
aliases: [ "AES CTR Mode", "Symmetric Encryption" ]
created: 2025-12-21
---

# 🔐 AES Encryption (CTR Mode)

> [!info] Concept
> **Symmetric Encryption:** One key (`Key`) is used for both locking and unlocking.
> **CTR (Counter) Mode:** Converts the block cipher into a stream cipher. It is very fast and allows parallel processing, making it ideal for ransomware that needs to encrypt large files quickly.

## 1. Generating a Key
You need a random 16-byte (128-bit) key.

- Generate 16 random bytes
- Output Example: b'\x13\xe8\xe3\x1a\xe7x>\x12\x8e\x9f4\x96\xfe\xce\x15='

```python title:Generate_Key.py
from Crypto import Random

key = Random.get_random_bytes(16)
print(key)
```

## 2. Encryption Function

This function takes the key and the text, sets up a counter, and encrypts the data.

- Create a 128-bit counter
- Create the cipher object in CTR mode
- Encrypt (Encode string to bytes first)
- --- Usage ---

```python
from Crypto import Random
from Crypto.Cipher import AES
from Crypto.Util import Counter

def encrypt_aes_ctr(key, plaintext):

    counter = Counter.new(128)

    cipher = AES.new(key, AES.MODE_CTR, counter=counter)

    encrypted_data = cipher.encrypt(plaintext.encode('ascii'))
    print(encrypted_data)

Key = b'\x13\xe8\xe3\x1a\xe7x>\x12\x8e\x9f4\x96\xfe\xce\x15='
encrypt_aes_ctr(Key, 'Attack at dawn!')
```

`
## 3. Decryption Function

To decrypt, you initialize the **same counter** and use the **same key**.

- Critical: The counter must start at the same point as encryption
- Decrypt
- --- Usage ---
- The strange bytes below are the output from the encryption step
- Output: b'Attack at dawn!'

```python
from Crypto import Random
from Crypto.Cipher import AES
from Crypto.Util import Counter

def decrypt_aes_ctr(key, ciphertext):

    counter = Counter.new(128)

    cipher = AES.new(key, AES.MODE_CTR, counter=counter)

    decrypted_data = cipher.decrypt(ciphertext)
    print(decrypted_data)

Key = b'\x13\xe8\xe3\x1a\xe7x>\x12\x8e\x9f4\x96\xfe\xce\x15='

cipher_text = b'b\x94\xae\x942\x90\x18\xcc\xb3\x8a\xdd\x8cm\x9bK'

decrypt_aes_ctr(Key, cipher_text)
```
