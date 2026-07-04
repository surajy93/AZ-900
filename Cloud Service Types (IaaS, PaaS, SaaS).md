# ☁️ AZ-900 Notes – Cloud Service Types (IaaS, PaaS, SaaS)

---

# Cloud Service Models

Microsoft Azure provides cloud services at different levels.

There are three major service models:

1. Infrastructure as a Service (IaaS)
2. Platform as a Service (PaaS)
3. Software as a Service (SaaS)

The biggest difference is:

> **Who is responsible for managing what?**

As you move from **IaaS → PaaS → SaaS**, Microsoft takes more responsibility and you take less.

```
More Customer Responsibility                     More Microsoft Responsibility

On-Premises → IaaS → PaaS → SaaS
```

---

# Example Business

Suppose a company owns an Online Shopping Platform.

The application contains:

- Website
- Backend API
- Database
- Email System
- Employee Collaboration

Let's decide which cloud model is best for each workload.

---

# Workload 1 – Website Server

Current Setup

The company hosts its website on a Windows Server.

Developers need complete control over:

- Windows
- IIS
- Installed software
- Firewall

## Best Choice

✅ IaaS

Example

Azure Virtual Machine

Why?

The company wants complete control over the Operating System.

---

Responsibilities

Microsoft manages

- Physical servers
- Networking
- Storage
- Data center

Customer manages

- Windows/Linux
- Security patches
- Antivirus
- Application
- Data

---

Real Example

```
Azure VM

↓

Windows Server

↓

Website
```

---

Advantages

- Full control
- Install any software
- Suitable for legacy applications

Disadvantages

- You manage updates
- You manage security
- You manage backups

---

# Workload 2 – Backend API

The company develops APIs.

Developers don't want to manage Windows updates.

They only want to deploy code.

## Best Choice

✅ PaaS

Example

Azure App Service

---

Responsibilities

Microsoft manages

- Infrastructure
- Operating System
- Runtime
- Scaling
- Load Balancing
- Patching

Customer manages

- Application Code
- Configuration
- Data

---

Real Example

```
Git Push

↓

Azure App Service

↓

Application Running
```

Developers focus only on coding.

---

Advantages

- Automatic scaling
- Automatic updates
- Less maintenance
- Faster deployment

Disadvantages

- Less OS control
- Limited customization

---

# Workload 3 – Email System

Company employees need email.

Should they create mail servers?

No.

## Best Choice

✅ SaaS

Example

Microsoft 365 Outlook

---

Microsoft manages

- Infrastructure
- Exchange Server
- Security Updates
- Storage
- High Availability

Customer manages

- Users
- Passwords
- Permissions
- Emails

---

Advantages

- Ready to use
- No maintenance
- Automatic updates

---

# Workload 4 – Team Collaboration

Company wants

- Chat
- Video Meetings
- File Sharing

## Best Choice

✅ SaaS

Example

Microsoft Teams

Simply create user accounts.

Everything else is managed by Microsoft.

---

# Final Application Portfolio

| Workload | Best Model | Azure Example | Why? |
|----------|------------|---------------|------|
| Website Server | IaaS | Azure Virtual Machine | Full OS control |
| Backend API | PaaS | Azure App Service | Developers deploy only code |
| Employee Email | SaaS | Microsoft 365 Outlook | Ready-to-use email |
| Team Collaboration | SaaS | Microsoft Teams | No server management |
| SQL Database | PaaS | Azure SQL Database | Microsoft manages database infrastructure |
| File Storage | PaaS | Azure Storage | Highly scalable managed storage |

---

# Responsibility Comparison

| Component | On-Prem | IaaS | PaaS | SaaS |
|-----------|---------|------|------|------|
| Physical Datacenter | You | Microsoft | Microsoft | Microsoft |
| Physical Servers | You | Microsoft | Microsoft | Microsoft |
| Networking | You | Microsoft | Microsoft | Microsoft |
| Storage | You | Microsoft | Microsoft | Microsoft |
| Operating System | You | You | Microsoft | Microsoft |
| Runtime | You | You | Microsoft | Microsoft |
| Middleware | You | You | Microsoft | Microsoft |
| Application | You | You | You | Microsoft |
| Data | You | You | You | You |
| Users & Access | You | You | You | You |

---

# How Responsibilities Shift (IaaS → PaaS)

Suppose you own an Online Shopping API.

---

## Security

### IaaS

You must

