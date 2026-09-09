# Access Control Policy

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

This Access Control Policy defines how [COMPANY_NAME] manages logical access to information systems, applications, data, and infrastructure. It establishes the principles of least privilege, role-based access control (RBAC), segregation of duties, and multi-factor authentication to ensure that only authorized individuals access only the resources they need, for only as long as they need them.

Poorly managed access is the most common root cause of data breaches. This policy exists to prevent unauthorized access, reduce insider risk, and provide auditable evidence that access controls are operating effectively.

## 2. Scope

This policy applies to:

- All [COMPANY_NAME] information systems, including production infrastructure, SaaS applications, internal tools, code repositories, CI/CD pipelines, cloud platforms, and databases
- All user accounts, including employee accounts, contractor accounts, service accounts, shared accounts, and API keys
- All access methods, including interactive login, API access, SSH, VPN, and remote desktop
- All personnel, including employees, contractors, consultants, and third-party vendors with access to [COMPANY_NAME] systems

## 3. Policy Statements

### 3.1 Principle of Least Privilege

- All access shall be granted based on the principle of least privilege: users receive the minimum level of access required to perform their job functions, and no more.
- Default access for new accounts shall be restricted. Access to sensitive systems, production environments, customer data, and administrative functions must be explicitly requested, justified, and approved.
- Broad or unrestricted access (e.g., wildcard permissions, root/admin by default) is prohibited unless there is a documented and approved business justification.

### 3.2 Role-Based Access Control (RBAC)

- [COMPANY_NAME] shall define and maintain a set of standard roles that map to job functions. Each role defines a set of permissions appropriate to that function.
- Access shall be assigned based on roles rather than on an individual basis wherever technically feasible.
- The role catalog shall be reviewed and updated at least semi-annually to ensure it reflects current organizational structure and job functions.
- Standard roles shall include, at minimum:
  - **Read-Only/Viewer:** Can view but not modify data or configurations
  - **Contributor/Editor:** Can create and modify data within defined boundaries
  - **Administrator:** Can manage users, configurations, and system settings for a specific service
  - **Super Administrator/Root:** Unrestricted access; limited to the fewest possible individuals with documented justification

### 3.3 Access Request and Provisioning

- All access requests must be submitted through the organization's access request process (ticketing system or IT workflow).
- Each access request must include:
  - The system or resource being requested
  - The level of access or role being requested
  - The business justification for the access
  - The expected duration (permanent or time-limited)
- Access requests must be approved by:
  - The employee's direct manager (for standard access)
  - The system owner AND the Security Lead (for privileged or administrative access)
  - The Security Lead AND executive leadership (for access to production customer data)
- Access shall be provisioned within 1 business day of approval for standard requests and within 2 business days for privileged access requests.

### 3.4 Authentication Requirements

#### 3.4.1 Multi-Factor Authentication (MFA)

MFA is **mandatory** for the following:

- All access to production infrastructure and cloud management consoles (AWS, GCP, Azure)
- All access to source code repositories
- All access to the identity provider (IdP) and single sign-on (SSO) portal
- All remote access (VPN, remote desktop)
- All access to email and collaboration platforms
- All access to financial systems and HR systems
- All access to customer-facing admin portals
- All access to security tools (SIEM, endpoint management, vulnerability scanners)

Acceptable MFA methods, in order of preference:

1. Hardware security keys (FIDO2/WebAuthn) -- **required for administrative/privileged accounts**
2. Authenticator applications (TOTP) -- acceptable for standard accounts
3. Push-based authentication -- acceptable for standard accounts
4. SMS-based OTP -- **not accepted** due to known vulnerabilities (SIM swapping, interception)

#### 3.4.2 Password Requirements

For systems where passwords are used in conjunction with MFA:

- Minimum length: 12 characters
- No maximum length restriction below 128 characters
- Must not be present in known breach databases (checked at creation and rotation)
- Must not be a dictionary word or common pattern
- No mandatory complexity rules (uppercase/lowercase/special character requirements), consistent with NIST SP 800-63B guidance that length and breach-checking are more effective
- Passwords must be unique across all company accounts -- no reuse of passwords between services
- All personnel must use the company-approved password manager

#### 3.4.3 Service Accounts and API Keys

- Service accounts must be tied to a specific application or process, not to an individual.
- Each service account must have a designated human owner responsible for its lifecycle.
- Service account credentials must be stored in a secrets management system (e.g., AWS Secrets Manager, HashiCorp Vault, GCP Secret Manager) -- never in source code, configuration files, or environment variables committed to version control.
- API keys and service account credentials must be rotated at least every 90 days, or immediately upon suspected compromise.
- Service accounts must have the minimum permissions required for their specific function.

### 3.5 Privileged Access Management

