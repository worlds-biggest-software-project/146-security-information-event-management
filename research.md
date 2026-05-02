# Security Information & Event Management (SIEM)

> Candidate #146 · Researched: 2026-05-02

## Existing Products and Software Packages

| Tool | Description | Type | Pricing | Strengths / Weaknesses |
|------|-------------|------|---------|------------------------|
| Splunk Enterprise Security | High-throughput log indexing, search, dashboards, and correlation rules with an extensive app ecosystem | Commercial | ~$150/GB ingested per year (varies) | Strength: market-leading ecosystem and data volume; Weakness: expensive ingest model, cost escalates sharply with cloud/IoT sources |
| Microsoft Sentinel | Cloud-native SIEM on Azure with UEBA, SOAR automation, and Copilot AI integration | Commercial SaaS | Pay-per-GB (~$2.46/GB/day analytics tier) | Strength: deep Microsoft ecosystem integration; Weakness: complex pricing, multi-cloud coverage less mature |
| IBM Security QRadar | On-prem and SaaS SIEM with integrated SOAR; acquired by Palo Alto Networks 2024 | Commercial | EPS-based (events per second) licensing | Strength: mature correlation engine, large enterprise installed base; Weakness: acquisition uncertainty, UI feels legacy |
| Elastic Security | Open-core SIEM/EDR on the Elastic Stack with MITRE ATT&CK mappings and 8.5 user rating on PeerSpot | Open-core / Commercial | Free (basic); from $95/month (managed cloud) | Strength: flexible ingestion, strong search; Weakness: operational complexity at scale |
| Wazuh | Open-source SIEM and XDR with built-in MITRE ATT&CK alignment, active community | Open source | Free (self-hosted); paid support tiers | Strength: zero licence cost, broad integration; Weakness: requires significant engineering to operate |
| Google Chronicle | Cloud-native SIEM storing raw logs at flat-rate pricing with sub-second search at petabyte scale | Commercial SaaS | Flat-rate per-user | Strength: ingestion cost predictability; Weakness: immature rule ecosystem compared with Splunk |
| Exabeam | Next-gen SIEM focused on UEBA and automated timelines for threat investigation | Commercial SaaS | User-based pricing | Strength: analyst productivity, behaviour baselines; Weakness: less suitable as primary log store |
| Graylog | Log management and SIEM with built-in SOAR, UEBA anomaly detection, and AI-assisted investigation | Open-core / Commercial | Free (open source); enterprise pricing undisclosed | Strength: cost-effective for SMEs; Weakness: smaller enterprise reference base |
| Rapid7 InsightIDR | Detection-centric cloud-native SIEM with built-in MDR integration | Commercial SaaS | Per-asset subscription | Strength: low time-to-value; Weakness: limited customisation depth |

## Relevant Industry Standards or Protocols

- **NIST Cybersecurity Framework 2.0 (CSF 2.0)** — SIEM directly addresses the "Detect" function and supports "Respond" and "Recover"; CSF 2.0 added a "Govern" function relevant to SIEM programme governance
- **MITRE ATT&CK Framework** — De-facto standard for structuring SIEM detection use cases; most platforms ship ATT&CK-tagged detection rules and gap analysis dashboards
- **NIST SP 800-92** — Guide to computer security log management; specifies log retention, protection, and analysis requirements
- **ISO/IEC 27001:2022** — Information security management system standard requiring event logging and monitoring controls (Annex A 8.15, 8.16)
- **PCI DSS v4.0** — Requires centralised log collection, integrity, and review; SIEM is the primary control implementation mechanism for Requirement 10
- **SYSLOG (RFC 5424) / CEF / LEEF** — Common log transport and formatting protocols governing how events are ingested from network devices, endpoints, and applications

## Available Research Materials

