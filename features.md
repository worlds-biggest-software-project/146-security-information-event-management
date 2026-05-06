# Security Information & Event Management (SIEM) — Feature & Functionality Survey

> Candidate #146 · Researched: 2026-05-03

## Solutions Analysed

| Tool | Type | Licence / Model | URL |
|------|------|-----------------|-----|
| Splunk Enterprise Security | Commercial SaaS | Proprietary (per-GB ingestion pricing) | https://www.splunk.com/en_us/products/enterprise-security.html |
| Microsoft Sentinel | Commercial SaaS | Proprietary (pay-per-GB, cloud-native) | https://azure.microsoft.com/en-us/products/microsoft-sentinel |
| IBM Security QRadar | Commercial SaaS/On-prem | Proprietary (EPS-based licensing) | https://www.ibm.com/security/qradar |
| Elastic Security | Open-core / Commercial | Elastic Licence + SSPL; free tier available | https://www.elastic.co/security |
| Wazuh | Open source | SSPL (Server Side Public Licence) | https://github.com/wazuh/wazuh |
| Google Chronicle | Commercial SaaS | Proprietary (flat-rate per-user) | https://chronicle.security/ |
| Exabeam | Commercial SaaS | Proprietary (user-based pricing) | https://www.exabeam.com/ |
| Graylog | Open-core / Commercial | Server Side Public Licence; enterprise tier | https://graylog.org/ |
| Rapid7 InsightIDR | Commercial SaaS | Proprietary (per-asset subscription) | https://www.rapid7.com/products/insightidr/ |

## Feature Analysis by Solution

### Splunk Enterprise Security

**Core features**
- High-throughput log indexing and full-text search across petabyte-scale datasets
- Correlation search engine with pattern matching and temporal analysis
- Adaptive response actions triggered by detection rules
- Extensive app ecosystem (1000+ security-focused apps and integrations)
- Threat intelligence integration and enrichment
- Compliance reporting (PCI DSS, HIPAA, NIST frameworks)
- Real-time alerting and escalation workflows
- Custom search language (SPL) for advanced analytics

**Differentiating features**
- Market-leading app ecosystem with pre-built use cases
- Mature correlation search library covering standard attack patterns
- Strong community and third-party integrations
- Established compliance reporting templates

**UX patterns**
- Search-driven investigation interface with query builder
- Dashboards with drill-down capabilities
- Alert definition UI with throttling and action configuration
- Progressive disclosure through apps and add-ons

**Integration points**
- REST API for data ingestion and search queries
- Webhook integration for third-party notifications
- Splunk App Store for plugin ecosystem
- Syslog, CEF, LEEF ingestion support
- Native connectors for major cloud providers and security tools

**Known gaps**
- Per-GB ingest pricing creates unpredictable costs at cloud/IoT scale
- Requires significant expertise to optimize search performance
- UI complexity steep for new analysts
- No native SOAR automation (requires additional purchase)

**Licence / IP notes**
- Proprietary SaaS; extensive proprietary analytics and correlation algorithms; no open-source components; no known patent encumbrances

---

### Microsoft Sentinel

**Core features**
- Cloud-native SIEM built on Azure infrastructure
- User and Entity Behavior Analytics (UEBA) using machine learning
- SOAR automation with playbook workflows
- Copilot AI integration for alert summarization and incident investigation
- Integration with Microsoft 365 and Azure ecosystem
- Threat intelligence integration and management
- Pay-per-GB data analytics model
- Compliance reporting and audit logs

**Differentiating features**
- Deep integration with Microsoft security products (Defender, Office 365)
- Copilot AI assistant for analyst guidance
- SOAR automation built-in vs. standalone purchase
- Unified incident response across Microsoft tools

**UX patterns**
- Azure portal-native interface
- Playbook editor with drag-and-drop workflow
- Incident timeline with AI-guided investigation
- Copilot prompt interface for natural-language queries

**Integration points**
- Azure service integrations (AppGateway, Key Vault, VMs)
- Microsoft Defender integration
- REST API for custom connectors
- Logic Apps integration for workflow automation
- Third-party connector library

