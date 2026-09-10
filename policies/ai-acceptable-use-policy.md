# AI Acceptable Use Policy

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

This AI Acceptable Use Policy establishes rules and expectations for how [COMPANY_NAME] personnel use artificial intelligence (AI) tools, including large language models, code generation assistants, and other AI-powered services. The goal is to enable teams to benefit from AI productivity gains while protecting customer data, intellectual property, and compliance obligations.

AI tools introduce new categories of risk that traditional acceptable use policies do not adequately address: data leakage through prompts, over-reliance on AI-generated outputs, shadow AI adoption, and evolving regulatory expectations. This policy provides clear boundaries so employees can use AI confidently and responsibly.

## 2. Scope

This policy applies to:

- All employees, contractors, consultants, temporary workers, and interns of [COMPANY_NAME]
- All AI tools used in connection with [COMPANY_NAME] business, whether company-provided or personally accessed
- AI services accessed via web interfaces, APIs, IDE plugins, browser extensions, mobile applications, or embedded features within other software
- AI-generated outputs used in [COMPANY_NAME] products, code, documentation, communications, or decision-making

## 3. Policy Statements

### 3.1 Approved and Prohibited AI Tools

- [COMPANY_NAME] maintains an **Approved AI Tools List** managed by the Security Lead in coordination with IT. Only tools on this list may be used for company business.
- The Approved AI Tools List shall specify, for each tool:
  - The tool name and vendor
  - Approved use cases
  - Data classification levels permitted as input
  - Any configuration requirements (e.g., enterprise plans with data retention opt-out, SSO enforcement)
  - The date of last security assessment
- Common AI tools that may be evaluated for approval include, but are not limited to: ChatGPT (OpenAI), Claude (Anthropic), GitHub Copilot, Google Gemini, Microsoft Copilot, and domain-specific AI tools relevant to [COMPANY_NAME]'s operations.
- **Prohibited tools:** AI tools not on the Approved AI Tools List are prohibited for company business. This includes free-tier consumer versions of AI services where enterprise data protection agreements are not in place.
- Employees who identify a business need for a new AI tool must submit a request through the IT procurement process. The tool will be evaluated per Section 3.6 before approval.

### 3.2 Data Classification Rules for AI Inputs

All data input to AI tools must comply with the Data Classification Policy. The following rules apply:

- **Restricted data** must **never** be input into any AI tool under any circumstances. This includes:
  - Customer personally identifiable information (PII)
  - Customer authentication credentials, tokens, or API keys
  - Payment card data
  - Health information (PHI)
  - Employee Social Security/Social Insurance numbers or financial account details
  - Encryption keys, secrets, or private certificates
- **Confidential data** must **not** be input into AI tools unless the tool has been explicitly approved for Confidential data handling on the Approved AI Tools List, with a data processing agreement (DPA) in place that prohibits the vendor from training on [COMPANY_NAME] inputs.
  - Source code may only be input into AI tools approved for code-level access (e.g., enterprise code assistants with appropriate contractual protections).
  - Source code containing hardcoded secrets, API keys, credentials, or environment-specific configuration must **never** be input into any AI tool.
  - Internal financial data, customer lists, and security configurations must not be input into AI tools.
- **Internal data** may be input into approved AI tools, subject to the tool's approved use cases.
- **Public data** may be input into any approved AI tool without restriction.

When in doubt about whether data may be input into an AI tool, employees must consult the Security Lead before proceeding.

### 3.3 AI-Generated Code Review Requirements

AI-generated code introduces risks including security vulnerabilities, license contamination, hallucinated dependencies, and logic errors. The following requirements apply:

- All AI-generated code must go through the same code review process as human-written code. AI generation does not reduce or bypass review requirements.
- Pull requests containing AI-generated or AI-assisted code must be identified as such in the PR description. Reviewers must be informed that AI assistance was used.
- Reviewers of AI-generated code must specifically verify:
  - No hardcoded credentials, secrets, or sensitive values were introduced
  - Dependencies referenced actually exist and are from legitimate packages (to prevent dependency confusion attacks)
  - The code does not introduce known vulnerability patterns (e.g., SQL injection, XSS, insecure deserialization)
  - License compatibility of any code patterns that may have been derived from training data
  - The logic is correct and the developer understands what the code does (not just that it compiles or passes tests)
- AI-generated code must not be merged without a human reviewer approving it. Automated approval of AI-generated code is prohibited.
- Security-critical code paths (authentication, authorization, cryptography, payment processing, data access layers) must receive additional scrutiny when AI-assisted, including review by a senior engineer or the Security Lead.

### 3.4 Shadow AI Policy

Shadow AI refers to the use of unapproved AI tools for company business, analogous to shadow IT.

- The use of unapproved AI tools for any [COMPANY_NAME] business purpose is prohibited. This includes:
  - Pasting company data into consumer AI chatbots
  - Using personal AI tool accounts for work tasks
  - Installing unapproved AI browser extensions, IDE plugins, or desktop applications
  - Using AI features embedded in unapproved software (e.g., AI summarization features in non-approved note-taking apps)
- Employees who discover colleagues using unapproved AI tools should report it to [SECURITY_TEAM_EMAIL]. Reports will be handled constructively; the goal is to identify unmet needs and provide approved alternatives, not to punish.
- IT shall implement technical controls where feasible to detect and block access to unapproved AI services, including DNS filtering, endpoint monitoring, and browser extension policies.
- Managers are responsible for ensuring their teams are aware of approved AI tools and are not using unapproved alternatives.

