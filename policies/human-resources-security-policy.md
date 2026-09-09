# Human Resources Security Policy

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

This Human Resources Security Policy defines [COMPANY_NAME]'s requirements for managing the security aspects of the employee lifecycle: hiring, onboarding, ongoing employment, role changes, and offboarding. People are both an organization's greatest asset and its most significant security variable. This policy ensures that personnel are vetted before they receive access, trained to handle data responsibly, and properly deprovisioned when they leave.

## 2. Scope

This policy applies to:

- All full-time and part-time employees of [COMPANY_NAME]
- All contractors, consultants, temporary workers, and interns
- All stages of the employment lifecycle: pre-hire, onboarding, active employment, role changes, and separation
- All personnel with access to [COMPANY_NAME] information systems or data

## 3. Policy Statements

### 3.1 Pre-Employment Screening

- Background checks shall be conducted for all candidates prior to their start date, proportionate to the role and level of access they will receive.
- At minimum, background checks shall include:
  - **Identity verification**: confirmation of the candidate's legal identity
  - **Employment history verification**: confirmation of previous employment for the most recent relevant positions
  - **Criminal background check**: within the scope permitted by applicable law and jurisdiction
- For roles with access to Restricted data (as defined in the Data Classification Policy), financial systems, or administrative/privileged access to production systems, additional screening may include:
  - Credit history check (where legally permitted and relevant)
  - Professional certification verification
  - Education verification
  - Reference checks
- Background checks shall be conducted by an approved third-party screening provider.
- Candidates must consent to background checks as a condition of employment. The scope of checks shall be disclosed to the candidate in advance.
- Adverse findings shall be reviewed by HR in consultation with the hiring manager and, where applicable, legal counsel, before a hiring decision is made. Not all adverse findings result in disqualification: the assessment considers relevance, recency, and severity.
- Background check results shall be stored securely by HR with access restricted to authorized personnel, and retained in accordance with applicable data retention laws.

### 3.2 Onboarding

The onboarding process shall ensure that new personnel understand their security responsibilities before they access [COMPANY_NAME] systems and data:

**Before or on Day 1:**
1. **Employment agreement signed**: including confidentiality obligations, intellectual property assignment, and acknowledgment of the Acceptable Use Policy.
2. **Confidentiality / Non-Disclosure Agreement (NDA)** signed: covering the protection of [COMPANY_NAME] and customer proprietary information. The NDA must survive termination of employment.
3. **Security policy acknowledgment**: the employee must acknowledge that they have received, read, and agree to comply with [COMPANY_NAME]'s security policies, including at minimum: Information Security Policy, Acceptable Use Policy, and Data Classification Policy.
4. **Account provisioning**: IT provisions accounts based on the employee's role, following the Access Control Policy (role-based access, least privilege, MFA enrollment).
5. **Equipment issuance**: company devices are provisioned with required security configurations (full-disk encryption, endpoint protection, automatic updates enabled, remote wipe capability).

**Within the first 7 days:**
6. **Security awareness training**: the employee must complete the initial security awareness training module covering: phishing recognition, password management, data handling, incident reporting, and acceptable use. Training must be completed before the employee is granted access to Restricted or Confidential data.

**Within the first 30 days:**
7. **Role-specific security training**: employees in technical roles (engineering, DevOps, IT) must complete additional training on secure development practices, production access procedures, and any role-specific security controls.
8. **Manager verification**: the employee's manager confirms that onboarding security steps are complete and access is appropriate for the role.

### 3.3 Ongoing Employment

#### 3.3.1 Security Awareness Training

- All employees must complete security awareness training **annually** at minimum.
- Training shall cover:
  - Phishing and social engineering recognition (with simulated phishing exercises at least quarterly)
  - Password and authentication best practices
  - Data classification and handling
  - Incident reporting procedures
  - Remote work security
  - Physical security (clean desk, device security)
  - Insider threat awareness
  - Relevant regulatory requirements (privacy, data protection)
- Training completion shall be tracked. Employees who do not complete training within the required timeframe shall have their system access restricted until training is completed.
- Training content shall be updated at least annually to reflect current threats and organizational changes.

#### 3.3.2 Phishing Simulations

- Simulated phishing exercises shall be conducted at least **quarterly** for all employees.
- Employees who fail a phishing simulation (click a link, enter credentials, open an attachment) shall receive immediate remedial training.
- Employees who fail multiple simulations within a 12-month period shall be required to complete enhanced training and may have their access privileges reviewed.
- Phishing simulation results shall be tracked and reported to leadership as a KPI.

#### 3.3.3 Acceptable Behavior and Policy Compliance

- All employees are expected to comply with [COMPANY_NAME]'s security policies at all times.
- Managers are responsible for reinforcing security expectations within their teams.
- Security policy compliance may be verified through periodic audits, access reviews, and monitoring as described in the Acceptable Use Policy and Logging and Monitoring Policy.

#### 3.3.4 Ongoing Screening

- [COMPANY_NAME] reserves the right to conduct periodic re-screening for employees in high-sensitivity roles (e.g., those with access to Restricted data or administrative access to production systems), subject to applicable law.
- Re-screening may be triggered by promotion to a higher-sensitivity role.

### 3.4 Role Changes and Transfers

When an employee changes roles, departments, or responsibilities:

1. **Access review**: the employee's current access shall be reviewed against the requirements of the new role. Access that is no longer needed for the new role must be revoked.
2. **New access provisioning**: access required for the new role shall be requested and approved through the standard access request process defined in the Access Control Policy.
3. **Timeline**: access adjustments must be completed within 5 business days of the effective date of the role change. For transfers to lower-trust roles, excess access must be revoked before or on the effective date.
4. **Training**: if the new role has different security requirements (e.g., moving to an engineering role requiring secure development training), the employee must complete the relevant training within 30 days.

