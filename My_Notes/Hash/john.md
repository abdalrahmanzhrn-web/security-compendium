---
tags: [ "cracking", "john-the-ripper", "jtr", "md5", "hash" ]
aliases: [ "JtR Usage", "John Cracking" ]
created: 2025-12-21
---

# 🔨 John the Ripper (JtR) Usage

> [!info] Scenario
> In this example, we have a file (`hashshsh.txt`) containing a raw MD5 hash, and we are using a wordlist (`rockyou.txt`) to crack it.

## 1. The Cracking Command
To start the attack, you need to specify the format and the wordlist.

- Syntax: john --format=<format> --wordlist=<path_to_wordlist> <hash_file>
- Example (Cracking MD5):

```bash title:John_Command
john --format=raw-md5 --wordlist=rockyou.txt hashshsh.txt
```

When John cracks a hash, it prints the password immediately.

```text
Loaded 1 password hash (Raw-MD5 [MD5 128/128 AVX 4x3])
...
skins            (?)
...
1g 0:00:00:00 DONE ...
```

## Viewing Cracked Passwords

If you close the terminal or want to see the results later, John won't re-crack them. You must use the `--show` flag.

- Syntax: john --show --format=<format> <hash_file>

```bash title:John_Command
john --show --format=raw-md5 hashshsh.txt
```
