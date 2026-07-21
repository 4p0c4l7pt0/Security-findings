# 📱 MY MCI Android App — Penetration Test

**Client:** MCI (Mobile Communication Company of Iran — همراه اول)  
**Subscribers:** 40,000,000+  
**Assessment Type:** Black-Box · Android + Backend API  
**Standards:** OWASP MASVS L2 · OWASP WSTG · PTES · CVSSv3.1  
**Report Version:** 1.16 → English Edition 1.0

---

## Summary

| Severity | Count |
|:---:|:---:|
| 🔴 Critical | 7 |
| 🟠 High | 5 |
| 🟡 Medium | 6 |
| 🔵 Low / Info | 3 |
| **Total** | **22** |

---

## Top Findings

### 🔴 MCI-app-001 · SMS Spoofing · CVSS 10.0
Unauthenticated POST to the OTP dispatch endpoint accepted an arbitrary `msisdn` (any of 40M subscribers) and arbitrary message body. Attacker could send phishing SMS from the official MCI sender ID to any subscriber, unlimited times, with no authentication.

**Proven:** Custom URL delivered via MCI SMS to arbitrary subscriber.

---

### 🔴 MCI-app-002 · OTP Brute Force → Full Account Takeover · CVSS 9.9
4-digit OTP (10,000 values), no rate limiting, no expiry on failure, no lockout.  
Correct OTP recovered after **4,954 Burp Intruder requests**. JWT extracted. Victim profile accessed.

---

### 🔴 MCI-app-003 · BOLA — Unauthorised Paid Service on Victim · CVSS 9.9
RBT (Ring Back Tone) activation API accepted arbitrary `Msisdn` parameter.  
**Proven:** 16,500 IRR charged from victim balance (31,400 → 14,900 IRR). Victim received activation SMS.

---

### 🔴 MCI-app-004 · Parental Control Hijack via OTP Brute Force · CVSS 9.8
Bomino feature: add any MCI number as a "child" by brute-forcing their OTP. Once added, attacker can apply full internet blocking to the victim.  
**Proven:** Victim internet restricted via "Hezar Boom" plan. Activation SMS sent to victim.

---

### 🔴 MCI-app-005 · Race Condition — Loyalty Points Over-Expenditure · CVSS 9.4
Parallel charity requests processed simultaneously, spending more points than the account balance allows. No atomic transaction locking on the backend.

---

### 🟠 MCI-app-013 · CBC Padding Oracle · CVSS 7.1
APK decompilation reveals AES-CBC with PKCS5/PKCS7. Differential server error responses enable oracle-based decryption of arbitrary ciphertext blocks.

---

## Scope

| Asset | Details |
|---|---|
| Android APK | ir.mci.ecareapp.sandbox · v16 · targetSdk 33 · minSdk **16** |
| Staging API | https://stage-ebcom.mci.ir |
| Production API | https://ebcom.mci.ir |

## Tools Used

Burp Suite Pro · Genymotion · JADX · Apktool · Frida · MobSF · ADB · Drozer · Nessus

---

📄 **[→ View Full Report with Evidence Screenshots](./report.html)**
