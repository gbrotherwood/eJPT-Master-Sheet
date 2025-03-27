# 🛡️ eJPTv2 Comprehensive Exam Cheat Sheet

A practical, hands-on reference covering all the essential topics for passing the eLearnSecurity Junior Penetration Tester (eJPTv2) certification. Includes recon, exploitation, post-exploitation, web hacking, and exam strategy tips.

---

## 🧠 Exam Strategy and Time Management Tips

- **Enumerate Everything:** Begin with thorough reconnaissance on all targets – it’s crucial.
- **Plan Your Time:** You get 48 hours; divide time for recon, exploitation, and review.
- **Low-Hanging Fruit First:** Knock out easy wins to build confidence and bank points.
- **Take Notes:** Record every IP, port, tool, command, and finding.
- **Stay Calm:** If stuck, take a break or pivot to another question.

---

## 🔎 1. Network Reconnaissance & Enumeration

### 1.1 Passive Reconnaissance (OSINT)

**Tools:**
- `whois`, `nslookup`, `dig`
- Google Dorks: `site:target.com filetype:pdf`
- `theHarvester`, LinkedIn, job ads

**TryHackMe:**
- [Passive Reconnaissance](https://tryhackme.com/room/passiverecon)
- [Google Dorking](https://tryhackme.com/room/googledorking)

### 1.2 Active Host Discovery

- `nmap -sn 10.10.10.0/24`
- `fping -a -g 10.10.10.0/24`
- `netdiscover -r 10.10.50.0/24`

### 1.3 Port Scanning

- `nmap -sC -sV -p- -O <target>`
- `nmap -sU -sV -F <target>`
- `nmap --script vuln -p 139,445 <target>`

**TryHackMe:**
- [Nmap](https://tryhackme.com/room/nmap)
- [Network Services](https://tryhackme.com/room/networkservices)

### 1.4 Service Enumeration

**SMB:**
- `enum4linux -a <IP>`, `smbclient`, `smbmap`

**FTP/SSH/SNMP/HTTP:**
- Use version banners, test for weak auth, default creds

**TryHackMe:**
- [Kenobi](https://tryhackme.com/room/kenobi)
- [Blue](https://tryhackme.com/room/blue)

---

## 🧰 2. Host & Network Post-Exploitation

### 2.1 System Info

**Linux:**
- `uname -a`, `id`, `ip a`, `ps aux`

**Windows:**
- `systeminfo`, `ipconfig /all`, `net user`

### 2.2 Looting Files

**Linux:**
- `.bash_history`, `.ssh/`, `/etc/passwd`, `/etc/shadow`

**Windows:**
- `findstr /si password *.txt`
- Unattended install files, SAM & SYSTEM hives

### 2.3 File Transfers

**Linux:**
- `python3 -m http.server`, `wget`, `scp`, `nc`

**Windows:**
- `certutil`, PowerShell `Invoke-WebRequest`

**TryHackMe:**
- [Windows Fundamentals 2](https://tryhackme.com/room/windowsfundamentals2)

---

## 🎯 3. Exploitation & Privilege Escalation

### 3.1 Exploits

- `searchsploit`, `msfconsole`, `msfvenom`
- Reverse shells (bash, powershell, php)
- Modify IPs/ports in downloaded exploit scripts

### 3.2 Metasploit & Meterpreter

- `use`, `set RHOST`, `exploit`
- Meterpreter: `getuid`, `hashdump`, `upload`, `download`, `getsystem`
- Pivot: `autoroute`, `portfwd`

**TryHackMe:**
- [Ice](https://tryhackme.com/room/ice)
- [Metasploit](https://tryhackme.com/room/metasploit)

### 3.3 Password Attacks

**Hydra:**
- `hydra -l user -P rockyou.txt ssh://<IP>`
- `hydra http-post-form ...`

**John the Ripper:**
- `john --wordlist=rockyou.txt hash.txt`
- `zip2john file.zip > hash.txt`

**TryHackMe:**
- [Brute It](https://tryhackme.com/room/bruteit)
- [Bounty Hacker](https://tryhackme.com/room/cowboyhacker)

### 3.4 Privilege Escalation

**Linux:**
- `sudo -l`, SUID files, cron jobs, kernel exploits

**Windows:**
- `whoami /priv`, AlwaysInstallElevated, weak services

**TryHackMe:**
- [Linux PrivEsc](https://tryhackme.com/room/linuxprivesc)
- [Windows PrivEsc Arena](https://tryhackme.com/room/windowsprivescarena)

---

## 🌐 4. Web Application Penetration Testing

### 4.1 Web Recon

- `whatweb`, `wappalyzer`, `nikto`
- `gobuster`, `ffuf` for hidden paths and files
- SSL certs, virtual host discovery

**TryHackMe:**
- [Web Enumeration](https://tryhackme.com/room/webenumeration)
- [Vulnversity](https://tryhackme.com/room/vulnversity)

### 4.2 Web Exploits

**SQL Injection:**
- `' OR 1=1 --`
- `sqlmap -u "<url>" --dbs`

**XSS:**
- `<script>alert(1)</script>`

**Command Injection:**
- `8.8.8.8 && whoami`

**File Uploads:**
- `.php`, `.php.jpg`, tamper via Burp

**TryHackMe:**
- [Juice Shop](https://tryhackme.com/room/owaspjuiceshop)
- [OWASP Top 10](https://tryhackme.com/room/owasptop10)

### 4.3 Web Password Attacks

**Hydra:**
- `hydra -l admin -P pass.txt <IP> http-post-form "/login:..."`

**Defaults:**
- Try admin/admin, look in robots.txt, HTML comments

---

## ✅ Final Tips

- Use `enum4linux`, `nmap -p- -sV -sC`, and `gobuster` early
- Try the easiest questions first
- Keep notes for every tool and target
- Use Metasploit where allowed for efficiency

---

> 💡 Pro Tip: Create aliases and scripts for your recon workflow to speed up the exam process.
