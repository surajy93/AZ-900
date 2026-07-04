# AZ-900 Notes: Azure Identity, Security & Microsoft Entra

## Azure Security Overview

Azure security follows the **Zero Trust** principle:

> **Never Trust, Always Verify**

Every user, device, and application must prove its identity before accessing resources.

Core security services:

- Microsoft Entra ID
- Single Sign-On (SSO)
- Multi-Factor Authentication (MFA)
- Conditional Access
- Role-Based Access Control (RBAC)
- Microsoft Defender for Cloud
- Azure Key Vault
- Encryption
- Defense in Depth

---

# Zero Trust Model

Zero Trust assumes that no user or device is trusted automatically.

Three Principles:

```text
Verify Explicitly

↓

Use Least Privilege

↓

Assume Breach
```

This means:

- Verify every login
- Give minimum permissions
- Monitor continuously

---

# End-to-End Zero Trust Scenario

## Scenario

Employee **Alice** wants to access the company's HR application from her laptop while working remotely.

Architecture

```text
Alice

↓

Microsoft Entra ID

↓

Single Sign-On

↓

Multi-Factor Authentication

↓

Conditional Access Policy

↓

Role-Based Access Control

↓

HR Application
```

---

## Step 1 – User Authentication

Alice enters:

- Username
- Password

Microsoft Entra ID verifies her identity.

---

## Step 2 – Single Sign-On (SSO)

Alice signs in **once**.

She can now access:

- Outlook
- Teams
- SharePoint
- Azure Portal
- HR Portal

without entering her password again.

Example

```text
Login Once

↓

Outlook

↓

Teams

↓

SharePoint

↓

Azure Portal
```

Benefits

- Better user experience
- Fewer passwords
- Centralized authentication

---

## Step 3 – Multi-Factor Authentication (MFA)

Azure requests another verification.

Examples

- Microsoft Authenticator
- SMS Code
- Phone Call
- Fingerprint
- Face Recognition

Example

```text
Password

+

Phone Approval

=

Access Granted
```

Benefits

- Prevents password theft
- Stops phishing attacks
- Stronger identity protection

---

## Step 4 – Conditional Access

Azure evaluates several conditions.

Questions Azure asks:

- Is Alice in India?
- Is she using a trusted laptop?
- Is device compliant?
- Is the sign-in risky?

Policy Example

```text
IF

Outside Company Network

THEN

Require MFA
```

Another Policy

```text
IF

Unknown Device

THEN

Block Access
```

Benefits

- Adaptive security
- Risk-based access
- Reduced attack surface

---

## Step 5 – Role-Based Access Control (RBAC)

Authentication answers:

> **Who are you?**

RBAC answers:

> **What can you do?**

Example

Alice = HR Manager

Permissions

✅ Read Employee Records

✅ Update Employee Salary

❌ Delete Virtual Machines

Roles

- Owner
- Contributor
- Reader
- User Access Administrator

Example

```text
User

↓

Reader Role

↓

Read Storage Account

❌ Cannot Delete Storage
```

---

# How They Work Together

```text
User Login

↓

Microsoft Entra ID

↓

SSO

↓

MFA

↓

Conditional Access

↓

RBAC

↓

Azure Resource
```

Every layer increases security.

---

# Microsoft Entra ID

Previously called **Azure Active Directory (Azure AD)**.

Cloud-based identity provider.

Features

- User authentication
- Single Sign-On
- MFA
- Conditional Access
- Identity management

Example

Employees log into:

- Microsoft 365
- Azure
- Salesforce
- ServiceNow

using one identity.

---

# Microsoft Entra Domain Services

Provides traditional Active Directory services **without managing domain controllers**.

Includes

- Domain Join
- LDAP
- Kerberos
- Group Policy

Architecture

```text
On-prem AD

↓

Microsoft Entra ID

↓

Microsoft Entra Domain Services

↓

Virtual Machines
```

Use When

- Legacy applications
- Windows authentication
- Lift-and-shift migrations

---

# External Identities

Allows external users to access company resources.

Examples

- Customers
- Vendors
- Partners
- Suppliers

Example

Company invites:

```text
vendor@gmail.com

↓

Microsoft Entra B2B

↓

Access to SharePoint
```

Benefits

- Secure collaboration
- Guest accounts
- Controlled permissions

---

# Comparison

| Service | Purpose | Best For |
|----------|----------|----------|
| Microsoft Entra ID | Identity & Authentication | Employees |
| Entra Domain Services | Managed Active Directory | Legacy Apps |
| External Identities | Guest Collaboration | Customers & Partners |

---

# Encryption

Encryption converts readable data into unreadable ciphertext.

