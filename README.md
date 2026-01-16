# 🕵️‍♂️ Mr Robot CTF – TryHackMe Walkthrough

## 📌 Overview
- This repository contains my complete walkthrough of the Mr Robot CTF room on TryHackMe.
- The challenge is inspired by the Mr Robot TV series and focuses on real-world penetration testing techniques such as:
    - Enumeration
    - Web exploitation
    - Hash cracking
    - Privilege escalation

🔗 Room Link: https://tryhackme.com/room/mrrobot

## 🎯 Objectives
  - Gain access to the target machine
  - Capture all three hidden flags
  - Perform privilege escalation to root

## 🛠 Tools Used
  - Nmap
  - Gobuster
  - Hydra
  - John The Ripper
  - Linux privilege escalation techniques

## 🔍 Step 1: Enumeration
### Network Scanning
- nmap -sC -sV -oN scan.txt <TARGET_IP>


## Findings:
1. Port 80 (HTTP)
2. Port 443 (HTTPS)
3. Port 22 (SSH)

## 🌐 Step 2: Web Enumeration
### Directory Bruteforcing
- gobuster dir -u http://<TARGET_IP> -w /usr/share/wordlists/dirb/common.txt


### Interesting files found:
1. /robots.txt
2. /fsocity.dic
3. /key-1-of-3.txt

### 🏁 Flag 1
### Accessing:

- http://<TARGET_IP>/key-1-of-3.txt
  ✅ Flag 1 obtained

## 🔐 Step 3: Credential Discovery

### Using the discovered wordlist:
- hydra -l elliot -P fsocity.dic ssh://<TARGET_IP>
Password found for user elliot.

### 🏁 Flag 2
### Logged in via SSH:
- ssh elliot@<TARGET_IP>

### Found hidden file:
- cat key-2-of-3.txt
✅ Flag 2 obtained

## ⬆ Privilege Escalation

### Checked sudo privileges:
1. sudo -l
2. Found misconfigured binary.
3. Exploited it to gain root access:
4. sudo <vulnerable_binary>

### 🏁 Flag 3 (Root)
1. cat /root/key-3-of-3.txt
✅ Flag 3 obtained

# 📚  Lessons Learned

- Importance of robots.txt misconfigurations
- Using wordlists for credential attacks
- Identifying misconfigured sudo permissions
- Practical Linux privilege escalation

# 🧠 Skills Demonstrated
- Penetration testing methodology
- Linux system exploitation
- Hash cracking
- Enumeration techniques
- Report writing

## ⚠ Disclaimer
- This write-up is for educational purposes only.
- Do not attempt these techniques on systems you do not own or have permission to test.

👤 Author

Marvin Tshirufho
Cybersecurity Enthusiast | IT Graduate
📧 funananimunyai51@gmail.com
🔗 www.linkedin.com/in/funanani-tshirufho-b4ba3a276
🔗 Funanani
