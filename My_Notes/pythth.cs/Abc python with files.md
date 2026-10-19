---
tags: [ "python", "scripting", "file-io", "read-write", "ransomware-dev" ]
aliases: [ "File Handling", "Read Write Append" ]
created: 2025-12-21
---

# 📝 File Handling (Read & Write)

> [!danger] Data Loss Warning
> Be very careful with the modes.
> * **`"a"` (Append):** Adds to the end of the file (Safe).
> * **`"w"` (Write):** DELETES everything in the file and starts fresh (Destructive).

## 1. Reading Files (`"r"`)
Used to extract data *out* of a file (e.g., stealing passwords or reading content to encrypt).

- Syntax: open(path, mode)
- Print the entire content of the file
- Always close the file when done (good practice)

```python title:Read_File
#!/usr/bin/python3

file = open("/home/kali/Desktop/newwords.txt", "r")

print(file.read())

file.close()
```

## 2. Writing / Appending (`"a"`)

Used to add data _into_ a file.

- "a" = Append mode. It adds to the end without deleting existing content.
- Write the string. "\n" creates a new line.

```python
#!/usr/bin/python3

file = open("/home/kali/Desktop/newwords.txt", "a")

file.write("CChhhhhiiiiiiiiitoooooooooo\n\n")

file.close()
```

| **Mode**   | **Name**     | **Description**                       | **Use Case**                             |
| ---------- | ------------ | ------------------------------------- | ---------------------------------------- |
| **`"r"`**  | Read         | Error if file doesn't exist.          | Reading text files.                      |
| **`"a"`**  | Append       | Creates file if missing. Adds to end. | Logging keys/activity.                   |
| **`"w"`**  | Write        | **Overwrites** file content.          | Saving a new config.                     |
| **`"rb"`** | Read Binary  | Reads raw bytes.                      | **Reading .exe or .pdf for encryption.** |
| **`"wb"`** | Write Binary | Writes raw bytes.                     | **Saving the encrypted .locked file.**   |
