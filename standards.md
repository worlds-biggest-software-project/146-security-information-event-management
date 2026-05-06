# Standards & API Reference

> Project: Security Information & Event Management (SIEM) · Generated: 2026-05-03

## Industry Standards & Specifications

### ISO Standards

**ISO/IEC 27001:2022 — Information Security Management Systems (Annex A 8.15 and 8.16)**
- URL: https://www.iso.org/standard/27001 ; https://www.isms.online/iso-27001/annex-a-2022/8-15-logging-2022/ ; https://www.isms.online/iso-27001/annex-a-2022/8-16-monitoring-activities-2022/
- Relevance: ISO 27001:2022 Annex A Control 8.15 (Logging) requires organisations to produce, store, protect, and analyse event logs for security events. Control 8.16 (Monitoring Activities) mandates real-time monitoring of networks, systems, and applications for anomalous behaviour. Together, 8.15 and 8.16 are the primary compliance drivers that make SIEM a mandatory control for ISO 27001-certified organisations. Log records must include user ID, event type, date/time, success/failure indicator, originating location, and affected resource.

**ISO/IEC 27035 — Information Security Incident Management**
- URL: https://www.iso.org/standard/78973.html
- Relevance: The international standard for security incident management covering the full lifecycle from planning, detection, and reporting through containment, eradication, and recovery. SIEM is the detection and evidence collection layer that feeds into the ISO 27035 incident response process. Incident triage, escalation, and closure workflows in a SIEM should align with ISO 27035 phases.

**ISO 31000:2018 — Risk Management Guidelines**
- URL: https://www.iso.org/standard/65694.html
- Relevance: Provides risk management principles that underpin risk-based alert prioritisation, threat modelling, and detection rule tuning within a SIEM. Risk appetite and tolerance thresholds — which determine when an anomaly triggers a high-severity alert — should be calibrated against ISO 31000 risk assessment outcomes.

### W3C & IETF Standards

**RFC 5424 — The Syslog Protocol**
- URL: https://datatracker.ietf.org/doc/html/rfc5424
- Relevance: Syslog is the de facto standard for transmitting event messages from network devices, firewalls, operating systems, and applications to a centralised log management system. RFC 5424 defines the message format (facility, severity, timestamp, hostname, application, process ID, structured data) and transport via UDP, TCP, or TLS. All SIEM platforms must ingest RFC 5424 syslog. The structured data element enables machine-parseable key-value pairs within syslog messages — the foundation for security event normalization.

**RFC 5425 — Transport Layer Security (TLS) Transport Mapping for Syslog**
- URL: https://datatracker.ietf.org/doc/html/rfc5425
- Relevance: Defines encrypted syslog transport over TLS, ensuring log integrity and confidentiality in transit. Required by PCI DSS v4.0 and ISO 27001 for log transmission across untrusted networks. SIEM ingestion pipelines must support RFC 5425 TLS syslog alongside plaintext UDP for legacy sources.

**RFC 6749 — OAuth 2.0 Authorization Framework**
- URL: https://datatracker.ietf.org/doc/html/rfc6749
- Relevance: Authentication standard for SIEM integrations with cloud platforms (Azure Monitor, AWS CloudTrail, GCP Audit Logs), security tools (EDR, firewalls, identity providers), and SOAR platforms. SIEM APIs exposing incident data to downstream tools must use OAuth 2.0 for scoped, auditable access.

**RFC 7231 — HTTP/1.1 Semantics and Content**
- URL: https://datatracker.ietf.org/doc/html/rfc7231
- Relevance: Defines HTTP method semantics and status codes for all SIEM REST APIs — log ingestion endpoints, alert query APIs, detection rule management endpoints, and incident APIs. Correct idempotency in log ingestion (events submitted twice must not be double-counted) is essential for audit integrity.

**RFC 7807 — Problem Details for HTTP APIs**
- URL: https://datatracker.ietf.org/doc/html/rfc7807
- Relevance: Standardises structured error responses from REST APIs. SIEM APIs must return machine-parseable errors for ingestion failures (schema validation errors, authentication failures, rate-limit responses) to enable integration partners to implement deterministic retry logic.

