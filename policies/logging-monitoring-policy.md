# Logging and Monitoring Policy

| Field | Value |
|---|---|
| **Policy Owner** | [POLICY_OWNER] |
| **Approved By** | [APPROVED_BY] |
| **Effective Date** | [DATE] |
| **Next Review Date** | [REVIEW_DATE] |
| **Version** | [VERSION] |
| **Classification** | Internal |

---

## 1. Purpose

This Logging and Monitoring Policy defines [COMPANY_NAME]'s requirements for collecting, storing, protecting, reviewing, and alerting on security-relevant logs across all systems and infrastructure. Effective logging and monitoring is the foundation of threat detection, incident response, compliance evidence, and forensic investigation. Without logs, you cannot detect, investigate, or prove anything.

This policy ensures that [COMPANY_NAME] maintains sufficient visibility into its environment to detect security events, support incident investigations, and provide auditors with evidence of operating controls.

## 2. Scope

This policy applies to:

- All production systems, including application servers, databases, load balancers, API gateways, and microservices
- All cloud infrastructure and platform services (AWS, GCP, Azure management plane activity)
- All security systems, including firewalls, IDS/IPS, endpoint protection, WAF, and DLP tools
- All identity and access management systems, including the identity provider, SSO, and VPN
- All CI/CD pipelines and deployment systems
- All corporate IT systems, including email, collaboration tools, and administrative consoles
- All endpoints (laptops, mobile devices) managed by [COMPANY_NAME]

## 3. Policy Statements

### 3.1 Events to Log

The following events must be logged for all in-scope systems. If a system cannot log a specific event type, this must be documented as a gap and tracked for remediation.

**Authentication and Access Events:**
- Successful and failed authentication attempts (including username, source IP, timestamp, and MFA status)
- Account lockouts and unlock events
- MFA enrollment, changes, and bypass events
- Password changes and resets
- Session creation and termination
- Privilege escalation (sudo, runas, role assumption)
- Service account and API key usage

**Authorization and Access Control Events:**
- Access grants, modifications, and revocations
- Role assignments and changes
- Access to Restricted or Confidential data (where technically feasible)
- Permission denied events
- Attempts to access resources outside assigned scope

**System and Infrastructure Events:**
- System startup, shutdown, and restart events
- Configuration changes (security groups, firewall rules, IAM policies, DNS records)
- Cloud resource creation, modification, and deletion
- Network connection events for security-relevant systems (firewall logs, VPN connections)
- Certificate issuance, renewal, and expiration events
- Backup execution results (success/failure)

**Application Events:**
- Application errors and exceptions
- Input validation failures
- API request logs (source, endpoint, method, response code, latency)
- Data export or bulk download events
- Administrative actions within applications

**Security Events:**
- Malware detection and remediation actions
- Intrusion detection/prevention alerts
- Vulnerability scan results
- DLP alerts (data exfiltration attempts)
- Web application firewall (WAF) blocks and alerts
- Email security events (phishing detection, spam filtering, quarantine actions)

**Change and Deployment Events:**
- Code deployments to production (who, what, when, from where)
- Infrastructure-as-code changes applied
- Database migration execution
- Rollback events

### 3.2 Log Content Requirements

Each log entry must contain sufficient information for security analysis and forensic investigation. At minimum, log entries must include:

- **Timestamp** -- in UTC, with millisecond precision where supported
- **Event type** -- classification of the event
- **Source** -- the system, application, or service generating the log
- **Actor** -- the user, service account, or process that initiated the event
- **Source IP/location** -- the network address of the actor where applicable
- **Target** -- the resource, system, or data affected
- **Action** -- what was done (read, write, delete, modify, login, etc.)
- **Outcome** -- success, failure, or error
- **Severity/priority** -- the log level or severity classification

**Log content must NOT include:**
- Passwords, tokens, API keys, or other authentication secrets
- Full credit card numbers, Social Security/Social Insurance numbers, or other Restricted PII in plain text
- Encryption keys or cryptographic material
- Session tokens or cookies that could be used for session hijacking

If sensitive data must appear in logs for debugging, it must be masked or tokenized (e.g., last 4 digits of a card number, hashed user identifiers).

### 3.3 Centralized Log Management

- All security-relevant logs must be forwarded to [COMPANY_NAME]'s centralized log management platform (SIEM or log aggregation system).
- Logs must not rely solely on local storage on the systems that generate them. Local logs can be lost if a system is compromised or fails.
- The centralized log platform must:
  - Accept logs from all in-scope systems and environments
  - Provide search and query capabilities for investigation
  - Support alerting based on log content and patterns
  - Enforce access controls on who can read, modify, or delete logs
  - Maintain log integrity (detect tampering)

### 3.4 Log Retention

| Log Type | Active Retention (searchable) | Archive Retention (cold storage) | Total Retention |
|---|---|---|---|
| Security events (auth, access, privilege) | 90 days | 275 days | 1 year |
| Application logs | 90 days | 275 days | 1 year |
| Infrastructure/system logs | 90 days | 275 days | 1 year |
| Audit trail (admin actions, config changes) | 1 year | 2 years | 3 years |
| Incident investigation logs | Duration of investigation + 1 year | 2 years | 3 years minimum |

- Retention periods may be extended to meet regulatory, contractual, or legal hold requirements.
- Archived logs must be encrypted at rest and accessible for retrieval within 48 hours for investigation purposes.
- Log deletion must be automated based on retention schedules. Manual log deletion is prohibited without Security Lead approval.

### 3.5 Log Integrity and Protection

