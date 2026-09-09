# Incident Response Policy

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

This Incident Response Policy establishes [COMPANY_NAME]'s framework for detecting, responding to, containing, and recovering from information security incidents. It defines roles, responsibilities, severity classifications, escalation procedures, communication protocols, and post-incident review processes to ensure that incidents are handled consistently, efficiently, and with minimal impact to customers and business operations.

A security incident is not a matter of "if" but "when." The quality of your response determines whether an event becomes a minor disruption or a business-threatening crisis.

## 2. Scope

This policy applies to:

- All information security events and incidents affecting [COMPANY_NAME] systems, data, infrastructure, or personnel
- All environments, including production, staging, corporate IT, and cloud infrastructure
- All personnel, including employees, contractors, and third-party service providers who detect, report, or respond to security events
- All data, including customer data, employee data, intellectual property, and business operations data

## 3. Definitions

| Term | Definition |
|---|---|
| **Security Event** | An observable occurrence in a system or network that may be relevant to security (e.g., a failed login attempt, a firewall alert, a vulnerability scan detection). Not all events are incidents. |
| **Security Incident** | A security event that has been assessed and determined to have actually or potentially compromised the confidentiality, integrity, or availability of [COMPANY_NAME] information or systems. |
| **Data Breach** | A confirmed incident in which sensitive, protected, or confidential data has been accessed, disclosed, or exfiltrated by an unauthorized party. |
| **Incident Commander (IC)** | The individual responsible for coordinating the overall incident response, making decisions, and managing communication during an active incident. |
| **Subject Matter Expert (SME)** | An individual with specialized knowledge relevant to the incident (e.g., database administrator, cloud architect, application developer). |

## 4. Incident Severity Classification

| Severity | Definition | Response Time | Examples |
|---|---|---|---|
| **Critical (SEV-1)** | Active, confirmed breach of customer data; complete loss of production availability; active exploitation of a critical vulnerability; ransomware or destructive malware. | **Respond within 15 minutes.** All-hands engagement. | Customer data exfiltration confirmed; production database compromised; ransomware encrypting systems. |
| **High (SEV-2)** | Significant security compromise with potential for data loss; partial production outage affecting customers; privilege escalation or unauthorized admin access detected. | **Respond within 1 hour.** IR team engaged immediately. | Unauthorized access to production server; DDoS attack degrading service; compromised employee credentials with access to sensitive systems. |
| **Medium (SEV-3)** | Security event requiring investigation but without confirmed data compromise or customer impact; targeted phishing attempts; malware detected and contained on a single endpoint. | **Respond within 4 hours.** Assigned to IR team during business hours. | Successful phishing leading to credential reset; malware quarantined by endpoint protection; unauthorized configuration change detected and reverted. |
| **Low (SEV-4)** | Minor security events with low impact and no data compromise; policy violations without malicious intent; vulnerability discovered but not exploited. | **Respond within 1 business day.** Handled during normal operations. | Employee accessing unauthorized website; minor policy violation reported; informational vulnerability scan finding. |

## 5. Incident Response Process

### 5.1 Phase 1: Detection and Reporting

**Anyone** at [COMPANY_NAME] can report a suspected security event. Reporting channels:

- **Email:** [INCIDENT_RESPONSE_EMAIL]
- **Slack/Chat:** Dedicated #security-incidents channel
- **Phone/Pager:** On-call security contact via PagerDuty (or equivalent)
- **Automated:** Alerts from SIEM, endpoint detection, intrusion detection, and monitoring systems

Reports should include (as much as is known):
- What was observed
- When it was observed
- Which systems or data are affected
- Any actions already taken
- Contact information for the reporter

**There is no penalty for reporting a false positive.** It is always better to report and have the IR team triage than to ignore a potential incident.

### 5.2 Phase 2: Triage and Assessment

Upon receiving a report, the on-call responder shall:

1. **Acknowledge** the report within the timeframe specified by the severity level.
2. **Assess** the event to determine:
   - Is this a security incident or a false positive?
   - What is the scope (systems, data, users affected)?
   - What is the severity (using the classification in Section 4)?
   - Is customer data potentially involved?