### Data Model & API Specifications

**OpenAPI Specification 3.1 (OAS 3.1)**
- URL: https://spec.openapis.org/oas/v3.1.0.html ; https://swagger.io/specification/
- Relevance: The industry standard for documenting REST APIs. Splunk, Elastic, Wazuh, Microsoft Sentinel, and Google Chronicle all publish OpenAPI/Swagger specifications for their SIEM APIs. A SIEM platform should publish a comprehensive OAS 3.1 specification covering log ingestion, alert query, detection rule management, incident lifecycle, and SOAR playbook APIs — enabling integration partner SDK generation and automated contract testing.

**STIX 2.1 — Structured Threat Information Expression**
- URL: https://oasis-open.github.io/cti-documentation/stix/intro ; https://docs.oasis-open.org/cti/stix/v2.1/stix-v2.1.html
- Relevance: OASIS-standardised language and serialisation format for expressing cyber threat intelligence (CTI). STIX defines objects for Indicators of Compromise (IoCs), attack patterns, threat actors, campaigns, and malware. SIEM platforms must import and enrich events against STIX 2.1 threat intelligence feeds. Detection rules and IoC watchlists should be expressible in STIX 2.1 format for interoperability with threat intelligence platforms (TIPs).

**TAXII 2.1 — Trusted Automated Exchange of Intelligence Information**
- URL: https://oasis-open.github.io/cti-documentation/taxii/intro ; https://attack-taxii.mitre.org
- Relevance: OASIS protocol for exchanging STIX 2.1 threat intelligence over HTTPS REST API. TAXII 2.1 defines collection and channel endpoints for discovering and consuming threat feeds. MITRE ATT&CK publishes its full knowledge base as a TAXII 2.1 endpoint at attack-taxii.mitre.org. SIEM platforms must support TAXII 2.1 as both a consumer (ingesting threat intelligence) and optionally a publisher (sharing detection context with peer organisations).

**MITRE ATT&CK — Adversarial Tactics, Techniques, and Common Knowledge**
- URL: https://attack.mitre.org/ ; https://attack.mitre.org/resources/attack-data-and-tools/
- Relevance: De facto industry standard for structuring SIEM detection use cases. ATT&CK provides a matrix of adversary tactics (initial access, lateral movement, exfiltration, etc.) and techniques (T-codes), all available as STIX 2.1 data via TAXII 2.1 API. All modern SIEM platforms ship ATT&CK-tagged detection rules and gap analysis dashboards. Detection rules should reference ATT&CK technique IDs to enable coverage visualisation and gap analysis.

**CEF — Common Event Format**
- URL: https://www.microfocus.com/documentation/arcsight/arcsight-smartconnectors/pdfdoc/common-event-format-v25/common-event-format-v25.pdf (HP/Micro Focus specification)
- Relevance: CEF is a widely-adopted log format designed for interoperability between security products and SIEM systems. Originally developed by HP ArcSight, CEF defines a structured header and extension fields for security events including severity, event name, source/destination IP, user, and action. CEF over Syslog is the primary integration protocol for firewalls, intrusion detection systems, WAFs, and endpoint security tools. All SIEM platforms must parse CEF natively.

**OpenTelemetry (OTel) — OTLP Protocol**
- URL: https://opentelemetry.io/docs/specs/otel/ ; https://opentelemetry.io/docs/specs/otlp/
- Relevance: CNCF-graduated vendor-neutral framework for telemetry data (logs, metrics, traces). OpenTelemetry Protocol (OTLP) is the future-proof standard for application-layer telemetry ingestion into SIEM. SIEM platforms that accept OTLP can receive structured, trace-correlated log events directly from instrumented applications — enriching security events with execution context (which user, which service, what request, what outcome). SIEM integration with OpenTelemetry enables correlating firewall blocks with application-layer traces from the same transaction.

**JSON Schema 2020-12**
- URL: https://json-schema.org/specification
- Relevance: Standard for validating JSON payloads. SIEM detection rules, alert schemas, and SOAR playbook definitions must be validated against JSON Schema to ensure data quality and prevent malformed rules from causing missed detections or false negatives in production.

