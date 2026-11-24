# 🦉 OCertX

<p align="center">
  <img src="https://img.shields.io/badge/Platform-Linux-0a0c10?style=flat-square"/>
  <img src="https://img.shields.io/badge/Category-OCipher-blue?style=flat-square"/>
  <img src="https://img.shields.io/badge/License-Proprietary-orange?style=flat-square"/>
  <img src="https://img.shields.io/badge/Part%20of-OwlSec%20Toolkit-7b5ea7?style=flat-square"/>
  <img src="https://img.shields.io/badge/Version-2.1-cyan?style=flat-square"/>
</p>

> **OCertX** — X.509 Certificate Inspector (TLS/PKI Analysis)

---

> ⚠️ **AUTHORISED USE ONLY** — Use only on systems you own or have explicit written permission to test. Unauthorised use is illegal.

---

## 📌 Overview

OCertX is an X.509 certificate inspector for PKI and TLS work, parsing certificates from files or live SSL/TLS connections. It inspects certificate chains, expiry, fingerprints and hostname matches, decodes PEM/DER and CSRs, checks OCSP revocation and generates SPKI pins. Certificates can be compared, converted, bundle-split and exported, with JSON/CSV output.

---

## ✨ Features

- Parse and inspect X.509 certificates from PEM/DER files
- Live SSL/TLS connection and certificate-chain analysis
- Expiry monitoring, fingerprint verification and hostname matching
- OCSP revocation checks and SPKI pin generation
- PEM/DER decode/convert, bundle split and certificate compare
- JSON / CSV export (full field parsing with optional cryptography library)

---

## ⚙️ Requirements

- **Linux**
- **No Python installation needed** — runs as a standalone executable

---

## 🚀 Usage

```bash
./OCertX --host example.com
./OCertX --host example.com --port 8443
./OCertX --file server.pem
./OCertX --help
```

---

## 📦 Part of OwlSec Toolkit

This tool is part of the **OwlSec** suite — a collection of 275+ security and privacy tools.

🔗 [owlsec.org](https://owlsec.org)

---

## ©️ License

Proprietary — © 2026 Owlsec LLC. All rights reserved.

*Tools are distributed as pre-built executables. Source code is proprietary.*

---

## 🔍 Verification & Transparency

This tool is closed-source. These files let you see exactly what is inside it,
without the source:

- [`SBOM.cdx.json`](SBOM.cdx.json) — CycloneDX inventory: SHA-256 of this
  binary, bundled CPython version, and every bundled library with its exact
  version and license. Feed it to Grype, Trivy or Dependency-Track to audit
  our dependencies for CVEs yourself.
- [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md) — the full license text
  of every third-party component, extracted from this binary.

**No telemetry, no analytics, no licence check-in.** This tool does not phone
home. Verify that claim yourself:

```bash
sudo strace -f -e trace=network ./OCertX --help   # watch every network call
firejail --net=none ./OCertX --help               # deny the network entirely
```

Release signing, GPL compliance and vulnerability reporting:
[**TRUST.md**](https://github.com/owlsecx/owl-os/blob/main/TRUST.md)
