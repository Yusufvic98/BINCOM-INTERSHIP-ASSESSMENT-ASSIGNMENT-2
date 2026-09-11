# BINCOM-INTERSHIP-ASSESSMENT-ASSIGNMENT-2
Vulnerability Scan &amp; Exploit Simulation
# BINCOM Assessment 2 — Vulnerability Scan & Exploit Simulation

Authorized, lab-only vulnerability assessment against a **Metasploitable 2** target inside an isolated VirtualBox host-only network, performed as part of the BINCOM cybersecurity training program (Assessment 2).

## 🎯 Objective
Set up a deliberately vulnerable web app, run a full vulnerability scan, validate one discovered weakness through controlled exploitation, and produce a remediation plan — the full detect → validate → remediate lifecycle.

## 🧪 Lab Environment
| Component | Detail |
|---|---|
| Attacker / Scanner | Kali Linux — 192.168.56.101 |
| Target | Metasploitable 2 — 192.168.56.103 |
| Network | 192.168.56.0/24 (VirtualBox Host-Only, isolated) |
| Web app | DVWA 1.0.7 |
| Scanner | Nessus Essentials (used as the approved substitute after OpenVAS feed issues) |
| Exploitation | Metasploit Framework |

## 🔍 What Was Done
1. **Recon** — Nmap service/version enumeration across the full port range.
2. **Vulnerability scan** — Nessus Basic Network Scan (all ports, TCP/ARP/ICMP discovery) → **69 findings** (3 Critical, 16 High, 34 Medium, 6 Low, 10 Info).
3. **Exploitation attempt #1** — Ghostcat (Apache Tomcat AJP request injection, CVE-2020-1938) targeted at 8009/tcp. Module ran but could not read the target file — documented as a **failed validation**, not overstated.
4. **Exploitation #2 (successful)** — `auxiliary/scanner/vnc/vnc_login` against the weak VNC credential Nessus flagged on 5900/tcp (Plugin 61708, CVSS 10.0). Result: **Login Successful** — confirming the Critical finding was real and exploitable, not a false positive.
5. **Remediation plan** — credential rotation, service minimization, network access control, and a rescan-based validation plan, plus prioritized fixes for the other Critical/High findings (legacy SSHv1, Samba Badlock, world-readable NFS, rlogin, etc.).

## 📊 Results Summary
| Severity | Count |
|---|---|
| Critical | 3 |
| High | 16 |
| Medium | 34 |
| Low | 6 |
| Informational | 10 |

## 📁 Contents
- `Vulnerability_Scan_Report.pdf` — full scan methodology, findings, and analysis
- `Exploitation_Evidence.pdf` — Metasploit VNC validation walkthrough + screenshot
- `Mitigation_Remediation_Document.pdf` — remediation plan and hardening controls
- Supporting screenshots (Nmap, Nessus config/results, Metasploit console)

## ⚠️ Scope & Ethics Note
All activity was performed against an intentionally vulnerable, isolated lab target (Metasploitable 2) with no connectivity outside the host-only network. No persistence or destructive actions were taken. This repo is shared for educational/portfolio purposes only.

## 🛠️ Tools Used
`Kali Linux` · `Nmap` · `Nessus Essentials` · `Metasploit Framework` · `DVWA`

---
*Part of an ongoing hands-on cybersecurity portfolio — see other assessments in this profile.*