### Security & Compliance Standards

**NIST Cybersecurity Framework 2.0 (CSF 2.0)**
- URL: https://www.nist.gov/cyberframework ; https://nvlpubs.nist.gov/nistpubs/CSWP/NIST.CSWP.29.pdf
- Relevance: NIST CSF 2.0 (published 2024) defines six functions: Govern, Identify, Protect, Detect, Respond, Recover. SIEM directly implements the "Detect" function and supports "Respond" and "Recover." The new "Govern" function establishes programme governance requirements relevant to SIEM policy, metrics, and executive reporting. The Financial Services Sector-Specific CSF Profile and US government FedRAMP/CMMC requirements reference CSF 2.0 as the baseline framework.

**NIST SP 800-92 Rev. 1 — Cybersecurity Log Management Planning Guide**
- URL: https://csrc.nist.gov/pubs/sp/800/92/r1/ipd ; https://csrc.nist.gov/projects/log-management
- Relevance: The primary US government guidance on log management, currently in revision (Rev. 1 in public comment as of 2026). SP 800-92 defines log collection policies, retention requirements, protection measures, and analysis procedures. Required reading for SIEM implementations at US federal agencies and contractors; widely adopted as a reference standard in commercial and financial sectors. A SIEM platform should enable configuration that satisfies SP 800-92 log retention and integrity requirements.

**PCI DSS v4.0 — Requirement 10: Log and Monitor All Access**
- URL: https://www.pcisecuritystandards.org/document_library/
- Relevance: PCI DSS Requirement 10 mandates centralised log collection, integrity protection (logs must not be alterable by individuals whose access they record), daily review of critical system logs, and 12-month retention with 3-month immediate accessibility. A SIEM is the primary implementation mechanism for Requirement 10 across all cardholder data environments. Logs must capture user ID, event type, date/time, success/failure, origin, and affected resource. Full PANs and sensitive authentication data must never appear in logs.

**GDPR — General Data Protection Regulation (EU 2016/679)**
- URL: https://gdpr.eu/
- Relevance: SIEM platforms that process log data containing personal identifiers (usernames, email addresses, IP addresses, device IDs) of EU individuals are processing personal data under GDPR. SIEM must implement data minimisation (collect only security-relevant fields), retention limits aligned with GDPR principles, and subject access request support for log data. Security event logs must not be used for purposes beyond security monitoring and incident investigation.

**OWASP API Security Top 10 (2023)**
- URL: https://owasp.org/API-Security/editions/2023/en/0x11-t10/
- Relevance: SIEM APIs are high-value targets — access to security event data reveals the full picture of an organisation's attack surface and defensive posture. Key risks: Broken Object Level Authorization (analysts must access only their own team's alerts); Broken Authentication (SIEM APIs with weak auth expose all security telemetry); Unrestricted Access to Sensitive Business Flows (log ingestion endpoints can be abused for data exfiltration via log injection); and Improper Inventory Management (undocumented SIEM API endpoints may bypass audit controls).

### MCP Server Specifications

**Model Context Protocol (MCP) — Agentic Security Operations**
- URL: https://modelcontextprotocol.io/ ; https://panther.com/blog/how-model-context-protocol-helps-security-teams-scale-secops
- Relevance: MCP has become the dominant standard for connecting AI agents to security operations data. Exabeam, Panther, and Command Zero (which opened its autonomous SOC platform with MCP server support in April 2026) have all implemented MCP servers for SIEM-adjacent workflows. MCP enables AI agents to perform natural-language queries spanning multiple log sources, correlate alert contexts, automate investigation steps, and draft incident narratives without manual context switching. A SIEM platform exposing an MCP server allows AI agents (Claude, ChatGPT, custom agents) to interact with security data autonomously — accelerating SOC workflows that previously required 8+ hours of manual investigation to under 45 minutes. OASIS Open has published an MCP security taxonomy (January 2026) covering risks from MCP servers in security-sensitive deployments.

---

## Similar Products — Developer Documentation & APIs

### Splunk Enterprise Security (REST API)