- Administrative and privileged access shall be limited to the minimum number of individuals necessary to maintain operations.
- Privileged accounts must be separate from standard user accounts. Administrators must use their standard account for daily work and switch to their privileged account only when performing administrative tasks.
- All privileged access sessions shall be logged, including who accessed what, when, and what actions were performed.
- Where technically feasible, just-in-time (JIT) access shall be used for privileged operations: access is granted for a limited time window and automatically revoked after the task is completed.
- Emergency ("break glass") accounts shall exist for critical systems, stored securely with credentials sealed and monitored. Use of break-glass accounts must trigger an immediate alert and post-use review.

### 3.6 Access Reviews

- **Quarterly access reviews** shall be conducted for all production systems, cloud platforms, and systems containing customer data. System owners and managers shall verify that each user's access is still appropriate and necessary.
- **Semi-annual access reviews** shall be conducted for all other business systems.
- **Immediate review** shall be triggered upon role change, department transfer, or project completion.
- Access reviews must result in documented evidence of:
  - Who performed the review
  - Which accounts were reviewed
  - Which accounts were flagged for modification or removal
  - Actions taken on flagged accounts
  - Completion date
- Accounts belonging to terminated employees or completed contractors must be identified and confirmed disabled during each review cycle.

### 3.7 Access Revocation

- Access must be revoked **within 4 hours** of employment termination or contract completion for standard departures.
- Access must be revoked **immediately** (within 1 hour) for involuntary terminations, security-related departures, or any situation where there is risk of data exfiltration or sabotage.
- The offboarding checklist (maintained by HR and IT) must include revocation of access to all systems documented in the access inventory.
- Upon departure, the following must be completed:
  - Disable the user account in the identity provider (which cascades to SSO-connected applications)
  - Revoke VPN and remote access
  - Transfer ownership of shared resources (documents, code repositories, cloud resources)
  - Rotate any shared secrets or credentials the departing individual had access to
  - Recover company-owned devices and confirm remote wipe of BYOD devices with company data

### 3.8 Third-Party and Vendor Access

- Third-party and vendor access must be governed by written agreements specifying the scope, duration, and security requirements of access.
- Vendor access must be time-limited and scoped to the minimum systems necessary.
- All vendor access must use named accounts (no shared credentials) and MFA.
- Vendor access to production systems must be monitored and logged.
- Vendor access must be reviewed at least annually or upon contract renewal.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Security Lead** | Define access control standards; approve privileged access requests; oversee access reviews; manage the identity provider and SSO configuration; investigate access-related incidents. |
| **System Owners** | Define roles and permissions for their systems; approve access requests for their systems; participate in quarterly access reviews; ensure their system enforces this policy. |
| **Managers** | Approve standard access requests for direct reports; participate in access reviews; notify IT promptly of role changes, transfers, and departures. |
| **IT/Engineering** | Provision and deprovision access; maintain identity provider and directory services; implement technical access controls; manage service accounts and API keys. |
| **HR** | Notify IT of new hires, transfers, and terminations in a timely manner; maintain the onboarding/offboarding checklist; ensure access revocation is completed for departing personnel. |
| **All Users** | Use access only as authorized; do not share credentials; report unauthorized access or suspicious activity to [SECURITY_TEAM_EMAIL]; lock devices when unattended. |

## 5. Exceptions

Exceptions to this policy (e.g., temporary use of shared accounts during system migration, temporary elevation of privileges for a project) must be:

1. Documented with a business justification
2. Approved by the Security Lead
3. Time-limited (maximum 30 days, renewable with re-approval)
4. Logged in the risk register with compensating controls
5. Reviewed upon expiration

## 6. Review Cadence

This policy shall be reviewed **annually** or upon:

- Changes to the identity provider or authentication infrastructure
- Significant changes to the organizational structure
- Security incidents related to unauthorized access
- Changes in regulatory or compliance requirements

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC6.1 | Logical and Physical Access Controls -- Implements Logical Access Security |
| SOC 2 | CC6.2 | Prior to Issuing System Credentials, Registers and Authorizes New Users |
| SOC 2 | CC6.3 | Authorizes, Modifies, or Removes Access Based on Authorization |
| SOC 2 | CC6.5 | Restricts Registration and Devices to Authorized Individuals |
| SOC 2 | CC6.6 | Restricts Access to System and Data Based on Need |
| ISO 27001 | A.5.15 | Access Control |
| ISO 27001 | A.5.16 | Identity Management |
| ISO 27001 | A.5.17 | Authentication Information |
| ISO 27001 | A.5.18 | Access Rights |
| ISO 27001 | A.8.2 | Privileged Access Rights |
| ISO 27001 | A.8.3 | Information Access Restriction |
| ISO 27001 | A.8.4 | Access to Source Code |
| ISO 27001 | A.8.5 | Secure Authentication |

---

*Template provided by [TrazTech](https://traztech.ca) -- Security & Compliance Consultancy, Toronto. For guidance on preventing control drift in access reviews, read [Control Drift Between Audits](https://traztech.ca/blog/control-drift-between-audits).*
