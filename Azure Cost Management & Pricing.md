# AZ-900: Azure Cost Management & Pricing Notes

---

# 1. Azure Pricing Calculator

## Purpose
The **Azure Pricing Calculator** is used to estimate the monthly cost of Azure resources **before deployment**.

Use it to:
- Estimate cloud costs
- Compare service options
- Plan budgets
- Forecast expenses

---

## Example Workload

Application Architecture:

- 2 Azure Virtual Machines
- Azure SQL Database
- 1 TB Blob Storage
- Azure Load Balancer
- Azure Backup
- Azure Monitor

### Estimated Monthly Cost

| Service | Approx. Cost |
|----------|-------------:|
| Virtual Machines | $140 |
| Managed Disks | $30 |
| Azure SQL Database | $120 |
| Blob Storage | $25 |
| Load Balancer | $20 |
| Azure Monitor | $25 |
| Backup | $15 |
| Network Bandwidth | $30 |

**Estimated Total:** **~$405/month**

---

# Top Cost Drivers

## 1. Compute (Virtual Machines)

Pricing depends on:

- VM Size
- Number of VMs
- Running Hours
- Region

Example:

Running a VM:

24 hours/day
↓
Business hours only

can significantly reduce costs.

---

## 2. Database

Pricing depends on:

- vCores
- Performance Tier
- Storage
- Backup Retention

Premium databases cost much more than General Purpose.

---

## 3. Storage

Pricing depends on:

- Hot Tier
- Cool Tier
- Archive Tier
- Storage Redundancy

Moving old files to Cool or Archive storage reduces costs.

---

## 4. Networking

Azure charges mainly for:

- Outbound Internet Traffic

Inbound traffic is generally free.

---

## 5. Monitoring

Azure Monitor charges based on:

- Log ingestion
- Log retention
- Alerts

Collect only necessary logs.

---

# Pricing Calculator Assumptions

Always verify:

- Azure Region
- VM Size
- Hours per Month
- Storage Tier
- Storage Redundancy
- Reserved Instances
- Savings Plans
- Spot Pricing
- Licensing (Azure Hybrid Benefit)

---

# Cost Optimization Ideas

- Stop Dev/Test VMs when not in use.
- Use Autoscaling.
- Delete unused resources.
- Move data to Cool or Archive storage.
- Purchase Reservations for stable workloads.
- Use Savings Plans for flexible workloads.
- Monitor costs regularly.

---

# 2. Azure Cost Management

## Purpose

Azure Cost Management helps monitor, analyze, and optimize Azure spending after resources are deployed.

It allows you to:

- Analyze costs
- Create budgets
- Receive spending alerts
- Forecast future costs
- Optimize cloud spending

---

# Monthly FinOps Routine

## Week 1 – Review Spending

Tasks:

- Check monthly spending
- Compare with previous months
- Identify highest-cost resources
- Analyze spending by subscription

---

## Week 2 – Review Tags

Apply tags to every resource.

Example:

Environment = Production

Owner = Suraj

Department = IT

Project = Ecommerce

CostCenter = Finance

Benefits:

- Cost allocation
- Chargeback
- Better reporting
- Resource organization

---

## Week 3 – Budgets & Alerts

Example Monthly Budget

$1,000

Configure alerts at:

- 50%
- 75%
- 90%
- 100%

Notify:

- Cloud Administrator
- Finance Team
- Project Owner

---

## Week 4 – Cost Optimization

Review:

- Idle VMs
- Unattached Disks
- Old Snapshots
- Unused Public IPs
- Underutilized Databases

Take action:

- Resize VMs
- Delete unused resources
- Purchase Reservations
- Move storage to Cool Tier

---

# FinOps Checklist

✅ Review spending

✅ Analyze trends

✅ Validate resource tags

✅ Review budgets

✅ Configure alerts

✅ Optimize resources

✅ Export reports

---

# 3. Azure Tags

## Purpose

Tags are key-value pairs used to organize Azure resources.

Example:

Environment = Production

Owner = John

Department = Finance

Project = Ecommerce

Benefits:

- Cost tracking
- Resource organization
- Reporting
- Chargeback
- Governance

---

# 4. Azure Budgets

Budgets help prevent overspending.

