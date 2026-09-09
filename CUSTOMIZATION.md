# Customization Guide

This guide explains how to adapt each policy template to your organization. These templates are designed to be practical and audit-ready, but they must reflect your actual operating environment to pass auditor scrutiny.

> **Auditors do not want to see generic policies.** They want evidence that your policies describe what your organization actually does. A policy that claims 24/7 SOC monitoring when you have a three-person engineering team will raise more questions than it answers.

---

## General Customization Steps

### Step 1: Replace All Placeholders

Every template uses standardized placeholders enclosed in square brackets. Use your editor's find-and-replace to update them globally:

| Placeholder | What to Enter | Example |
|---|---|---|
| `[COMPANY_NAME]` | Your legal entity name | Acme SaaS Inc. |
| `[DATE]` | Policy effective date | 2026-01-15 |
| `[REVIEW_DATE]` | Next scheduled review | 2027-01-15 |
| `[POLICY_OWNER]` | Title of the person responsible | Chief Technology Officer |
| `[APPROVED_BY]` | Title of the approver | Chief Executive Officer |
| `[VERSION]` | Starting version number | 1.0 |
| `[COMPANY_DOMAIN]` | Your primary email/web domain | acme.com |
| `[SECURITY_TEAM_EMAIL]` | Security team distribution list | security@acme.com |
| `[INCIDENT_RESPONSE_EMAIL]` | IR notification address | incidents@acme.com |
| `[HR_CONTACT]` | HR department contact | hr@acme.com |
| `[LEGAL_CONTACT]` | Legal counsel contact | legal@acme.com |

### Step 2: Adjust Scope to Match Your Reality

Each policy has a **Scope** section. Tailor it to reflect:

- **Which systems are in scope.** If you only need SOC 2 for your production SaaS platform, say so. Do not claim your entire corporate network is covered unless it genuinely is.
- **Which personnel are covered.** Full-time employees, contractors, third-party vendors: be specific about who must comply.
- **Which locations apply.** Remote-first? Single office? Coworking space? Your physical security policy should match.

### Step 3: Align Timelines and SLAs to Your Capacity

Templates include suggested timelines (e.g., "respond to incidents within 1 hour," "review access quarterly"). Adjust these based on what your team can actually sustain. Auditors will ask for evidence that you met your own timelines: setting unrealistic targets creates audit findings.

### Step 4: Remove What Does Not Apply

If your organization does not have physical office space, you can simplify the Physical Security Policy to cover endpoint security and cloud datacenter reliance. If you do not process payment card data, you do not need PCI-specific controls in your Encryption Policy. Delete sections that do not apply rather than leaving them as aspirational statements.

### Step 5: Add What Is Missing

These templates cover the most common controls, but your organization may need additional sections for:

- Industry-specific regulations (HIPAA, PCI DSS, PIPEDA, GDPR)
- Customer contractual obligations
- Specific technology stacks (e.g., Kubernetes-specific deployment controls)

---

## Policy-Specific Customization Notes

### Information Security Policy
- Update the **risk appetite statement** to reflect your board's actual position. A seed-stage startup and a Series C company have very different risk tolerances.
- List your actual security leadership structure. If you do not have a CISO, name whoever holds that responsibility (CTO, VP Engineering, Head of Security).
- Reference your actual security tools and platforms in the supporting controls section.

### Acceptable Use Policy
- Tailor the acceptable and prohibited activities to your culture. A developer tools company may allow broader internet usage than a healthcare startup.
- Specify your actual BYOD stance: do you issue company devices, or do employees use personal laptops? The policy must match.
- Include your specific collaboration tools (Slack, Google Workspace, Microsoft 365) rather than generic references.

### Access Control Policy
- List your actual identity provider (Okta, Google Workspace, Azure AD, JumpCloud).
- Specify which systems require MFA and what MFA methods you accept (hardware keys, authenticator apps, SMS: be honest about your current state).
- Define your actual role hierarchy. If you use a flat structure with minimal RBAC, do not claim enterprise-grade role segregation.
- Set access review frequencies you can sustain. Quarterly reviews are standard; monthly may be aspirational.

### Change Management Policy
- Reference your actual CI/CD tools (GitHub Actions, GitLab CI, CircleCI, Jenkins).
- Describe your real code review requirements. If you require one reviewer, do not claim two.
- List your actual environments (development, staging, production) and the promotion process between them.
- Specify your deployment strategy (blue-green, canary, rolling, manual).

