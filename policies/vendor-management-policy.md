# Vendor Management Policy

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

This Vendor Management Policy establishes [COMPANY_NAME]'s requirements for assessing, selecting, monitoring, and managing third-party vendors and service providers. Every vendor that accesses, processes, stores, or transmits [COMPANY_NAME] or customer data represents a potential extension of our attack surface. This policy ensures that third-party risk is identified, evaluated, and managed throughout the vendor lifecycle.

Your security program is only as strong as your weakest vendor. This policy exists to ensure that vendors meet the same security standards we hold ourselves to.

## 2. Scope

This policy applies to:

- All third-party vendors, service providers, contractors, and business partners that access, process, store, or transmit [COMPANY_NAME] data or customer data
- All third-party software, SaaS applications, and cloud services used by [COMPANY_NAME]
- All [COMPANY_NAME] personnel involved in vendor selection, procurement, management, or oversight
- Subcontractors and fourth parties engaged by [COMPANY_NAME]'s vendors who handle [COMPANY_NAME] data

**Exclusions:** This policy does not apply to off-the-shelf consumer products that do not process company data (e.g., office supplies, furniture).

## 3. Vendor Tiering

Vendors shall be classified into tiers based on the sensitivity of data they access and the criticality of services they provide:

| Tier | Criteria | Due Diligence Level | Review Frequency |
|---|---|---|---|
| **Tier 1: Critical** | Processes or stores Restricted or Confidential data; provides services critical to production operations; failure would cause significant business disruption or regulatory exposure. | Comprehensive assessment | Annually |
| **Tier 2: Important** | Accesses Internal data; provides services that support business operations but are not production-critical; moderate impact if service is disrupted. | Standard assessment | Every 2 years |
| **Tier 3: Low Risk** | No access to sensitive data; provides non-critical services; limited impact if service is disrupted. | Lightweight review | Every 3 years or at renewal |

**Examples by tier:**

- **Tier 1:** Cloud infrastructure provider (AWS, GCP, Azure), identity provider (Okta, Auth0), customer database hosting, payment processor, SIEM/logging platform, CI/CD platform
- **Tier 2:** Project management tools, HR/payroll platform, marketing automation, customer support platform, communication tools (Slack, email)
- **Tier 3:** Office supplies vendor, design tools, non-data-processing SaaS tools

## 4. Policy Statements

### 4.1 Vendor Due Diligence

Before engaging a new vendor, [COMPANY_NAME] shall conduct due diligence proportionate to the vendor's tier:

