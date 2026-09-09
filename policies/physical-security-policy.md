# Physical Security Policy

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

This Physical Security Policy defines [COMPANY_NAME]'s requirements for protecting physical facilities, equipment, and information assets from unauthorized physical access, damage, theft, and environmental threats. Physical security is the often-overlooked counterpart to logical security -- the best firewall in the world does not help if someone walks into your office and takes a laptop with unencrypted customer data.

For organizations operating primarily in the cloud with remote workforces, physical security focuses on endpoint protection, device management, and reliance on cloud providers' physical security controls. This policy addresses both scenarios.

## 2. Scope

This policy applies to:

- All [COMPANY_NAME] office locations, including leased and owned spaces, coworking spaces, and shared office environments
- All data centers and server rooms operated by or on behalf of [COMPANY_NAME] (if applicable)
- All company-owned equipment, including laptops, mobile devices, monitors, networking equipment, and peripherals
- All remote work locations where [COMPANY_NAME] business is conducted
- All personnel, including employees, contractors, visitors, and third-party service providers who access [COMPANY_NAME] physical premises
- Cloud infrastructure providers' physical security (shared responsibility model)

## 3. Policy Statements

### 3.1 Office and Facility Security

#### 3.1.1 Physical Access Controls

- All [COMPANY_NAME] office spaces must have controlled entry using electronic badge access, key card, or equivalent access control system.
- Access badges/cards must be assigned to named individuals. Sharing of badges or access credentials is prohibited.
- Access to office spaces must be logged electronically, recording who entered, when, and through which access point.
- Access permissions must be based on role and business need. Not all employees require access to all areas (e.g., server rooms, executive offices, HR file storage areas).
- Doors to controlled areas must be self-closing and self-locking. Propping open secured doors is prohibited.
- Tailgating (following another person through a controlled door without badging in) is prohibited. Employees must challenge unfamiliar individuals in restricted areas.

#### 3.1.2 Visitor Management

- All visitors must be registered at reception upon arrival, including: visitor name, company affiliation, purpose of visit, host employee, date/time of arrival and departure.
- Visitors must be issued a visible visitor badge that is clearly distinguishable from employee badges.
- Visitors must be escorted by a [COMPANY_NAME] employee at all times while in controlled areas.
- Visitors must not be given unescorted access to areas where Restricted or Confidential data is accessible (screens, printed documents, whiteboards).
- Visitor logs must be retained for a minimum of 90 days.
- Visitors must return visitor badges upon departure.

#### 3.1.3 Secure Areas

If [COMPANY_NAME] maintains areas with heightened security requirements (server rooms, network closets, secure storage):

- Access to secure areas must be restricted to specifically authorized personnel.
- Secure areas must have separate access controls (additional badge access, key lock, or biometric) beyond the general office access.
- Entry to secure areas must be logged and monitored.
- No food, drink, or smoking in secure areas containing IT equipment.
- Secure areas must be locked when unoccupied.

#### 3.1.4 Surveillance

- Security cameras should be deployed at building entry/exit points, lobby/reception areas, and access points to secure areas.
- Camera footage must be retained for a minimum of 30 days.
- Camera systems must be maintained and regularly checked to ensure they are operational.
- Access to surveillance footage must be restricted to authorized security and management personnel.
- Signage must be posted to notify individuals that video surveillance is in operation, as required by applicable law.

### 3.2 Cloud and Colocation Data Centers

- [COMPANY_NAME] relies on cloud infrastructure providers (AWS, GCP, Azure, or equivalent) for production hosting. The physical security of cloud data centers is the responsibility of the cloud provider under the shared responsibility model.
- Cloud providers must maintain SOC 2 Type II or equivalent certification covering physical security controls. This must be verified during vendor assessment per the Vendor Management Policy.
- If [COMPANY_NAME] uses colocation facilities, the colocation provider's physical security controls must be assessed and must include at minimum: 24/7 manned security, biometric access controls, video surveillance, visitor escort policies, environmental controls, and power redundancy.
- [COMPANY_NAME] personnel accessing colocation facilities must follow the provider's access procedures and [COMPANY_NAME]'s Access Control Policy.

