# AZ-900: Azure Governance & Compliance Notes

---

# What is Azure Governance?

**Azure Governance** is the process of ensuring Azure resources are:

- Secure
- Compliant
- Organized
- Cost-effective
- Managed consistently

Governance helps organizations control **who can do what, where resources can be deployed, and whether resources meet company policies.**

---

# Azure Governance Services

| Service | Purpose |
|----------|----------|
| Azure Policy | Enforce organizational rules |
| Resource Locks | Prevent accidental deletion or modification |
| Microsoft Purview | Data governance and compliance |
| Service Trust Portal | Compliance reports and audit documents |

---

# Governance Architecture

```
                   Organization Rules
                           │
                           ▼
                  Azure Subscription
                           │
        ┌──────────────────┼──────────────────┐
        │                  │                  │
        ▼                  ▼                  ▼
 Azure Policy      Resource Locks     Microsoft Purview
        │                  │                  │
        ▼                  ▼                  ▼
 Enforce Rules     Protect Resources   Govern Data
        │
        ▼
 Policy Compliance
        │
        ▼
 Service Trust Portal
        │
        ▼
 Audit Evidence
```

---

# 1. Azure Policy

## Purpose

Azure Policy ensures that Azure resources comply with organizational standards.

Instead of checking resources manually, Azure Policy automatically evaluates whether resources follow defined rules.

---

## What Azure Policy Can Do

- Restrict resource locations
- Enforce naming conventions
- Require tags
- Require encryption
- Restrict VM sizes
- Audit resources
- Deny non-compliant deployments
- Automatically remediate issues

---

## Example Policies

### Only allow resources in Central India

```
Allowed Regions

✔ Central India

❌ East US

❌ West Europe
```

---

### Require Tags

Every resource must have:

```
Environment = Production

Owner = Suraj

Department = IT
```

If tags are missing:

Deployment can be denied.

---

### Restrict VM Sizes

Allowed:

```
B2ms
D2s_v5
```

Blocked:

```
E64s_v5
```

---

# Policy Effects

| Effect | Meaning |
|---------|----------|
| Audit | Report non-compliance only |
| Deny | Prevent deployment |
| Append | Add missing information |
| Modify | Change resource during deployment |
| DeployIfNotExists | Deploy required resources automatically |
| AuditIfNotExists | Report if required resource is missing |

---

# Azure Policy Lifecycle

```
Create Policy
      │
      ▼
Assign Policy
      │
      ▼
Resources Evaluated
      │
      ▼
Compliant?
      │
 ┌────┴────┐
 │         │
Yes        No
 │         │
 ▼         ▼
Nothing   Audit / Deny / Remediate
```

---

# 2. Resource Locks

## Purpose

Resource Locks prevent accidental deletion or modification.

They provide an additional layer of protection.

---

# Types of Resource Locks

## ReadOnly Lock

Users can:

✔ View resources

Cannot:

❌ Modify

❌ Delete

---

## Delete Lock

Users can:

✔ Modify

Cannot:

❌ Delete

---

# Example

Production SQL Database

Without Lock:

Developer accidentally deletes database.

With Delete Lock:

Azure blocks deletion.

---

# Lock Hierarchy

Locks can be applied at:

- Subscription
- Resource Group
- Individual Resource

Inheritance:

```
Subscription
      │
      ▼
Resource Group
      │
      ▼
Resource
```

Child resources inherit parent locks.

---

# 3. Microsoft Purview

## Purpose

Microsoft Purview is Microsoft's unified data governance solution.

It helps organizations:

- Discover data
- Classify data
- Protect sensitive information
- Meet compliance requirements

---

# What Purview Can Do

- Scan data sources
- Automatically classify sensitive data
- Create data catalogs
- Track data lineage
- Manage data lifecycle
- Apply governance policies

---

# Example

Purview scans storage account.

Finds:

- Credit Card Numbers
- Aadhaar Numbers
- PAN Numbers
- Passport Numbers

Automatically labels them as:

Sensitive Data

---

# Purview Workflow

```
Data Sources
      │
      ▼
Data Scan
      │
      ▼
Classification
      │
      ▼
Data Catalog
      │
      ▼
Compliance Reporting
```

---

# 4. Service Trust Portal

## Purpose

The Service Trust Portal provides Microsoft compliance documentation.