### Incident Response Policy
- Insert your actual escalation contacts and on-call rotation details.
- List the real communication channels you will use during incidents (Slack channel, PagerDuty, phone tree).
- Specify your regulatory notification obligations based on your jurisdiction and customer contracts (e.g., GDPR 72-hour notification, state breach notification laws).
- Reference your actual incident tracking system (Jira, Linear, PagerDuty).

### Data Classification Policy
- Adjust classification levels to your data landscape. A B2B SaaS company handling customer PII needs different categories than an infrastructure tools company.
- Map your actual data stores (databases, object storage, SaaS tools) to classification levels.
- Specify your real data retention periods based on legal requirements and business needs.

### Vendor Management Policy
- Set vendor tier thresholds that match your procurement reality. A startup spending $500/month on a tool has different due diligence needs than one signing a $500K annual contract.
- List the actual security certifications and reports you require from vendors (SOC 2, ISO 27001, penetration test reports).
- Define your vendor review cycle based on team capacity. Annual reviews are standard for critical vendors.

### Business Continuity Policy
- Set RTO and RPO values based on your actual architecture and customer SLAs. Do not claim a 15-minute RTO if your database restore takes 2 hours.
- Document your real backup strategy (frequency, storage location, encryption, testing schedule).
- List your actual critical systems and their dependencies.

### Encryption Policy
- Specify the encryption algorithms and key lengths you actually use (e.g., AES-256 for data at rest, TLS 1.2+ for data in transit).
- Document your actual key management approach (AWS KMS, GCP KMS, HashiCorp Vault, application-level).
- List which data stores are encrypted and how.

### Human Resources Security Policy
- Align onboarding and offboarding checklists with your actual IT provisioning process.
- Specify your real background check requirements (which roles, which checks, which provider).
- Reference your actual security awareness training platform (KnowBe4, Curricula, internal training).
- Set training frequency you will maintain: annual is standard, but new hires should complete training within their first week.

### Logging & Monitoring Policy
- Name your actual logging platform (Datadog, Splunk, CloudWatch, ELK stack).
- Specify real log retention periods based on your storage budget and compliance requirements (90 days active, 1 year archive is a common baseline).
- List the specific events you actually log (authentication events, API calls, admin actions, data access).
- Define your real alerting thresholds and on-call process.

### Physical Security Policy
- If you are fully remote with no office, focus this policy on endpoint security and state that production infrastructure runs in SOC 2-certified cloud datacenters.
- If you have office space, describe your actual physical controls (badge access, visitor logs, cameras).
- For coworking spaces, document the shared responsibility model with your space provider.

### Risk Management Policy
- Choose a risk scoring methodology your team understands and will use. A simple 5x5 likelihood-impact matrix works well for most startups.
- Populate the risk register template with your actual top risks, not hypothetical ones.
- Set a risk review cadence you will maintain. Quarterly is standard; tie it to your board meetings if possible.

---

## Version Control Best Practices

- Store policies in version control (this repo) alongside your code. Auditors appreciate seeing a full change history.
- Use meaningful commit messages when updating policies (e.g., "Update access control policy to require hardware MFA for admin accounts").
- Tag releases when policies are formally approved (e.g., `v1.0-approved-2026-01`).
- Reference TrazTech's guide on [keeping evidence fresh](https://traztech.ca/blog/keeping-evidence-fresh) for maintaining your evidence collection process alongside policy updates.

## Review Cadence

All policies should be reviewed at least annually, or upon:
- Significant organizational changes (acquisitions, new product lines, major headcount changes)
- Major security incidents
- Changes to applicable regulations or standards
- Changes to your technology stack or architecture

For guidance on building a sustainable review calendar, see TrazTech's post on [compliance calendar: what actually recurs](https://traztech.ca/blog/compliance-calendar-what-actually-recurs).

## Getting Help

If you need assistance customizing these policies for your specific audit or compliance program, [TrazTech](https://traztech.ca) offers hands-on SOC 2 readiness, ISO 27001 implementation, and compliance consulting. Start with the free [SOC 2 Readiness Checklist](https://traztech.ca/soc-2-readiness-checklist) to understand where you stand today.