**Known gaps**
- Complex pricing model with multiple tiers
- Multi-cloud coverage less mature than single-cloud
- Heavy vendor lock-in with Microsoft ecosystem
- Learning curve for organizations outside Azure

**Licence / IP notes**
- Proprietary SaaS; Copilot AI features may use proprietary techniques; no licensing conflicts for standard deployments

---

### IBM Security QRadar

**Core features**
- High-performance event correlation and anomaly detection
- Integrated SOAR platform (acquired post-2024)
- User behavior analytics for insider threat detection
- Flexible deployment (on-prem, SaaS, hybrid)
- EPS-based licensing supporting massive event throughput
- Threat intelligence feed integration
- Compliance reporting (PCI DSS, HIPAA, GDPR)
- Advanced search and query capabilities

**Differentiating features**
- Mature, field-proven correlation engine with decades of development
- Strong installed base in large enterprises
- Integrated SOAR eliminating separate tool purchase
- Flexible licensing (EPS-based scales with load)

**UX patterns**
- Console-based interface with network overview dashboards
- Alert investigation workflow with timeline visualization
- Custom correlation rule editor with visual workflow
- Integration management UI

**Integration points**
- Syslog, CEF, LEEF protocol support
- REST API for data submission and query
- Custom protocol adapters for proprietary systems
- Webhook integration for third-party notifications
- App ecosystem for integrations

**Known gaps**
- UI feels legacy compared to cloud-native competitors
- Acquisition by Palo Alto Networks (2024) creates uncertainty
- Expensive on-premises deployment and maintenance
- Slower innovation cycle vs. cloud-native vendors

**Licence / IP notes**
- Proprietary; EPS-based licensing complex; no known patent encumbrances but mature correlation algorithms likely protected as trade secrets

---

### Elastic Security

**Core features**
- Built on Elastic Stack (Elasticsearch, Kibana, Beats) with full-text search
- MITRE ATT&CK-aligned detection rules
- Integrated endpoint detection and response (EDR)
- Flexible data ingestion via Beats and Logstash
- Open-source core with commercial enhancements
- User behavior analytics and anomaly detection
- Custom query language (KQL) for investigation
- Threat intelligence integration

**Differentiating features**
- Open-core model allowing self-hosting with zero licence cost
- Strong search and analytics performance at scale
- Integrated EDR capabilities
- Flexible ingest pipeline for complex data transformation

**UX patterns**
- Kibana dashboard interface for exploration
- Rule builder with visual editor for detection rules
- Incident response timeline with enrichment
- Unified view of alerts, events, and assets

**Integration points**
- Elastic API for custom integrations
- Logstash pipeline for event processing
- Beats lightweight agents for log collection
- REST API for external tool integration
- Extensive integration marketplace

**Known gaps**
- Operational complexity at enterprise scale (requires DevOps expertise)
- Smaller commercial customer base than Splunk
- Less mature SOAR automation compared to purpose-built tools
- Community-driven rule quality varies

**Licence / IP notes**
- Open-core: Elastic License and SSPL; free tier available; community contributions may be subject to SSPL requiring source disclosure in certain scenarios—review compatibility with deployment model

---

### Wazuh

**Core features**
- Open-source SIEM and XDR with no licensing costs
- Built-in agent for endpoint monitoring and log collection
- MITRE ATT&CK framework mapping in detection rules
- Vulnerability assessment and patch management integration
- Real-time alert generation and incident response workflows
- File integrity monitoring and configuration management
- Multi-platform support (Linux, Windows, macOS, cloud)
- Community-driven rule library and use cases

**Differentiating features**
- Zero licensing cost enabling broad deployments
- Unified SIEM and XDR capabilities in single platform
- Built-in agent simplifying data collection across endpoints
- Active open-source community and development

**UX patterns**
- Web-based dashboard for alert monitoring
- Rule editor for custom detection logic
- Agent management interface for fleet operations
- Alert investigation with contextual logs