3. **Create an incident ticket** in the incident tracking system with:
   - Incident ID (auto-generated or sequential)
   - Date and time of detection
   - Reporter
   - Initial assessment and severity
   - Assigned Incident Commander
4. **Escalate** based on severity:
   - SEV-1 and SEV-2: Immediately notify the Security Lead, Engineering Lead, and CEO. Open a dedicated incident response communication channel.
   - SEV-3: Notify the Security Lead. Assign to IR team for investigation.
   - SEV-4: Assign to the appropriate team member for investigation during business hours.

### 5.3 Phase 3: Containment

The goal of containment is to stop the incident from spreading and prevent further damage. The Incident Commander coordinates containment activities, which may include:

**Short-term containment (immediate):**
- Isolate affected systems from the network
- Disable compromised user accounts
- Block malicious IP addresses or domains
- Revoke compromised credentials or API keys
- Enable enhanced logging on affected systems
- Preserve volatile evidence (memory dumps, running processes) before taking destructive containment actions

**Long-term containment (stabilization):**
- Deploy patches or temporary fixes to prevent re-exploitation
- Implement additional monitoring on affected systems
- Stand up clean replacement systems if necessary
- Redirect traffic away from compromised systems

**Critical rule:** Do not destroy evidence. If a system is compromised, image the disk and capture memory before wiping. Forensic evidence may be required for legal proceedings, regulatory notifications, or root cause analysis.

### 5.4 Phase 4: Eradication

Once the incident is contained, the IR team shall:

1. Identify the root cause of the incident (attack vector, vulnerability exploited, initial point of compromise)
2. Remove the attacker's access (backdoors, persistence mechanisms, compromised accounts)
3. Patch the vulnerability or close the attack vector that allowed the incident
4. Scan for indicators of compromise (IOCs) across the environment to confirm the incident is fully contained
5. Verify that no additional systems were compromised

### 5.5 Phase 5: Recovery

Recovery restores affected systems to normal operations:

1. Restore systems from known-good backups or rebuild from clean images
2. Verify system integrity before returning to production
3. Re-enable user access in a controlled manner
4. Implement enhanced monitoring for a defined period (minimum 30 days) to detect any recurrence
5. Confirm with stakeholders that business operations have returned to normal
6. Communicate recovery status to affected customers (if applicable)

### 5.6 Phase 6: Post-Incident Review

A post-incident review (blameless retrospective) shall be conducted for all SEV-1 and SEV-2 incidents, and optionally for SEV-3 incidents at the Security Lead's discretion.

The review shall be completed within **5 business days** of incident closure and shall document:

- **Timeline:** Chronological sequence of events from detection through recovery
- **Root cause analysis:** What caused the incident, including contributing factors
- **Impact assessment:** Systems, data, and customers affected; duration of impact
- **Response evaluation:** What went well, what could be improved, what was missing
- **Action items:** Specific, assigned, time-bound actions to prevent recurrence
- **Lessons learned:** Key takeaways for the team and organization

Post-incident review reports shall be stored in the incident management system and made available for audit purposes. Action items shall be tracked to completion.

## 6. Communication and Notification

### 6.1 Internal Communication

- SEV-1 and SEV-2 incidents require a dedicated communication channel (Slack channel, bridge call) for real-time coordination.
- The Incident Commander is the single point of communication during active incidents. All external communications must be approved by the IC.
- Status updates shall be provided at regular intervals during active incidents:
  - SEV-1: Every 30 minutes
  - SEV-2: Every 2 hours
  - SEV-3: Daily

### 6.2 Customer Notification

- Customers must be notified when a confirmed incident has or may have affected their data or service availability.
- Customer notifications must be:
  - Honest and transparent about what happened and what data was affected
  - Clear about what [COMPANY_NAME] is doing to resolve the issue
  - Specific about what actions (if any) customers should take
  - Reviewed by legal counsel before distribution
- Customer notification timing: within 72 hours of confirming a data breach, or sooner if required by contract or regulation.

### 6.3 Regulatory and Legal Notification

- If the incident constitutes a data breach under applicable law, [COMPANY_NAME] shall notify the relevant regulatory authorities within the timeframes required by law (e.g., GDPR requires notification within 72 hours; specific US state laws vary).
- Legal counsel ([LEGAL_CONTACT]) must be engaged for all SEV-1 incidents and any incident involving confirmed data breach.
- Law enforcement shall be engaged when the incident involves criminal activity, at the direction of legal counsel.

