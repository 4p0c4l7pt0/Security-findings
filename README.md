<div align="center">

# 🔐 Security Research Portfolio

### AK — Penetration Tester · SOC Analyst · Security Engineer

<<<<<<< HEAD
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Profile-0A66C2?style=flat&logo=linkedin)](https://linkedin.com/in/ak-365a24188/)
=======
[![LinkedIn](https://img.shields.io/badge/LinkedIn-alireza--kamani-0A66C2?style=flat&logo=linkedin)](https://www.linkedin.com/in/ak-365a24188/)
>>>>>>> dea1f4de4a7fac0a79f950b9be332f86c0064e64
[![Email](https://img.shields.io/badge/Email-alex123kamany%40gmail.com-D14836?style=flat&logo=gmail)](mailto:alex123kamany@gmail.com)
[![PortSwigger](https://img.shields.io/badge/PortSwigger_Academy-100%25_Complete-FF6633?style=flat)](https://portswigger.net)
[![OSCP](https://img.shields.io/badge/OSCP-Pursuing_2025%2F26-4CAF50?style=flat)](https://www.offensive-security.com/pwk-oscp/)
[![Location](https://img.shields.io/badge/Location-Turkey_(Open_to_Relocation)-gray?style=flat)](/)

---

<<<<<<< HEAD
*Real-world penetration test findings, CIS hardening audits, and proof-of-concept research from production security engagements conducted under formal agreements. Client names anonymised in public version — full details available to employers on request.*
=======
*Real-world penetration test findings, CIS hardening audits, and proof-of-concept research from production security engagements. All work conducted under formal signed agreements. Published with explicit client permission after NDA expiry.*
(*_all the reports with their corresponding findings and POCs can be found on the Reports repository as HTML formats_*)
>>>>>>> dea1f4de4a7fac0a79f950b9be332f86c0064e64

</div>

---

## 📊 At a Glance

| | |
|---|---|
| 🎯 **Total Vulnerabilities Found** | **38+ across 4 engagements** |
| 🔴 **Critical Severity** | **11 findings** |
| 👥 **Users Protected** | **40,000,000+** |
| 🏢 **Clients** | Major telecom (40M users), travel platform, CDN infrastructure |
| 🛡️ **CIS Controls Audited** | 368 (Ubuntu 20.04 + IIS 10) |
| 📱 **Assessment Types** | Android · Web · Network · CIS Hardening |

---

## 🏆 Headline Findings

| Severity | Finding | Impact |
|:---:|---|---|
| 🔴 **Critical** | **SMS Spoofing** — unauthenticated API injects arbitrary message to any subscriber | Forged SMS to 40M+ users from official sender ID |
| 🔴 **Critical** | **OTP Brute Force** — 4-digit, no rate limiting, full account takeover | Any account compromised in <10,000 requests |
| 🔴 **Critical** | **BOLA** — unauthorised paid service activation billed to victim | 16,500 IRR charged from victim; proven live |
| 🔴 **Critical** | **Race Condition** — loyalty points over-expenditure via parallel requests | Balance limits bypassed |
| 🔴 **Critical** | **RCE** — file upload double-extension bypass, JS from trusted CDN | Cookie theft; patched pre-launch |
| 🟠 **High** | **SQL Injection** (time-based blind) in search/filter API | Full DB extraction confirmed |
| 🟠 **High** | **Stored XSS** — admin panel content management | All admin sessions hijackable |
| 🟠 **High** | **CBC Padding Oracle** — AES-CBC with PKCS7 in Android app | Ciphertext decryption without key |

---

## 📁 Reports

> 💡 **To view reports:** Click **"View Report (Live)"** for the rendered version, or **"Download HTML"** to save locally.  
> *Reports open directly in your browser — no software needed.*

---

### 📱 Report 1 — Android Mobile Application Penetration Test

> **Type:** Black-Box · Android + Backend API · OWASP MASVS L2 · CVSSv3.1  
> **Findings:** 7 Critical · 5 High · 6 Medium · 3 Low = **22 total**  
> **Target:** Major telecom self-service app — 40M+ subscriber base

Key findings: SMS spoofing, OTP brute-force ATO, BOLA (paid service on victim account, proven), race condition on loyalty points, CBC padding oracle, logical DoS, session persistence post-logout.

| | Link |
|---|---|
| 🌐 **View Report (Live)** | [Open in browser →](https://4p0c4l7pt0.github.io/Security-findings/Reports/01_MCI_MyMCI_Android/report.html) |
| 🔗 **Fallback viewer** | [htmlpreview →](https://htmlpreview.github.io/?https://raw.githubusercontent.com/4p0c4l7pt0/Security-findings/main/Reports/01_MCI_MyMCI_Android/report.html) |
| 📋 **Summary** | [README →](./Reports/01_MCI_MyMCI_Android/README.md) |

---

### ✈️ Report 2 — CIS Hardening Audit & Web Penetration Test

> **Type:** Gray-Box · IIS 10 / Ubuntu 18.04 / MSSQL · CIS Benchmark v1.2.1  
> **Findings:** RCE · Stored XSS (live cookie exfiltration PoC) · Open Redirect · 22 CIS FAILED  
> **Outcome:** All critical findings patched and verified **before public launch** ✅

Key findings: RCE via file upload double-extension bypass (working JS payload served from trusted CDN, cookies exfiltrated to attacker webhook). Full CIS IIS 10 and Ubuntu hardening with command-level remediation.

| | Link |
|---|---|
| 🌐 **View Report (Live)** | [Open in browser →](https://4p0c4l7pt0.github.io/Security-findings/Reports/02_Flytoday_Hardening/report.html) |
| 🔗 **Fallback viewer** | [htmlpreview →](https://htmlpreview.github.io/?https://raw.githubusercontent.com/4p0c4l7pt0/Security-findings/main/Reports/02_Flytoday_Hardening/report.html) |
| 📋 **Summary** | [README →](./Reports/02_Flytoday_Hardening/README.md) |

---

### 🛒 Report 3 — E-Commerce Web Penetration Test

> **Type:** Black-Box · Web · OWASP WSTG · PTES · CVSSv3.1  
> **Findings:** 2 Critical · 4 High = **6 total**  
> **Target:** Subscriber self-service e-commerce portal (same 40M user base)

Key findings: OTP brute-force ATO, alternative auth channel bypass, account enumeration via differential HTTP responses, unlimited SMS bombing, unauthorised package purchase billed to victim.

| | Link |
|---|---|
| 🌐 **View Report (Live)** | [Open in browser →](https://4p0c4l7pt0.github.io/Security-findings/Reports/03_MCI_OnlineShop/report.html) |
| 🔗 **Fallback viewer** | [htmlpreview →](https://htmlpreview.github.io/?https://raw.githubusercontent.com/4p0c4l7pt0/Security-findings/main/Reports/03_MCI_OnlineShop/report.html) |
| 📋 **Summary** | [README →](./Reports/03_MCI_OnlineShop/README.md) |

---

### 🌐 Report 4 — Comprehensive CDN/Cache Infrastructure Assessment

> **Type:** Re-Pentest · Web + Network + CIS Ubuntu 20.04 · OWASP WSTG · PTES  
> **Findings:** 2 Critical · 4 High · 4 Medium (web) · 3 Network · **41 CIS FAILED / 47 WARNING / 280 PASSED**  
> **Target:** Content delivery and cache infrastructure serving the same telco subscriber base

Key findings: Internet-exposed admin panel (no MFA), stored XSS, time-based blind SQLi, IDOR, CSRF. Network: SSH weak ciphers (arcfour/3DES), unauthenticated Memcached. CIS: 368-control audit with `sysctl`/`apt`/`chmod` remediation for every failure.

| | Link |
|---|---|
| 🌐 **View Report (Live)** | [Open in browser →](https://4p0c4l7pt0.github.io/Security-findings/Reports/04_Ewano_Cache/report.html) |
| 🔗 **Fallback viewer** | [htmlpreview →](https://htmlpreview.github.io/?https://raw.githubusercontent.com/4p0c4l7pt0/Security-findings/main/Reports/04_Ewano_Cache/report.html) |
| 📋 **Summary** | [README →](./Reports/04_Ewano_Cache/README.md) |

---

## 🛠️ Technical Skills Demonstrated

### Offensive
```
Web:      SQLi (blind/time-based) · XSS (stored/reflected/DOM) · CSRF · IDOR/BOLA
          File Upload Bypass (RCE) · Host Header Injection · Business Logic Flaws
          Race Conditions · OTP Brute Force · Response Manipulation · CBC Padding Oracle

Mobile:   Android APK analysis (JADX/Apktool) · Dynamic instrumentation (Frida)
          SSL unpinning · IPC/exported component abuse · ADB · MobSF · Drozer
          OWASP MASVS L2 full test coverage

Network:  Service enumeration (Nmap) · SSH algorithm audit · Weak cipher exploitation
          Memcached UDP amplification · TLS configuration assessment

AD:       Kerberos delegation abuse · AD CS attacks · SMB/LDAP relay
          LLMNR/NBT-NS poisoning · BloodHound · Impacket · Covenant
```

### Defensive / Compliance
```
CIS:      IIS 10 Benchmark v1.2.1 · Ubuntu 18.04/20.04 LTS · MSSQL Benchmark
          Nessus compliance scanning · Command-level remediation

Hardening: Active Directory (Kerberos-only, NTLM removal, SYSVOL restriction)
           FortiGate & Kerio Control firewalls · VPN · Patch management

SIEM:     ELK Stack · Alert triage (Tier 1) · IOC identification · Log analysis

Standards: ISO 27001 · CVSSv3.1 · MITRE ATT&CK · OWASP WSTG · PTES
```

### Tools
```
Burp Suite Pro · Nessus · Nmap · SQLMap · Metasploit · Frida · MobSF · JADX
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
| **OSCP** — Offensive Security Certified Professional | 🔄 Pursuing 2025/26 | Offensive Security |
| **PortSwigger Web Security Academy** | ✅ 100% Complete | PortSwigger |
| **TryHackMe** — Pentester + Web Pentester paths | ✅ Complete | TryHackMe |
| **HackTheBox Academy** — Junior Red Team path | 🔄 In Progress | HackTheBox |

---

## ⚖️ Legal Notice

All security assessments in this portfolio were conducted under formal written agreements.

- NDA periods have elapsed for all engagements
- Client permission for publication obtained via written correspondence
- Client names anonymised in the public version; full details available to employers on request
- Production credentials, internal IPs, and user PII have been removed
- No ready-to-run weaponised exploit code is published here

→ [LEGAL_DISCLAIMER.md](./LEGAL_DISCLAIMER.md) · [SECURITY.md](./SECURITY.md)

---

## 📬 Contact

Open to **full international relocation**.

- 📧 alex123kamany@gmail.com
- 💼 [linkedin.com/in/ak-365a24188/](https://linkedin.com/in/ak-365a24188/)
- 📱 +90 553 518 37 43

*Preferred roles: Penetration Tester · Red Team Analyst · Security Engineer · SOC Analyst (Tier 2/3)*  
*Languages: Persian (Native) · English C1 (IELTS 7.0) · German A2*

---

<div align="center">
<sub>All assessments conducted ethically and legally under signed agreements · Open to relocation worldwide</sub>
</div>