**Integration points**
- REST API for external tool integration
- Agent architecture for distributed log collection
- Webhook integration for third-party alerting
- Integration with cloud providers (AWS, Azure, GCP)
- Custom decoder and alert rules

**Known gaps**
- Requires significant engineering to operate at enterprise scale
- SOAR automation capabilities limited
- Smaller ecosystem of commercial integrations
- Community support vs. vendor-backed support

**Licence / IP notes**
- Open source (SSPL); server-side deployment requires source disclosure if services offered to third parties; self-hosted deployments for internal use have no restrictions; review licensing terms if building commercial SaaS offering

---

### Google Chronicle

**Core features**
- Cloud-native SIEM with flat-rate per-user pricing model
- Raw log storage at petabyte scale with sub-second search
- Unified data model for normalization across sources
- MITRE ATT&CK rule mapping
- Automated investigation timeline assembly
- Threat intelligence feeds and enrichment
- UDM (Unified Data Model) for normalized event correlation
- Investigation collaboration features

**Differentiating features**
- Flat-rate pricing eliminating ingest cost unpredictability
- Sub-second search on petabyte-scale datasets
- Automated timeline generation for investigations
- Unified data model reducing normalization burden

**UX patterns**
- Investigation-centric interface with timeline focus
- UDM browser for exploring normalized data
- Rule creation with visual editor
- Collaborative investigation features
- Automated alert context enrichment

**Integration points**
- REST API for custom ingestion
- Connector library for major security tools
- Webhook integration for notifications
- Cloud-native integrations (GCP, AWS, Azure)
- Community-driven detection rules

**Known gaps**
- Smaller rule ecosystem compared with Splunk
- Less mature multi-cloud support
- Newer platform with smaller customer base
- Limited on-premises deployment options

**Licence / IP notes**
- Proprietary SaaS; no licensing concerns; timeline automation and UDM normalization represent proprietary techniques

---

### Exabeam

**Core features**
- Next-generation SIEM focused on user and entity behavior analytics (UEBA)
- Automated timeline assembly for threat investigation
- Behavior baseline detection for anomalous activity
- Machine learning for insider threat and lateral movement
- Real-time scoring of user and asset risk
- Simplified alert triage with AI-driven context
- Cloud-native SaaS deployment
- Integration with security incident workflow

**Differentiating features**
- Deep UEBA and behavioral analytics focus
- Automated incident timeline reducing manual investigation
- Behavior baselines improving zero-day lateral movement detection
- Simplified analyst workflow vs. raw log hunting

**UX patterns**
- Dashboard-centric view of user/entity risk
- Automated timeline with annotated events
- Risk scoring interface highlighting high-priority users
- Simplified alert triage workflow

**Integration points**
- REST API for external tool integration
- Webhook integration for third-party alerting
- Integration with log sources and identity systems
- SOAR integration capabilities
- API for risk scoring queries

**Known gaps**
- Not designed as primary log archive (better as supplemental)
- Less suitable for compliance-driven log retention
- Limited customization of detection models
- Smaller ecosystem vs. Splunk and Elastic

**Licence / IP notes**
- Proprietary SaaS; behavioral analytics algorithms are proprietary; no known patent encumbrances but machine learning models represent protected IP

---

### Graylog

**Core features**
- Log management and SIEM with open-source core
- Built-in SOAR for workflow automation
- UEBA and anomaly detection using machine learning
- AI-assisted investigation with context enrichment
- Extractors for log field parsing and normalization
- Cluster deployment for high availability
- Threat intelligence integration
- Compliance reporting (GDPR, HIPAA, PCI DSS)

**Differentiating features**
- Open-source core reducing licensing costs
- Integrated SOAR without separate purchase
- Cost-effective for mid-market deployments
- Flexible deployment options (self-hosted or cloud)

**UX patterns**
- Web-based dashboard with customizable widgets
- Pipeline editor for log processing
- Rule creation with visual builder
- Alert workflow and ticketing integration
- Investigation with contextual enrichment

