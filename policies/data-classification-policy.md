# Data Classification Policy

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

This Data Classification Policy establishes a framework for categorizing [COMPANY_NAME]'s information assets based on their sensitivity and business value, and defines the handling requirements for each classification level. Proper data classification ensures that information is protected with controls proportionate to its sensitivity, reduces the risk of data exposure, and enables employees to make informed decisions about how to handle the data they work with.

You cannot protect data effectively if you do not know what it is and how sensitive it is. Classification is the foundation of data protection.

## 2. Scope

This policy applies to:

- All data created, received, maintained, or transmitted by [COMPANY_NAME], regardless of format (electronic, paper, verbal)
- All systems that store, process, or transmit [COMPANY_NAME] data, including databases, file storage, SaaS applications, communication tools, and endpoints
- All personnel, including employees, contractors, and third parties who handle [COMPANY_NAME] data

## 3. Classification Levels

[COMPANY_NAME] uses four classification levels. All data must be assigned to one of these levels by the data owner.

### 3.1 Restricted

**Definition:** The most sensitive data whose unauthorized disclosure would cause severe harm to [COMPANY_NAME], its customers, or its employees. Exposure could result in significant legal liability, regulatory penalties, loss of customer trust, or competitive damage.

**Examples:**
- Customer personal data subject to privacy regulations (PII: names, email addresses, phone numbers, physical addresses in combination with identifiers)
- Customer authentication credentials (passwords, tokens, API keys managed on behalf of customers)
- Payment card data (PAN, CVV, cardholder data)
- Health information (PHI) if applicable
- Employee Social Security/Social Insurance numbers, financial account details
- Encryption keys and secrets management data
- Security vulnerability reports and penetration test results (prior to remediation)
- Board and executive communications regarding legal, M&A, or regulatory matters

### 3.2 Confidential

**Definition:** Sensitive business information whose unauthorized disclosure could cause material harm to [COMPANY_NAME]'s operations, competitive position, or relationships. This is the default classification for most internal business data.

**Examples:**
- Source code and proprietary algorithms
- Internal financial statements, revenue data, forecasts
- Customer lists and contract details
- Employee performance reviews, compensation data, HR records
- Security configurations, network diagrams, architecture documents
- Vendor contracts and pricing
- Product roadmaps and unreleased feature plans
- Internal audit reports and compliance findings
- Incident response reports

### 3.3 Internal

**Definition:** Information intended for use within [COMPANY_NAME] that is not sensitive enough to be classified as Confidential, but should not be made public. Unauthorized disclosure would cause minor inconvenience but not material harm.

**Examples:**
- Internal policies and procedures (including these security policies)
- Internal wikis and knowledge base articles
- Meeting notes and general project documentation
- Internal announcements and communications
- Non-sensitive operational data
- General IT support documentation

### 3.4 Public

**Definition:** Information that has been approved for public distribution. Disclosure carries no risk to [COMPANY_NAME].

**Examples:**
- Published marketing materials, blog posts, press releases
- Public-facing documentation and help center content
- Open-source code published by [COMPANY_NAME]
- Job postings
- Published financial reports (for public companies)

## 4. Data Handling Requirements

### 4.1 Handling Matrix

| Requirement | Restricted | Confidential | Internal | Public |
|---|---|---|---|---|
| **Encryption at rest** | Required (AES-256 or equivalent) | Required | Recommended | Not required |
| **Encryption in transit** | Required (TLS 1.2+) | Required (TLS 1.2+) | Required (TLS 1.2+) | Recommended |
| **Access control** | Need-to-know, explicit approval by data owner and Security Lead | Need-to-know, manager approval | Role-based, available to employees | No restriction |
| **Storage** | Approved encrypted systems only; no local copies without approval | Approved company systems only | Approved company systems | Any |
| **Sharing - Internal** | Encrypted channels only; recipient must have explicit authorization | Standard company communication tools | Standard company communication tools | Any channel |
| **Sharing - External** | Only with legal/contractual basis; encrypted transfer; Security Lead approval required | NDA required; encrypted transfer recommended; manager approval | Not recommended without business justification | Freely shareable |
| **Printing** | Avoid; if necessary, retrieve immediately and shred when no longer needed | Minimize; secure when printed | No special requirements | No restriction |
| **Labeling** | Must be labeled "RESTRICTED" in document headers, file names, or metadata where feasible | Must be labeled "CONFIDENTIAL" where feasible | Optional: "INTERNAL" | Optional: "PUBLIC" |
| **Retention** | Per retention schedule; secure deletion required | Per retention schedule; secure deletion required | Per retention schedule | Per retention schedule |
| **Disposal** | Cryptographic erasure or physical destruction; documented | Secure deletion; documented | Standard deletion | Standard deletion |
| **Backup** | Encrypted backups in approved locations; tested restore | Encrypted backups | Standard backups | As needed |
| **Monitoring** | Enhanced logging and alerting on all access | Standard access logging | Standard logging | Minimal |

