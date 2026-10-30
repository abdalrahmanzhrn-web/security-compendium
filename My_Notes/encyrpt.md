# encyrpt

VeraCrypt

Due to the laws of mathematics, **random noise looks exactly like random noise**. If an investigator plugs the drive in, they cannot prove a hidden volume exists. If the FBI demands the password under a court order, the user can hand over the Outer Password. The FBI opens the drive, sees mundane files, and mathematically _cannot prove_ there is a second password or a hidden vault containing the actual hacking data.

---

Phase 1: Creating the Outer Volume (The Decoy)

1. **Download and Install VeraCrypt:** Get it only from the official site (`veracrypt.fr`).
2. **Launch the App:** Click on **Create Volume**.
3. **Select Volume Type:** Choose **Encrypt a non-system partition/drive** (if using an external HDD) and click Next.
4. **Select Hidden Volume:** Choose **Hidden VeraCrypt volume** and click Next.
5. **Mode selection:** Choose **Normal mode** (this will guide you through creating both the Outer and Hidden volumes sequentially).
6. **Select Device:** Click **Select Device...**, choose your external HDD partition, and click Next.
    - _Warning: This process will format the drive. Back up any existing data first._
7. **Outer Volume Options:** Leave the Encryption Algorithm as **AES** (or choose the **AES-Twofish-Serpent** cascade for maximum security). Set Hash Algorithm to **SHA-512**. Click Next.
8. **Outer Volume Size:** Choose how much of the drive you want to use. Usually, you select the maximum size available.
9. **Outer Volume Password (Password #1):** Choose a secure password, but make it distinct from your real password. **This is the password you will give to police/investigators under duress.**
10. **Format Outer Volume:** Move your mouse randomly inside the window until the progress bar turns green (this generates cryptographic randomness). Click **Format**.

Once the Outer Volume format finishes, VeraCrypt will automatically prompt you to begin creating the Hidden Volume inside it.

---

Phase 2: Creating the Hidden Volume (The Safe)

1. **Hidden Volume Options:** Here, choose your ultra-secure **AES-Twofish-Serpent** cascade.
2. **Hidden Volume Size:** Choose how much space to reserve for your actual sensitive data (e.g., your Obsidian vaults, private keys).
    - _Example:_ If your HDD is 1000 GB, you might give the Hidden Volume 200 GB. This leaves 800 GB for your "Outer/Decoy" volume.
3. **Hidden Volume Password (Password #2):** This must be **completely different** from the outer password. Make it highly complex. This is the password you never reveal to anyone.
4. **Hidden Volume PIM (Optional):** You can enter a custom **Personal Iterations Multiplier (PIM)** number here (e.g., 200 or 500) to drastically slow down brute-force attacks. Write this down somewhere safe alongside your password.
5. **Format Hidden Volume:** Move your mouse randomly again to generate the entropy pool, select your filesystem (NTFS or exFAT is recommended for HDDs), and click **Format**.

---

How to Use It (The Magic Part)

Now your drive looks like a corrupted, unformatted disk to any normal computer. To access your data, open VeraCrypt, select a drive letter (like `X:`), click **Select Device**, and choose your HDD.

- **To open the Decoy (Outer Drive):** Click **Mount** and type **Password #1**. You will see your fake files (tax returns, family photos, normal software).
- **To open the Secret Safe (Hidden Drive):** Click **Mount** and type **Password #2**. VeraCrypt will bypass the outer layer and open your hidden files instead.

---

🚨 Critical Rule for Plausible Deniability

If you mount the **Outer Volume** using Password #1 to add new decoy files, you must protect the hidden data from being accidentally overwritten.

When mounting the Outer volume, click **Mount Options** and check **Protect hidden volume against damage caused by writing to outer volume**. Enter your Hidden Volume password (Password #2) to authorize the protection. If you don't do this, copying a massive file into the decoy volume could physically overwrite your hidden Obsidian notes.

To ensure this setup works smoothly for your specific environment, let me know:

- What **Operating System** (Windows, Linux, or macOS) are you running?
- Is this an **external storage drive** or an **internal secondary drive**?

I can provide specific optimizations for file systems and performance based on your answers.