**Integration points**
- REST API for data ingestion and queries
- Syslog and CEF protocol support
- Extractor pipeline for field extraction
- Webhook integration
- Community integrations and plugins

**Known gaps**
- Smaller enterprise customer base
- Less mature ecosystem than Splunk
- Operational complexity increases with scale
- SOAR and anomaly detection not as sophisticated as purpose-built tools

**Licence / IP notes**
- Open-core: Server Side Public Licence (SSPL); enterprise edition proprietary; SSPL requires source disclosure for service offerings—review compatibility with intended deployment model

---

### Rapid7 InsightIDR

**Core features**
- Detection-focused cloud-native SIEM
- Built-in managed detection and response (MDR) integration
- Real-time investigation with automated correlation
- Risk-based alert prioritization
- Endpoint detection and response (EDR) capabilities
- User and asset intelligence with risk scoring
- Threat intelligence integration
- Low time-to-value deployment

**Differentiating features**
- Rapid deployment with minimal tuning
- Built-in MDR integration reducing separate tool purchase
- Risk-based alert prioritization vs. volume-based
- Simplified analyst experience vs. complex queries

**UX patterns**
- Dashboard-centric alert triage interface
- Automated investigation with context enrichment
- Risk scoring highlighted prominently
- Built-in MDR action recommendations
- Quick-start templates for use cases

**Integration points**
- REST API for external tool integration
- Webhook integration for third-party alerts
- Endpoint agent for log collection
- Cloud provider integrations
- Detection rule API

**Known gaps**
- Limited deep customization of detection logic
- Less suitable for organizations with complex compliance logging
- Smaller ecosystem of third-party integrations
- Per-asset pricing may be expensive at large scale

**Licence / IP notes**
- Proprietary SaaS; no licensing concerns; built-in MDR integration represents proprietary service model

---

## Cross-Cutting Feature Themes

### Table-Stakes Features

- **Log indexing and full-text search** — All SIEM solutions offer high-performance search across large datasets, though performance and cost models vary
- **Real-time alerting** — All support rule-based detection with immediate alert generation upon pattern match
- **Correlation and event aggregation** — All solutions combine related events to reduce false positives and reveal multi-step attacks
- **Threat intelligence integration** — All support ingestion of threat feeds for enrichment and detection
- **Dashboard and visualization** — All provide customizable dashboards for security monitoring
- **API and integration** — All expose REST APIs for custom integrations and data ingestion
- **Compliance reporting** — All support PCI DSS, HIPAA, GDPR, and other regulatory frameworks
- **MITRE ATT&CK alignment** — Modern solutions ship with ATT&CK-mapped detection rules

### Differentiating Features

- **Pricing models** — Splunk uses per-GB ingest (expensive at scale), Google Chronicle uses flat-rate per-user (cost-predictable), Wazuh is open-source (zero cost), others use EPS or per-asset models
- **UEBA and behavior analytics** — Exabeam and Elastic built UEBA in; others treat as secondary
- **Integrated SOAR** — Microsoft Sentinel, IBM QRadar, and Graylog include workflow automation; Splunk requires separate purchase
- **Automated investigation timelines** — Google Chronicle and Exabeam stand out for automated timeline generation
- **Copilot/AI-assisted investigation** — Microsoft Sentinel unique with Copilot integration
- **MDR integration** — Rapid7 InsightIDR built-in; others require separate services
- **Open-source options** — Wazuh (SSPL), Elastic (Elastic License + SSPL), Graylog (SSPL) allow self-hosting

### Underserved Areas / Opportunities