- Configure Firewall
- Install Antivirus
- Patch Windows
- Secure VM

Microsoft secures only the physical infrastructure.

---

### PaaS

Microsoft manages

- OS patches
- Runtime updates
- Infrastructure security

You manage

- Application security
- Authentication
- Authorization
- Data security

Less work.

---

# Patching

## IaaS

Every month

Administrator installs

- Windows Updates
- Security Patches
- Runtime Updates

Manual effort.

---

## PaaS

Microsoft performs

- OS Updates
- Runtime Updates
- Platform Maintenance

Developers deploy code.

---

# Scalability

## IaaS

Traffic increases.

Administrator manually creates new Virtual Machines.

```
1 VM

↓

3 VMs

↓

Load Balancer
```

Requires configuration.

---

## PaaS

Traffic increases.

Azure automatically scales.

```
Users

↓

Azure App Service

↓

Automatic Scale Out
```

No manual server management.

---

# Summary of Operational Shift

| Area | IaaS | PaaS |
|------|------|------|
| OS Updates | Customer | Microsoft |
| Runtime Updates | Customer | Microsoft |
| Infrastructure | Microsoft | Microsoft |
| Scaling | Mostly Customer | Mostly Microsoft (configure autoscaling) |
| Application | Customer | Customer |
| Data | Customer | Customer |

---

# Which Service Should You Choose?

## Choose IaaS When

- Need complete OS control
- Running legacy applications
- Need custom software
- Lift-and-shift migration

Examples

- Azure Virtual Machine

---

## Choose PaaS When

- Building new applications
- Developers only want to write code
- Automatic scaling required
- Fast deployment needed

Examples

- Azure App Service
- Azure SQL Database

---

## Choose SaaS When

- Ready-made software is enough
- No infrastructure management
- Fastest deployment

Examples

- Microsoft Teams
- Microsoft 365
- Outlook

---

# Scenario Quiz (AZ-900 Style)

---

## Question 1

A company wants complete control over Windows Server and needs to install custom software.

A. SaaS

B. PaaS

C. IaaS

D. Hybrid Cloud

✅ Answer

**C – IaaS**

Reason

The company needs Operating System control.

---

## Question 2

Developers only want to deploy code.

They don't want to manage Windows updates.

A. IaaS

B. PaaS

C. SaaS

D. Private Cloud

✅ Answer

**B – PaaS**

Reason

Microsoft manages the infrastructure and platform.

---

## Question 3

A company needs email for 500 employees.

Should they build an Exchange Server?

A. IaaS

B. PaaS

C. SaaS

D. Azure VM

✅ Answer

**C – SaaS**

Reason

Microsoft 365 is ready to use.

---

## Question 4

Which service model gives customers the **most responsibility**?

A. SaaS

B. PaaS

C. IaaS

D. All are equal

✅ Answer

**C – IaaS**

Reason

Customers manage the operating system, applications, patches, and data.

---

## Question 5

Which service model gives Microsoft the **most responsibility**?

A. IaaS

B. PaaS

C. SaaS

D. Hybrid

✅ Answer

**C – SaaS**

Reason

Microsoft manages almost everything except your data, users, and configuration.

---

## Question 6

A startup wants to deploy a Node.js API quickly without worrying about servers.

A. Azure VM

B. Azure App Service

C. Microsoft Teams

D. Windows Server

✅ Answer

**B – Azure App Service (PaaS)**

Reason

Developers only deploy the application code.

---

# AZ-900 Exam Keywords

| Keyword | Answer |
|----------|--------|
| Full OS control | IaaS |
| Install custom software | IaaS |
| Deploy code only | PaaS |
| Automatic OS patching | PaaS |
| Automatic scaling | PaaS |
| Ready-to-use software | SaaS |
| Email solution | SaaS |
| Microsoft Teams | SaaS |
| Azure Virtual Machine | IaaS |
| Azure App Service | PaaS |
| Azure SQL Database | PaaS |

---

# Easy Memory Tricks

🏗️ **IaaS = Empty Plot of Land**

You build and maintain the house.

---

🏠 **PaaS = Ready-Built House**

The house is ready.

You only decorate and live in it.

---

🏨 **SaaS = Hotel**

Everything is managed.

Just check in and use it.

---

# One-Line Revision

- **IaaS** → Manage the OS, applications, and data.
- **PaaS** → Manage only the application and data.
- **SaaS** → Use the software; manage your users, configuration, and data.
