# Risk Management Policy

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

This Risk Management Policy defines [COMPANY_NAME]'s framework for identifying, assessing, treating, monitoring, and communicating information security risks. Risk management is the backbone of any security program: it ensures that controls are deployed where they matter most and that leadership has visibility into the threats that could impact the business.

This policy ensures that security investment is directed by evidence and business impact, not by checklists or vendor fear-mongering. It also provides auditors with confidence that [COMPANY_NAME] understands its risk landscape and manages it deliberately.

## 2. Scope

This policy applies to:

- All information assets, systems, processes, and data owned or managed by [COMPANY_NAME]
- All risk types that could affect the confidentiality, integrity, or availability of information, including technical, operational, human, legal, regulatory, and third-party risks
- All personnel involved in risk identification, assessment, treatment, and review
- All environments, including production, development, corporate IT, and third-party services

## 3. Policy Statements

### 3.1 Risk Management Principles

[COMPANY_NAME]'s risk management program is guided by the following principles:

1. **Risk-based decision making:** Security controls, investments, and priorities are driven by assessed risk, not by assumption or industry trend alone.
2. **Proportionality:** The cost and effort of risk treatment should be proportionate to the potential impact of the risk.
3. **Transparency:** Risks are documented, communicated to relevant stakeholders, and reviewed by leadership. Hiding or ignoring risks is not acceptable.
4. **Continuous process:** Risk management is ongoing, not a point-in-time exercise. The risk register is a living document.
5. **Accountability:** Every identified risk has an owner responsible for its treatment and monitoring.

### 3.2 Risk Assessment Methodology

[COMPANY_NAME] uses a qualitative risk assessment methodology based on likelihood and impact scoring:

#### 3.2.1 Likelihood Scale

| Score | Likelihood | Definition |
|---|---|---|
| 1 | Rare | Unlikely to occur within the next 3 years. No known history. |
| 2 | Unlikely | Could occur but not expected within the next year. Limited history. |
| 3 | Possible | Reasonable chance of occurring within the next year. Has occurred in similar organizations. |
| 4 | Likely | Expected to occur within the next year. Has occurred at [COMPANY_NAME] or is a known active threat. |
| 5 | Almost Certain | Expected to occur multiple times within the next year. Active threat with high probability. |

#### 3.2.2 Impact Scale

| Score | Impact | Definition |
|---|---|---|
| 1 | Negligible | Minimal impact. No data loss, no customer impact, no regulatory concern. Resolved through normal operations. |
| 2 | Minor | Limited impact. Minor inconvenience to internal operations. No customer data loss. No regulatory notification required. |
| 3 | Moderate | Noticeable impact. Temporary service degradation. Potential loss of non-critical data. May require customer notification. Recovery within 24 hours. |
| 4 | Major | Significant impact. Extended service disruption. Loss of Confidential data. Regulatory notification likely required. Financial loss or reputational damage. Recovery takes days. |
| 5 | Severe | Critical impact. Loss or exposure of Restricted data (customer PII, credentials). Major regulatory penalties. Significant financial loss. Long-term reputational damage. Business-threatening. |

#### 3.2.3 Risk Rating Matrix

| | Negligible (1) | Minor (2) | Moderate (3) | Major (4) | Severe (5) |
|---|---|---|---|---|---|
| **Almost Certain (5)** | Medium (5) | Medium (10) | High (15) | Critical (20) | Critical (25) |
| **Likely (4)** | Low (4) | Medium (8) | High (12) | High (16) | Critical (20) |
| **Possible (3)** | Low (3) | Medium (6) | Medium (9) | High (12) | High (15) |
| **Unlikely (2)** | Low (2) | Low (4) | Medium (6) | Medium (8) | Medium (10) |
| **Rare (1)** | Low (1) | Low (2) | Low (3) | Low (4) | Medium (5) |

**Risk Rating = Likelihood x Impact**

| Rating | Score Range | Required Action |
|---|---|---|
| **Critical** | 20-25 | Immediate treatment required. Escalate to executive leadership within 24 hours. Treatment plan must be defined within 1 week. |
| **High** | 12-16 | Treatment required. Risk owner must define a treatment plan within 30 days. Reviewed by Security Lead. |
| **Medium** | 5-10 | Treatment or acceptance required with documented justification. Reviewed quarterly. |
| **Low** | 1-4 | Accept and monitor. Reviewed annually. |

### 3.3 Risk Assessment Process