### 3.3 Equipment Security

#### 3.3.1 Endpoint Device Security

- All company-issued laptops and mobile devices must be configured with:
  - Full-disk encryption (FileVault, BitLocker, or LUKS)
  - Endpoint detection and response (EDR) agent
  - Automatic screen lock after 5 minutes of inactivity
  - Remote wipe capability
  - Automatic operating system and security updates
  - Company-managed device management (MDM) enrollment
- Company devices must not be left unattended in public spaces (airports, cafes, hotel lobbies, vehicles) or visible from outside vehicles.
- Lost or stolen devices must be reported to [SECURITY_TEAM_EMAIL] within 1 hour of discovery. IT will initiate a remote wipe upon report.
- Company equipment must not be lent to non-employees (family members, friends) without written approval from IT.

#### 3.3.2 Equipment Siting and Protection

- Workstations and displays must be positioned to prevent unauthorized viewing of screens by visitors, passersby, or surveillance from windows ("shoulder surfing").
- Privacy screens are recommended for employees who frequently work in open or public spaces.
- Networking equipment (routers, switches, wireless access points) must be physically secured and not accessible to unauthorized personnel.
- UPS (uninterruptible power supply) must be used for critical on-premises equipment (if applicable).

#### 3.3.3 Asset Tracking

- [COMPANY_NAME] shall maintain an inventory of all company-owned hardware assets, including:
  - Asset tag or serial number
  - Device type and model
  - Assigned user
  - Location
  - Encryption status
  - MDM enrollment status
- The hardware asset inventory must be reconciled at least annually.

### 3.4 Clean Desk and Clear Screen

- Employees must follow a clean desk practice: Restricted and Confidential documents must not be left on desks, printers, or common areas when the workspace is unattended.
- At the end of each workday or when leaving the workspace for an extended period, employees must:
  - Lock their computer screen
  - Store Restricted and Confidential paper documents in locked drawers or cabinets
  - Remove any sticky notes or printouts containing sensitive information
  - Clear whiteboards used for sensitive discussions
- Printers must be checked for uncollected printouts containing sensitive information. Secure print (pull printing) is recommended.

### 3.5 Remote Work Physical Security

For employees working remotely (home office, coworking spaces):

- The remote workspace must provide a reasonable level of privacy to prevent unauthorized persons from viewing screens or overhearing sensitive conversations.
- Company devices must be stored securely when not in use (locked room, locked drawer/cabinet).
- Employees must not use public or shared computers (library, internet cafe, hotel business center) to access [COMPANY_NAME] systems.
- Video calls involving Restricted or Confidential information should be taken in a private space. Virtual backgrounds or blurred backgrounds should be used when surroundings may reveal sensitive information.
- Home Wi-Fi networks must be secured with WPA3 or WPA2 encryption and a strong password. Default router passwords must be changed.

### 3.6 Secure Disposal and Reuse

- Company equipment being decommissioned, returned from departing employees, or transferred to another user must have all data securely erased before reuse or disposal.
- Data sanitization must follow NIST SP 800-88 guidelines:
  - **SSDs and flash storage:** Cryptographic erasure (destroy encryption keys) or manufacturer-provided secure erase
  - **HDDs:** Overwrite or degauss; physical destruction for drives that contained Restricted data
  - **Mobile devices:** Factory reset via MDM, confirmed cleared
- Equipment being disposed of (recycled, donated, or discarded) must have data sanitization verified and documented before leaving [COMPANY_NAME]'s custody.
- Paper documents containing Restricted or Confidential information must be cross-cut shredded or securely destroyed.

### 3.7 Environmental Controls

If [COMPANY_NAME] maintains on-premises IT equipment (server rooms, network closets):

- Fire detection and suppression systems must be installed and maintained per local building codes.
- Temperature and humidity must be monitored and maintained within acceptable ranges for IT equipment.
- Water leak detection should be deployed where IT equipment is located at risk of water damage (below bathrooms, near pipes, ground-floor flood risk).
- Emergency power (UPS, generator) must be available for critical equipment to allow graceful shutdown.