- **Natural-language query interfaces** — None of the solutions highlighted LLM-based query builders allowing analysts to ask questions in plain English vs. learning SPL/KQL
- **Automatic rule generation** — Despite MITRE ATT&CK coverage, no solution mentioned AI-driven generation of rules from plain-language descriptions of attacker behavior
- **Intelligent log compression and tiering** — No solution highlighted AI-powered distinction between high-signal and low-value telemetry for cost reduction
- **Zero-day detection via continuous baselines** — While UEBA exists (Exabeam), no solution emphasized continuous behavioral re-baselining as primary zero-day mechanism
- **Cross-organization threat intelligence sharing** — All solutions ingest threat feeds, but none highlighted private, federated intelligence sharing between peer organizations
- **Automated incident response orchestration** — While SOAR exists, no solution emphasized autonomous incident escalation and remediation without analyst intervention
- **Forensic-grade evidence preservation** — No solution highlighted cryptographic integrity verification or chain-of-custody documentation for legal proceedings
- **Cost optimization recommendations** — No solution mentioned AI-driven suggestions for tuning ingest policies or rule efficiency based on signal value

### AI-Augmentation Candidates

- **Natural-language detection rule authoring** — Convert analyst intent ("flag repeated failed logins followed by privilege escalation") into SPL/KQL rules automatically
- **Autonomous alert triage and correlation** — AI agents autonomously merge related alerts, draft incident summaries, and recommend escalation without analyst intervention
- **Continuous behavioral baselining with anomaly detection** — Real-time baselines on user activity, asset behavior, and network traffic to surface zero-day patterns (without static rule maintenance)
- **Generative rule templates from attack descriptions** — AI generates MITRE ATT&CK-aligned detection rules from natural-language descriptions of attacker behavior
- **Intelligent log sampling and compression** — AI distinguishes high-signal events from low-value telemetry, enabling cost-optimized ingest policies
- **Automated investigation narrative generation** — AI drafts incident narratives with context, IOCs, and remediation recommendations for analyst review
- **Threat modeling and scenario generation** — AI generates realistic attack scenarios based on detected techniques, highlighting coverage gaps in detection rules

---

## Legal & IP Summary

All solutions analysed are proprietary or open-core with no copyright or licensing conflicts identified. Splunk, Microsoft, IBM, Google, Exabeam, and Rapid7 are closed proprietary solutions with no open-source components; no licensing concerns. Elastic, Wazuh, and Graylog are open-source or open-core with SSPL/Elastic License; SSPL requires source disclosure if deployment constitutes a service offering to third parties—review licensing terms carefully if building a commercial SaaS or MSP offering. No solutions disclosed active software patents, but correlation algorithms, UEBA models, and timeline automation likely represent protected trade secrets. No materials were omitted due to uncertainty. Recommend legal review of SSPL terms if adopting Wazuh, Elastic, or Graylog for commercial service offerings.

---

## Recommended Feature Scope

Based on the feature survey above, a competitive SIEM should prioritise the following scope:

**Must-have (MVP)**
- High-performance log indexing and full-text search with sub-second latency on 1TB+ datasets
- Real-time rule-based detection with alert generation and escalation workflows
- Event correlation and aggregation reducing false positives
- Threat intelligence integration for IOC enrichment
- MITRE ATT&CK-aligned detection rules (pre-built library of 50+ use cases)
- RESTful API for data ingestion and external tool integration
- Dashboard and visualization with drill-down capabilities
- PCI DSS and HIPAA compliance reporting

**Should-have (v1.1)**
- User and Entity Behavior Analytics (UEBA) with behavioral baselining
- Automated incident timeline assembly with enriched context
- Integrated SOAR with playbook automation for common incident types
- Natural-language query interface allowing analysts to explore logs without learning SPL/KQL
- Multi-cloud ingestion (AWS CloudTrail, Azure Activity Log, GCP Audit Logs)
- Cost-predictable pricing model (flat-rate or usage-based, not per-GB ingest)
- Risk-based alert prioritization using UEBA scoring
- Community-driven or commercial detection rule marketplace

**Nice-to-have (backlog)**
- AI-assisted investigation with context enrichment and narrative generation
- Autonomous rule generation from plain-language threat descriptions
- Intelligent log sampling and compression to optimize ingest costs
- Federated threat intelligence sharing with peer organizations
- Copilot-style AI assistant for investigation guidance
- Forensic-grade evidence preservation with cryptographic integrity
- Autonomous incident response and remediation without analyst intervention
- Custom ML model training on organization-specific attack patterns