#### 3.3.1 Risk Identification

Risks shall be identified through multiple channels:

- **Formal risk assessments** conducted at least annually (covering the full scope of the ISMS)
- **Threat intelligence** from industry sources, security advisories, and peer organizations
- **Vulnerability assessments and penetration testing** findings
- **Incident post-mortems** and near-miss analyses
- **Audit findings** (internal and external)
- **Vendor risk assessments** (per the Vendor Management Policy)
- **Change management**: new systems, services, or significant changes trigger risk reassessment
- **Employee reporting**: any employee can identify and report a risk to [SECURITY_TEAM_EMAIL]

#### 3.3.2 Risk Analysis

For each identified risk, the following shall be documented:

1. **Risk description:** Clear statement of the threat, vulnerability, and potential impact
2. **Risk category:** Technical, operational, human, compliance, third-party, physical, or business
3. **Affected assets:** Systems, data, processes, or personnel at risk
4. **Likelihood score:** Based on the scale in Section 3.2.1
5. **Impact score:** Based on the scale in Section 3.2.2
6. **Inherent risk rating:** Likelihood x Impact (before considering existing controls)
7. **Existing controls:** Controls currently in place that mitigate the risk
8. **Residual risk rating:** Risk remaining after existing controls are considered
9. **Risk owner:** Individual accountable for managing the risk

#### 3.3.3 Risk Evaluation

- Residual risks are evaluated against [COMPANY_NAME]'s risk appetite as defined in the Information Security Policy.
- Risks that exceed the organization's risk appetite require treatment.
- Risks within the organization's risk appetite may be accepted with documented justification.

### 3.4 Risk Treatment

Each risk that requires treatment must have a treatment plan specifying one of the following strategies:

| Strategy | Description | When to Use |
|---|---|---|
| **Mitigate** | Implement controls to reduce the likelihood or impact of the risk. | Most common. The risk can be reduced to an acceptable level through reasonable controls. |
| **Transfer** | Shift the risk to a third party (e.g., insurance, outsourcing to a specialist provider). | The risk is better managed by a third party, or residual risk can be covered by insurance. |
| **Avoid** | Eliminate the risk by removing the activity, system, or process that creates it. | The risk is too high and cannot be adequately mitigated. The business can function without the risk-creating activity. |
| **Accept** | Acknowledge the risk and choose to take no further action. | The risk is within the organization's risk appetite, and the cost of treatment exceeds the potential impact. Requires documented approval. |

Treatment plans must include:
- Specific actions to be taken
- Responsible individual(s)
- Target completion date
- Expected residual risk after treatment
- Resources required
- Success criteria

### 3.5 Risk Register

[COMPANY_NAME] shall maintain a Risk Register as the central repository for all identified risks. The risk register must include for each entry:

| Field | Description |
|---|---|
| Risk ID | Unique identifier |
| Date identified | When the risk was first recorded |
| Risk description | Clear statement of the risk |
| Risk category | Technical, operational, human, compliance, third-party, physical, business |
| Affected assets | Systems, data, or processes at risk |
| Likelihood (inherent) | Score before controls |
| Impact (inherent) | Score before controls |
| Inherent risk rating | Likelihood x Impact |
| Existing controls | Controls currently mitigating the risk |
| Likelihood (residual) | Score after controls |
| Impact (residual) | Score after controls |
| Residual risk rating | Likelihood x Impact |
| Treatment strategy | Mitigate, transfer, avoid, or accept |
| Treatment plan | Specific actions, if applicable |
| Target completion date | For treatment actions |
| Risk owner | Individual accountable |
| Status | Open, in treatment, accepted, closed |
| Last reviewed | Date of most recent review |
| Notes | Additional context, links to related incidents or findings |

The risk register must be:
- Accessible to the Security Lead, executive leadership, and policy owners
- Updated whenever new risks are identified or existing risks change
- Reviewed in its entirety at least quarterly
- Presented to leadership during the annual ISMS management review

### 3.6 Risk Monitoring and Review

- **Quarterly reviews:** The Security Lead shall review the full risk register quarterly, updating risk ratings for any changes in threat landscape, controls, or business context. The results shall be reported to executive leadership.
- **Annual risk assessment:** A comprehensive risk assessment shall be conducted annually, covering the full scope of the ISMS. This assessment shall consider new threats, organizational changes, technology changes, and the effectiveness of existing controls.
- **Event-triggered reviews:** The risk register shall be updated whenever:
  - A security incident occurs
  - A significant vulnerability is discovered
  - A new system, service, or vendor is introduced
  - A significant organizational change occurs (restructuring, acquisition, market expansion)
  - An audit identifies new findings