### 3.5 Vendor Assessment Requirements for AI Tools

AI tool vendors must be assessed before approval, following the Vendor Management Policy with the following additional AI-specific requirements:

- **Data handling and training:** The vendor must contractually commit that [COMPANY_NAME] inputs will not be used to train, fine-tune, or improve their models or any third-party models. Data processing agreements must explicitly address AI training exclusions.
- **Data residency and retention:** The vendor must disclose where data is processed and stored, and for how long inputs and outputs are retained. Retention periods must be minimized and aligned with [COMPANY_NAME]'s data retention requirements.
- **Sub-processors:** The vendor must disclose all sub-processors involved in handling [COMPANY_NAME] data, including cloud infrastructure providers and any third-party model providers.
- **Security posture:** The vendor must demonstrate appropriate security controls, evidenced by SOC 2 Type II report, ISO 27001 certification, or equivalent. Penetration test results should be reviewed where available.
- **Model transparency:** The vendor should provide information about model provenance, training data sourcing practices, and how they address intellectual property risks in model outputs.
- **Incident notification:** The vendor must commit to notifying [COMPANY_NAME] of security incidents, data breaches, or material changes to their data handling practices within contractually defined timeframes.
- **Enterprise configuration:** Where available, enterprise features must be enabled, including SSO integration, audit logging, data retention controls, and admin-level visibility into usage.
- AI tool assessments must be reviewed at least annually or when the vendor makes material changes to their service, model, or data handling practices.

### 3.6 Logging and Monitoring of AI Tool Usage

- [COMPANY_NAME] shall implement logging and monitoring of AI tool usage to the extent technically feasible and legally permissible:
  - Enterprise AI tool admin consoles shall be configured to retain usage logs, including user identity, timestamps, and usage volume.
  - Network-level monitoring shall track access to known AI service domains.
  - Endpoint monitoring shall detect installation of unapproved AI applications or browser extensions.
  - DLP controls shall be configured to detect and alert on potential transmission of Restricted or Confidential data to AI service endpoints.
- Logs of AI tool usage shall be retained for a minimum of 12 months.
- The Security Lead shall review AI tool usage patterns quarterly to identify:
  - Potential shadow AI usage
  - Unusual data volumes being sent to AI services
  - Compliance with approved use cases
  - Opportunities to expand or restrict approved tools based on actual usage

### 3.7 Responsible Use Guidelines

- Employees must not rely on AI-generated outputs as authoritative without independent verification. AI tools can produce plausible but incorrect information (hallucinations).
- AI-generated content used in customer-facing materials, legal documents, regulatory submissions, or security documentation must be reviewed for accuracy by a qualified human before publication or submission.
- Employees must not use AI tools to generate content that misrepresents its origin (e.g., presenting AI-generated analysis as original human research in contexts where the distinction matters).
- AI tools must not be used to make or justify decisions affecting individuals (hiring, performance evaluation, access decisions) without human oversight and accountability.
- Employees must not attempt to jailbreak, bypass safety filters, or extract training data from AI tools.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **All Users** | Comply with this policy; use only approved AI tools; verify AI outputs before use; report shadow AI usage and data handling concerns to [SECURITY_TEAM_EMAIL]; complete AI-specific security awareness training. |
| **Managers** | Ensure team awareness of approved AI tools and prohibited uses; monitor for shadow AI adoption; escalate requests for new AI tools through proper channels. |
| **Security Lead** | Maintain this policy and the Approved AI Tools List; conduct AI vendor security assessments; review AI usage logs; investigate policy violations; provide guidance on AI data handling questions. |
| **IT/Engineering** | Implement technical controls for AI tool management (SSO, DLP, network filtering, endpoint monitoring); provision approved AI tool licenses; maintain enterprise configurations. |
| **Legal** | Review AI vendor contracts and DPAs; advise on intellectual property implications of AI-generated outputs; monitor regulatory developments affecting AI use. |
| **Engineering Leads** | Enforce AI-generated code review requirements; ensure PR processes capture AI-assisted contributions; mentor teams on responsible AI use in development. |

## 5. Exceptions

Exceptions to this policy must be requested in writing to [SECURITY_TEAM_EMAIL] with:

- The specific policy requirement being excepted
- Business justification
- Duration of the exception
- Risk assessment, including data classification of any inputs involved
- Compensating controls in place

Exceptions must be approved by the Security Lead and are tracked in the risk register. Exceptions are time-limited and must be renewed if still needed at expiration.

## 6. Review Cadence

This policy shall be reviewed **semi-annually** due to the rapid evolution of AI technology and associated risks, or upon:

- Introduction of new AI tools or significant changes to existing approved tools
- Material changes in AI vendor data handling practices
- New regulatory requirements or industry guidance affecting AI use
- AI-related security incidents

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC1.4 | Demonstrates Commitment to Competence |
| SOC 2 | CC6.1 | Logical and Physical Access Controls |
| SOC 2 | CC6.7 | Restricts Transmission, Movement, and Removal of Information |
| ISO 27001 | A.5.10 | Acceptable Use of Information and Other Associated Assets |
| ISO 27001 | A.5.23 | Information Security for Use of Cloud Services |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. For guidance on managing AI tools within your compliance program, read [Control Drift Between Audits](https://traztech.ca/blog/control-drift-between-audits).*
