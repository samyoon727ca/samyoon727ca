## Samuel Yoon

Security engineering for embedded and autonomous systems: threat models and derived requirements, secure and measured boot, and firmware analysis. M.S. Cybersecurity student at the University of Arizona.

<!-- Uncomment once the site is live:
[Website](https://example.com) · [Résumé](https://example.com/resume.pdf) · [LinkedIn](https://www.linkedin.com/in/example) · you@example.com
-->

### UAS security portfolio

This portfolio secures one notional, unclassified small UAS across a series of repos: a PX4 flight controller, a Linux companion computer, a ground control station and a MAVLink C2 link. Together they read as one security engineering effort, from threat model to test evidence. Every requirement traces back to the P1 architecture.

| # | Project | Purpose | Status |
|---|---|---|---|
| P1 | [Security architecture and requirements](https://github.com/samyoon727ca/uas-sec-p1-architecture) | Trust boundaries, STRIDE/EMB3D/ATT&CK for ICS threat model, NIST SP 800-160 resiliency mapping, derived "shall" requirements with machine-checked traceability and a verification plan, SysML v2 model. Five-minute read: [PDR brief](https://github.com/samyoon727ca/uas-sec-p1-architecture/blob/main/brief/pdr-brief.pdf) | Complete |
| P2 | [Verified boot chain](https://github.com/samyoon727ca/uas-sec-p2-verified-boot) | Verified boot from a hardware root of trust, TPM-sealed keys under signed PCR policies with anti-rollback, PX4 Bootloader Secure Boot. Scripted evidence in QEMU with swtpm, then on an NXP i.MX 8M Plus board (DEBIX Model A) and a Pixhawk 6X | In progress: [every case CI can run passes](https://github.com/samyoon727ca/uas-sec-p2-verified-boot/blob/main/evidence/ve07-ci/20261013-d9149f6/summary.md); hardware runs pending |
| P3 | PKI and signed updates | Offline root CA, HSM-backed intermediate, device identity, firmware signing, rotation and revocation | Planned |
| P4 | Hardened image and supply chain | Read-only, integrity-protected Linux image; SBOM, CVE scanning, signed artifacts and build provenance in CI | Planned |
| P5 | Hardware and firmware assessment | Debug-interface access, firmware extraction and analysis, with findings mapped to P1 requirements | Planned |
| P6 | RMF-as-code | OSCAL system security plan, NIST SP 800-53 Rev. 5 control mapping, evidence pulled from P4 | Planned |
| P7 | Protocol fuzzing (optional) | Coverage-guided fuzzing of a MAVLink or CAN parser | Planned |

Every repo opens the same way: **threat → requirement → design → verification evidence**.

All work is notional and unclassified. It is built only from public sources (PX4 and MAVLink documentation, NIST, MITRE) and uses standard cryptography through existing libraries.

### Firmware security research

[firmware-security-research](https://github.com/samyoon727ca/firmware-security-research) holds patch-diff case studies on public router firmware and the tooling behind them. Every target is public, and firmware images are never redistributed.

- [DrayTek Vigor300B `download_ovpn` command injection](https://github.com/samyoon727ca/firmware-security-research/blob/main/writeups/draytek-vigor300b-download_ovpn-cmdinjection.md): rediscovers CVE-2024-45890 on a sibling device by diffing the public firmware chain. It also shows how a single-model dedup nearly labeled a known n-day as new.
- [D-Link DIR-816L HNAP `SOAPAction` command injection](https://github.com/samyoon727ca/firmware-security-research/blob/main/writeups/dir-816l-hnap-soapaction-cmdinjection.md): the same funnel run end to end on real vendor firmware (CVE-2015-2051 class).
- The funnel itself: firmware triage, version-to-version binary diffing, CVSS-scored vendor reports and CVE write-ups, plus a MAVLink security test harness for ArduPilot and PX4 SITL.

### Other work

- [DER-blockchain](https://github.com/samyoon727ca/DER-blockchain): a proof-of-concept peer-to-peer energy marketplace. Rooftop-solar exports become kWh tokens minted from meter-signed readings. Neighbors buy them with a stablecoin, and the tokens burn when the buyer's meter shows the energy was used. Three Solidity contracts on a local Hardhat chain, with an oracle, trading bots, a live dashboard and 88 tests.