It contains:

- Audit reports
- Certifications
- Security documents
- Compliance reports

---

# Common Reports

- ISO 27001
- SOC 1
- SOC 2
- SOC 3
- PCI DSS
- GDPR
- HIPAA

---

# Why Use Service Trust Portal?

Organizations need evidence for audits.

Instead of requesting documents manually:

Download them directly.

---

# Governance Blueprint

```
Company Standards
        │
        ▼
Azure Policy
        │
Enforce Configuration
        │
        ▼
Azure Resources
        │
        ├───────────────┐
        │               │
        ▼               ▼
Resource Locks    Microsoft Purview
        │               │
Protect Resources Govern Data
        │               │
        └───────┬───────┘
                ▼
      Compliance Reports
                │
                ▼
      Service Trust Portal
                │
                ▼
            External Audit
```

---

# Agent-Assisted Azure Policy Workflow

Imagine an AI agent helping cloud administrators.

## Step 1

Agent analyzes Azure environment.

Finds:

- Missing tags
- Public Storage Accounts
- Open Network Security Groups

---

## Step 2

Agent drafts policies.

Example:

Policy 1

Require Owner tag.

Policy 2

Only deploy in India.

Policy 3

Disable public Blob access.

---

## Step 3

Administrator reviews.

Possible actions:

✔ Approve

✔ Reject

✔ Modify

---

## Step 4

Policy assigned.

Azure evaluates all resources.

---

## Step 5

Non-compliant resources detected.

Agent recommends remediation.

Example:

Missing Tag

↓

Automatically add tag.

---

## Step 6

Administrator approves remediation.

Azure fixes resources.

---

# Workflow Diagram

```
AI Agent
     │
     ▼
Analyze Azure
     │
     ▼
Draft Policies
     │
     ▼
Human Review
     │
     ▼
Policy Assignment
     │
     ▼
Compliance Scan
     │
     ▼
Agent Suggests Fixes
     │
     ▼
Human Approval
     │
     ▼
Automatic Remediation
```

---

# Audit Evidence Checklist

Every month or quarter collect:

## Azure Policy

- Policy assignments
- Compliance percentage
- Non-compliant resources
- Remediation history

---

## Resource Locks

Verify:

- Critical databases locked
- Production storage locked
- Production resource groups locked

---

## Microsoft Purview

Review:

- Data classifications
- Sensitive data reports
- Data lineage
- Scan results

---

## Service Trust Portal

Download latest:

- SOC Reports
- ISO Certificates
- GDPR Documentation
- PCI DSS Reports
- HIPAA Reports (if applicable)

---

## Activity Logs

Review:

- Resource creation
- Resource deletion
- Policy changes
- Lock removal
- Administrative actions

---

# Monthly Governance Checklist

✅ Review Azure Policy compliance

✅ Check non-compliant resources

✅ Verify required tags

✅ Review Resource Locks

✅ Download latest Service Trust reports

✅ Scan sensitive data with Purview

✅ Review audit logs

✅ Approve remediation actions

---

# AZ-900 Exam Tips

## Azure Policy

Used to:

- Enforce rules
- Audit compliance
- Deny non-compliant deployments

---

## Resource Locks

Prevent:

- Accidental deletion
- Accidental modification

---

## Microsoft Purview

Used for:

- Data governance
- Data discovery
- Classification
- Compliance

---

## Service Trust Portal

Provides:

- Compliance certifications
- Audit reports
- Microsoft security documentation

---

# Service Comparison

| Service | Primary Purpose |
|----------|-----------------|
| Azure Policy | Enforce configuration rules |
| Resource Locks | Protect resources from deletion/modification |
| Microsoft Purview | Govern and classify data |
| Service Trust Portal | Download compliance and audit evidence |

---

# Quick Revision

```
Azure Policy
↓
Enforce Rules

Resource Locks
↓
Protect Resources

Microsoft Purview
↓
Govern Data

Service Trust Portal
↓
Audit Evidence
```

---

# One-Line Memory Tricks

- **Azure Policy** → Enforce organizational rules.
- **Resource Locks** → Prevent accidental deletion or changes.
- **Microsoft Purview** → Discover, classify, and govern data.
- **Service Trust Portal** → Download Microsoft compliance reports.
- **Governance** → Keep Azure secure, compliant, and well-managed.
