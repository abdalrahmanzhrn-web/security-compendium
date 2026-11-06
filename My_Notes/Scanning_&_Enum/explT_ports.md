---
tags: [ "networking", "ports", "smb", "mysql", "ftp", "ssh", "reference" ]
aliases: [ "Common Ports", "Service Ports Cheat Sheet" ]
created: 2025-12-21
---

# 🔌 Common Service Ports

> [!summary] Quick Reference
> A cheat sheet for the most common services encountered during enumeration.

| Service | Port(s) | Transport | Description |
| :--- | :--- | :--- | :--- |
| **FTP** | **20, 21** | TCP | File Transfer Protocol. <br>21 = Control (Commands)<br>20 = Data (File transfer) |
| **SSH** | **22** | TCP | Secure Shell. Encrypted remote login and administration. |
| **SMB** | **139, 445** | TCP | Server Message Block (Windows File Shares).<br>139 = NetBIOS Session<br>445 = Direct SMB over TCP |
| **MySQL** | **3306** | TCP | Default listening port for MySQL databases. |

## 📝 Notes
* **SMB (139 vs 445):** Modern Windows systems primarily use **445**. If you see **139**, NetBIOS is active.
* **FTP:** If you only see port 21 open, Passive Mode FTP might be required for data transfer.

---