**Tier 1: Comprehensive Assessment:**
- Request and review the vendor's SOC 2 Type II report (or equivalent: SOC 1, ISO 27001 certificate, or PCI DSS AOC if applicable). The report must be current (issued within the last 12 months).
- Review any exceptions, qualifications, or findings noted in the report and assess their relevance to [COMPANY_NAME]'s use case.
- Complete a vendor security questionnaire (SIG Lite, CAIQ, or [COMPANY_NAME]'s custom questionnaire) covering: data handling, encryption, access controls, incident response, business continuity, employee security, and subprocessor management.
- Review the vendor's data processing agreement (DPA) or equivalent, ensuring it addresses data handling, breach notification timelines, data deletion, and audit rights.
- Evaluate the vendor's insurance coverage (cyber liability, errors and omissions) where applicable.
- Verify the vendor's incident response and breach notification commitments (notification within 72 hours or less is expected).
- Assess the vendor's financial stability if the engagement involves critical services or significant spend.

**Tier 2: Standard Assessment:**
- Request and review the vendor's SOC 2 report or ISO 27001 certificate, or the vendor's published security page/trust center.
- Complete an abbreviated security questionnaire focusing on data handling, encryption, and access controls.
- Review the vendor's terms of service and privacy policy for data handling provisions.

**Tier 3: Lightweight Review:**
- Review the vendor's published security information (security page, privacy policy).
- Confirm that no sensitive data will be shared with the vendor.
- Document the vendor's purpose and scope of engagement.

### 4.2 Contractual Requirements

All vendor agreements (for Tier 1 and Tier 2 vendors) must include or reference the following provisions:

- **Confidentiality and data protection obligations** specifying how the vendor will protect [COMPANY_NAME] data
- **Data processing terms** defining the purpose, duration, and type of processing performed
- **Security requirements** requiring the vendor to maintain security controls appropriate to the data they handle
- **Breach notification** requiring the vendor to notify [COMPANY_NAME] of any security incident affecting [COMPANY_NAME] data within a defined timeframe (72 hours maximum for Tier 1 vendors)
- **Audit rights** allowing [COMPANY_NAME] or its auditors to assess the vendor's security controls (or accept SOC 2/ISO 27001 reports in lieu of direct audit)
- **Data return and deletion** specifying the vendor's obligations to return or securely delete [COMPANY_NAME] data upon termination of the agreement
- **Subprocessor disclosure** requiring the vendor to disclose and obtain approval for any subprocessors handling [COMPANY_NAME] data
- **Insurance requirements** for Tier 1 vendors handling Restricted data
- **Right to terminate** if the vendor experiences a material security breach or fails to maintain agreed-upon security controls

### 4.3 Vendor Inventory

[COMPANY_NAME] shall maintain a vendor inventory (vendor register) that includes:

- Vendor name and primary contact
- Description of services provided
- Tier classification
- Types of data shared or accessible
- SOC 2/ISO 27001 report status and expiration dates
- Contract effective date and renewal date
- Date of last security assessment
- Date of next scheduled review
- Risk rating and any open findings
- Data processing agreement status

The vendor inventory shall be reviewed and updated at least quarterly.

### 4.4 Ongoing Monitoring

- **Tier 1 vendors** shall be reviewed annually. Reviews include requesting updated SOC 2 reports, reviewing any disclosed incidents, assessing performance against SLAs, and confirming that contractual security requirements continue to be met.
- **Tier 2 vendors** shall be reviewed every 2 years or upon contract renewal.
- **Ad hoc reviews** shall be triggered by:
  - A vendor-reported security incident
  - Public disclosure of a breach involving the vendor
  - Significant changes to the vendor's services or subprocessors
  - Changes in the data shared with the vendor
  - Concerns raised by any [COMPANY_NAME] employee regarding vendor security

### 4.5 Vendor Access Controls

- Vendor access to [COMPANY_NAME] systems must follow the Access Control Policy: named accounts, MFA, least privilege, and time-limited access.
- Shared credentials with vendors are prohibited.
- Vendor access to production systems must be logged and monitored.
- Vendor access must be revoked promptly upon termination of the vendor relationship or completion of the engagement.

### 4.6 Subprocessor Management

- Tier 1 vendors must disclose all subprocessors that handle [COMPANY_NAME] data.
- [COMPANY_NAME] reserves the right to object to subprocessors that do not meet its security requirements.
- Vendors must notify [COMPANY_NAME] before engaging new subprocessors that will access [COMPANY_NAME] data, with reasonable advance notice (minimum 30 days).

### 4.7 Vendor Offboarding

When a vendor relationship is terminated:

1. Confirm all [COMPANY_NAME] data has been returned or securely deleted, and obtain written certification of deletion.
2. Revoke all vendor access to [COMPANY_NAME] systems.
3. Remove the vendor's API keys, credentials, and integrations.
4. Update the vendor inventory to reflect the terminated status.
5. Retain vendor assessment records for a minimum of 3 years for audit purposes.

## 5. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Security Lead** | Maintain vendor assessment process and questionnaires; conduct or oversee security assessments; maintain the vendor inventory; review SOC 2 reports and assessment results; approve Tier 1 vendor engagements from a security perspective. |
| **Procurement / Finance** | Coordinate vendor selection process; ensure contracts include required security provisions; manage contract renewals; track vendor spend. |
| **Legal** | Review and negotiate vendor contracts, DPAs, and security addenda; advise on regulatory data handling requirements; ensure contractual protections are adequate. |
| **System Owners / Business Sponsors** | Identify the need for new vendors; define the business requirements; serve as the primary relationship manager; participate in vendor reviews; classify the vendor tier based on data access and criticality. |
| **IT/Engineering** | Provision and manage vendor access; monitor vendor integrations; implement technical controls for vendor connectivity; support vendor offboarding. |

## 6. Exceptions

Exceptions to vendor assessment requirements must be documented, approved by the Security Lead, and tracked in the risk register. Emergency vendor engagements (e.g., incident response retainers activated during an active incident) may proceed with abbreviated due diligence, but a full assessment must be completed within 30 days.

## 7. Review Cadence

This policy shall be reviewed **annually** or upon:

- Major vendor security incidents affecting [COMPANY_NAME]
- Changes to regulatory requirements for vendor management
- Significant changes to [COMPANY_NAME]'s vendor landscape
- Audit findings related to vendor management

## 7. Related Policies

- [Information Security Policy](information-security-policy.md)
- [Data Classification Policy](data-classification-policy.md)
- [Risk Management Policy](risk-management-policy.md)

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC9.2 | Assesses and Manages Risks Associated with Vendors and Business Partners |
| SOC 2 | CC3.2 | Identifies and Assesses Risks |
| SOC 2 | CC2.3 | Communicates with Third Parties |
| ISO 27001 | A.5.19 | Information Security in Supplier Relationships |
| ISO 27001 | A.5.20 | Addressing Information Security within Supplier Agreements |
| ISO 27001 | A.5.21 | Managing Information Security in the ICT Supply Chain |
| ISO 27001 | A.5.22 | Monitoring, Review, and Change Management of Supplier Services |
| ISO 27001 | A.5.23 | Information Security for Use of Cloud Services |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. Assess your cloud vendor security posture with the free [Cloud Security Posture Check](https://traztech.ca/tools/cloud-security-posture-check).*
