# AZ-900 Notes: Azure Storage Services & Data Migration

## Azure Storage Overview

Azure Storage is Microsoft's cloud storage platform that provides secure, scalable, durable, and highly available storage.

### Types of Azure Storage

- Blob Storage
- Azure Files
- Managed Disks
- Queue Storage
- Table Storage

---

# Azure Storage Account

A Storage Account is the top-level container that holds Azure storage services.

```text
Storage Account
│
├── Blob Containers
├── File Shares
├── Queues
├── Tables
└── Managed Disks
```

Benefits

- Secure
- Scalable
- Highly available
- Encrypted by default

---

# Azure Blob Storage

Stores **unstructured data**.

Examples

- Images
- Videos
- PDFs
- Documents
- Backups
- Logs

Architecture

```text
Storage Account
      │
Blob Container
      │
├── image.jpg
├── video.mp4
├── backup.zip
└── report.pdf
```

Advantages

- Massive scalability
- Low cost
- Excellent durability
- Global access

Best For

- Website images
- Media files
- Backups
- Data lakes
- AI datasets

---

# Azure Files

Provides fully managed file shares using SMB/NFS protocols.

Example

```text
Azure File Share

├── HR
├── Finance
├── Marketing
└── IT
```

Can be mounted as a network drive on:

- Windows
- Linux
- macOS

Best For

- Shared company files
- Lift-and-shift file servers
- Home directories
- Legacy applications

---

# Managed Disks

Persistent block storage for Azure Virtual Machines.

Example

```text
Virtual Machine

├── OS Disk
├── Data Disk
└── Temporary Disk
```

Advantages

- High performance
- Automatic backups
- Encryption
- High availability

Best For

- Virtual Machines
- SQL Server
- Enterprise applications

---

# Queue Storage

Stores messages between applications.

Architecture

```text
Application A

↓

Queue

↓

Application B
```

Advantages

- Asynchronous communication
- Decouples applications
- Reliable message delivery

Best For

- Background jobs
- Order processing
- Notifications

---

# Table Storage

NoSQL key-value database.

Example

```text
Customer

Partition Key
Row Key

Name
Email
City
```

Advantages

- Very fast
- Low cost
- Massive scalability

Best For

- User profiles
- IoT metadata
- Large datasets

---

# Decision Matrix

## Workload 1

### Company Website

Requirements

- Store images
- Videos
- Documents
- Global access

Recommended Service

✅ Azure Blob Storage

Why?

- Optimized for unstructured files
- CDN integration
- High durability
- Low cost

---

## Workload 2

### Company File Server

Requirements

- Shared folders
- Network drive
- Windows compatibility

Recommended Service

✅ Azure Files

Why?

- SMB support
- Easy migration
- Shared access
- Cloud file server replacement

---

## Workload 3

### Banking Database VM

Requirements

- High IOPS
- Low latency
- Persistent storage

Recommended Service

✅ Managed Disks

Why?

- Designed for virtual machines
- Excellent performance
- Reliable
- Persistent storage

---

## Workload 4

### Order Processing System

Requirements

- Queue customer orders
- Process asynchronously
- Reliable delivery

Recommended Service

✅ Queue Storage

Why?

- Loose coupling
- Message buffering
- Scalable processing

---

# Storage Comparison

| Storage Service | Best For | Data Type | Performance |
|----------------|----------|-----------|-------------|
| Blob Storage | Images, Videos, Backups | Unstructured | High |
| Azure Files | Shared Folders | Files | High |
| Managed Disks | Virtual Machines | Block Storage | Very High |
| Queue Storage | Messaging | Messages | High |
| Table Storage | NoSQL Data | Structured | Very High |

---

# Storage Redundancy

Azure automatically replicates data to protect against failures.

## 1. LRS (Locally Redundant Storage)

Stores **3 copies** within a single datacenter.

```text
Datacenter

Copy 1

Copy 2

Copy 3
```

Advantages

- Lowest cost
- High durability
- Simple

Disadvantages

- Datacenter failure = data unavailable

Best For

- Development
- Test environments
- Non-critical data

---

## 2. ZRS (Zone-Redundant Storage)

Stores copies across multiple Availability Zones.

```text
Zone 1

Copy

Zone 2

Copy

Zone 3

Copy
```

Advantages

- Survives datacenter failure
- High availability
- Low latency

Best For

- Business-critical applications
- Regional resiliency

---

## 3. GRS (Geo-Redundant Storage)

Replicates data to another Azure region.

```text
Primary Region

3 Copies

↓

Secondary Region

3 Copies
```

Advantages

- Regional disaster recovery
- High durability

Disadvantages

- Higher cost
- Secondary region isn't immediately readable by default

Best For

- Disaster recovery
- Business continuity

---

## 4. GZRS (Geo-Zone Redundant Storage)

Combines ZRS + GRS.

```text
Primary Region

Zone 1

Zone 2

Zone 3

↓

Secondary Region

3 Copies
```

