# RESOURCES FOR SHIFT LEFT APPLICATION SECURITY
## Preference towards Open Source Software

_Last reviewed: October 2026. Originally compiled for SeaGL 2019; see
[whats-changed.md](whats-changed.md) for how the landscape has moved since the talk._

Tags used below: `[SAST]` static analysis, `[SCA]` software composition analysis,
`[DAST]` dynamic testing, `[IAST]`, `[RASP]`, `[SECRETS]`, `[IaC]` infrastructure-as-code,
`[CONTAINER]`, `[SBOM]`, `[SUPPLY-CHAIN]`, `[LOCAL]` runs on a dev machine,
`[CI/CD]` pipeline-friendly, `[PAID]` commercial (free tiers may exist).

- [Frameworks & Standards](#frameworks--standards)
- [Articles & Reports](#articles--reports)
- [Culture & Threat Modeling](#culture--threat-modeling)
- [CI/CD Platforms with Security Built In](#cicd-platforms-with-security-built-in)
- [Tools](#tools)
- [Software Supply Chain Security](#software-supply-chain-security)
- [AI / LLM Application Security](#ai--llm-application-security)
- [Vulnerability Databases & Prioritization](#vulnerability-databases--prioritization)
- [Security Education](#security-education)
- [Vulnerable Applications (Practice Targets)](#vulnerable-applications-practice-targets)
- [Public Speaking & Influence](#public-speaking--influence)
- [Retired / Superseded Resources](#retired--superseded-resources)

---

## Frameworks & Standards

##### NIST Secure Software Development Framework (SSDF, SP 800-218)
The reference set of secure development practices; widely used for software attestation.
- https://csrc.nist.gov/projects/ssdf

##### CISA Secure by Design
Pushes responsibility for security outcomes onto software producers, not customers.
- https://www.cisa.gov/securebydesign

##### OWASP Top 10 (web) and OWASP API Security Top 10
- https://owasp.org/www-project-top-ten/
- https://owasp.org/www-project-api-security/

##### OWASP Application Security Verification Standard (ASVS)
Testable security requirements — useful as acceptance criteria in stories.
- https://owasp.org/www-project-application-security-verification-standard/

##### OWASP SAMM (Software Assurance Maturity Model)
Measure and plan an AppSec program.
- https://owaspsamm.org/

##### OWASP Mobile Application Security (MASVS / MASTG)
- https://mas.owasp.org/

##### SLSA (Supply-chain Levels for Software Artifacts)
- https://slsa.dev/

##### NIST Cybersecurity Framework 2.0
- https://www.nist.gov/cyberframework

##### NIST container security (SP 800-190)
- https://csrc.nist.gov/pubs/sp/800/190/final

##### EU Cyber Resilience Act (CRA)
Brings mandatory vulnerability handling and SBOM-style obligations to products sold in the EU.
- https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act

---

## Articles & Reports

##### OWASP Cheat Sheet Series (concise, developer-focused guidance on almost every topic)
- https://cheatsheetseries.owasp.org/

##### OWASP DevSecOps Guideline
- https://owasp.org/www-project-devsecops-guideline/

##### Web Application Security basics (Martin Fowler)
- https://martinfowler.com/articles/web-security-basics.html

##### CNCF Kubernetes security audits & Cloud Native Security Whitepaper
- https://github.com/kubernetes/sig-security/tree/main/sig-security-external-audit
- https://github.com/cncf/tag-security

##### Verizon Data Breach Investigations Report (annual breach statistics)
- https://www.verizon.com/business/resources/reports/dbir/

##### ISC2 Cybersecurity Workforce Study (annual workforce-gap statistics)
- https://www.isc2.org/research

##### OpenSSF Concise Guide for Developing More Secure Software
- https://best.openssf.org/Concise-Guide-for-Developing-More-Secure-Software

---

## Culture & Threat Modeling

##### Read: The Phoenix Project / The Unicorn Project
Gene Kim, Kevin Behr, George Spafford — IT Revolution Press

##### Read: Alice and Bob Learn Application Security / Alice and Bob Learn Secure Coding
Tanya Janca — Wiley

##### Pushing Left, Like a Boss — Tanya Janca
Delivered from the perspective of a security specialist, with lots of developer tips.
- https://www.youtube.com/watch?v=8kqtrX6C10c
- https://github.com/shehackspurple/TTT-Pushing-Left

##### OWASP Security Champions Guide
- https://securitychampions.owasp.org/

##### Threat Modeling Manifesto
- https://www.threatmodelingmanifesto.org/

##### OWASP Threat Modeling Cheat Sheet
- https://cheatsheetseries.owasp.org/cheatsheets/Threat_Modeling_Cheat_Sheet.html

##### OWASP Threat Dragon (open source threat modeling tool)
- https://owasp.org/www-project-threat-dragon/

##### OWASP pytm (threat modeling as code)
- https://github.com/OWASP/pytm

##### Elevation of Privilege (STRIDE card game) & OWASP Cornucopia
- https://github.com/adamshostack/eop
- https://owasp.org/www-project-cornucopia/

##### Sensible Agile Threat Modelling cards (Thoughtworks)
- https://github.com/thoughtworksinc/sensible-security-conversations

##### Cost of fixing issues — a word of caution
The "100x more expensive to fix in production" figure is widely repeated, but its original
source is disputed. The argument for shifting left still holds: feedback is faster and context is
fresher, but don't lean on that one number.

---

## CI/CD Platforms with Security Built In

##### GitHub Actions + GitHub Advanced Security
CodeQL code scanning, Dependabot, secret scanning with push protection. Free for public repos.
- https://docs.github.com/en/code-security

##### GitLab Application Security
SAST, DAST, dependency/container scanning, secret detection, IaC scanning.
- https://docs.gitlab.com/user/application_security/

##### CircleCI Orbs (e.g. Snyk, Trivy, OWASP ZAP integrations)
- https://circleci.com/developer/orbs

##### Jenkins
- https://www.jenkins.io/

##### Tekton + Tekton Chains (signed provenance for builds)
- https://tekton.dev/docs/chains/

##### GoCD
- https://www.gocd.org/

##### Hardening the pipeline itself
- [OWASP Top 10 CI/CD Security Risks](https://owasp.org/www-project-top-10-ci-cd-security-risks/)
- [zizmor — static analysis for GitHub Actions workflows](https://github.com/zizmorcore/zizmor)
- [StepSecurity Harden-Runner](https://github.com/step-security/harden-runner)

---

## Tools

### Pre-commit / Secrets
##### pre-commit (framework for git hooks) [LOCAL]
- https://pre-commit.com/

##### Gitleaks [SECRETS][LOCAL][CI/CD]
- https://github.com/gitleaks/gitleaks

##### TruffleHog [SECRETS][LOCAL][CI/CD]
- https://github.com/trufflesecurity/trufflehog

##### detect-secrets (Yelp) [SECRETS][LOCAL]
- https://github.com/Yelp/detect-secrets

##### Talisman (Thoughtworks git pre-push hook) [SECRETS][LOCAL]
- https://github.com/thoughtworks/talisman

### Static Analysis (SAST)
##### Semgrep Community Edition / Opengrep [SAST][LOCAL][CI/CD]
Opengrep is a community fork created after Semgrep's 2024 licensing changes.
- https://github.com/semgrep/semgrep
- https://github.com/opengrep/opengrep

##### CodeQL [SAST][CI/CD]
Free for open source; requires GitHub Advanced Security for private code.
- https://codeql.github.com/

##### SonarQube Community Build [SAST][CodeQuality][CI/CD]
- https://www.sonarsource.com/open-source-editions/sonarqube-community-edition/

##### Language-specific analyzers [SAST][LOCAL]
- Python: [Bandit](https://github.com/PyCQA/bandit)
- Go: [gosec](https://github.com/securego/gosec), [govulncheck](https://go.dev/doc/security/vuln/)
- Ruby on Rails: [Brakeman](https://brakemanscanner.org/)
- Java: [SpotBugs](https://spotbugs.github.io/) + [Find Security Bugs](https://find-sec-bugs.github.io/)
- JavaScript/TypeScript: [eslint-plugin-security](https://github.com/eslint-community/eslint-plugin-security)

### Dependencies (SCA)
##### OSV-Scanner [SCA][LOCAL][CI/CD]
- https://google.github.io/osv-scanner/

##### OWASP Dependency-Check [SCA][LOCAL][CI/CD]
- https://owasp.org/www-project-dependency-check/

##### OWASP Dependency-Track (continuous SBOM analysis platform) [SCA][SBOM]
- https://dependencytrack.org/

##### Dependabot / Renovate (automated dependency updates) [SCA][CI/CD]
- https://docs.github.com/en/code-security/dependabot
- https://docs.renovatebot.com/

##### Snyk CLI [SCA][SAST][LOCAL][PAID]
- https://docs.snyk.io/snyk-cli

### Containers, IaC & Cloud Native
##### Trivy [CONTAINER][SCA][IaC][SECRETS][SBOM][LOCAL][CI/CD]
Replaces Aqua's retired MicroScanner; tfsec has also been folded into Trivy.
- https://trivy.dev/

##### Grype + Syft (vulnerability scanning + SBOM generation) [CONTAINER][SBOM][LOCAL]
- https://github.com/anchore/grype
- https://github.com/anchore/syft

##### Checkov [IaC][LOCAL][CI/CD]
- https://www.checkov.io/

##### KICS [IaC][LOCAL][CI/CD]
- https://kics.io/

##### Hadolint (Dockerfile linter) [CONTAINER][LOCAL]
- https://github.com/hadolint/hadolint

##### Kubernetes: kube-bench, Kubescape, Kyverno, Falco
- [kube-bench (CIS benchmark)](https://github.com/aquasecurity/kube-bench)
- [Kubescape](https://kubescape.io/)
- [Kyverno (policy as code)](https://kyverno.io/)
- [Falco (runtime threat detection)](https://falco.org/)

### Dynamic Testing (DAST) & API Testing
##### ZAP [DAST][LOCAL][GUI][CI/CD]
Formerly OWASP ZAP; now maintained under the ZAP project.
- https://www.zaproxy.org/
- https://www.zaproxy.org/docs/automate/

##### Nuclei (template-based scanner) [DAST][CI/CD]
- https://github.com/projectdiscovery/nuclei

##### Burp Suite Community Edition [DAST][GUI]
- https://portswigger.net/burp/communitydownload

##### Schemathesis (property-based API testing from OpenAPI/GraphQL) [DAST][CI/CD]
- https://schemathesis.io/

### Mobile (MAST)
##### MobSF — Mobile Security Framework [SAST][DAST][LOCAL]
- https://github.com/MobSF/Mobile-Security-Framework-MobSF

### Runtime Protection
##### OWASP CRS (Core Rule Set) for ModSecurity / Coraza WAF
- https://coreruleset.org/
- https://coraza.io/

### Findings Management
##### OWASP DefectDojo (aggregate and de-duplicate results from many scanners)
- https://github.com/DefectDojo/django-DefectDojo

---

## Software Supply Chain Security

##### OpenSSF Scorecard (automated security health checks for open source projects)
- https://scorecard.dev/

##### Sigstore / Cosign (keyless signing & verification of artifacts)
- https://www.sigstore.dev/

##### in-toto (supply chain attestations)
- https://in-toto.io/

##### SBOM standards: CycloneDX & SPDX
- https://cyclonedx.org/
- https://spdx.dev/

##### OpenVEX (communicate whether a vulnerability actually affects you)
- https://github.com/openvex/spec

##### GitHub artifact attestations (SLSA build provenance)
- https://docs.github.com/en/actions/security-for-github-actions/using-artifact-attestations

##### OpenSSF Package Analysis / malicious-packages (malware in open source registries)
- https://github.com/ossf/malicious-packages

---

## AI / LLM Application Security

##### OWASP Top 10 for LLM Applications & Generative AI Security Project
- https://genai.owasp.org/

##### MITRE ATLAS (adversarial threat landscape for AI systems)
- https://atlas.mitre.org/

##### NIST AI Risk Management Framework
- https://www.nist.gov/itl/ai-risk-management-framework

##### OpenSSF guidance for AI code assistants
Treat AI-generated code like any untrusted contribution: review it, scan it, and watch for
hallucinated ("slopsquatted") package names.
- https://best.openssf.org/

##### Open source LLM red-teaming / testing tools
- [garak (LLM vulnerability scanner)](https://github.com/NVIDIA/garak)
- [promptfoo (LLM evals & red teaming)](https://github.com/promptfoo/promptfoo)
- [PyRIT (Microsoft)](https://github.com/Azure/PyRIT)

---

## Vulnerability Databases & Prioritization

##### OSV.dev (open source vulnerability database, aggregates ecosystem advisories)
- https://osv.dev/

##### GitHub Advisory Database
- https://github.com/advisories

##### CVE Program
- https://www.cve.org/

##### NIST National Vulnerability Database
- https://nvd.nist.gov/vuln/search

##### CISA Known Exploited Vulnerabilities (KEV) catalog — fix these first
- https://www.cisa.gov/known-exploited-vulnerabilities-catalog

##### FIRST EPSS (Exploit Prediction Scoring System)
- https://www.first.org/epss/

##### CVSS v4.0
- https://www.first.org/cvss/

##### Snyk Vulnerability Database
- https://security.snyk.io/

##### Vendor / platform security advisories
- See [security-advisories.md](security-advisories.md)

---

## Security Education

##### PortSwigger Web Security Academy (free, hands-on labs)
- https://portswigger.net/web-security

##### OpenSSF: Developing Secure Software (LFD121, free)
- https://training.linuxfoundation.org/training/developing-secure-software-lfd121/

##### OWASP Cheat Sheet Series
- https://cheatsheetseries.owasp.org/

##### OWASP Web Security Testing Guide (WSTG)
- https://owasp.org/www-project-web-security-testing-guide/

##### SAFECode training
- https://safecode.org/training/

##### Red Hat Developer — Secure coding
- https://developers.redhat.com/topics/secure-coding

##### Secure Code Warrior / Codebashing / Security Journey [PAID]
- https://www.securecodewarrior.com/
- https://checkmarx.com/product/codebashing-secure-code-training/
- https://www.securityjourney.com/

---

## Vulnerable Applications (Practice Targets)

##### OWASP Juice Shop — modern JavaScript web application
- https://owasp.org/www-project-juice-shop/
- https://github.com/juice-shop/juice-shop

##### OWASP WebGoat
- https://owasp.org/www-project-webgoat/

##### OWASP crAPI (completely ridiculous API) & VAmPI — API security practice
- https://github.com/OWASP/crAPI
- https://github.com/erev0s/VAmPI

##### OWASP WrongSecrets — secrets management mistakes
- https://owasp.org/www-project-wrongsecrets/

##### Kubernetes Goat & CI/CD Goat
- https://madhuakula.com/kubernetes-goat/
- https://github.com/cider-security-research/cicd-goat

##### DVWA (Damn Vulnerable Web Application)
- https://github.com/digininja/DVWA

##### Google Gruyere
- https://google-gruyere.appspot.com/

##### OWASP Vulnerable Web Applications Directory
- https://owasp.org/www-project-vulnerable-web-applications-directory/

---

## Public Speaking & Influence

##### How to be a more convincing speaker
- https://www.youtube.com/watch?v=02EJ1IdC6tE

##### "Train the Trainer" (Pushing Left, Like a Boss)
- https://www.youtube.com/watch?v=bWjPl-cKzFs

---

## Retired / Superseded Resources

Kept for historical context from the 2019 talk. Don't use these for new work.

| 2019 resource | Status | Use instead |
|---|---|---|
| Aqua MicroScanner | Retired | Trivy |
| SourceClear vulnerability DB | Acquired by Veracode | OSV.dev, GitHub Advisory Database |
| Sqreen (instrumentation agents, checklists) | Acquired by Datadog (2021) | Datadog App & API Protection, OWASP Cheat Sheets |
| Hdiv Security | Acquired by Datadog (2022) | Datadog Code Security |
| WhiteHat Security | Acquired by Synopsys, now Black Duck | ISC2 Workforce Study for statistics |
| Gauntlt, Mittn, BDD-Security, Reapsaw | Unmaintained / archived | ZAP Automation Framework, Nuclei, Schemathesis in CI |
| Therapist git hook | Unmaintained | pre-commit |
| tfsec | Merged into Trivy | Trivy (`trivy config`) |
| owasp.org/index.php/... wiki pages | Wiki retired (2020) | owasp.org/www-project-... pages |
| modsecurity.org/crs | Moved | coreruleset.org |
| juice-shop.herokuapp.com | Heroku free tier ended | Run locally via Docker |
| scotch.io git hooks tutorial | Site offline | pre-commit.com |
| CentOS Linux advisories | CentOS Linux EOL (2024) | CentOS Stream, Rocky Linux, AlmaLinux |
| NVD legacy JSON data feeds | Retired | NVD API 2.0 |
