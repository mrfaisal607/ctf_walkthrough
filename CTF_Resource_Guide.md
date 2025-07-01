# 🎯 CTF Resource Guide – Universe of Hacking

Welcome to the **CTF Resource Guide** curated by **Universe of Hacking**. This document compiles essential tools, platforms, walkthroughs, and learning resources to level up your skills in cybersecurity and Capture The Flag (CTF) competitions.

> 🔐 "A Master's Guide to Learning Security" — Walkthroughs, Tools, Resources & Cheatsheets.

---

## 📌 Table of Contents

1. [📺 YouTube Channels](#youtube-channels)
2. [🧪 CTF Practice & Learning Platforms](#ctf-practice--learning-platforms)
3. [📁 Category-Based Resources](#category-based-resources)
    - OSINT
    - Forensics / Stego
    - Crypto
    - Pwn / Binary
    - Web
    - Smart Contracts
    - Cloud
4. [🛠️ Tools List](#tools-list)
5. [📜 CTF Cheat Sheet](#ctf-cheat-sheet)
6. [🧰 Red Team Arsenal](#red-team-arsenal)
7. [🛡️ Blue Team & Defense Tools](#blue-team--defense-tools)
8. [📦 File Transfer Tools](#file-transfer-tools)
9. [🧠 Learning Resources](#learning-resources)
10. [🏆 CTF Competitions & Aggregators](#ctf-competitions--aggregators)


---

## 📺 YouTube Channels

| Channel              | Description |
|----------------------|-------------|
| John Hammond         | Great CTF tutorials and walkthroughs |
| Live Overflow        | In-depth pwn/web reverse engineering |
| IppSec               | HackTheBox machine walkthroughs |
| PwnFunction          | Animated videos about binary exploitation |
| pwn.college          | Guided courses & practice problems |
| Martin Carlisle      | picoCTF writeup videos |
| stacksmashing        | Reverse engineering & hardware hacks |
| Sam Bowne            | College-level free cyber security content |
| Gynvael              | Advanced reverse engineering |
| RPISEC               | Advanced pwn and exploit lectures |
| Black Hills InfoSec  | Cybersecurity training and live demos |

---

## 🧪 CTF Practice & Learning Platforms

| Platform        | Focus Area |
|----------------|-------------|
| TryHackMe       | Step-by-step learning paths |
| HackTheBox      | Hands-on labs & realistic VMs |
| PicoCTF         | Beginner-friendly challenges |
| OverTheWire     | Wargames for basics of Linux, pwn |
| Root Me         | Diverse challenge categories |
| VulnHub         | Bootable VMs for offline practice |
| Pwnable.kr/.tw  | Binary exploitation |
| CryptoHack      | Cryptography-focused challenges |
| Capture the Ether| Smart contract hacking |
| flaws.cloud     | AWS cloud exploitation |
| CTFtime         | Global competition calendar |

---

## 📁 Category-Based Resources

### OSINT

- [Shodan](https://shodan.io)
- [theHarvester](https://github.com/laramies/theHarvester)
- [SpiderFoot](https://www.spiderfoot.net/)
- [OSINT Framework](https://osintframework.com)

### Forensics / Stego

- AperiSolve, Steghide, stegseek, zsteg, binwalk, exiftool
- Spectrograms, SSTV, SSTV decoders, Morse, DTMF decoding
- Ltrace, hexedit, file signature recovery, GHex
- grep for flags: `grep -r --text 'picoCTF{.*}'`

### Crypto

- [CyberChef](https://gchq.github.io/CyberChef/)
- [Ciphey](https://github.com/Ciphey/Ciphey)
- [Cryptopals](https://cryptopals.com/)
- [CryptoHack](https://cryptohack.org/)

### Pwn / Binary Exploitation

- Buffer Overflow, Format String, ROP, Stack Canary
- [pwndbg](https://github.com/pwndbg/pwndbg)
- [GEF](https://github.com/hugsy/gef)
- [OneGadget](https://github.com/david942j/one_gadget)
- [how2heap](https://github.com/shellphish/how2heap)
- [ROP Emporium](https://ropemporium.com)

### Web

- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [PortSwigger Labs](https://portswigger.net/web-security)
- [DVWA](http://www.dvwa.co.uk/)
- [websec.fr](https://websec.fr)
- [webhacking.kr](http://webhacking.kr)

### Smart Contracts

- [Capture the Ether](https://capturetheether.com/)
- [Damn Vulnerable DeFi](https://github.com/smartcontractkit/damn-vulnerable-defi)

### Cloud

- [CloudFoxable](https://github.com/BishopFox/CloudFoxable)
- [flaws.cloud](https://flaws.cloud/)

---

## 🛠️ Tools List

- **Recon**: Nmap, theHarvester, Amass, Sublist3r  
- **Web**: Burp Suite, SQLMap, Nikto, Wapiti  
- **Reverse Shells**: revshells.com, MSFvenom  
- **Exploitation**: Metasploit, PayloadsAllTheThings  
- **Cracking**: John the Ripper, Hashcat, Hydra  
- **Forensics**: binwalk, foremost, strings, exiftool  
- **Debugging**: GDB, pwndbg, GEF, IDA Pro, Ghidra

---

## 📜 CTF Cheat Sheet

- [PayloadsAllTheThings](https://github.com/swisskyrepo/PayloadsAllTheThings)
- [HackTricks](https://book.hacktricks.xyz)
- [GTFOBins](https://gtfobins.github.io/)
- [LOLBAS](https://lolbas-project.github.io/)
- [Linux Priv Esc](https://github.com/sleventyeleven/linuxprivchecker)
- [Windows Priv Esc](https://github.com/swisskyrepo/Windows-Privilege-Escalation)
- [Reverse Engineering Cheatsheet](https://github.com/onethawt/reverseengineering-cheatsheet)

---

## 🧰 Red Team Arsenal

| Tool           | Purpose |
|----------------|---------|
| Cobalt Strike  | Red team simulation |
| Sliver         | Open-source C2 |
| Empire         | PowerShell post-exploitation |
| Mimikatz       | Credential dumping |
| SharpHound     | AD enumeration |
| Covenant       | .NET C2 framework |
| ScareCrow      | AV evasion |
| Evil-WinRM     | WinRM shell access |

---

## 🛡️ Blue Team & Defense Tools

| Tool          | Purpose |
|---------------|---------|
| Security Onion| Network monitoring |
| Wazuh         | SIEM and EDR |
| Suricata      | Threat detection |
| Zeek          | Network analysis |
| Velociraptor  | Endpoint forensics |
| ELK Stack     | Log management |
| MISP          | Threat intel sharing |
| TheHive       | Incident response |

---

## 📦 File Transfer Tools

| Tool           | Description |
|----------------|-------------|
| OnionShare     | Secure file sharing via Tor |
| Transfer.sh    | CLI file transfer |
| Wormhole       | Encrypted one-time transfer |
| FilePizza      | Peer-to-peer sharing |
| ToffeeShare    | Direct encrypted file transfer |

---

## 🧠 Learning Resources

- [Cyber Aces by SANS](https://www.cyberaces.org/)
- [CTF101](https://ctf101.org/)
- [Pwn.college](https://pwn.college/)
- [Security Summer School](https://security.cs.pub.ro/)
- [Trail of Bits CTF Guide](https://github.com/trailofbits/ctf)

---

## 🏆 CTF Competitions & Aggregators

| Event Name           | URL |
|----------------------|-----|
| DEF CON CTF          | [Link](https://defcon.org) |
| CSAW CTF             | [Link](https://csaw.engineering.nyu.edu/ctf) |
| PICOCTF              | [Link](https://picoctf.org) |
| Hack.lu              | [Link](https://hack.lu/) |
| CTFtime              | [Link](https://ctftime.org) |
| Insomni’hack         | [Link](https://insomnihack.ch/) |
| ZeroDays CTF         | [Link](https://zerodays.ie/) |

---



---

💚 Happy Hacking, Stay Ethical & Sharp!  
— Team Universe of Hacking
