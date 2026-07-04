# AZ-900 Notes: Azure Compute Services & Resiliency

## Azure Compute Services Overview

Azure provides multiple compute options depending on how much control and management you need.

| Service | Best For | You Manage | Azure Manages |
|----------|----------|------------|---------------|
| Virtual Machines | Full control over OS and software | OS, patches, apps | Physical infrastructure |
| Containers | Portable applications and microservices | Container image | Infrastructure and orchestration |
| Azure App Service | Web apps and APIs | Application code | OS, runtime, scaling |
| Azure Functions | Event-driven serverless workloads | Function code | Infrastructure, scaling, execution |

---

# Decision Matrix

## Choosing the Right Compute Service

| Requirement | Virtual Machines | Containers | Azure App Service | Azure Functions |
|-------------|------------------|------------|-------------------|-----------------|
| Full OS control | ✅ | ❌ | ❌ | ❌ |
| Legacy applications | ✅ | ❌ | ❌ | ❌ |
| Microservices | ❌ | ✅ | ✅ | ❌ |
| Web applications | ✅ | ✅ | ⭐ Best | ✅ |
| REST APIs | ✅ | ✅ | ⭐ Best | ✅ |
| Event-driven processing | ❌ | ❌ | ❌ | ⭐ Best |
| Automatic scaling | Limited | Yes | Yes | Excellent |
| Pay only when running | ❌ | ❌ | ❌ | ✅ |
| Startup time | Slow | Fast | Fast | Very Fast |

---

# Workload 1: E-commerce Website

## Requirements

- Public website
- REST APIs
- Authentication
- Automatic scaling
- SSL
- Custom domain

### Best Choice

✅ Azure App Service

### Why?

- No server management
- Built-in HTTPS
- Auto Scaling
- Easy deployment from GitHub
- Supports .NET, Node.js, Java, Python, PHP

Architecture

```text
Users
   │
Azure Front Door
   │
Azure App Service
   │
Azure SQL Database
```

---

# Workload 2: Video Processing System

## Requirements

- User uploads videos
- Process each upload
- Generate thumbnails
- Runs only when uploads occur

### Best Choice

✅ Azure Functions

### Why?

- Event-driven
- Runs only when needed
- No idle cost
- Automatically scales

Architecture

```text
Video Upload
      │
Azure Storage
      │
Blob Created Event
      │
Azure Function
      │
Generate Thumbnail
```

---

# Workload 3: Banking System

## Requirements

- Custom software
- Windows Server
- Full OS control
- Third-party software
- Compliance

### Best Choice

✅ Azure Virtual Machines

### Why?

- Complete control
- Install any software
- Supports legacy applications
- Custom networking

Architecture

```text
Users
   │
Load Balancer
   │
VM Scale Set
   │
SQL Server
```

---

# Containers

Containers package:

- Application
- Libraries
- Dependencies

Advantages:

- Lightweight
- Fast startup
- Portable
- Ideal for microservices

Azure services:

- Azure Kubernetes Service (AKS)
- Azure Container Apps
- Azure Container Instances (ACI)

Example

```text
Container

├── Application
├── Runtime
├── Libraries
└── Dependencies
```

---

# Virtual Machine Scale Sets (VMSS)

VM Scale Sets automatically create or remove VMs based on demand.

Example

```text
Users
   │
Load Balancer
   │
───────────────
│     │      │
VM1  VM2   VM3
```

Benefits

- Auto Scaling
- Load balancing
- High availability
- Reduced manual management

Use when:

- Traffic varies
- Large web applications
- APIs

---

# Availability Sets

Availability Sets protect against hardware failures inside one datacenter.

They distribute VMs across:

- Fault Domains
- Update Domains

Example

```text
Datacenter

Fault Domain 1
    VM1

Fault Domain 2
    VM2
```

If one rack loses power:

VM2 remains online.

Use when:

- Running multiple VMs in one datacenter
- Protecting against hardware failures

---

# Availability Zones

Availability Zones are physically separate datacenters within the same Azure region.

