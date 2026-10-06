# What's Changed Since the 2019 Talk

The core message of the 2019 slides still holds: change process and culture, empower the team,
test early and continuously, and treat tools as support for people and process. Several specific
claims and recommendations have aged, though. Use this page alongside `slides-min.pdf`.

_Last reviewed: October 2026._

## Concepts

| 2019 slide | Where things stand now |
|---|---|
| **"The 'AST' family"**: SAST, DAST, SCA, IAST, RASP, MAST | Still valid, but the list has grown: **secrets scanning**, **IaC scanning**, **container scanning**, **SBOMs** and **CI/CD pipeline security** are now standard pipeline stages. **ASPM** (Application Security Posture Management) tools aggregate and correlate findings across all of them. |
| **"IAST is predicted to eventually replace DAST"** | That didn't happen. DAST is still widely used, especially for APIs (ZAP, Nuclei, Schemathesis). IAST and RASP remain niche and mostly commercial. Much of their role has moved into runtime/observability platforms and WAF/WAAP products. |
| **SAST "poor accuracy"** | Modern rule-based engines (Semgrep/Opengrep, CodeQL) are much more precise and fast enough to run on every pull request. Reachability analysis also reduces SCA noise. |
| **Modern cloud native architecture is diverse** | Still true, and Kubernetes security is now a mature field: admission policy (Kyverno, OPA Gatekeeper), runtime detection (Falco), CIS benchmarks (kube-bench), and Pod Security Standards. Docker Swarm is rarely used. |
| **"Be sure to keep track of dependencies"** | This is now its own discipline, **software supply chain security**. After SolarWinds (2020), Log4Shell (2021) and xz-utils (2024), teams generate SBOMs (CycloneDX/SPDX), sign artifacts (Sigstore), produce build provenance (SLSA), and watch for malicious packages, not just vulnerable ones. |
| **Vuln scan ≠ vuln assessment** | Still true. Prioritization now has better inputs: **CISA KEV** (known to be exploited), **EPSS** (likelihood of exploitation), **CVSS v4.0**, reachability analysis, and **VEX** statements to record "not affected". |
| **Git hooks for security (Talisman, Therapist)** | Use the **pre-commit** framework with Gitleaks/TruffleHog. Server-side **push protection** (GitHub, GitLab) now blocks secrets even when local hooks are skipped. |
| **Threat modeling: STRIDE, VAST, OCTAVE, Trike, PASTA** | Still relevant. The **Threat Modeling Manifesto** (2020) and lightweight, continuous approaches are now mainstream. Threat modeling as code (pytm, Threat Dragon) fits developer workflows. |
| **Skill-up: OWASP chapter, NIST, cybrary, safecode, sqreen** | Sqreen no longer exists (acquired by Datadog). Free, high-quality options now include PortSwigger Web Security Academy, OpenSSF's LFD121 course, and the OWASP Cheat Sheet Series. |
| **Not covered in 2019** | **AI/LLM security**: prompt injection, insecure output handling and data leakage (OWASP Top 10 for LLM Applications), plus reviewing AI-generated code and watching for hallucinated package names. **Regulation and policy**: NIST SSDF, CISA Secure by Design, the EU Cyber Resilience Act, and US federal secure-software attestation. |

## Statistics in the slides

These numbers came from 2017–2019 sources and should not be quoted as current:

- **Unfilled cybersecurity jobs (350K → 500K by 2021)**: see the latest
  [ISC2 Cybersecurity Workforce Study](https://www.isc2.org/research).
- **Breach costs**: see the latest IBM Cost of a Data Breach report and the
  [Verizon DBIR](https://www.verizon.com/business/resources/reports/dbir/).
- **Bad bot traffic (2019 Bad Bot Report, Distil Networks)**: Distil was acquired by Imperva,
  which still publishes an annual Bad Bot Report.
- **Cost-to-fix multipliers by SDLC phase**: the original source of the popular "100x" figure is
  disputed. The case for shifting left rests on faster feedback, not that specific number.

## Tools named in the slides or resources

See the "Retired / Superseded Resources" table at the end of [resources.md](resources.md).
