# ☁️ AZ-900 Notes – Cloud Concepts (Simple + Interview/Exam Friendly)

---

# 1. What is Cloud Computing?

Cloud computing means **using IT resources (servers, storage, networking, databases, software, etc.) over the internet instead of owning and maintaining them yourself.**

Instead of buying a physical server, you rent one from Microsoft Azure and pay only for what you use.

### Example

Imagine you want to start an e-commerce website.

### Traditional Way

You need to buy:

- Servers
- Networking equipment
- Storage
- Cooling system
- UPS
- Internet connection

This costs a lot of money before your website even launches.

### Cloud Way

You simply log into Azure.

Click **Create Virtual Machine**.

Within minutes your server is ready.

No hardware purchase.

---

# Benefits of Cloud

- No upfront hardware cost
- Pay only for what you use
- Easy to scale
- High availability
- Global infrastructure
- Managed by Microsoft

---

# 2. Cloud Models

There are four cloud deployment models.

- Public Cloud
- Private Cloud
- Hybrid Cloud
- Multicloud

---

# Public Cloud

## Definition

Infrastructure owned and managed by Microsoft (Azure).

Many customers share the infrastructure securely.

You simply rent resources.

## Example

A startup wants to launch a shopping website.

Instead of buying servers they deploy everything on Azure.

```
Microsoft Data Center

------------------------
| Customer A           |
| Customer B           |
| Customer C           |
------------------------

You rent resources.
```

## Advantages

- Cheapest
- Very scalable
- Fast deployment
- No hardware maintenance

## Disadvantages

- Less infrastructure control than a private cloud
- Some organizations may have regulatory requirements that limit its use

## Best For

- Startups
- Small businesses
- Mobile apps
- Websites
- APIs

---

# Private Cloud

## Definition

Infrastructure dedicated to one organization only.

Nobody else shares the servers.

```
Company Data Center

-----------------------
| Server              |
| Storage             |
| Network             |
-----------------------
```

## Example

A military organization stores confidential data in its own data center.

## Advantages

- Maximum control
- Dedicated hardware
- High security
- Highly customizable

## Disadvantages

- Expensive
- Company manages everything
- Limited scalability compared to public cloud

## Best For

- Banks
- Government
- Defense
- Hospitals

---

# Hybrid Cloud

## Definition

Combination of Private Cloud + Public Cloud.

Some workloads stay on-premises.

Others move to Azure.

```
Private Cloud
      +
Azure Public Cloud
```

## Example

Hospital

Patient Records

↓

Private Cloud

Website

↓

Azure

## Advantages

- Best of both worlds
- Gradual migration
- Sensitive data remains private

## Disadvantages

- More complex
- Two environments to manage

## Best For

Companies migrating to Azure.

---

# Multicloud

## Definition

Using multiple public cloud providers.

Example

- Azure
- AWS
- Google Cloud

```
Company

   |
-----------------------------
| Azure | AWS | Google Cloud |
-----------------------------
```

## Example

Website → Azure

AI → Google Cloud

Backup → AWS

## Advantages

- Avoid vendor lock-in
- Use best service from each provider
- Increased flexibility

## Disadvantages

- More complex management
- Different security and billing models

---

# Hybrid vs Multicloud

| Hybrid | Multicloud |
|----------|------------|
| Private + Public | Multiple Public Clouds |
| Azure + On-premises | Azure + AWS |
| Mix of private and public | No private cloud required |

---

# Azure Arc

## Definition

Azure Arc allows you to manage Azure resources, on-premises servers, and resources in other cloud providers from Azure.

Think of it as one management dashboard.

```
          Azure Arc

      /       |       \
Azure      AWS      On-Premises
```

## Example

Company has

- Azure servers
- AWS servers
- Office servers

Instead of managing each separately,

Azure Arc provides a unified management experience.

### Remember

Azure Arc **does not move resources**.

It **manages** them.

---

# Azure VMware Solution (AVS)

## What is VMware?

VMware creates Virtual Machines.

One physical server can run many VMs.

```
Physical Server

-------------------
| VM1 |
| VM2 |
| VM3 |
-------------------
```

Many companies already use VMware.

## Problem

Company wants Azure.

But rebuilding everything takes months.

## Solution

Azure VMware Solution

Move VMware workloads to Azure without redesigning them.

```
Before

Office

↓

VMware

After

Azure

↓

VMware
```

---

# 3. Shared Responsibility Model