1. Muhammad et al. (2023). *Integrated SIEM with Intrusion Detection System for Live Analysis Based on Machine Learning*. Procedia Computer Science / ScienceDirect. https://www.sciencedirect.com/science/article/pii/S1877050922024243 — peer-reviewed
2. Tendikov et al. (2024). *Security Information Event Management Data Acquisition and Analysis Methods with Machine Learning Principles*. ScienceDirect. https://www.sciencedirect.com/science/article/pii/S2590123024005097 — peer-reviewed
3. Various authors (2024). *Enhancing Security Information and Event Management by Incorporating Machine Learning for Cyber Attack Detection*. IEEE Xplore. https://ieeexplore.ieee.org/document/10425288/ — peer-reviewed
4. Various authors (2023). *Machine Learning in SIEM: A Survey on Intelligent Event Correlation and Anomaly Detection*. ResearchGate. https://www.researchgate.net/publication/398679746 — not peer-reviewed (preprint/survey)
5. Akbari, I. (2024). *MITRE ATT&CK Framework as a Standard for Developing SIEM Use Cases*. Medium / practitioner publication. https://medium.com/@imanvanpersien/mitre-att-ck-framework-as-a-standard-for-developing-siem-use-cases-d7dc7db4e1ba — not peer-reviewed
6. CISA (2025). *Guidance on Security Operations Logging Priorities*. US Government advisory. https://www.cisa.gov — practitioner guidance (non-peer-reviewed)
7. California Department of Technology (2025). *SIMM 5335-B: Continuous Security Monitoring and Event Management*. Aligned with NIST CSF 2.0 and MITRE ATT&CK. https://www.cdt.ca.gov/wp-content/uploads/2025/08/SIMM-5335-B-Continuous-Monitoring-Final.pdf — government standard

## Market Research

**Market Size:** The SIEM market was valued at approximately USD 12.06 billion in 2026, forecast to reach USD 20.78 billion by 2031 at a CAGR of approximately 11.5%. A broader definition including managed SIEM services puts the 2033 figure at USD 33.69 billion.

**Funding:** Splunk was acquired by Cisco for USD 28 billion in 2024. IBM's QRadar SaaS business was acquired by Palo Alto Networks. Exabeam merged with LogRhythm in 2023. Wazuh raised growth capital to expand its open-source-led commercial model.

**Pricing Landscape:** Ingest-based pricing (Splunk: ~$150/GB/year) creates budget unpredictability as cloud, SaaS, and IoT sources explode; organisations that budgeted 500 GB/day in 2024 frequently exceeded 2 TB/day by 2025. Google Chronicle's flat-rate model and Wazuh's open-source approach represent counter-positioning strategies. Managed SIEM (MDR/SOC-as-a-service) layered on top is the fastest-growing delivery model.

**Key Buyer Personas:** Security operations centre (SOC) managers at enterprises; CISOs seeking compliance evidence for PCI DSS and ISO 27001 audits; IT directors at mid-market companies replacing legacy SIEM; government agencies under FedRAMP or CMMC requirements.

**Notable Trends:** Convergence of SIEM, SOAR, UEBA, and XDR into unified security operations platforms is eroding standalone SIEM distinctions. AI-driven alert triage and automated threat timelines are becoming baseline expectations. Pay-by-ingest licensing is facing buyer resistance, accelerating flat-rate and open-source alternatives. BFSI vertical accounts for 27% of demand; large enterprises hold 65% of market share.

## AI-Native Opportunity

- LLM-based natural-language query interfaces allow security analysts to explore logs without writing SPL or KQL, dramatically lowering the skill barrier for investigation
- AI agents can autonomously triage alerts, correlate related events across sources, and draft incident tickets with enriched context, reducing mean-time-to-respond without expanding headcount
- Continuous ML-based behavioural baselines can surface zero-day lateral movement and insider threat patterns that static correlation rules miss, improving detection without rule maintenance overhead
- Generative AI can auto-draft MITRE ATT&CK-aligned detection rules from plain-language descriptions of attacker behaviour, accelerating use-case coverage for new threat techniques
- AI-powered log compression and intelligent tiering can dramatically cut storage costs by distinguishing high-signal events from low-value telemetry, addressing the core ingest pricing problem
