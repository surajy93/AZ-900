# AZ-900: Azure Management Tools, Infrastructure as Code (IaC) & Azure Arc Notes

---

# Azure Management Tools

Azure provides multiple ways to manage resources.

| Tool | Best For |
|------|-----------|
| Azure Portal | Graphical (GUI) management |
| Azure Cloud Shell | Browser-based command line |
| Azure CLI | Cross-platform scripting and automation |
| Azure PowerShell | PowerShell automation for Windows administrators |

---

# 1. Azure Portal

## What is Azure Portal?

Azure Portal is a **web-based graphical interface (GUI)** for managing Azure resources.

Website:

https://portal.azure.com

---

## Features

- Create resources
- Delete resources
- Configure networking
- Monitor resources
- View dashboards
- Manage users
- Manage subscriptions

---

## Advantages

✅ Beginner friendly

✅ No installation required

✅ Visual interface

✅ Easy monitoring

---

## Disadvantages

❌ Difficult to automate

❌ Manual operations

---

## Best Use Cases

- Learning Azure
- Small deployments
- Monitoring resources
- One-time administrative tasks

---

# Azure Portal Workflow

```
Login
   │
   ▼
Portal Dashboard
   │
   ▼
Create Resource
   │
   ▼
Configure Settings
   │
   ▼
Deploy Resource
```

---

# 2. Azure Cloud Shell

## What is Cloud Shell?

Cloud Shell is a browser-based command-line environment hosted by Azure.

No installation required.

Supports:

- Bash
- PowerShell

---

## Features

- Azure CLI pre-installed
- Azure PowerShell pre-installed
- Git
- Terraform
- Bicep
- kubectl
- Docker tools

---

## Advantages

✅ Works from any browser

✅ Always updated

✅ No installation

---

## Best Use Cases

- Quick administration
- Learning CLI
- Running scripts
- Remote troubleshooting

---

# Example

Create Resource Group

```bash
az group create \
  --name DemoRG \
  --location centralindia
```

---

# 3. Azure CLI

## What is Azure CLI?

Azure CLI is Microsoft's cross-platform command-line tool.

Runs on:

- Windows
- Linux
- macOS

---

## Installation

```
az login
```

Authenticate once and manage Azure resources.

---

## Example Commands

Create Resource Group

```bash
az group create \
--name DemoRG \
--location centralindia
```

List Virtual Machines

```bash
az vm list
```

Delete Resource Group

```bash
az group delete \
--name DemoRG
```

---

## Advantages

✅ Automation

✅ Cross-platform

✅ Easy scripting

✅ DevOps friendly

---

## Best Use Cases

- CI/CD pipelines
- Automation
- Bash scripting
- DevOps

---

# 4. Azure PowerShell

## What is Azure PowerShell?

Azure PowerShell is a collection of PowerShell modules for managing Azure resources.

Uses PowerShell syntax.

---

## Login

```powershell
Connect-AzAccount
```

---

## Example

Create Resource Group

```powershell
New-AzResourceGroup `
-Name DemoRG `
-Location "Central India"
```

---

List VMs

```powershell
Get-AzVM
```

---

Delete Resource Group

```powershell
Remove-AzResourceGroup
```

---

## Advantages

✅ Great for Windows administrators

✅ Powerful object-based scripting

✅ Works with existing PowerShell scripts

---

## Best Use Cases

- Enterprise automation
- Windows administration
- Scheduled scripts
- Hybrid environments

---

# Comparison

| Feature | Portal | Cloud Shell | Azure CLI | Azure PowerShell |
|----------|--------|-------------|------------|------------------|
| GUI | ✅ | ❌ | ❌ | ❌ |
| Browser | ✅ | ✅ | ❌ | ❌ |
| Automation | ❌ | ✅ | ✅ | ✅ |
| Scripting | ❌ | ✅ | ✅ | ✅ |
| Cross Platform | Browser | Browser | ✅ | ✅ (PowerShell 7) |
| Beginner Friendly | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ | ⭐⭐⭐ | ⭐⭐⭐ |

---

# Which Tool Should You Choose?

## Portal

Choose when:

- Learning Azure
- Creating resources manually
- Monitoring

---

## Cloud Shell

Choose when:

- Using a browser
- Running quick scripts
- No local installation

---

## Azure CLI

Choose when:

- Automating deployments
- CI/CD
- DevOps

---

## Azure PowerShell

Choose when:

- Working in Windows
- Existing PowerShell environment
- Enterprise automation

---

# Infrastructure as Code (IaC)

Infrastructure as Code means defining infrastructure using code instead of manual configuration.

Benefits:

- Repeatable deployments
- Version control
- Automation
- Consistency

---

# ARM Templates

## What are ARM Templates?

ARM (Azure Resource Manager) templates use **JSON** to define Azure infrastructure.

Example:

```
{
  "type": "Microsoft.Storage/storageAccounts",
  "name": "mystorage"
}
```

---

## Advantages

- Declarative
- Repeatable
- Version controlled

---

# Bicep

