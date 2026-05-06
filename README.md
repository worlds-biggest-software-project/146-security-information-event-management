# Security Information & Event Management (SIEM)

> Part of the [worlds-biggest-software-project](https://github.com/worlds-biggest-software-project) initiative.
>
> An AI-native, open-source SIEM that delivers log collection, correlation, threat detection, and incident management without ingest-based pricing lock-in.

This project is a candidate for an open-source Security Information & Event Management platform aimed at security operations teams, CISOs, and IT leaders who need centralised log collection, correlation rules, threat detection, and incident management. It targets the core pain of unpredictable per-GB ingest pricing and the operational overhead of running existing open-source SIEMs at scale.

---

## Why SIEM?

- Ingest-based pricing on tools such as Splunk (~$150/GB/year) creates budget unpredictability as cloud, SaaS, and IoT log volumes routinely double year-over-year.
- Microsoft Sentinel ties buyers deeply into the Azure ecosystem and has less mature multi-cloud coverage; IBM QRadar's UI feels legacy and its 2024 acquisition by Palo Alto Networks creates uncertainty for installed customers.
- Existing open-source options (Wazuh, Elastic Security, Graylog) are licensed under SSPL or Elastic License, requiring careful legal review for commercial service offerings and demanding significant engineering effort to operate at enterprise scale.
- No incumbent surveyed offers a true natural-language query interface, AI-driven rule generation from plain-language threat descriptions, or intelligent log compression to address the root cause of ingest cost escalation.
- Convergence of SIEM, SOAR, UEBA, and XDR is now a baseline expectation, but standalone tools still force buyers to assemble these capabilities from multiple vendors.

---

## Key Features

### Detection & Correlation

- Real-time rule-based detection with alert generation and escalation workflows
- Event correlation and aggregation to reduce false positives and reveal multi-step attacks
- MITRE ATT&CK-aligned detection rule library covering standard attack techniques
- Threat intelligence integration for IOC enrichment

### Search, Storage & Ingestion

- High-performance log indexing and full-text search with sub-second latency on terabyte-scale datasets
- Multi-cloud ingestion for AWS CloudTrail, Azure Activity Log, and GCP Audit Logs
- Standard log transport support: SYSLOG (RFC 5424), CEF, and LEEF
- Cost-predictable pricing model designed to avoid per-GB ingest economics

### Investigation & Response

- Automated incident timeline assembly with enriched context
- Integrated SOAR with playbook automation for common incident types
- Risk-based alert prioritisation using UEBA scoring
- User and Entity Behavior Analytics with behavioural baselining

### Compliance & Reporting

- PCI DSS v4.0 Requirement 10 log collection, integrity, and review controls
- HIPAA, GDPR, and ISO/IEC 27001:2022 (Annex A 8.15, 8.16) reporting templates
- Alignment with NIST Cybersecurity Framework 2.0 and NIST SP 800-92 log management guidance

### Platform & Integrations

- RESTful API for data ingestion, search, and external tool integration
- Webhook integration for third-party notification and ticketing
- Customisable dashboards with drill-down capabilities
- Detection rule marketplace for community and commercial content

---

## AI-Native Advantage

LLM-based natural-language query interfaces let analysts explore logs without learning SPL or KQL, lowering the skill barrier for investigation. AI agents can autonomously triage alerts, correlate related events across sources, and draft incident tickets with enriched context to reduce mean-time-to-respond. Continuous ML-based behavioural baselines surface zero-day lateral movement and insider-threat patterns that static correlation rules miss, while generative AI auto-drafts MITRE ATT&CK-aligned rules from plain-language descriptions. AI-powered log compression and intelligent tiering distinguish high-signal events from low-value telemetry, directly addressing the ingest-cost problem.

---

## Tech Stack & Deployment

The platform is intended to support self-hosted, cloud, and hybrid deployment, mirroring the flexibility offered by IBM QRadar and the open-source posture of Wazuh and Elastic Security. Standards alignment includes SYSLOG (RFC 5424), CEF, LEEF, MITRE ATT&CK, NIST CSF 2.0, NIST SP 800-92, ISO/IEC 27001:2022, and PCI DSS v4.0. Integration is API-first, with REST endpoints for ingestion and search and webhook outputs for downstream tooling.

---

## Market Context

The SIEM market was valued at approximately USD 12.06 billion in 2026 and is forecast to reach USD 20.78 billion by 2031 at a CAGR of approximately 11.5%; including managed SIEM services, the 2033 figure is projected at USD 33.69 billion (research.md). Incumbent pricing ranges from ~$150/GB/year (Splunk) through ~$2.46/GB/day (Microsoft Sentinel analytics tier) to flat-rate per-user (Google Chronicle) and free self-hosted (Wazuh). Primary buyers are SOC managers, CISOs pursuing PCI DSS and ISO 27001 evidence, mid-market IT directors replacing legacy SIEM, and government agencies with FedRAMP or CMMC obligations; large enterprises hold roughly 65% of market share and BFSI accounts for 27% of demand.

---

## Project Status

> This project is in the **research and specification phase**.  
> Contributions, feedback, and domain expertise are welcome.

---

## Contributing

We welcome contributions from developers, domain experts, and potential users.
See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

**Important:** All contributions must be your own original work or clearly attributed
open-source material with a compatible licence. Copyright infringement and licence
violations will not be tolerated and will result in immediate removal of the offending
contribution. If you are unsure whether a piece of code, text, or other material is
safe to contribute, open an issue and ask before submitting.

---

## Licence

Licence to be determined. See [discussion](#) for context.