Advantages

- Datacenter protection
- Regional protection
- Highest durability
- Highest availability

Disadvantages

- Highest cost

Best For

- Banking
- Healthcare
- Enterprise systems

---

# Redundancy Comparison

| Feature | LRS | ZRS | GRS | GZRS |
|----------|-----|------|------|------|
|Copies in Datacenter|3|❌|3|❌|
|Multiple Zones|❌|✅|❌|✅|
|Secondary Region|❌|❌|✅|✅|
|Lowest Cost|✅|❌|❌|❌|
|Highest Availability|❌|✅|❌|✅|
|Disaster Recovery|❌|Limited|✅|✅|
|Best Overall Protection|❌|Good|Better|⭐ Best|

---

# Recommendation

## Scenario

Company

- Banking Application
- 24×7 availability
- Mission critical
- Moderate budget
- Disaster recovery required

Recommendation

✅ GZRS

Reason

- Protects against server failures
- Protects against datacenter failures
- Protects against regional failures
- Highest availability

---

# Recovery Concepts

## RPO (Recovery Point Objective)

Maximum acceptable amount of data loss.

Example

RPO = 10 minutes

Maximum data loss = 10 minutes

Smaller RPO = Better protection

---

## RTO (Recovery Time Objective)

Maximum acceptable downtime.

Example

RTO = 30 minutes

Application must recover within 30 minutes.

---

# Migration Tools

Azure provides several migration tools depending on the workload.

---

## Azure Migrate

Purpose

Discover, assess, and migrate:

- Servers
- Databases
- Applications
- Virtual Machines

Best For

- Large migrations
- Assessment
- Planning

---

## Azure Data Box

Physical appliance shipped by Microsoft.

Process

```text
Copy Data

↓

Data Box

↓

Ship Device

↓

Microsoft Uploads Data
```

Best For

- Hundreds of TBs
- Poor internet connectivity

---

## AzCopy

Command-line tool.

Copies data between:

- Local computer
- Azure Blob Storage
- Azure Files

Example

```bash
azcopy copy "C:\Data" "https://storage.blob.core.windows.net/container"
```

Best For

- Fast uploads
- Automation
- Bulk transfers

---

## Azure Storage Explorer

GUI tool.

Can

- Upload files
- Download files
- Manage Blob Storage
- Manage File Shares

Best For

- Administrators
- Developers
- Manual management

---

## Azure File Sync

Synchronizes on-premises Windows Server file shares with Azure Files.

Architecture

```text
Windows Server

↓

Azure File Sync

↓

Azure Files
```

Benefits

- Cloud backup
- Hybrid storage
- Local caching
- Easy migration

---

# Migration Checklist

## Existing Virtual Machines

✅ Azure Migrate

---

## 500 TB Backup

✅ Azure Data Box

---

## Upload 100 GB Files

✅ AzCopy

---

## Browse Storage Account

✅ Storage Explorer

---

## Hybrid File Server

✅ Azure File Sync

---

# Migration Decision Table

| Scenario | Recommended Tool |
|-----------|------------------|
| Assess servers before migration | Azure Migrate |
| Offline migration of huge datasets | Azure Data Box |
| Fast command-line uploads | AzCopy |
| GUI management of storage | Storage Explorer |
| Synchronize on-prem file servers | Azure File Sync |

---

# AZ-900 Exam Tips

## Blob Storage

- Unstructured data
- Images
- Videos
- Backups

---

## Azure Files

- SMB/NFS file shares
- Shared folders
- Lift-and-shift file servers

---

## Managed Disks

- VM storage
- High performance
- Persistent block storage

---

## Queue Storage

- Messaging
- Asynchronous processing

---

## Table Storage

- NoSQL
- Key-value storage

---

## LRS

- Three copies
- One datacenter
- Lowest cost

---

## ZRS

- Multiple Availability Zones
- High availability

---

## GRS

- Secondary region
- Disaster recovery

---

## GZRS

- Zones + Region replication
- Highest durability
- Best resiliency

---

## Azure Migrate

- Assessment + Migration

---

## Azure Data Box

- Offline migration

---

## AzCopy

- CLI uploads

---

## Storage Explorer

- GUI management

---

## Azure File Sync

- Hybrid file synchronization

---

# 30-Second Revision

- **Blob Storage** → Images, videos, backups
- **Azure Files** → Shared file server
- **Managed Disks** → VM storage
- **Queue Storage** → Messaging
- **Table Storage** → NoSQL key-value
- **LRS** → Cheapest, one datacenter
- **ZRS** → Multiple Availability Zones
- **GRS** → Cross-region disaster recovery
- **GZRS** → Zones + Region (best protection)
- **Azure Migrate** → Assess & migrate workloads
- **Data Box** → Offline migration
- **AzCopy** → Fast CLI data transfer
- **Storage Explorer** → GUI storage management
- **Azure File Sync** → Hybrid file server