### 3.8 Cabling Security

- Network and power cabling for critical systems must be protected from physical damage, interception, and interference.
- Network cabling in shared or accessible areas should be enclosed in conduit or cable trays.
- Network ports in public areas (reception, conference rooms) must be disabled or on isolated VLANs.

## 4. Roles and Responsibilities

| Role | Responsibilities |
|---|---|
| **Security Lead** | Maintain this policy; oversee physical security assessments; manage visitor policy; coordinate with building management on facility security; manage endpoint security standards. |
| **IT / DevOps** | Manage endpoint device configuration and MDM; maintain the hardware asset inventory; execute data sanitization for decommissioned equipment; manage physical IT infrastructure. |
| **Office Manager / Facilities** | Manage badge access provisioning and revocation; maintain visitor logs; coordinate with building security; manage camera systems; ensure environmental controls. |
| **HR** | Coordinate badge provisioning during onboarding; ensure badge collection during offboarding; communicate clean desk policies. |
| **All Employees** | Comply with clean desk and clear screen policies; secure devices when unattended; report lost/stolen equipment immediately; challenge unfamiliar individuals in restricted areas; escort visitors. |
| **Managers** | Ensure team compliance with physical security policies; approve visitor access requests for their areas; report physical security concerns. |

## 5. Coworking and Shared Office Spaces

If [COMPANY_NAME] operates from a coworking or shared office space:

- The coworking provider's physical security controls must be assessed for adequacy (entry controls, surveillance, visitor management).
- [COMPANY_NAME] must maintain its own locked area (private office, locked cabinet) for sensitive equipment and documents if feasible.
- Clean desk policies are especially critical in shared environments.
- Employees must be vigilant about screen visibility and sensitive conversations in open areas.
- The shared responsibility for physical security must be documented.

## 6. Exceptions

Exceptions to physical security requirements must be documented with a risk assessment, approved by the Security Lead, and tracked in the risk register. Common exceptions include operating from coworking spaces without dedicated physical controls, which must be compensated with enhanced endpoint security and clean desk enforcement.

## 7. Review Cadence

This policy shall be reviewed **annually** or upon:

- Office moves, expansions, or changes to the physical workspace
- Security incidents involving physical access or device theft
- Changes to the remote work posture of the organization
- Audit findings related to physical security

---

## Compliance Mapping

| Framework | Control | Description |
|---|---|---|
| SOC 2 | CC6.4 | Restricts Physical Access to Facilities and Protected Information Assets |
| SOC 2 | CC6.5 | Restricts Registration and Devices to Authorized Individuals |
| ISO 27001 | A.7.1 | Physical Security Perimeters |
| ISO 27001 | A.7.2 | Physical Entry |
| ISO 27001 | A.7.3 | Securing Offices, Rooms, and Facilities |
| ISO 27001 | A.7.4 | Physical Security Monitoring |
| ISO 27001 | A.7.5 | Protecting against Physical and Environmental Threats |
| ISO 27001 | A.7.6 | Working in Secure Areas |
| ISO 27001 | A.7.7 | Clear Desk and Clear Screen |
| ISO 27001 | A.7.8 | Equipment Siting and Protection |
| ISO 27001 | A.7.9 | Security of Assets Off-Premises |
| ISO 27001 | A.7.10 | Storage Media |
| ISO 27001 | A.7.11 | Supporting Utilities |
| ISO 27001 | A.7.12 | Cabling Security |
| ISO 27001 | A.7.13 | Equipment Maintenance |
| ISO 27001 | A.7.14 | Secure Disposal or Re-Use of Equipment |

---

*Template provided by [TrazTech](https://traztech.ca) -- Security & Compliance Consultancy, Toronto. For a comprehensive readiness assessment, use the free [SOC 2 Readiness Checklist](https://traztech.ca/soc-2-readiness-checklist).*