Example

```text
Region

├── Zone 1
├── Zone 2
└── Zone 3
```

Each zone has:

- Independent power
- Independent networking
- Independent cooling

Benefits

- Survives datacenter failures
- Higher availability
- Better disaster resilience

---

# Failure Scenario Comparison

## Scenario

A hardware rack fails.

### Without Availability Set

```text
VM
│
Hardware Failure
│
Application Down
```

Result:

❌ Downtime

---

### With Availability Set

```text
Rack 1
VM1

Rack 2
VM2
```

Rack 1 fails.

VM2 continues running.

Result:

✅ Application stays online.

---

## Scenario

Entire datacenter loses power.

### Without Availability Zones

```text
Datacenter

VM1
VM2

Power Failure

Everything Offline
```

Result:

❌ Complete outage

---

### With Availability Zones

```text
Zone 1
VM1

Zone 2
VM2

Zone 1 fails

Zone 2 continues serving users
```

Result:

✅ Service remains available.

---

## Scenario

Website traffic suddenly increases.

### Without Scale Set

```text
Users
   │
Single VM

CPU = 100%
```

Result

- Slow website
- Possible crashes

---

### With VM Scale Set

```text
Users
    │
Load Balancer
    │
VM1 VM2 VM3 VM4 VM5
```

Azure automatically adds more VMs.

Result

✅ Application scales automatically.

---

# Architecture Walkthrough

## Smart Factory Monitoring System

### Goal

Collect machine temperature and vibration data from factory equipment and detect anomalies using AI.

Architecture

```text
Factory Machines
        │
 IoT Sensors
        │
 Azure IoT Edge
        │
 Azure IoT Hub
        │
 Azure Functions
        │
 Azure AI Service
        │
 Power BI Dashboard
```

---

## Why Each Component?

### Azure IoT Edge

Runs workloads locally on factory devices.

Benefits

- Low latency
- Continues working even if internet is unavailable
- Reduces cloud traffic

---

### Azure IoT Hub

Receives telemetry securely.

Responsibilities

- Device management
- Secure communication
- Message routing

---

### Azure Functions

Processes incoming sensor data.

Reasons

- Event-driven
- Automatic scaling
- Pay only when events occur

---

### Azure AI Service

Analyzes sensor data.

Examples

- Predict machine failures
- Detect anomalies
- Forecast maintenance

---

### Power BI

Displays

- Machine health
- Alerts
- Dashboards
- Reports

---

# Which Service Should I Choose?

| Situation | Recommended Service |
|-----------|---------------------|
| Need full control over OS | Virtual Machine |
| Run microservices | Containers |
| Host web app or API | Azure App Service |
| Event-driven processing | Azure Functions |
| Auto-scale virtual machines | VM Scale Sets |
| Protect against rack failures | Availability Sets |
| Protect against datacenter failures | Availability Zones |
| Edge computing | Azure IoT Edge |

---

# AZ-900 Exam Tips

### Virtual Machine

- Infrastructure as a Service (IaaS)
- Full OS control
- User manages operating system

---

### Azure App Service

- Platform as a Service (PaaS)
- Host web apps and APIs
- No server management

---

### Azure Functions

- Serverless
- Event-driven
- Pay per execution

---

### Containers

- Lightweight
- Portable
- Excellent for microservices

---

### VM Scale Sets

- Automatic scaling
- Multiple VM instances
- Load-balanced applications

---

### Availability Sets

- Protect against hardware/rack failures
- Same datacenter

---

### Availability Zones

- Protect against complete datacenter failures
- Multiple physical datacenters within one region

---

# 30-Second Revision

- **Virtual Machine** → Full OS control
- **Containers** → Portable microservices
- **Azure App Service** → Web apps & APIs
- **Azure Functions** → Event-driven serverless
- **VM Scale Sets** → Auto Scaling
- **Availability Sets** → Rack protection
- **Availability Zones** → Datacenter protection
- **IoT Edge** → Process data near devices
- **Azure AI Service** → AI-powered predictions and analytics
