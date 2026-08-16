# 🔒 Vulnerability Assessment Report — ShopNow Web App

A passive, non-intrusive security assessment of a live e-commerce web application, performed as part of a Cyber Security internship task. This project demonstrates the full workflow of a professional security audit — from scanning to client-ready reporting.

![Status](https://img.shields.io/badge/status-completed-brightgreen)
![Type](https://img.shields.io/badge/assessment-passive%20scan-blue)
![Risk](https://img.shields.io/badge/highest%20risk-medium-orange)

---

## 📌 About the Task

Every business today owns a website — but most websites are not secure. Small businesses, startups, and agencies often use outdated plugins, misconfigure security headers, or expose sensitive information unknowingly.

Clients rarely ask for hacking. They ask for clarity:
> "Is my website safe? What are the risks? What should we fix first?"

This project answers that — professionally and ethically.

## 🎯 Objective

- Analyze a live web application for common security weaknesses
- Classify risks in a business-friendly way (Low / Medium / High)
- Explain issues in plain language, without jargon overload
- Suggest practical, actionable remediation steps
- Present findings in a clean, professional audit report

**This is security consulting, not hacking.**

## ⚖️ Scope & Ethics

This assessment followed strict ethical guidelines throughout.

**✅ Allowed**
- Public-facing pages only
- Passive scanning
- Security header checks
- Configuration analysis

**❌ Not Allowed**
- Login bypass
- Exploitation
- Brute-force attacks
- Denial-of-Service (DoS)
- Any activity that could harm the target application

> Think like an auditor, not an attacker.

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **OWASP ZAP 2.17.0** (Passive Scan) | Identify vulnerabilities without attacking the app |
| **Browser DevTools** | Inspect headers, cookies, and client-side code |
| **Nmap** | Basic port & exposure analysis |
| **Microsoft Word / Canva** | Professional report design |

## 🌐 Target Application

- **App:** ShopNow (E-commerce web application)
- **Frontend:** `http://localhost:3000` (React SPA)
- **API Backend:** `http://localhost:5000` (Express.js REST API)
- **Assessment type:** Passive / read-only scan

## 📋 Summary of Findings

| # | Finding | Risk | Instances |
|---|---|---|---|
| 1 | Content Security Policy (CSP) Header Not Set | 🟠 Medium | 6 URLs |
| 2 | Cross-Domain Misconfiguration (permissive CORS) | 🟠 Medium | 1 URL |
| 3 | Missing Anti-Clickjacking Header (X-Frame-Options) | 🟠 Medium | 1 URL |
| 4 | Strict-Transport-Security Header Not Set | 🟢 Low | Systemic |
| 5 | Server Leaks Information via "X-Powered-By" Header | 🟢 Low | 1 URL |
| 6 | X-Content-Type-Options Header Missing | 🟢 Low | 8 URLs |
| 7 | Timestamp Disclosure (Unix timestamp in bundle.js) | 🟢 Low | 1 URL |
| 8 | Information Disclosure — Suspicious Comments | 🟢 Low | 12 instances |
| 9 | Authentication Request Identified (credential handling) | ⚪ Informational | 1 endpoint |
| 10 | Modern Web Application Detected | ⚪ Informational | 1 URL |

**Risk key:** 🔴 High = fix immediately · 🟠 Medium = fix this sprint · 🟢 Low = fix when convenient · ⚪ Informational = awareness only

No High-risk issues were identified. Findings were driven primarily by missing/misconfigured HTTP security headers rather than any critical application flaw.

## 🔍 Methodology

1. Selected a public-facing test web application
2. Performed read-only, passive analysis using OWASP ZAP
3. Checked security headers, CORS policy, and information disclosure
4. Documented each finding: what it is, why it matters, and its risk level
5. Classified all findings by severity
6. Wrote clear, non-technical remediation guidance for each issue

## ✅ Recommended Fix Priority

1. **Immediate:** Add `Content-Security-Policy`, `X-Frame-Options`, and lock down CORS to trusted origins
2. **Short term:** Add `X-Content-Type-Options: nosniff` and `Strict-Transport-Security`, remove `X-Powered-By`, strip build timestamps/comments from production bundles
3. **Ongoing:** Re-scan after every release; extend future testing to authenticated flows under a properly scoped, authorized engagement

## 📄 Full Report

The complete Vulnerability Assessment Report — including affected URLs, evidence, business impact, and remediation steps for every finding — is available in two formats:

📎 [`VULNERABILITY_ASSESSMENT_REPORT.pdf`](./VULNERABILITY_ASSESSMENT_REPORT.pdf) — recommended for viewing/printing
📎 [`VULNERABILITY_ASSESSMENT_REPORT.docx`](./VULNERABILITY_ASSESSMENT_REPORT.docx) — editable Word version

## 🖼️ Evidence

Raw OWASP ZAP screenshots supporting each finding are included in [`/screenshots`](./screenshots) and are also embedded directly inside the PDF/DOCX report next to their corresponding finding:

| Screenshot | Finding |
|---|---|
| `01-csp-header-not-set.png` | CSP Header Not Set |
| `02-csp-header-detail.png` | CSP Header Not Set (request detail) |
| `03-cross-domain-misconfig-cors.png` | Cross-Domain Misconfiguration (CORS) |
| `04-x-powered-by-header.png` | X-Powered-By Header Leak |
| `05-timestamp-disclosure.png` | Timestamp Disclosure |
| `06-authentication-request.png` | Authentication Request Identified |
| `07-modern-web-application.png` | Modern Web Application Detected |

## 🧠 Skills Demonstrated

`Vulnerability Analysis` · `Risk Classification` · `Security Reporting` · `Client Communication` · `OWASP ZAP` · `HTTP Security Headers` · `Ethical/Passive Security Testing`

---

⚠️ **Disclaimer:** This assessment was performed on a local/test instance of the application for educational purposes only, using strictly passive, non-intrusive techniques. No exploitation, unauthorized access, or disruptive testing was carried out.
