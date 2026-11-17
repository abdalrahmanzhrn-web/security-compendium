---
tags: [ "cracking", "john-the-ripper", "hashcat", "zip", "pdf", "forensics" ]
aliases: [ "File Cracking", "Encrypted Archives" ]
created: 2025-12-21
---

# 🔐 Cracking Encrypted Files (ZIP & PDF)

> [!info] Workflow Overview
> This note covers a "Matryoshka" scenario: Cracking an encrypted ZIP file to extract an encrypted PDF, then cracking the PDF itself.

## 1. Cracking Encrypted ZIPs
The goal is to extract the hash from the archive headers so John/Hashcat can attack it.

**Step A: Extract Hash (`zip2john`)**

- Convert the zip file into a format John can understand
- Option 1: John the Ripper
- (If it finishes instantly, run: john --show zip.hash)(try john weak one first)
- Option 2: Hashcat (Mode 17225)
- Note: You may need --force if on a VM without GPU drivers
- Check file version
- Output: PDF document, version 1.7 ...
- Convert to hash

```bash title:ZIP_Hash_Extraction
zip2john evidence.zip > zip.hash

john --wordlist=/usr/share/wordlists/rockyou.txt zip.hash

hashcat -m 17225 -a 3 zip.hash rockyou.txt

```

**Unzip** Once you have the password (e.g., `outerlock555`), extract the contents.

```bash title:ZIP_Hash_Extraction
unzip evidence.zip

2. Cracking Encrypted PDFs

file locked1.pdf

pdf2john locked1.pdf > pdf.hash

john --wordlist=rockyou.txt pdf.hash
```

**Step C: Hashcat (GPU) - The "Clean Up"** Hashcat is sensitive. It hates the filename prefix (`locked1.pdf:`). You must remove it.

1. Open `pdf.hash`.

2. Delete `locked1.pdf:` at the start.

3. Keep the rest: `$pdf$2*3*128...`

**Step D: Hashcat Mode Selection** Look at the start of the hash signature to pick the right mode.

| **Signature** | **Mode**  | **Description**                   |
| ------------- | --------- | --------------------------------- |
| **$pdf$2***   | **10500** | Older PDFs (Most likely for CTFs) |
| **$pdf$4***   | **10600** | Intermediate Versions             |
| **$pdf$5***   | **10700** | Modern PDFs (Stronger encryption) |

- Example for $pdf$2* (Mode 10500)

```text
hashcat.exe -m 10500 pdf.hash rockyou.txt
```

## 3. Post-Crack Decryption

Once you have the PDF password (e.g., `admin123`), create a clean, unencrypted version.

```text
qpdf --password=admin123 --decrypt locked1.pdf unlocked1.pdf
```

https://hashcat.net/wiki/doku.php?id=example_hashes
po prosto (CrackStation)