- Logs must be protected against unauthorized modification or deletion:
  - Write-once storage or append-only log streams are preferred for security-critical logs
  - Access to modify or delete logs in the centralized platform must be restricted to the minimum necessary administrators
  - All administrative actions on the log platform itself must be logged (who accessed, queried, or modified log settings)
- Logs in transit from source systems to the centralized platform must be transmitted over encrypted channels (TLS).
- Log storage must be encrypted at rest.
- Log platform availability must be monitored. Gaps in logging must be detected and investigated.

### 3.6 Clock Synchronization

- All systems generating logs must synchronize their clocks to a reliable NTP source (e.g., pool.ntp.org, cloud provider NTP service, internal NTP server).
- Time synchronization must use UTC to avoid ambiguity across time zones.
- NTP synchronization status must be monitored. Systems that drift more than 1 second from the NTP source must generate an alert.
- Consistent timestamps across systems are critical for correlating events during incident investigations.

### 3.7 Monitoring and Alerting

[COMPANY_NAME] shall maintain automated alerting for security-relevant events. Alerts must be directed to the appropriate team with enough context to assess and act.

**Required alert categories (minimum):**

| Alert | Severity | Notification Target |
|---|---|---|
| Multiple failed login attempts (5+ in 5 minutes) from a single source | Medium | Security team |
| Successful login from a new or unusual location/device | Low | User and security team |
| Privileged account login outside business hours | Medium | Security team |
| New administrative user created | High | Security team |
| Changes to IAM policies or security group rules | High | Security team |
| Production database direct access (outside application) | High | Security and engineering |
| Data export exceeding threshold (bulk download) | High | Security team |
| Malware detected on endpoint | High | Security and IT |
| Multiple permission-denied events from a single user | Medium | Security team |
| Log forwarding failure (gap in logging) | High | Security and DevOps |
| TLS certificate approaching expiration (30 days) | Medium | DevOps |
| Backup failure | High | DevOps and security |
| Service account used from unexpected source | High | Security team |

**Alert configuration requirements:**
- Alerts must be routed to the on-call responder via the organization's alerting system (PagerDuty, Opsgenie, or equivalent) for high-severity alerts.
- Alert fatigue must be actively managed: alerts that consistently fire without requiring action must be tuned, suppressed, or reclassified. An alert that is always ignored is worse than no alert.
- Alert response must be documented: who received the alert, when it was acknowledged, what action was taken, and the outcome.
- Alert rules must be reviewed at least quarterly to ensure they remain relevant and properly tuned.

### 3.8 Log Review

- Security logs shall be reviewed on a regular cadence:
  - **Daily:** Automated review via SIEM correlation rules and dashboards. High-severity alerts triaged within SLA.
  - **Weekly:** Manual review of security dashboards and alert trends by the security team.
  - **Monthly:** Review of log coverage (are all systems sending logs?), retention compliance, and alert effectiveness metrics.
  - **Quarterly:** Comprehensive review of logging and monitoring posture, including gap analysis and alert tuning.
- Log review findings must be documented. Issues identified during review must be tracked to resolution.

### 3.9 Incident Investigation Support

- The logging infrastructure must support ad hoc queries for incident investigation, including the ability to:
  - Search across all log sources by time range, user, IP address, system, or event type
  - Correlate events across multiple systems
  - Export logs for forensic analysis
  - Preserve logs related to an incident beyond normal retention periods (litigation hold)
- During an active incident, additional logging or increased log verbosity may be enabled on affected systems as directed by the Incident Commander.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Security Lead** | Define logging and alerting requirements; manage the SIEM platform; review alerts and dashboards; tune alert rules; conduct log-based investigations; ensure logging compliance across all systems. |
| **DevOps / Platform Engineers** | Implement log forwarding from all systems; manage the centralized log platform infrastructure; ensure NTP synchronization; monitor log pipeline health; manage log retention automation. |
| **Application Developers** | Implement application-level logging per this policy; ensure sensitive data is not logged in plain text; include correlation IDs in application logs for traceability. |
| **System Owners** | Ensure their systems are configured to forward logs to the centralized platform; verify that required event types are being logged; participate in log coverage reviews. |
| **On-Call Responders** | Triage and respond to security alerts per SLA; document alert response actions; escalate alerts per the Incident Response Policy. |
| **IT** | Ensure corporate IT systems (email, endpoints, identity provider) forward logs; manage endpoint logging agents. |

## 5. Exceptions

Exceptions to logging requirements (e.g., a legacy system that cannot forward logs) must be documented with:
- The system and the specific logging gap
- Risk assessment of the gap
- Compensating controls (e.g., enhanced network monitoring around the system)
- Remediation timeline
- Approval from the Security Lead

Exceptions are tracked in the risk register and reviewed quarterly.

## 6. Review Cadence

This policy shall be reviewed **annually** or upon:

- Changes to the logging or SIEM platform
- Security incidents that reveal logging gaps
- Audit findings related to logging and monitoring
- Changes to regulatory retention requirements

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC7.1 | Monitors Infrastructure and Software for Vulnerabilities and Security Events |
| SOC 2 | CC7.2 | Monitors System Components for Anomalies |
| SOC 2 | CC7.3 | Evaluates Security Events to Determine Whether They Are Incidents |
| ISO 27001 | A.8.15 | Logging |
| ISO 27001 | A.8.16 | Monitoring Activities |
| ISO 27001 | A.8.17 | Clock Synchronization |

---

*Template provided by [TrazTech](https://traztech.ca) -- Security & Compliance Consultancy, Toronto. For guidance on maintaining logging evidence between audits, read [Keeping Evidence Fresh](https://traztech.ca/blog/keeping-evidence-fresh).*
