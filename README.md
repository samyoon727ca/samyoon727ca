## Systems security engineering portfolio

This portfolio secures one notional, unclassified small UAS across a series of repos: a PX4 flight controller, a Linux companion computer, a ground control station and a MAVLink C2 link. Together they read as one security engineering effort, from threat model to test evidence. Every requirement traces back to the P1 architecture.

| # | Project | Purpose | Status |
|---|---|---|---|
| P1 | [Security architecture and requirements](https://github.com/samyoon727ca/uas-sec-p1-architecture) | System description, trust boundaries, STRIDE/EMB3D/ATT&CK for ICS threat model, derived "shall" requirements with machine-checked traceability, SysML v2 model, PDR-style brief | In progress |
| P2 | Verified boot chain | Signed images, rollback protection and measured boot on a development board | Planned |
| P3 | PKI and signed updates | Offline root CA, HSM-backed intermediate, device identity, firmware signing, rotation and revocation | Planned |
| P4 | Hardened image and supply chain | Read-only, integrity-protected Linux image; SBOM, CVE scanning, signed artifacts and build provenance in CI | Planned |
| P5 | Hardware and firmware assessment | Debug-interface access, firmware extraction and analysis, with findings mapped to P1 requirements | Planned |
| P6 | RMF-as-code | OSCAL system security plan, NIST SP 800-53 Rev. 5 control mapping, evidence pulled from P4 | Planned |
| P7 | Protocol fuzzing (optional) | Coverage-guided fuzzing of a MAVLink or CAN parser | Planned |

Every repo opens the same way: **threat → requirement → design → verification evidence**.

All work is notional and unclassified. It is built only from public sources (PX4 and MAVLink documentation, NIST, MITRE) and uses standard cryptography through existing libraries.