### 3.5 Offboarding and Separation

Offboarding must be handled promptly and thoroughly to prevent unauthorized access by former personnel. The offboarding process differs based on the type of separation:

#### 3.5.1 Voluntary Departure (Resignation)

1. **HR notifies IT and the Security Lead** upon receiving a resignation, including the employee's last working day.
2. **Access revocation planning**: IT prepares an access revocation checklist for all systems the employee has access to.
3. **Knowledge transfer**: the employee's manager coordinates transfer of responsibilities, shared accounts, and documentation ownership.
4. **Exit interview**: HR conducts an exit interview that includes reminders of ongoing confidentiality obligations under the NDA.
5. **On or before the last day:**
   - All system access is revoked (identity provider account disabled, SSO sessions terminated, VPN access removed)
   - Email forwarding is configured to the employee's manager (with a defined expiration, typically 30 days)
   - Company devices are collected and wiped
   - Shared credentials or API keys the employee had knowledge of are rotated
   - Physical access (badge, keys) is revoked
   - The employee confirms return of all company property and data
6. **Access revocation verification**: IT confirms all access has been revoked within 4 hours of the employee's last working moment.

#### 3.5.2 Involuntary Termination

For involuntary terminations, all access must be revoked **simultaneously with or immediately before** the notification of termination:

1. **Pre-termination planning**: HR, the manager, and IT coordinate the termination timeline. IT prepares access revocation to execute on signal from HR.
2. **At the time of notification:**
   - All system access is immediately revoked (identity provider disabled, active sessions terminated)
   - VPN and remote access is disabled
   - Company devices are collected (or remote wiped if not physically recoverable)
   - Email account is suspended
   - Physical access is revoked
3. **Shared credentials and API keys** the terminated employee had knowledge of must be rotated within 24 hours.
4. **Enhanced monitoring** may be implemented for a period following involuntary termination if there is concern about data exfiltration or retaliation.
5. **Access revocation verification** within 1 hour.

#### 3.5.3 Contractor and Temporary Worker Offboarding

- Contractor and temporary worker access must be revoked on or before the last day of the engagement.
- Access should be provisioned with a defined end date wherever technically feasible, so that access expires automatically.
- The business sponsor is responsible for notifying IT when a contractor's engagement ends or is extended.

### 3.6 Disciplinary Process

- Violations of security policies shall be addressed through the organization's disciplinary process, which may include:
  - Verbal warning and additional training (first minor offense)
  - Written warning (repeated minor offenses or first significant offense)
  - Suspension of system access pending investigation
  - Termination of employment or contract (severe violations, malicious activity, or repeated offenses)
  - Referral to law enforcement (criminal activity)
- The severity of disciplinary action shall be proportionate to the nature, intent, and impact of the violation.
- All disciplinary actions related to security policy violations shall be documented by HR.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **HR / People Operations** | Administer background checks; manage onboarding/offboarding checklists; track training completion; conduct exit interviews; maintain employee records; coordinate disciplinary actions. |
| **Managers** | Initiate access requests for new hires; verify onboarding completion; ensure team compliance with training requirements; notify HR and IT of departures and role changes promptly; participate in access reviews. |
| **IT** | Provision and deprovision accounts; configure and collect devices; implement technical onboarding/offboarding controls; rotate shared credentials upon departures; maintain the access revocation checklist. |
| **Security Lead** | Define training content and frequency; oversee phishing simulations; review background check requirements; consult on disciplinary actions for security violations; verify offboarding completeness. |
| **Legal** | Advise on NDA terms and enforceability; review background check compliance with applicable law; advise on disciplinary matters involving potential legal exposure. |
| **All Employees** | Complete required training on time; comply with security policies; report security concerns; return company property and data upon separation. |

## 5. Records and Evidence

- Background check completion records (date, scope, result summary: not full reports) shall be maintained for the duration of employment plus 3 years.
- Training completion records (date, course, employee name) shall be maintained for audit purposes.
- Policy acknowledgment records shall be maintained for the duration of employment plus 3 years.
- Onboarding and offboarding checklists shall be maintained for 3 years for audit evidence.

## 6. Exceptions

Exceptions to background check requirements or training timelines must be documented with a justification, approved by HR and the Security Lead, and tracked in the risk register. No exceptions are permitted for NDA signing or access revocation timelines.

## 7. Review Cadence

This policy shall be reviewed **annually** or upon:

- Changes to employment law or privacy regulations affecting HR processes
- Security incidents involving insider threats or personnel-related vectors
- Audit findings related to HR security controls
- Significant changes to the organization's structure or hiring practices

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC1.4 | Demonstrates Commitment to Competence |
| SOC 2 | CC1.5 | Enforces Accountability |
| SOC 2 | CC2.2 | Communicates with External Parties |
| SOC 2 | CC6.2 | Prior to Issuing System Credentials, Registers and Authorizes New Users |
| SOC 2 | CC6.3 | Authorizes, Modifies, or Removes Access Based on Authorization |
| ISO 27001 | A.6.1 | Screening |
| ISO 27001 | A.6.2 | Terms and Conditions of Employment |
| ISO 27001 | A.6.3 | Information Security Awareness, Education, and Training |
| ISO 27001 | A.6.4 | Disciplinary Process |
| ISO 27001 | A.6.5 | Responsibilities after Termination or Change of Employment |
| ISO 27001 | A.6.6 | Confidentiality or Non-Disclosure Agreements |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. For a complete view of recurring compliance tasks including training cycles, read [Compliance Calendar: What Actually Recurs](https://traztech.ca/blog/compliance-calendar-what-actually-recurs).*