### 4.2 Data in Development and Testing

- **Restricted data** must never be used in development, testing, staging, or QA environments unless it has been anonymized or pseudonymized to a degree that it cannot be re-identified.
- **Confidential data** should not be used in non-production environments. Where unavoidable, it must be approved by the data owner and Security Lead, and the non-production environment must have equivalent access controls.
- Synthetic data or properly anonymized datasets should be used for testing wherever possible.

### 4.3 Data in Transit

- All Restricted and Confidential data must be encrypted in transit using TLS 1.2 or higher.
- Email transmission of Restricted data is prohibited unless end-to-end encryption is used.
- File transfers of Restricted data must use encrypted transfer mechanisms (SFTP, SCP, encrypted cloud storage links with access controls).
- Restricted data must not be transmitted via consumer messaging apps (SMS, personal messaging applications).

### 4.4 Data Retention and Disposal

- Each data category shall have a defined retention period based on legal, regulatory, contractual, and business requirements. The retention schedule shall be maintained by the Security Lead in coordination with legal counsel.
- When data reaches the end of its retention period, it must be disposed of according to the handling matrix above.
- Disposal of Restricted data must be documented, including what was destroyed, when, by whom, and the method of destruction.
- Electronic media containing Restricted or Confidential data must be sanitized using methods consistent with NIST SP 800-88 before reuse or disposal.

## 5. Data Ownership

- Every data set or information asset must have a designated **data owner** -- typically the head of the department or function that creates or manages that data.
- Data owners are responsible for:
  - Assigning and reviewing the classification level of their data
  - Defining who may access their data
  - Ensuring data handling requirements are met
  - Approving access requests for their data
  - Reviewing classification levels annually or when the nature of the data changes
- Data ownership does not imply personal ownership. All data remains the property of [COMPANY_NAME].

## 6. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Data Owners** | Classify data; define access requirements; approve access requests; review classifications annually; ensure compliance with handling requirements within their domain. |
| **Security Lead** | Maintain this policy; provide guidance on classification decisions; approve handling exceptions; monitor compliance; manage data loss prevention (DLP) tools. |
| **All Employees** | Handle data according to its classification level; label data where required; report suspected mishandling or data exposure to [SECURITY_TEAM_EMAIL]; complete data handling training. |
| **IT/Engineering** | Implement technical controls (encryption, access controls, DLP, secure deletion); maintain systems used to store and process classified data; support data inventory efforts. |
| **Legal** | Advise on regulatory retention requirements; define contractual data handling obligations; support data breach notification decisions. |
| **HR** | Ensure employees acknowledge data handling responsibilities; coordinate training on data classification; manage access to employee data in accordance with this policy. |

## 7. Data Inventory

- [COMPANY_NAME] shall maintain an inventory of data stores that identifies:
  - The system or service where data is stored
  - The types of data contained
  - The classification level
  - The data owner
  - Encryption status (at rest and in transit)
  - Backup status
  - Retention period
- The data inventory shall be reviewed and updated at least semi-annually.

## 8. Exceptions

Exceptions to data handling requirements must be documented with:
- The specific requirement being excepted
- Business justification
- Duration of the exception
- Compensating controls in place
- Approval from the data owner and Security Lead

Exceptions are tracked in the risk register and reviewed quarterly.

## 9. Review Cadence

This policy shall be reviewed **annually** or upon:

- Introduction of new data types or systems
- Changes to regulatory requirements affecting data handling
- Data-related security incidents
- Changes to the organization's business model that affect data sensitivity

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC6.1 | Logical and Physical Access Controls |
| SOC 2 | CC6.5 | Restricts Registration and Devices to Authorized Individuals |
| SOC 2 | CC6.7 | Restricts Transmission, Movement, and Removal of Information |
| ISO 27001 | A.5.9 | Inventory of Information and Other Associated Assets |
| ISO 27001 | A.5.10 | Acceptable Use of Information and Other Associated Assets |
| ISO 27001 | A.5.12 | Classification of Information |
| ISO 27001 | A.5.13 | Labelling of Information |
| ISO 27001 | A.5.14 | Information Transfer |

---

*Template provided by [TrazTech](https://traztech.ca) -- Security & Compliance Consultancy, Toronto. For guidance on managing evidence of data handling controls, read [Keeping Evidence Fresh](https://traztech.ca/blog/keeping-evidence-fresh).*