- **Description:** Market-leading SIEM with high-throughput log indexing, SPL search language, 1000+ app ecosystem, and correlation search engine. Acquired by Cisco (2024). REST API provides full programmatic access to search, data ingestion, alert management, and app configuration.
- **API Documentation:** https://docs.splunk.com/Documentation/Splunk/latest/RESTUM/RESTusing
- **Developer Program:** https://dev.splunk.com/enterprise/reference/
- **SDKs/Libraries:** Python SDK, JavaScript SDK, Java SDK, C# SDK — https://dev.splunk.com/
- **Developer Guide:** https://docs.splunk.com/Documentation/Splunk/latest/RESTTUT/RESTsearches
- **Standards:** REST/JSON; OpenAPI specification; SPL (Splunk Processing Language); syslog, CEF, LEEF ingestion
- **Authentication:** Session token (username/password); API token; Splunk-specific authentication

### Microsoft Sentinel (REST API)

- **Description:** Cloud-native SIEM/SOAR on Azure with UEBA, Copilot AI integration, and deep Microsoft ecosystem connectivity. Pay-per-GB analytics model. REST API enables incident management, alert rule configuration, and data connector management.
- **API Documentation:** https://learn.microsoft.com/en-us/rest/api/securityinsights/
- **Data Connectors Reference:** https://learn.microsoft.com/en-us/azure/sentinel/data-connectors-reference
- **Custom Connectors:** https://learn.microsoft.com/en-us/azure/sentinel/connect-rest-api-template
- **SDKs/Libraries:** Azure SDK for Python, .NET, Java, JavaScript — https://azure.github.io/azure-sdk/
- **Standards:** REST/JSON; Azure Resource Manager API; OpenAPI specification published via Azure; Log Analytics Data Collector API for ingestion; CEF/Syslog via AMA connector
- **Authentication:** OAuth 2.0 (Azure Active Directory / Entra ID)

### Elastic Security (REST API / Kibana Detections API)

- **Description:** Open-core SIEM/EDR on the Elastic Stack covering log ingestion, MITRE ATT&CK-aligned detection rules, UEBA, and endpoint protection. Open-source core (Elastic License + SSPL). REST API exposes detection rule management, alert queries, and index management.
- **API Documentation:** https://www.elastic.co/guide/en/security/8.19/security-apis.html
- **Kibana Detections API:** https://www.elastic.co/docs/api/doc/kibana/group/endpoint-security-detections-api
- **Detection Rules GitHub:** https://github.com/elastic/detection-rules
- **SDKs/Libraries:** Elasticsearch Python client, JavaScript client, Java client, Go client — https://www.elastic.co/guide/en/elasticsearch/client/
- **Standards:** REST/JSON; OpenAPI specification; KQL (Kibana Query Language); ECS (Elastic Common Schema) for log normalization; CEF integration
- **Authentication:** API Key; Username/Password; OAuth 2.0 (Elastic Cloud)

### Wazuh Server API

- **Description:** Open-source SIEM and XDR (SSPL licence) with built-in agents for endpoint monitoring, MITRE ATT&CK alignment, file integrity monitoring, vulnerability assessment, and active response. Full REST API for agent management, alert retrieval, and rule administration.
- **API Documentation:** https://documentation.wazuh.com/current/user-manual/api/index.html
- **API Reference:** https://documentation.wazuh.com/current/user-manual/api/reference.html
- **GitHub:** https://github.com/wazuh/wazuh-api
- **Postman Collection:** https://www.postman.com/api-evangelist/wazuh/documentation/
- **Standards:** REST/JSON; JWT authentication; OpenAPI specification; syslog and agent-based ingestion
- **Authentication:** JWT tokens (15-minute lifetime); RBAC for role-based endpoint access

### Google Chronicle (Security Operations) API

- **Description:** Cloud-native SIEM (Google Security Operations) with flat-rate per-user pricing, sub-second petabyte-scale search, Unified Data Model (UDM) for log normalisation, and automated investigation timelines. REST API for log ingestion, search, rule management, and investigation workflows.
- **API Documentation:** https://docs.cloud.google.com/chronicle/docs/reference/rest
- **Ingestion API:** https://docs.cloud.google.com/chronicle/docs/reference/ingestion-api
- **Ingestion Methods:** https://docs.cloud.google.com/chronicle/docs/reference/ingestion-methods
- **Developer Guide:** https://cloud.google.com/chronicle/docs/overview
- **Standards:** REST/JSON; Google API Design Guide; regional endpoints per geography
- **Authentication:** OAuth 2.0 (Google service account credentials); API key