## What is Bicep?

Bicep is Microsoft's modern language for Azure deployments.

It compiles into ARM templates.

---

## ARM vs Bicep

ARM

```json
{
 "type":"Microsoft.Storage/storageAccounts"
}
```

Bicep

```bicep
resource storage 'Microsoft.Storage/storageAccounts@2023-01-01' = {
  name: 'mystorage'
  location: resourceGroup().location
}
```

Bicep is:

- Easier to read
- Less code
- Easier to maintain

---

# Deployment Workflow

```
Developer
     │
     ▼
Create Bicep File
     │
     ▼
Validate Template
     │
     ▼
Human Review
     │
     ▼
Deploy to Test
     │
     ▼
Testing
     │
     ▼
Human Approval
     │
     ▼
Deploy to Production
     │
     ▼
Monitoring
```

---

# Agent-Assisted Deployment Workflow

Imagine an AI agent assisting with deployments.

## Step 1

Developer creates Bicep template.

---

## Step 2

AI Agent reviews template.

Checks:

- Missing tags
- Naming standards
- Security
- Cost estimates

---

## Step 3

Human approves template.

---

## Step 4

Deploy to Development.

---

## Step 5

Agent validates deployment.

Checks:

- VM running
- Storage created
- Network healthy

---

## Step 6

Human approves Production rollout.

---

## Step 7

Deployment starts.

---

## Step 8

Agent monitors health.

If deployment fails:

Rollback suggested.

Human approves rollback.

---

# Deployment Flow

```
Developer
     │
     ▼
Bicep Template
     │
     ▼
AI Validation
     │
     ▼
Human Approval
     │
     ▼
Deploy Test
     │
     ▼
Testing
     │
     ▼
Human Approval
     │
     ▼
Deploy Production
     │
     ▼
Health Check
     │
     ▼
Rollback if Required
```

---

# Azure Arc

## What is Azure Arc?

Azure Arc extends Azure management to resources running:

- On-premises
- Other cloud providers (AWS, Google Cloud)
- Edge environments

Manage them from Azure as if they were native Azure resources.

---

# Azure Arc Can Manage

- Windows Servers
- Linux Servers
- Kubernetes Clusters
- SQL Servers

---

# Why Azure Arc?

Without Azure Arc:

```
Azure
AWS
On-Prem
Google Cloud

Managed Separately
```

With Azure Arc:

```
           Azure Portal
                │
      ┌─────────┼─────────┐
      ▼         ▼         ▼
 Azure VM   AWS VM   On-Prem Server
      ▼         ▼         ▼
 Managed from One Place
```

---

# Azure Arc Benefits

- Centralized management
- Apply Azure Policy everywhere
- Monitor all servers
- Inventory management
- Security management
- Governance
- Automation

---

# Practical Scenario

A company has:

- 40 Azure Virtual Machines
- 30 AWS Virtual Machines
- 20 On-Premises Servers

Without Azure Arc:

Administrators manage three different environments.

With Azure Arc:

All 90 servers appear in the Azure Portal.

Administrators can:

- Apply Azure Policy
- Monitor health
- Track compliance
- Use Azure Monitor
- Use Microsoft Defender for Cloud

Everything is managed from a single control plane.

---

# Azure Arc Workflow

```
Azure Portal
      │
      ▼
Azure Arc
      │
 ┌────┼────┐
 ▼    ▼    ▼
Azure AWS On-Prem
 ▼    ▼    ▼
Unified Management
```

---

# AZ-900 Exam Tips

## Azure Portal

GUI for managing Azure resources.

---

## Cloud Shell

Browser-based shell with Azure CLI and PowerShell pre-installed.

---

## Azure CLI

Best for:

- Automation
- Bash scripting
- DevOps
- Cross-platform management

---

## Azure PowerShell

Best for:

- Windows administrators
- PowerShell scripting
- Enterprise automation

---

## ARM Templates

JSON-based Infrastructure as Code.

---

## Bicep

Simpler language for Azure deployments that compiles into ARM templates.

---

## Azure Arc

Extends Azure management to:

- On-premises resources
- AWS resources
- Google Cloud resources
- Edge environments

---

# Quick Comparison

| Service | Purpose |
|----------|----------|
| Azure Portal | GUI management |
| Cloud Shell | Browser-based command line |
| Azure CLI | Cross-platform automation |
| Azure PowerShell | PowerShell automation |
| ARM Templates | JSON Infrastructure as Code |
| Bicep | Simplified IaC language |
| Azure Arc | Hybrid and multicloud management |

---

# One-Line Memory Tricks

- **Azure Portal** → Manage Azure visually.
- **Cloud Shell** → Run Azure commands from any browser.
- **Azure CLI** → Automate Azure with cross-platform commands.
- **Azure PowerShell** → Automate Azure using PowerShell.
- **ARM Templates** → Define Azure infrastructure with JSON.
- **Bicep** → Simpler, cleaner way to write ARM deployments.
- **Azure Arc** → Manage Azure, on-premises, and multicloud resources from one place.