Example:

Monthly Budget = $2,000

Alert Levels:

- 50%
- 75%
- 90%
- 100%

Budgets do NOT stop resources automatically.

They only send notifications.

---

# 5. Azure Cost Alerts

Alerts notify administrators when spending exceeds a threshold.

Example:

Budget = $1,000

Alert at:

50%

75%

90%

100%

Notifications can be sent through:

- Email
- Action Groups
- Automation

---

# 6. Reservations

## Best For

Predictable, long-running workloads.

Examples:

- Production Servers
- SQL Databases
- Always-running Applications

Benefits:

- Up to ~72% savings
- 1-year or 3-year commitment
- Lower long-term costs

Trade-off:

Less flexibility.

---

# 7. Azure Savings Plan

## Best For

Flexible compute workloads.

Examples:

- Autoscaling Applications
- Growing Web Applications
- Mixed VM Sizes

Benefits:

- Discounts across eligible compute services
- More flexible than Reservations

Trade-off:

Requires a committed hourly spend.

---

# 8. Spot Virtual Machines

## Best For

Interruptible workloads.

Examples:

- Batch Processing
- Rendering
- Testing
- CI/CD Pipelines
- Machine Learning Training

Benefits:

- Up to ~90% savings

Trade-off:

Azure can evict (stop) the VM at any time if capacity is needed.

Never use Spot VMs for production-critical applications.

---

# Choosing the Right Pricing Model

## Scenario 1

Production ERP System

Characteristics:

- Runs 24×7
- Stable workload
- Predictable usage

Recommendation:

✅ Reservations

---

## Scenario 2

Growing Web Application

Characteristics:

- Autoscaling
- Flexible workload
- VM sizes may change

Recommendation:

✅ Azure Savings Plan

---

## Scenario 3

Nightly Batch Processing

Characteristics:

- Can restart
- Not customer-facing
- Interruptions acceptable

Recommendation:

✅ Spot Virtual Machines

---

# Comparison Table

| Feature | Reservations | Savings Plan | Spot VM |
|----------|--------------|--------------|----------|
| Discount | High | High | Very High |
| Flexibility | Low | High | High |
| Interruptions | No | No | Yes |
| Best For | Stable Production | Flexible Compute | Batch Jobs |
| Commitment | 1–3 Years | Hourly Spend Commitment | None |

---

# Decision Flow

```
Is the workload interruptible?
        │
   Yes ─────► Spot VM
        │
       No
        │
Is it predictable and always running?
        │
   Yes ─────► Reservations
        │
       No
        │
Need flexibility?
        │
   Yes ─────► Azure Savings Plan
```

---

# AZ-900 Exam Tips

## Pricing Calculator

Used **before deployment** to estimate costs.

---

## Cost Management

Used **after deployment** to monitor and optimize costs.

---

## Tags

Used for:

- Cost allocation
- Reporting
- Resource organization

---

## Budgets

Help monitor spending.

They **do not stop resources**.

---

## Alerts

Notify administrators when spending reaches thresholds.

---

## Reservations

Best for:

- Stable
- Predictable
- Always-running workloads

---

## Savings Plan

Best for:

- Flexible
- Dynamic
- Autoscaling compute workloads

---

## Spot VM

Best for:

- Interruptible workloads
- Batch jobs
- Testing
- CI/CD
- Rendering

---

# AZ-900 Quick Revision

| Service | Purpose |
|----------|----------|
| Pricing Calculator | Estimate future Azure costs |
| Cost Management | Monitor and optimize spending |
| Tags | Organize and allocate costs |
| Budgets | Track spending limits |
| Alerts | Notify when budgets are exceeded |
| Reservations | Save on predictable workloads |
| Savings Plan | Save on flexible compute usage |
| Spot VM | Lowest-cost option for interruptible workloads |

---

# One-Line Memory Tricks

- **Pricing Calculator** → Estimate before deployment.
- **Cost Management** → Control costs after deployment.
- **Tags** → Organize and track spending.
- **Budgets** → Monitor spending limits.
- **Alerts** → Notify before overspending.
- **Reservations** → Predictable workloads.
- **Savings Plan** → Flexible compute workloads.
- **Spot VM** → Cheapest option for interruptible workloads.