### 6.4 Third-Party Notification

- If the incident originated from or involves a third-party vendor, the vendor must be notified in accordance with the Vendor Management Policy and the terms of the vendor agreement.
- If the incident may affect other organizations (e.g., supply chain compromise), those organizations should be notified through appropriate channels.

## 7. Incident Response Team

| Role | Responsibilities |
|---|---|
| **Incident Commander (IC)** | Coordinate the overall response; assign tasks; make containment and communication decisions; ensure documentation; conduct post-incident review. Rotates based on on-call schedule. |
| **Security Lead** | Technical leadership on security incidents; forensic analysis; threat intelligence; approve containment strategies; manage security tooling during incidents. |
| **Engineering Lead / CTO** | Provide engineering resources; approve emergency changes; make decisions on system isolation or shutdown; coordinate recovery efforts. |
| **On-Call Engineer** | First responder for automated alerts; initial triage and assessment; execute containment actions under IC direction. |
| **Subject Matter Experts** | Provide specialized knowledge (database, cloud, networking, application) as needed during the investigation and recovery. |
| **Legal Counsel** | Advise on regulatory notification requirements; review customer and public communications; manage law enforcement engagement; preserve legal privilege. |
| **CEO / Executive Leadership** | Approve customer communications for SEV-1 incidents; make business decisions during major incidents; authorize spending for incident response resources. |
| **Communications/PR** | Draft external communications (if applicable); manage media inquiries; coordinate with marketing on customer-facing messaging. |

## 8. Incident Response Readiness

- The Incident Response Plan shall be tested at least **annually** through tabletop exercises simulating realistic incident scenarios.
- On-call rotations shall be maintained and tested to ensure responders are reachable.
- Incident response runbooks shall be maintained for common incident types (e.g., compromised credentials, ransomware, DDoS, data exfiltration).
- Contact lists (internal escalation, external vendors, legal counsel, regulatory bodies) shall be maintained and updated quarterly.
- Forensic tools and capabilities shall be maintained and tested to ensure they are operational when needed.

## 9. Evidence Preservation

- All evidence collected during an incident shall be handled with chain-of-custody procedures:
  - Document who collected the evidence, when, how, and where it is stored
  - Store evidence in a secure, access-controlled location
  - Create cryptographic hashes (SHA-256) of forensic images and evidence files
  - Maintain evidence integrity logs
- Evidence shall be retained for a minimum of 3 years, or longer if required by legal proceedings or regulatory obligations.

## 10. Exceptions

This policy does not permit exceptions for reporting obligations. All security events must be reported through the channels defined in this policy. Exceptions to response procedures may be granted by the Security Lead for documented operational reasons and must be recorded in the incident ticket.

## 11. Review Cadence

This policy shall be reviewed **annually** or upon:

- Completion of a post-incident review that identifies policy gaps
- Completion of a tabletop exercise that identifies improvements
- Changes to regulatory notification requirements
- Significant changes to the organization's systems or infrastructure

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC7.2 | Monitors System Components for Anomalies |
| SOC 2 | CC7.3 | Evaluates Security Events to Determine Whether They Are Incidents |
| SOC 2 | CC7.4 | Responds to Identified Security Incidents |
| SOC 2 | CC7.5 | Identifies and Assesses the Impact of Incidents |
| SOC 2 | CC2.2 | Communicates with External Parties |
| ISO 27001 | A.5.24 | Information Security Incident Management Planning and Preparation |
| ISO 27001 | A.5.25 | Assessment and Decision on Information Security Events |
| ISO 27001 | A.5.26 | Response to Information Security Incidents |
| ISO 27001 | A.5.27 | Learning from Information Security Incidents |
| ISO 27001 | A.5.28 | Collection of Evidence |
| ISO 27001 | A.6.8 | Information Security Event Reporting |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. For guidance on maintaining incident response readiness between audits, read [Compliance Calendar: What Actually Recurs](https://traztech.ca/blog/compliance-calendar-what-actually-recurs).*
