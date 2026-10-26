---
tags: [ "python", "scripting", "os-module", "file-system", "ransomware-dev" ]
aliases: [ "File Traversal", "os.walk" ]
created: 2025-12-21
---

# 📂 File System Traversal (`os.walk`)

> [!danger] Cyber Context
> This function is the "crawler" engine. Whether you are writing a virus scanner or ransomware, this is the code used to visit every single folder and list every single file.

## 1. Basic Usage (Listing Files)
`os.walk` generates the file names in a directory tree by walking the tree either top-down or bottom-up. It returns a tuple of 3 things: `(dirpath, dirnames, filenames)`.

- Walk through the D: drive
- 'files' is just a list of names (e.g., ['passwords.txt', 'photo.jpg'])

```python title:Basic_Walk
import os

for dir, subdirs, files in os.walk(r'D:\\'):

    print(files)
```
