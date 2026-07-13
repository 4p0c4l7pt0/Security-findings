# 🛒 MCI Online Shop — Web Penetration Test

**Client:** MCI — sandbox-ebcom.mci.ir/ecm/mci/eshop/  
**Assessment Type:** Black-Box Web Application Penetration Test  
**Stack:** React · NGINX OpenResty 1.15.8.3 · jQuery  
**Standards:** OWASP WSTG · PTES · CVSSv3.1

---

## Findings

| ID | Vulnerability | CVSS | Severity |
|---|---|:---:|:---:|
| SHOP-001 | **OTP Brute Force — Full Account Takeover** | 9.4 | 🔴 Critical |
| SHOP-002 | **Alternative Auth Channel Bypass** | 9.1 | 🔴 Critical |
| SHOP-003 | Account Enumeration via Differential Responses | 8.3 | 🟠 High |
| SHOP-004 | Password Change Brute Force (No Rate Limit / CAPTCHA) | 8.3 | 🟠 High |
| SHOP-005 | Unlimited OTP SMS Bombing (All Shop Flows) | 7.5 | 🟠 High |
| SHOP-006 | Unauthorised Package Purchase Billed to Victim | 7.1 | 🟠 High |

---

## Key Attack Chain

**SHOP-001/006 Combined:** Attacker targets victim's phone number → initiates package purchase using "Bill/Credit Deduction" → brute-forces the victim's 4-digit OTP → purchases a data package charged to the victim's account. The victim has no prior warning and receives no consent prompt.

**SHOP-003 Enumeration:** HTTP 403 = valid number with wrong password · HTTP 520 = number not registered. Attacker can build a validated subscriber list using Burp Intruder.

---

## Root Cause

All 6 findings share a single root cause: **no server-side OTP lifecycle management**. Rate limiting, lockout, and expiry were absent from every OTP endpoint across the shop. A single middleware fix would close 4 of the 6 findings simultaneously.

---

## Scope

- URL: https://sandbox-ebcom.mci.ir/ecm/mci/eshop/
- Backend: https://stage-ebcom.mci.ir (shared with MY MCI app)
- Tools: Burp Suite Pro · Netsparker · Acunetix · SQLMap · Nmap · Wappalyzer

---

📄 **[→ View Full Report with Evidence Screenshots](./report.html)**