- **Key Risk Indicators (KRIs):** [COMPANY_NAME] shall define and monitor KRIs to provide early warning of increasing risk, such as:
  - Number of critical/high vulnerabilities unpatched past SLA
  - Phishing simulation failure rate trend
  - Number of access review exceptions
  - Vendor assessment completion rate
  - Incident volume and severity trends
  - Training completion rate

### 3.7 Risk Communication and Reporting

- The Security Lead shall report on risk posture to executive leadership at least **quarterly**, including:
  - Summary of current risk register (number of risks by rating and category)
  - New risks identified since last report
  - Risks that have changed in rating
  - Status of risk treatment plans
  - Key Risk Indicators
  - Recommendations for leadership attention or resource allocation
- **Critical and High risks** shall be communicated to executive leadership within the timeframes specified in Section 3.2.3.
- The annual ISMS management review shall include a comprehensive risk review.

### 3.8 Integration with Other Processes

Risk management is not a standalone activity. It integrates with:

- **Incident Response:** Incidents inform risk identification and may change risk ratings
- **Vendor Management:** Vendor assessments feed into the risk register
- **Change Management:** Significant changes trigger risk reassessment
- **Internal Audit:** Audit findings are captured as risks or used to validate existing risk ratings
- **Business Continuity:** BIA results inform impact assessments
- **Vulnerability Management:** Vulnerability findings feed into risk identification

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Executive Leadership** | Set risk appetite; approve the risk management framework; review risk reports quarterly; make resource allocation decisions based on risk priorities; participate in the annual ISMS management review. |
| **Security Lead** | Maintain the risk management framework and risk register; conduct and coordinate risk assessments; monitor risks and KRIs; report to leadership; facilitate risk treatment planning; ensure integration with other security processes. |
| **Risk Owners** | Accountable for specific risks assigned to them; implement treatment plans; monitor residual risk; report on treatment progress; escalate when risks increase beyond tolerance. |
| **Policy Owners** | Identify risks related to their policy domains; ensure controls described in their policies effectively mitigate identified risks; participate in risk reviews. |
| **All Employees** | Report potential risks, vulnerabilities, and security concerns to [SECURITY_TEAM_EMAIL]; participate in risk assessments when requested; implement risk treatment actions within their domain. |

## 5. Risk Acceptance Authority

| Risk Rating | Acceptance Authority |
|---|---|
| Low | Security Lead |
| Medium | Security Lead with documentation |
| High | CTO/CEO with Security Lead recommendation |
| Critical | CEO or Board, with Security Lead and CTO recommendation. Must include formal acceptance statement and compensating controls. |

Risk acceptance must be documented in the risk register with the approver's name, date, justification, and any compensating controls.

## 6. Exceptions

There are no exceptions to the requirement to identify and assess risks. Exceptions to specific risk treatment plans must be approved per the risk acceptance authority in Section 5 and documented in the risk register.

## 7. Review Cadence

This policy shall be reviewed **annually** or upon:

- Significant changes to the organization's risk profile
- Major security incidents
- Changes to regulatory or compliance requirements
- Audit findings related to risk management
- Changes to the organization's business strategy or operating model

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC3.1 | Specifies Suitable Objectives |
| SOC 2 | CC3.2 | Identifies and Assesses Risks |
| SOC 2 | CC3.3 | Estimates Significance of Risks Identified |
| SOC 2 | CC3.4 | Identifies and Assesses Changes |
| SOC 2 | CC4.1 | Selects and Develops Ongoing and Separate Evaluations |
| SOC 2 | CC4.2 | Evaluates and Communicates Deficiencies |
| SOC 2 | CC5.1 | Selects and Develops Control Activities |
| ISO 27001 | A.5.2 | Information Security Roles and Responsibilities |
| ISO 27001 | A.5.3 | Segregation of Duties |
| ISO 27001 | A.5.4 | Management Responsibilities |
| ISO 27001 | A.5.5 | Contact with Authorities |
| ISO 27001 | A.5.6 | Contact with Special Interest Groups |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. For guidance on preventing control and risk drift between audits, read [Control Drift Between Audits](https://traztech.ca/blog/control-drift-between-audits).*
