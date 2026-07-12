<div align="center">

# 🔐 Security Research Portfolio

### Alireza Kamani — Penetration Tester · SOC Analyst · Security Engineer

[![LinkedIn](https://img.shields.io/badge/LinkedIn-alireza--kamani-0A66C2?style=flat&logo=linkedin)](https://linkedin.com/in/alireza-kamani)
[![Email](https://img.shields.io/badge/Email-alex123kamany%40gmail.com-D14836?style=flat&logo=gmail)](mailto:alex123kamany@gmail.com)
[![PortSwigger](https://img.shields.io/badge/PortSwigger_Academy-100%25_Complete-FF6633?style=flat)](https://portswigger.net)
[![OSCP](https://img.shields.io/badge/OSCP-Pursuing_2025%2F26-4CAF50?style=flat)](https://www.offensive-security.com/pwk-oscp/)
[![Location](https://img.shields.io/badge/Location-Turkey_(Open_to_Relocation)-gray?style=flat)](/)

---

*Real-world penetration test findings, CIS hardening audits, and proof-of-concept research from production security engagements. All work conducted under formal signed agreements. Published with explicit client permission after NDA expiry.*

</div>

---

## 📊 At a Glance

| | |
|---|---|
| 🎯 **Total Vulnerabilities Found** | **38+ across 4 engagements** |
| 🔴 **Critical Severity** | **11 findings** |
| 👥 **Users Protected** | **40,000,000+ (MCI subscribers)** |
| 🏢 **Clients** | MCI (Iran's largest telco), Flytoday, Ewano |
| 🛡️ **CIS Controls Audited** | 368 (Ubuntu 20.04 + IIS 10) |
| 📱 **Assessment Types** | Android · Web · Network · CIS Hardening |

---

## 🏆 Headline Findings

> These are the findings that matter most to a hiring manager.

| Severity | Finding | Client | Impact |
|:---:|---|---|---|
| 🔴 **Critical** | **SMS Spoofing** — arbitrary message injection via unauthenticated API | MCI | Any of 40M subscribers could receive forged MCI SMS |
| 🔴 **Critical** | **OTP Brute Force** — 4-digit space, no rate limiting, full ATO | MCI / Shop | Account takeover of any subscriber in <10,000 requests |
| 🔴 **Critical** | **BOLA** — unauthorised paid service activation billed to victim | MCI | 16,500 IRR charged from victim; proven in test |
| 🔴 **Critical** | **Race Condition** — loyalty points over-expenditure | MCI | Parallel requests bypass balance limits |
| 🔴 **Critical** | **RCE** — file upload double-extension bypass, JS execution from CDN | Flytoday | Cookie theft from trusted domain; patched pre-launch |
| 🟠 **High** | **SQL Injection** (time-based blind) in search/filter API | Ewano/MCI | Full DB extraction possible |
| 🟠 **High** | **Stored XSS** — admin panel content management | Ewano/MCI | Session hijack of all admin users |
| 🟠 **High** | **CBC Padding Oracle** — AES-CBC with PKCS7 | MCI Android | Decrypt arbitrary ciphertext without key |

---

## 📁 Security Assessment Reports

### 1. 📱 MY MCI Android App — Black-Box Penetration Test
> **Client:** MCI (Mobile Communication Company of Iran — همراه اول, 40M+ subscribers)  
> **Type:** Black-Box · Android + API · OWASP MASVS L2  
> **Findings:** 7 Critical · 5 High · 6 Medium · 3 Low/Info = **22 total**

Key findings: SMS spoofing to arbitrary subscriber, OTP brute-force ATO, BOLA (paid service on victim), race condition on loyalty points, CBC padding oracle, logical DoS, session persistence after logout.

📄 **[View Full Report](./reports/01_MCI_MyMCI_Android/report.html)** · [Summary](./reports/01_MCI_MyMCI_Android/README.md)

---

### 2. ✈️ Flytoday Travel Platform — CIS Hardening + Web Pentest
> **Client:** Flytoday.ir — Pre-launch travel booking platform  
> **Type:** Gray-Box · IIS 10 / Ubuntu 18.04 / MSSQL  
> **Findings:** RCE (Critical) · Stored XSS · Open Redirect · 22 CIS FAILED · 9 WARNING

Key findings: Remote Code Execution via double-extension file upload bypass (working PoC: JS executing from CDN, session cookies exfiltrated). All critical findings patched before public launch. Full CIS IIS 10 and Ubuntu hardening audit with command-level remediation.

📄 **[View Full Report](./reports/02_Flytoday_Hardening/report.html)** · [Summary](./reports/02_Flytoday_Hardening/README.md)

---

### 3. 🛒 MCI Online Shop — Black-Box Web Penetration Test
> **Client:** MCI — eshop.mci.ir (subscriber self-service e-commerce)  
> **Type:** Black-Box · Web · OWASP WSTG · PTES  
> **Findings:** 2 Critical · 4 High = **6 total**

Key findings: OTP brute-force account takeover, alternative authentication channel bypass, account enumeration via differential responses, unlimited SMS bombing, unauthorised package purchase billed to victim account.

📄 **[View Full Report](./reports/03_MCI_OnlineShop/report.html)** · [Summary](./reports/03_MCI_OnlineShop/README.md)

---

### 4. 🌐 Ewano Cache Platform (MCI) — Comprehensive Security Assessment
> **Client:** Ewano Co. / MCI — CDN and cache infrastructure  
> **Type:** Re-Pentest · Web + Network + CIS Ubuntu 20.04  
> **Findings:** 2 Critical · 4 High · 4 Medium (web) · 3 Network · **41 CIS FAILED / 47 WARNING / 280 PASSED**

Key findings: Admin panel exposed to internet without MFA, stored XSS, SQL injection (time-based blind), IDOR, CSRF. Network: SSH weak ciphers, exposed Memcached. CIS: 368-control audit with command-level remediation for all failures.

📄 **[View Full Report](./reports/04_Ewano_Cache/report.html)** · [Summary](./reports/04_Ewano_Cache/README.md)

---

## 🛠️ Technical Skills Demonstrated

### Offensive
```
Web:      SQLi (blind/time-based) · XSS (stored/reflected/DOM) · CSRF · IDOR/BOLA ·
          File Upload Bypass (RCE) · Host Header Injection · Business Logic ·
          Race Conditions · OTP Brute Force · Response Manipulation · CBC Padding Oracle

Mobile:   Android APK analysis (JADX/Apktool) · Dynamic instrumentation (Frida) ·
          SSL unpinning · IPC/exported component abuse · ADB · MobSF · Drozer ·
          OWASP MASVS L2 full test coverage

Network:  Service enumeration (Nmap) · SSH audit · Cipher/KEX weakness exploitation ·
          Memcached UDP amplification analysis · TLS configuration assessment

AD:       Kerberos delegation abuse · AD CS attacks · SMB/LDAP relay ·
          LLMNR/NBT-NS poisoning · BloodHound · Impacket · Covenant
```

### Defensive / Compliance
```
CIS:      IIS 10 Benchmark v1.2.1 · Ubuntu 18.04/20.04 LTS Benchmark ·
          MSSQL Benchmark · Nessus compliance scanning

Hardening: Active Directory hardening (Kerberos-only auth, NTLM removal, SYSVOL restriction)
           FortiGate & Kerio Control firewalls · VPN configuration · Patch management

SIEM:     ELK Stack deployment and operations · Alert triage (Tier 1) ·
          IOC identification · Log analysis · Incident ticketing

Standards: ISO 27001 implementation · CVSSv3.1 · MITRE ATT&CK · OWASP WSTG · PTES
```

### Tools
```
Burp Suite Pro · Nessus · Nmap · SQLMap · Metasploit · Frida · MobSF · JADX ·
BloodHound · Impacket · Wireshark · ELK Stack · IDA Pro · Covenant · Snort · Suricata
```

---

## 📝 Technical Writing

| Article | Platform | Topic |
|---|---|---|
| [How I Found SMS Spoofing Affecting 40M Subscribers](https://medium.com/@alex123kamany) | Medium | Business Logic · API Security |
| [Breaking OTP Authentication: Account Takeover via Brute Force](https://medium.com/@alex123kamany) | Medium | Authentication · Rate Limiting |
| [RCE via File Upload: From Double Extension to Cookie Theft](https://medium.com/@alex123kamany) | Medium | File Upload · XSS · CDN Security |

---

## 📜 Certifications & Training

| Credential | Status | Issuer |
|---|---|---|
| **OSCP** — Offensive Security Certified Professional | 🔄 Pursuing (2025/26) | Offensive Security |
| **PortSwigger Web Security Academy** | ✅ 100% Complete | PortSwigger |
| **TryHackMe** — Pentester + Web Pentester paths | ✅ Complete | TryHackMe |
| **HackTheBox Academy** — Junior Red Team path | 🔄 In Progress | HackTheBox |

---

## ⚖️ Legal Notice

All security assessments documented in this portfolio were conducted under formal written agreements between Sadra Secure Corp. (کیان امن صدرا) and the respective clients.

- NDA periods have elapsed for all engagements
- Explicit written permission to publish has been obtained from all clients
- Sensitive production credentials, internal IP addresses, and user PII have been removed or anonymised
- No working exploit code capable of mass exploitation is published here
- This portfolio is for educational and professional demonstration purposes only

See [LEGAL_DISCLAIMER.md](./LEGAL_DISCLAIMER.md) for full details.

---

## 📬 Contact

I am currently based in Turkey and **open to full international relocation**.

- 📧 **Email:** alex123kamany@gmail.com
- 💼 **LinkedIn:** [linkedin.com/in/alireza-kamani](https://linkedin.com/in/alireza-kamani)
- 📱 **Phone:** +90 553 518 37 43

> *Preferred roles: Penetration Tester · Red Team Analyst · Security Engineer · SOC Analyst (Tier 2/3)*  
> *Languages: Persian (Native) · English C1 (IELTS 7.0) · German A2*

---

<div align="center">
<sub>© AK · All assessments conducted ethically and legally · Open to relocation worldwide</sub>
</div>
