# Change Management Policy

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

This Change Management Policy defines how [COMPANY_NAME] manages changes to information systems, applications, infrastructure, and configurations. It establishes requirements for the software development lifecycle (SDLC), code review, testing, approval, and deployment to ensure that changes are authorized, tested, and traceable, and that they do not introduce unacceptable risk to the confidentiality, integrity, or availability of systems and data.

Uncontrolled changes are a leading cause of outages and security incidents. This policy exists to balance the speed startups need with the controls auditors expect.

## 2. Scope

This policy applies to:

- All changes to production systems, including application code, infrastructure, configurations, database schemas, network settings, and security controls
- All changes to staging and pre-production environments that mirror production
- All changes to SaaS configurations and third-party integrations that affect security posture
- All personnel who develop, test, review, approve, or deploy changes, including employees, contractors, and third-party developers

**Out of scope:** Changes to local development environments that do not affect shared or production systems.

## 3. Policy Statements

### 3.1 Change Categories

All changes shall be classified into one of the following categories:

| Category | Description | Approval | Lead Time |
|---|---|---|---|
| **Standard** | Routine changes with well-understood risk (e.g., application feature deployments, dependency updates, minor configuration changes). Pre-approved when following the standard CI/CD pipeline. | Peer code review + automated checks | Normal release cycle |
| **Significant** | Changes with elevated risk or broader impact (e.g., infrastructure migrations, new third-party integrations, database schema changes, security control modifications). | Peer code review + Engineering Lead approval + Security review where applicable | Minimum 24 hours before deployment |
| **Emergency** | Changes required to resolve active incidents, outages, or critical security vulnerabilities. | Post-deployment review required within 48 hours. Verbal or Slack approval from Engineering Lead is sufficient during the incident. | Immediate |

### 3.2 Software Development Lifecycle (SDLC)

[COMPANY_NAME] follows a secure SDLC process that incorporates security at each phase:

1. **Requirements:** Security requirements are identified alongside functional requirements. Data classification and access control needs are defined before development begins.

2. **Design:** System and feature designs are reviewed for security implications. Threat modeling is performed for features that handle sensitive data, authentication, authorization, or integrate with external systems.

3. **Development:**
   - All code is written in accordance with secure coding practices (OWASP Top 10 mitigation, input validation, parameterized queries, output encoding).
   - Secrets, credentials, and API keys are never hardcoded in source code. Secrets must be managed through the approved secrets management system.
   - Dependencies are tracked and monitored for known vulnerabilities using automated dependency scanning (e.g., Dependabot, Snyk, Renovate).

4. **Testing:**
   - All changes must pass automated test suites (unit tests, integration tests) before merge.
   - Static application security testing (SAST) shall be integrated into the CI pipeline.
   - Dynamic application security testing (DAST) shall be performed on a regular cadence (at minimum, quarterly) against staging environments.
   - Penetration testing shall be conducted at least annually by a qualified third party.

5. **Deployment:** Governed by the deployment controls in Section 3.5.

6. **Maintenance:** Ongoing monitoring, patching, and vulnerability management as defined in the Logging and Monitoring Policy.

### 3.3 Code Review Requirements

- **All changes to production code must be reviewed by at least one qualified peer** before merge. Self-approvals are not permitted.
- Code reviews must be conducted via pull request (or equivalent) in the version control system, providing an auditable record of the review.
- Reviewers must assess:
  - Correctness and logic
  - Security implications (injection risks, authentication/authorization changes, data exposure)
  - Test coverage
  - Compliance with coding standards
  - Proper handling of secrets and sensitive data
- Reviews must be completed and approved before the change is merged to the main branch.
- For significant changes (as defined in Section 3.1), the reviewer should include someone with security expertise or knowledge of the affected system's security architecture.

### 3.4 Version Control

- All application source code, infrastructure-as-code (IaC), and configuration files must be stored in the organization's approved version control system.
- The main/production branch must be protected:
  - Direct commits to the main branch are prohibited
  - Merges require at least one approved review
  - Force pushes to the main branch are prohibited
  - Status checks (CI pipeline, tests, security scans) must pass before merge is allowed
- Meaningful commit messages are required. Commits must reference the relevant ticket or issue number.
- Code signing is recommended for production deployments and required for releases that are distributed to customers.

### 3.5 Deployment Controls

- Production deployments must be performed through the automated CI/CD pipeline. Manual deployments to production are prohibited except during approved emergency changes.
- The CI/CD pipeline must enforce:
  - Automated build and compilation
  - Automated test execution (unit, integration)
  - Security scanning (SAST, dependency scanning)
  - Artifact signing or integrity verification
  - Deployment to staging for validation before production
- Production deployments must be logged with: who initiated the deployment, what was deployed (commit hash or artifact version), when it was deployed, and the outcome (success/failure).
- Rollback procedures must exist and be tested. The team must be able to revert to the previous known-good state within 30 minutes.

### 3.6 Environment Separation

