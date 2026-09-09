# Encryption Policy

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

This Encryption Policy defines [COMPANY_NAME]'s requirements for the use of cryptographic controls to protect the confidentiality and integrity of data at rest, in transit, and in use. It establishes approved cryptographic algorithms, key management practices, and implementation standards to ensure that encryption is applied consistently and effectively across all systems that handle sensitive data.

Encryption is not a checkbox: it is a foundational control. Improperly implemented encryption (weak algorithms, poor key management, unencrypted backups) provides a false sense of security that is worse than no encryption claim at all.

## 2. Scope

This policy applies to:

- All data classified as Restricted or Confidential per the Data Classification Policy
- All systems that store, process, or transmit [COMPANY_NAME] data, including production infrastructure, databases, file storage, endpoints, backups, and SaaS applications
- All encryption keys, certificates, and cryptographic materials managed by or on behalf of [COMPANY_NAME]
- All personnel responsible for implementing, managing, or configuring cryptographic controls

## 3. Policy Statements

### 3.1 Encryption at Rest

All data classified as Restricted or Confidential must be encrypted at rest. Encryption at rest requirements:

| Storage Type | Requirement | Minimum Standard |
|---|---|---|
| **Databases (production)** | Mandatory | AES-256 (or AES-128 minimum). Transparent data encryption (TDE) or volume-level encryption. |
| **Object storage / file storage** | Mandatory for Restricted and Confidential data | AES-256 server-side encryption. Customer-managed keys (CMK) preferred for Restricted data. |
| **Backups** | Mandatory | AES-256. Backup encryption keys must be stored separately from primary keys. |
| **Endpoints (laptops, mobile devices)** | Mandatory for all company devices | Full-disk encryption: BitLocker (Windows), FileVault (macOS), LUKS (Linux). |
| **Removable media** | Mandatory if used to transport sensitive data (discouraged) | AES-256 encrypted containers or hardware-encrypted drives. |
| **SaaS applications** | Required for Tier 1 vendors handling Restricted data | Vendor must provide encryption at rest; verify via SOC 2 report or security documentation. |
| **Development and staging** | Mandatory if containing production-equivalent data | Same standard as production. |

### 3.2 Encryption in Transit

All data transmitted over networks must be encrypted in transit:

| Transport Type | Requirement | Minimum Standard |
|---|---|---|
| **Web traffic (HTTPS)** | Mandatory for all services | TLS 1.2 minimum; TLS 1.3 preferred. SSL and TLS 1.0/1.1 are prohibited. |
| **API communications** | Mandatory | TLS 1.2+. Mutual TLS (mTLS) recommended for service-to-service communication. |
| **Email** | Mandatory for Restricted data; recommended for all | TLS for transport (opportunistic TLS minimum, enforced TLS for sensitive communications). S/MIME or PGP for end-to-end encryption of Restricted data. |
| **File transfers** | Mandatory | SFTP, SCP, or HTTPS. FTP is prohibited. |
| **VPN** | Mandatory for remote access | IPsec or WireGuard with AES-256 or ChaCha20. PPTP is prohibited. |
| **Internal service communication** | Mandatory in production | TLS 1.2+ between services. Unencrypted internal traffic in production is prohibited. |
| **Database connections** | Mandatory | TLS-encrypted connections; reject unencrypted connections in production. |

### 3.3 Approved Cryptographic Algorithms

[COMPANY_NAME] approves the following cryptographic algorithms. Use of algorithms not on this list requires Security Lead approval:

**Symmetric Encryption:**
| Algorithm | Key Length | Status | Use Case |
|---|---|---|---|
| AES | 256-bit | Approved (preferred) | Data at rest, data in transit |
| AES | 128-bit | Approved | Acceptable where 256-bit is not supported |
| ChaCha20-Poly1305 | 256-bit | Approved | Alternative to AES for data in transit |

**Asymmetric Encryption:**
| Algorithm | Key Length | Status | Use Case |
|---|---|---|---|
| RSA | 2048-bit minimum; 4096-bit preferred | Approved | Key exchange, digital signatures |
| ECDSA | P-256 minimum; P-384 preferred | Approved | Digital signatures, TLS |
| Ed25519 | 256-bit | Approved (preferred) | SSH keys, digital signatures |
| X25519 | 256-bit | Approved | Key agreement |

**Hashing:**
| Algorithm | Status | Use Case |
|---|---|---|
| SHA-256 | Approved | General-purpose hashing, integrity verification |
| SHA-384 / SHA-512 | Approved | Higher-security hashing requirements |
| SHA-3 | Approved | Alternative to SHA-2 family |
| bcrypt | Approved | Password hashing (cost factor 12+) |
| Argon2id | Approved (preferred) | Password hashing |
| PBKDF2 | Approved | Password hashing (minimum 600,000 iterations with SHA-256) |

**Prohibited Algorithms:**
| Algorithm | Reason |
|---|---|
| DES, 3DES | Insufficient key length; known vulnerabilities |
| RC4 | Known biases and vulnerabilities |
| MD5 | Collision attacks; broken for security purposes |
| SHA-1 | Collision attacks demonstrated; deprecated |
| RSA < 2048-bit | Insufficient key length |
| SSL 2.0/3.0, TLS 1.0/1.1 | Known vulnerabilities (POODLE, BEAST, etc.) |

### 3.4 TLS Configuration

