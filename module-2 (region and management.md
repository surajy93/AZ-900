# AZ-900 Notes: Azure Regions, Availability Zones, Resource Hierarchy & Governance

## Azure Resource Hierarchy

Azure resources are organized in the following hierarchy:

```text
Management Group
    ↓
Subscription
    ↓
Resource Group
    ↓
Resources
```

### Management Group
- Highest level of organization.
- Used to group multiple subscriptions.
- Apply governance across subscriptions.
- Policies and RBAC can be inherited by all child subscriptions.

**Example**

```text
Contoso
│
├── Production Management Group
├── Development Management Group
└── Sandbox Management Group
```

---

### Subscription
A subscription is a logical container that provides:

- Billing boundary
- Access control boundary
- Resource quota boundary

Each department can have its own subscription.

Example:

- HR Subscription
- Finance Subscription
- Sales Subscription

Benefits:

- Separate billing
- Better security isolation
- Easier cost tracking
- Independent resource limits

---

### Resource Group

A Resource Group is a logical container that holds Azure resources.

Example:

```text
Finance Subscription
│
├── Payroll Resource Group
├── Accounting Resource Group
└── Audit Resource Group
```

A Resource Group can contain:

- Virtual Machines
- Storage Accounts
- SQL Databases
- App Services
- Virtual Networks

Resources inside the same Resource Group usually belong to the same application or project.

---

### Resources

Resources are the actual Azure services.

Examples:

- Virtual Machine
- Storage Account
- Azure SQL Database
- Azure App Service
- Azure Kubernetes Service (AKS)
- Virtual Network

---

# Azure Regions

A Region is a geographic location where Azure has one or more datacenters.

Examples:

- East US
- West Europe
- India Central
- Japan East

Reasons to choose a region:

- Lower latency
- Regulatory compliance
- Data residency
- Service availability

---

# Availability Zones

An Availability Zone is a physically separate datacenter inside the same Azure region.

Example:

```text
India Central

├── Zone 1
├── Zone 2
└── Zone 3
```

Each zone has:

- Independent power
- Independent cooling
- Independent networking

Benefits:

- High availability
- Fault isolation
- Protection against datacenter failures

Example:

```text
           Users
              │
       Azure Load Balancer
          ┌─────┴─────┐
          │           │
      VM (Zone 1)  VM (Zone 2)
```

If Zone 1 fails, Zone 2 continues serving traffic.

---

# Datacenters

A Datacenter is a physical building that contains:

- Servers
- Storage
- Networking equipment
- Cooling systems
- Power infrastructure

Availability Zones are built using separate datacenters.

---

# Region Pairs

Azure pairs regions within the same geography for disaster recovery.

Example:

```text
East US
    │
Replication
    │
West US
```

Benefits:

- Disaster recovery
- Business continuity
- Sequential Azure updates
- Data replication options

Examples of region pairs:

- East US ↔ West US
- North Europe ↔ West Europe

---

# Sovereign Regions

Sovereign Regions are isolated Azure clouds designed for governments and regulated industries.

Examples:

- Azure Government
- Azure China

Characteristics:

- Physically isolated
- Separate authentication systems
- Country-specific compliance
- Government-grade security

---

# Data Residency

Data residency means data must remain inside a specific country or geography.

Example:

A bank operating in India may require all customer data to remain within India.

Best practices:

- Deploy workloads only in approved Azure regions.
- Avoid replication outside permitted geographies.
- Use Availability Zones for high availability.
- Use approved paired regions only if regulations allow.

---

# Example Azure Organization Structure

```text
Azure Tenant
│
├── Corporate Management Group
│
├── Production Management Group
│   ├── HR Subscription
│   ├── Finance Subscription
│   └── Sales Subscription
│
├── Development Management Group
│   ├── HR Dev Subscription
│   ├── Finance Dev Subscription
│   └── Sales Dev Subscription
│
└── Sandbox Management Group
    └── Test Subscription
```

---

# Recommended Architecture for High Availability

```text
                    Users
                      │
              Azure Front Door
                      │
              Azure Load Balancer
               ┌──────────────┐
               │              │
          Zone 1 VM      Zone 2 VM
               │              │
          Azure SQL Database
         (Zone Redundant)
               │
         Azure Backup Storage
```

This architecture provides:

- High availability
- Fault tolerance
- Disaster recovery readiness
- Improved resiliency

---

# AZ-900 Exam Tips

| Service | Remember |
|----------|----------|
| Management Group | Organizes subscriptions |
| Subscription | Billing and access boundary |
| Resource Group | Logical container for resources |
| Resource | Azure service |
| Region | Geographic location |
| Availability Zone | Separate datacenter within a region |
| Datacenter | Physical Azure facility |
| Region Pair | Disaster recovery between regions |
| Sovereign Region | Isolated Azure cloud for regulatory compliance |
| Data Residency | Keep data in approved geographic locations |

---

# Memory Trick

```
Management Group
        ↓
Subscription
        ↓
Resource Group
        ↓
Resources
        ↓
Region
        ↓
Availability Zone
        ↓
Datacenter
```

---

# AZ-900 Interview Questions

### What is the difference between a Subscription and a Resource Group?

**Subscription**
- Billing boundary
- Access control boundary
- Contains multiple Resource Groups

**Resource Group**
- Logical container
- Holds Azure resources
- Used for lifecycle management

---

### What is the difference between a Region and an Availability Zone?

| Region | Availability Zone |
|---------|-------------------|
| Geographic area | Separate datacenter within a region |
| Contains multiple datacenters | One isolated datacenter |
| Used for choosing deployment location | Used for high availability |

---

### Why use Management Groups?

- Centralized governance
- Apply Azure Policy
- Apply RBAC
- Organize subscriptions

---

### Why use Availability Zones?

- Protect against datacenter failures
- Improve application uptime
- Increase fault tolerance

---

### When should Region Pairs be used?

Use Region Pairs for:

- Disaster recovery
- Business continuity
- Cross-region replication
- Planned Azure maintenance

---

# Quick Revision (30 Seconds)

- **Management Group** → Groups subscriptions
- **Subscription** → Billing & access boundary
- **Resource Group** → Groups related resources
- **Resource** → Azure service
- **Region** → Geographic deployment location
- **Availability Zone** → Separate datacenter inside a region
- **Datacenter** → Physical Azure building
- **Region Pair** → Disaster recovery
- **Sovereign Region** → Government & regulated cloud
- **Data Residency** → Keep data in approved locations