- [COMPANY_NAME] shall maintain separate environments for development, staging/testing, and production.
- Production data must not be used in development or testing environments unless it has been anonymized or pseudonymized and approved by the Security Lead.
- Access to production environments shall be restricted to authorized personnel, separate from development access, as defined in the Access Control Policy.
- Configuration differences between environments must be managed through environment-specific configuration files or variables, not through code changes.

### 3.7 Infrastructure Changes

- Changes to infrastructure (cloud resources, network configurations, DNS, load balancers, firewalls) must follow the same approval and review process as application changes.
- Infrastructure must be managed as code (IaC) wherever feasible, using tools such as Terraform, CloudFormation, Pulumi, or equivalent.
- Infrastructure changes must be tested in a non-production environment before applying to production.
- Configuration drift detection shall be implemented to identify unauthorized or unplanned changes to production infrastructure.

### 3.8 Emergency Changes

- Emergency changes are permitted only to resolve active incidents, critical outages, or security vulnerabilities being actively exploited.
- Emergency changes must still be:
  - Logged in the version control system
  - Documented in the incident ticket
  - Reviewed post-deployment within 48 hours
- The post-deployment review must include: description of the change, reason it was classified as emergency, who approved it, whether it followed secure coding practices, and any follow-up actions needed.
- If the emergency change bypassed normal review, a full code review must be completed retroactively, and any necessary corrections must be applied.

### 3.9 Database Changes

- Database schema changes (migrations) must be version-controlled and applied through automated migration tools.
- Destructive database changes (dropping tables, columns, or modifying data types) require approval from the Engineering Lead and must be tested against a copy of production data in a non-production environment.
- Direct SQL execution against production databases is prohibited except during approved emergency changes, and all such access must be logged.

### 3.10 Patch Management

- Security patches for operating systems, frameworks, libraries, and dependencies shall be applied according to the following timelines:
  - **Critical (CVSS 9.0+):** Within 72 hours of patch availability, or immediately if actively exploited
  - **High (CVSS 7.0-8.9):** Within 14 days
  - **Medium (CVSS 4.0-6.9):** Within 30 days
  - **Low (CVSS 0.1-3.9):** Within 90 days or at the next scheduled maintenance window
- Patch compliance shall be tracked and reported monthly.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Engineering Lead / CTO** | Approve significant changes; ensure SDLC processes are followed; maintain CI/CD pipeline; oversee environment separation; approve emergency changes. |
| **Security Lead** | Review changes with security implications; maintain SAST/DAST tooling; approve changes to security controls; conduct or coordinate penetration testing; review emergency changes post-deployment. |
| **Developers** | Follow secure coding practices; write and maintain tests; submit changes via pull request; participate in code reviews; respond to security findings in their code. |
| **Code Reviewers** | Review submitted changes for correctness, security, and quality; approve or request changes; document review findings in the pull request. |
| **DevOps/Platform Engineers** | Maintain CI/CD pipelines and deployment automation; manage infrastructure as code; enforce environment separation; maintain rollback capabilities. |
| **All Change Initiators** | Classify changes appropriately; provide sufficient context for review; verify changes in staging before promoting to production; monitor deployments for issues. |

## 5. Change Records and Audit Trail

- All changes must produce an auditable record that includes:
  - Description of the change
  - Requester and approver
  - Date and time of the change
  - Systems affected
  - Review and approval evidence (pull request link, approval comments)
  - Deployment record (CI/CD pipeline run, deployment log)
  - Test results
- Change records shall be retained for a minimum of 3 years for audit purposes.

## 6. Exceptions

Exceptions to this policy must be documented, justified, and approved by the Engineering Lead and Security Lead. Exceptions are time-limited and tracked in the risk register.

## 7. Review Cadence

This policy shall be reviewed **annually** or upon:

- Significant changes to the development process or toolchain
- Major incidents caused by change-related failures
- Audit findings related to change management
- Changes to compliance requirements

## 7. Related Policies

- [Information Security Policy](information-security-policy.md)
- [Access Control Policy](access-control-policy.md)
- [Logging and Monitoring Policy](logging-monitoring-policy.md)

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC8.1 | Authorizes, Designs, Develops, Configures, Documents, Tests, Approves, and Implements Changes |
| SOC 2 | CC7.1 | Monitors Infrastructure and Software for Vulnerabilities |
| SOC 2 | CC6.1 | Logical and Physical Access Controls |
| ISO 27001 | A.8.9 | Configuration Management |
| ISO 27001 | A.8.25 | Secure Development Life Cycle |
| ISO 27001 | A.8.26 | Application Security Requirements |
| ISO 27001 | A.8.27 | Secure System Architecture and Engineering Principles |
| ISO 27001 | A.8.28 | Secure Coding |
| ISO 27001 | A.8.29 | Security Testing in Development and Acceptance |
| ISO 27001 | A.8.30 | Outsourced Development |
| ISO 27001 | A.8.31 | Separation of Development, Test, and Production Environments |
| ISO 27001 | A.8.32 | Change Management |
| ISO 27001 | A.8.33 | Test Information |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. For guidance on maintaining evidence of change management controls between audits, read [Keeping Evidence Fresh](https://traztech.ca/blog/keeping-evidence-fresh).*