- All externally facing services must support TLS 1.3 and accept TLS 1.2 as a minimum.
- Cipher suite configuration must prioritize forward secrecy (ECDHE or DHE key exchange).
- Weak cipher suites (NULL, export, anonymous, RC4, DES, 3DES) must be disabled.
- HSTS (HTTP Strict Transport Security) must be enabled on all web-facing services with a minimum max-age of 1 year and includeSubDomains.
- TLS certificates must be obtained from a trusted Certificate Authority (CA). Self-signed certificates are prohibited in production.
- TLS certificates must use RSA 2048-bit or ECDSA P-256 keys at minimum.
- Certificate expiration must be monitored. Certificates must be renewed before expiration, with automated renewal preferred (e.g., Let's Encrypt, ACM).

### 3.5 Key Management

Effective encryption depends entirely on proper key management. Keys that are poorly stored, never rotated, or widely shared negate the protection encryption provides.

#### 3.5.1 Key Generation

- Cryptographic keys must be generated using cryptographically secure random number generators (CSPRNG) provided by the operating system, hardware security module (HSM), or cloud KMS.
- Key generation must not rely on user-provided seeds, predictable values, or weak entropy sources.

#### 3.5.2 Key Storage

- Encryption keys must be stored in a dedicated key management system (KMS) or secrets management system:
  - Cloud KMS (AWS KMS, GCP KMS, Azure Key Vault) for cloud-hosted encryption keys
  - Hardware Security Modules (HSMs) for the highest-sensitivity keys
  - Secrets management tools (HashiCorp Vault, AWS Secrets Manager) for application secrets and API keys
- Encryption keys must **never** be:
  - Stored in source code or version control
  - Stored in plain text on disk or in configuration files
  - Transmitted via email, chat, or other unencrypted channels
  - Stored alongside the data they protect (the key and the locked box must be in different places)
- Access to key management systems must be restricted to authorized personnel and follow the Access Control Policy.

#### 3.5.3 Key Rotation

| Key Type | Rotation Frequency | Trigger for Immediate Rotation |
|---|---|---|
| Master encryption keys (KMS) | Annually | Suspected compromise |
| Data encryption keys (DEK) | Annually (or per cloud provider's automatic rotation) | Suspected compromise |
| TLS certificates | Before expiration (automated preferred) | Suspected compromise of private key |
| SSH keys | Annually | Personnel departure, suspected compromise |
| API keys and tokens | Every 90 days | Personnel departure, suspected compromise |
| Signing keys | Annually | Suspected compromise |

- Key rotation must be performed without service disruption. Systems must support decryption with both old and new keys during rotation periods.
- Retired keys must be archived (not deleted) for the duration required to decrypt data encrypted under those keys, and must be protected with the same controls as active keys.

#### 3.5.4 Key Revocation and Destruction

- Compromised keys must be revoked immediately and replaced.
- When keys are no longer needed (all data encrypted under the key has been re-encrypted or deleted), keys shall be securely destroyed using methods that prevent recovery.
- Key destruction must be documented with the key identifier, destruction date, method, and authorizing personnel.

#### 3.5.5 Key Backup and Recovery

- Master keys and critical encryption keys must be backed up in a secure, geographically separate location.
- Key backup and recovery procedures must be tested at least annually.
- Key recovery must require multi-person authorization (split knowledge or dual control) for master keys and keys protecting Restricted data.

### 3.6 Certificate Management

- [COMPANY_NAME] shall maintain an inventory of all TLS/SSL certificates, including: domain, issuing CA, expiration date, key type and length, and responsible team.
- Certificate expiration alerts must be configured to notify the responsible team at least 30 days before expiration.
- Wildcard certificates should be used sparingly and only where justified. Prefer individual certificates to limit blast radius of compromise.
- Certificate pinning should be avoided for web applications (it can cause outages) but may be considered for mobile applications or high-security API integrations.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Security Lead** | Maintain this policy; approve cryptographic standards and exceptions; oversee key management practices; review encryption configurations; coordinate certificate management. |
| **Engineering / DevOps** | Implement encryption controls in applications and infrastructure; configure TLS settings; manage secrets in approved secrets management systems; implement automated certificate renewal. |
| **System Owners** | Ensure their systems comply with encryption requirements; verify encryption at rest and in transit for data they are responsible for; participate in key rotation and certificate renewal for their systems. |
| **Cloud/Platform Engineers** | Configure and manage cloud KMS settings; implement encryption at the infrastructure layer; monitor encryption compliance across cloud resources. |
| **All Developers** | Never hardcode secrets or keys in source code; use approved libraries and algorithms; follow secure coding practices for cryptographic operations. |

## 5. Compliance Verification

- Encryption compliance shall be verified through:
  - Automated scanning of TLS configurations (e.g., SSL Labs, testssl.sh) on a quarterly basis
  - Infrastructure-as-code checks for encryption-at-rest settings
  - Code review checks for hardcoded secrets (SAST tooling)
  - Periodic review of key management system access logs
  - Annual review of certificate inventory

## 6. Exceptions

Exceptions to this policy (e.g., use of a non-approved algorithm required by a legacy system or third-party integration) must be documented with a risk assessment, approved by the Security Lead, time-limited, and tracked in the risk register with compensating controls.

## 7. Review Cadence

This policy shall be reviewed **annually** or upon:

- Publication of new cryptographic vulnerabilities or algorithm deprecations
- Changes to regulatory requirements affecting encryption
- Introduction of new systems or data types requiring encryption
- Audit findings related to cryptographic controls

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC6.1 | Logical and Physical Access Controls |
| SOC 2 | CC6.7 | Restricts Transmission, Movement, and Removal of Information |
| ISO 27001 | A.8.24 | Use of Cryptography |
| ISO 27001 | A.5.14 | Information Transfer |
| ISO 27001 | A.8.9 | Configuration Management |

---

*Template provided by [TrazTech](https://traztech.ca): Security & Compliance Consultancy, Toronto. Assess your cloud encryption posture with the free [Cloud Security Posture Check](https://traztech.ca/tools/cloud-security-posture-check).*