```text
Hello World

↓

Encryption

↓

XKJ83@#PAA

↓

Decryption

↓

Hello World
```

Types

### Data at Rest

Protects stored data.

Examples

- Blob Storage
- Managed Disks
- SQL Database

---

### Data in Transit

Protects moving data.

Uses

- HTTPS
- TLS
- VPN

---

# Azure Key Vault

Stores sensitive information securely.

Stores

- Secrets
- Passwords
- Certificates
- Encryption Keys

Example

```text
Application

↓

Azure Key Vault

↓

Retrieve Secret

↓

Connect to Database
```

Benefits

- Centralized key management
- Automatic rotation
- Better security

---

# Defense in Depth

Multiple layers of protection.

```text
Physical Security

↓

Identity

↓

Perimeter

↓

Network

↓

Compute

↓

Application

↓

Data
```

If one layer fails, others continue protecting the system.

---

# Microsoft Defender for Cloud

Cloud Security Posture Management (CSPM) and workload protection.

Capabilities

- Security recommendations
- Vulnerability assessment
- Threat detection
- Compliance monitoring
- Secure score

Example Recommendations

- Enable MFA
- Encrypt disks
- Close open ports
- Install endpoint protection

---

# Security Incident Simulation

## Scenario

An attacker steals an employee's password.

Without Security

```text
Password Stolen

↓

Login Successful

↓

Access Company Data
```

Result

❌ Data Breach

---

## With Azure Security

```text
Password Stolen

↓

MFA Requested

↓

Attacker Cannot Approve

↓

Login Blocked
```

Result

✅ Attack Stopped

---

### Another Attack

Attacker steals a hard drive.

Without Encryption

```text
Disk Stolen

↓

Read Files
```

Result

❌ Data Exposed

---

### With Encryption

```text
Disk Stolen

↓

Encrypted Data

↓

Unreadable
```

Result

✅ Data Safe

---

### Key Management Protection

Application needs a database password.

Without Key Vault

```text
Password

Stored in Code
```

Anyone with source code can read it.

---

With Azure Key Vault

```text
Application

↓

Azure Key Vault

↓

Retrieve Secret Securely
```

Result

✅ Password protected

---

### Defender for Cloud Detection

Administrator accidentally opens port **3389 (RDP)** to the internet.

Microsoft Defender for Cloud detects:

- Open management port
- High-risk configuration
- Security recommendation

Administrator closes the port before attackers exploit it.

Result

✅ Reduced attack risk

---

# Security Layers Together

```text
User

↓

Microsoft Entra ID

↓

MFA

↓

Conditional Access

↓

RBAC

↓

Encrypted Data

↓

Azure Key Vault

↓

Microsoft Defender for Cloud
```

Each layer reduces the likelihood and impact of an attack.

---

# Shared Responsibility Model

| Service Type | Customer Responsibility | Microsoft Responsibility |
|--------------|-------------------------|--------------------------|
| IaaS | OS, apps, identities, data | Physical datacenter, networking, hardware |
| PaaS | Apps, identities, data | OS, runtime, infrastructure |
| SaaS | Identities, data | Entire application and infrastructure |

---

# AZ-900 Exam Tips

## Microsoft Entra ID

- Cloud identity service
- Authentication
- SSO
- MFA
- Conditional Access

---

## Single Sign-On

- One login
- Access multiple applications

---

## MFA

- Password + another verification factor
- Strong identity protection

---

## Conditional Access

- Policy-based access control
- Checks user, device, location, and risk

---

## RBAC

- Controls **what users can do**
- Uses least privilege

---

## Entra Domain Services

- Managed domain services
- LDAP
- Kerberos
- Group Policy
- No domain controllers to manage

---

## External Identities

- Guest users
- Partners
- Vendors
- B2B collaboration

---

## Azure Key Vault

- Stores secrets
- Stores certificates
- Stores encryption keys

---

## Encryption

- Data at Rest
- Data in Transit

---

## Microsoft Defender for Cloud

- Security recommendations
- Threat protection
- Compliance
- Secure Score

---

# 30-Second Revision

- **Microsoft Entra ID** → Cloud identity service
- **SSO** → One login, many apps
- **MFA** → Two or more verification methods
- **Conditional Access** → Policy-based sign-in decisions
- **RBAC** → Controls permissions after authentication
- **Entra Domain Services** → Managed Active Directory features
- **External Identities** → Secure guest access
- **Encryption** → Protects stored and transmitted data
- **Azure Key Vault** → Secure storage for keys and secrets
- **Defense in Depth** → Multiple security layers
- **Microsoft Defender for Cloud** → Security posture management and threat protection