### Exabeam Fusion API

- **Description:** Next-generation SIEM focused on UEBA, automated investigation timelines, and behavioural analytics for insider threat and lateral movement detection. Merged with LogRhythm (2023). REST API for risk scoring queries, alert management, and integration with security tools.
- **API Documentation:** https://docs.exabeam.com/ (contact vendor for developer portal access)
- **Standards:** REST/JSON; webhook callbacks for alert notifications
- **Authentication:** API Key; OAuth 2.0 for enterprise SSO

### Graylog API

- **Description:** Open-core log management and SIEM (SSPL licence) with integrated SOAR, UEBA anomaly detection, and AI-assisted investigation. Cost-effective for mid-market. REST API for log search, stream management, alert configuration, and pipeline processing.
- **API Documentation:** https://go2docs.graylog.org/current/what_is_graylog/what_is_graylog.htm
- **Standards:** REST/JSON; OpenAPI specification published; syslog, CEF, GELF (Graylog Extended Log Format) ingestion; SSPL licence
- **Authentication:** Session token; API token; LDAP/AD integration

### Rapid7 InsightIDR API

- **Description:** Detection-focused cloud-native SIEM with built-in MDR integration, risk-based alert prioritisation, and rapid time-to-value deployment. Per-asset subscription pricing. REST API for log search, alert management, investigation workflows, and threat intelligence.
- **API Documentation:** https://docs.rapid7.com/insight/
- **InsightIDR API:** https://docs.rapid7.com/insightidr/
- **Standards:** REST/JSON; OpenAPI specification available; webhook callbacks for alert notifications
- **Authentication:** API Key (X-Api-Key header)

### Panther Security (MCP-enabled SIEM)

- **Description:** Cloud-native SIEM platform for security monitoring with detection-as-code (Python), MITRE ATT&CK alignment, and MCP server integration enabling AI agents to query security data via natural language. Targets engineering-driven security teams.
- **API Documentation:** https://docs.panther.com/
- **MCP Integration:** https://panther.com/blog/how-model-context-protocol-helps-security-teams-scale-secops
- **Standards:** REST/JSON; Python-based detection rules; OpenAPI specification
- **Authentication:** API Key; OAuth 2.0

---

## Notes

**MITRE ATT&CK TAXII Endpoint:** MITRE publishes the complete ATT&CK knowledge base as a public TAXII 2.1 API at https://attack-taxii.mitre.org/api/v21/ — accessible without authentication. Any SIEM implementing TAXII 2.1 client support can automatically ingest the full ATT&CK technique library for detection rule tagging and coverage gap analysis. This is the most important free, standardised data source for SIEM development.

**ECS — Elastic Common Schema:** Elastic publishes the Elastic Common Schema (ECS) as an open specification for normalising log fields across log sources — https://www.elastic.co/guide/en/ecs/current/index.html. ECS provides a vendor-neutral common data model for security events. While not an official ISO/IETF standard, ECS is increasingly adopted as a de facto normalisation standard and provides a useful reference for designing a SIEM's internal event schema.

**MCP Security Taxonomy:** OASIS Open published a Coalition for Secure AI MCP Security Taxonomy in January 2026, covering attack surfaces, privilege escalation risks, and mitigations for MCP deployments — directly relevant to SIEM platforms exposing MCP servers. This taxonomy should be reviewed before implementing an MCP server with access to sensitive security telemetry.

**SSPL Licensing Advisory:** Wazuh, Elastic (open-source tier), and Graylog use the Server Side Public Licence (SSPL), which requires source disclosure if the software is offered as a service to third parties. Any commercial SIEM product built on these codebases must obtain a commercial licence or fully comply with SSPL disclosure requirements. Independent legal review is recommended before adopting SSPL components in a commercial SaaS SIEM offering.
