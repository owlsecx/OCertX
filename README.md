# 🦉 OCertX

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux%20%2F%20Windows-informational?style=flat-square&logo=linux&logoColor=white&color=0a0c10"/>
  <img src="https://img.shields.io/badge/Category-OCipher%20%2F%20PKI%20%26%20TLS-cyan?style=flat-square"/>
  <img src="https://img.shields.io/badge/Stdlib%20Only-No%20Deps%20Required-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-MIT-green?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-1.0-cyan?style=flat-square"/>
</p>

> **OCertX** is an X.509 certificate inspector — live TLS inspection, PEM/DER file parsing, full certificate chain analysis, bulk expiry monitoring, and fingerprint verification, with JSON export to `ocert_output/`.

---

## 📌 Overview

OCertX connects to live TLS servers or parses local certificate files to extract and analyse every significant X.509 field — subject, issuer, validity dates, key type, signature algorithm, SANs, key usage, OCSP, and more — then scores the overall security posture and exports a structured JSON report.

---

## 🖥️ Modules

| # | Module | Description |
|---|--------|-------------|
| **[1] Live TLS Inspect** | Connect to any host:port, fetch the live certificate, analyse all fields, rate TLS protocol, compute security score |
| **[2] Certificate File** | Parse a local PEM or DER certificate file and display all fields |
| **[3] Chain Inspection** | Fetch the full TLS certificate chain, inspect each cert in the chain, and rate the TLS protocol version |
| **[4] Expiry Monitor** | Bulk-check expiry dates for a list of hosts — colour-coded days remaining per host |
| **[5] Fingerprint Verify** | Compute SHA-256, SHA-1, and MD5 fingerprints and compare against a trusted expected value |

---

## 🔍 Certificate Fields Displayed

| Category | Fields |
|----------|--------|
| **Subject** | CN · Organization · Org Unit · Country |
| **Issuer** | CN · Organization |
| **Validity** | Not Before · Not After · Days remaining (colour-coded) |
| **Public Key** | Algorithm (RSA/EC/DSA) · Bit size · EC curve name |
| **Signature** | Signature hash algorithm |
| **Extensions** | Subject Alternative Names (DNS + IP) · Key Usage · Extended Key Usage · Is CA flag |
| **OCSP** | OCSP responder URL |
| **TLS Session** | Protocol version · Cipher suite · Key length |
| **Fingerprints** | SHA-256 · SHA-1 · MD5 (formatted as colon-separated hex) |
| **Metadata** | Serial number · Certificate version |

---

## 📊 Security Score

Each certificate is rated 0–100 with deductions for weaknesses:

| Rating | Score | Conditions |
|--------|-------|------------|
| **EXCELLENT** | 90–100 | Valid, RSA-2048+, SHA-256 or better |
| **GOOD** | 70–89 | Minor issues |
| **MODERATE** | 50–69 | Expiring within 90 days |
| **POOR** | 30–49 | Weak key or SHA-1 signature |
| **CRITICAL** | < 30 | Expired or MD5 signature |

Deductions: −40 expired · −20 expiring soon · −30 RSA < 2048-bit · −20 EC < 256-bit · −30 MD5 signature · −15 SHA-1 signature

---

## 🔒 TLS Protocol Ratings

| Protocol | Rating | Display |
|----------|--------|---------|
| TLS 1.3 | ✅ Modern | Green |
| TLS 1.2 | 🟡 Acceptable | Yellow |
| TLS 1.1 | ⚠️ Deprecated | Orange |
| TLS 1.0 | ❌ Insecure | Red |
| SSL 3.0 / SSL 2.0 | ❌ Broken | Red |

---

## ✅ Fingerprint Verification

Module [5] computes SHA-256, SHA-1, and MD5 fingerprints of the certificate and compares against a user-supplied expected value — accepts hex with or without colons. Displays a clear `VERIFIED` or `MISMATCH` result. Works with live hosts or local cert files.

---

## 📤 Output

JSON reports saved to `ocert_output/`:

```
ocert_output/ocert_YYYYMMDD_HHMMSS.json
```

Each report contains: tool metadata, host, port, TLS protocol, cipher suite, security score, rating, all fingerprints, and full certificate field set.

---

## ⚙️ Requirements

- **Linux or Windows**
- **No Python installation needed** — runs as a standalone executable
- **`cryptography` library** is optional but enables full field parsing: SANs, Key Usage, Extended Key Usage, OCSP, EC curve name, Is CA flag

---

## 🚀 Usage

```bash
./OCertX
```

---

## 📦 Part of OwlSec Toolkit

This tool is part of the **OwlSec** suite — a collection of 300+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

MIT License — © Khaled S. Haddad

*Tools are distributed as pre-built executables. Source code is proprietary.*