As cloud services become more managed, Microsoft takes on more responsibility.

---

# On-Premises

You manage everything.

```
Company

✓ Building
✓ Servers
✓ Network
✓ Storage
✓ OS
✓ Runtime
✓ Application
✓ Data
```

---

# IaaS (Infrastructure as a Service)

Microsoft manages infrastructure.

You manage software.

Microsoft

- Building
- Physical servers
- Networking
- Storage

You

- Operating System
- Runtime
- Applications
- Data

### Example

Azure Virtual Machine

---

# PaaS (Platform as a Service)

Microsoft manages infrastructure + platform.

You only manage your application and data.

Microsoft

- Infrastructure
- OS
- Runtime
- Scaling
- Updates

You

- Application
- Data

### Example

Azure App Service

---

# SaaS (Software as a Service)

Microsoft manages almost everything.

You simply use the software.

Microsoft

- Infrastructure
- OS
- Application
- Updates

You

- Users
- Data
- Configuration

### Examples

- Microsoft 365
- Outlook
- Teams

---

# Responsibility Comparison

| Service | You Manage |
|-----------|------------|
| On-Premises | Everything |
| IaaS | OS, Runtime, Applications, Data |
| PaaS | Applications, Data |
| SaaS | Data, Users, Configuration |

---

# Easy Memory Trick

On-Premises

Everything is yours.

IaaS

Infrastructure is rented.

PaaS

Platform is ready.

Deploy code.

SaaS

Just login and use.

---

# 4. CapEx vs OpEx

---

# CapEx (Capital Expenditure)

Large upfront investment.

Examples

- Buy servers
- Buy storage
- Buy networking equipment

You own everything.

### Example

Open a Gym

Buy

- Building
- Machines
- Furniture

Huge upfront investment.

---

# OpEx (Operational Expenditure)

Pay as you use.

Monthly or usage-based payments.

Example

Rent a Gym.

Monthly fee.

No huge investment.

---

# Cloud = OpEx

Azure uses a consumption-based pricing model.

Need one VM?

Pay only while it runs.

Delete VM.

Billing stops.

---

# Comparison

| CapEx | OpEx |
|--------|------|
| Buy | Rent |
| High upfront cost | Low upfront cost |
| Own hardware | Cloud provider owns hardware |
| Fixed assets | Pay-as-you-go |

---

# 5. Consumption-Based Model

Also called

Pay-As-You-Go.

You pay only for what you consume.

Examples

Storage

Use 100 GB

Pay for 100 GB

Use 2 TB

Pay for 2 TB

Virtual Machine

Run

24 hours

Pay for 24 hours

Delete VM

No billing.

---

# Why Companies Love Cloud

- No hardware purchase
- Easy scaling
- Faster deployment
- Lower upfront investment
- Global reach

---

# AZ-900 Exam Keywords

| Keyword | Answer |
|-----------|---------|
| Lowest cost | Public Cloud |
| Dedicated hardware | Private Cloud |
| Azure + On-Premises | Hybrid Cloud |
| Azure + AWS | Multicloud |
| One management portal | Azure Arc |
| Existing VMware workloads | Azure VMware Solution |
| Deploy code only | PaaS |
| Manage Virtual Machine | IaaS |
| Just use software | SaaS |
| Pay only when using | OpEx |
| Buy servers | CapEx |

---

# Quick Revision

## Public Cloud

- Rent
- Cheap
- Scalable

---

## Private Cloud

- Own
- Secure
- Expensive

---

## Hybrid Cloud

Private + Public

---

## Multicloud

Azure + AWS + Google Cloud

---

## Azure Arc

Manage everything from Azure.

---

## Azure VMware Solution

Run VMware workloads in Azure.

---

## On-Premises

You manage everything.

---

## IaaS

Manage

- OS
- Applications
- Data

---

## PaaS

Manage

- Applications
- Data

---

## SaaS

Just use the application.

---

## CapEx

Buy.

Own.

Large upfront investment.

---

## OpEx

Rent.

Pay-As-You-Go.

No large upfront cost.

---

# Memory Tricks

🏨 Public Cloud = Hotel

🏠 Private Cloud = Own House

🏠 + 🏨 Hybrid = House + Hotel

🏨🏨🏨 Multicloud = Many Hotels

🖥️ Azure Arc = Universal Remote

🚚 Azure VMware Solution = Move your VMware environment to Azure

💰 CapEx = Buy

💳 OpEx = Rent
