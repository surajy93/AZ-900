# AZ-900 Notes: Azure Networking, Hybrid Connectivity & DNS

## Azure Networking Overview

Azure networking connects users, applications, and on-premises infrastructure securely.

Core networking services:

- Virtual Network (VNet)
- Subnets
- Network Security Groups (NSG)
- VPN Gateway
- ExpressRoute
- Azure DNS
- Azure Load Balancer
- Azure Application Gateway
- Azure Firewall
- Azure Bastion

---

# Azure Virtual Network (VNet)

A Virtual Network (VNet) is your own private network inside Azure.

Think of it as your company's office network, but hosted in Microsoft's cloud.

Example:

```text
Azure Virtual Network

├── Subnet-Web
│      ├── Web VM
│      └── App Service Environment
│
├── Subnet-App
│      ├── API VM
│      └── AKS
│
└── Subnet-Database
       └── Azure SQL Managed Instance
```

Benefits

- Secure communication
- Network isolation
- Internet connectivity
- On-premises connectivity
- Azure resource communication

---

# Subnets

Subnets divide a VNet into smaller logical networks.

Example

```text
VNet

├── Web Subnet
├── App Subnet
└── Database Subnet
```

Benefits

- Better security
- Easier management
- Traffic separation

---

# Network Security Groups (NSG)

NSGs control inbound and outbound traffic.

Example

```text
Internet

      │

NSG Rules

Allow HTTPS (443)

Allow SSH (22)

Block Everything Else

      │

Virtual Machine
```

Example Rules

| Priority | Source | Port | Action |
|----------|---------|------|--------|
|100|Internet|443|Allow|
|200|Admin IP|22|Allow|
|300|Any|Any|Deny|

---

# VPN Gateway

VPN Gateway connects on-premises networks to Azure using the public Internet.

Encryption

✅ IPSec

Architecture

```text
Office

   │
Encrypted VPN Tunnel
   │
Internet
   │
Azure VPN Gateway
   │
Azure Virtual Network
```

Advantages

- Low cost
- Quick deployment
- Secure encrypted traffic
- Good for branch offices

Disadvantages

- Internet latency
- Performance depends on ISP
- Less predictable

---

# ExpressRoute

ExpressRoute provides a dedicated private connection to Azure.

Traffic does NOT travel over the public Internet.

Architecture

```text
Office

     │

Private MPLS Circuit

     │

ExpressRoute

     │

Azure Virtual Network
```

Advantages

- Very low latency
- Higher bandwidth
- More reliable
- Private connectivity
- Better SLA

Disadvantages

- Expensive
- Longer deployment
- Requires connectivity provider

---

# VPN Gateway vs ExpressRoute

| Feature | VPN Gateway | ExpressRoute |
|----------|-------------|--------------|
|Connection|Internet|Private circuit|
|Encryption|Yes|Optional|
|Latency|Medium|Very Low|
|Reliability|Good|Excellent|
|Bandwidth|Lower|Higher|
|Cost|Low|High|
|Deployment|Easy|Complex|
|Best For|Small/Medium Business|Enterprise|

---

# Decision Matrix

## Scenario 1

Company:

- 50 employees
- One office
- Budget conscious

Recommendation

✅ VPN Gateway

Reason

- Low cost
- Easy deployment
- Secure enough

---

## Scenario 2

Company

- Global bank
- Thousands of users
- Mission critical applications
- Financial regulations

Recommendation

✅ ExpressRoute

Reason

- Highest reliability
- Low latency
- Private connection
- Better performance

---

## Scenario 3

Healthcare Organization

Requirements

- Secure patient data
- Reliable connectivity
- Disaster recovery

Recommendation

Hybrid

```text
Primary

ExpressRoute

Backup

VPN Gateway
```

Reason

ExpressRoute handles normal traffic.

VPN provides failover.

---

# Cost vs Reliability Tradeoff

| Requirement | Best Choice |
|-------------|------------|
|Lowest cost|VPN Gateway|
|Lowest latency|ExpressRoute|
|Highest reliability|ExpressRoute|
|Quick setup|VPN Gateway|
|Mission critical workloads|ExpressRoute|
|Branch offices|VPN Gateway|

---

# Azure DNS

Azure DNS hosts DNS records for your applications.

DNS converts

```text
www.contoso.com

↓

20.45.xx.xx
```

Without DNS

Users would need to remember IP addresses.

---

# Public DNS

Used for internet-facing applications.

Example

```text
User

www.contoso.com

↓

Azure DNS

↓

Public IP

↓

Web Application
```

Examples

- company.com
- api.company.com
- shop.company.com

---

# Private DNS

Private DNS resolves names only inside Azure Virtual Networks.

Example

```text
Web Server

↓

db.internal.local

↓

Private DNS Zone

↓

Database
```

Benefits

- Hidden from Internet
- Better security
- Internal communication

---

# DNS Strategy

Application

- Public Website
- Internal API
- Database

Architecture

```text
Internet Users

      │

Azure DNS

www.contoso.com

      │

Application Gateway

      │

Web App

      │

Private DNS

api.internal.local

      │

API

      │

Private DNS

db.internal.local

      │

Database
```

Public

- Website
- API Gateway

Private

- API
- Database
- Backend services

Benefits

- Public services stay accessible
- Internal services remain protected
- Easier management

---

# Azure Load Balancer

Distributes network traffic across multiple servers.

Example

```text
Users

     │

Load Balancer

  │     │     │

 VM1  VM2  VM3
```

Benefits

- High availability
- Better performance
- Automatic failover

Layer

✅ Layer 4

---

# Azure Application Gateway

Layer 7 load balancer.

Features

- URL routing
- SSL termination
- Web Application Firewall (WAF)

Example

```text
Internet

      │

Application Gateway

 ├── /shop

 ├── /login

 └── /api
```

---

# Azure Firewall

Centralized firewall service.

Provides

- Network filtering
- Threat protection
- Logging
- Application filtering

---

# Azure Bastion

Securely access Azure VMs without exposing RDP or SSH ports.

Instead of

```text
Internet

↓

VM Port 3389
```

Use

```text
Internet

↓

Azure Bastion

↓

Virtual Machine
```

Benefits

- No public IP required
- Improved security
- Browser-based access

---

# Troubleshooting Flowchart

## Problem

On-premises users cannot reach Azure application.

```text
Start

↓

Can user access Internet?

↓

NO

↓

Fix ISP or local network

↓

YES

↓

Can VPN/ExpressRoute connect?

↓

NO

↓

Check Gateway status

↓

Check Shared Keys

↓

Check ExpressRoute Circuit

↓

YES

↓

Can Azure VNet reach VM?

↓

NO

↓

Check Route Tables

↓

Check NSGs

↓

Check Firewall

↓

YES

↓

Can VM respond?

↓

NO

↓

Check VM Running

↓

Check OS Firewall

↓

Check Service Status

↓

YES

↓

Check DNS Resolution

↓

Wrong IP?

↓

Fix DNS Record

↓

Application Works
```

---

# Common Connectivity Issues

| Problem | Possible Cause |
|----------|----------------|
|Cannot connect to Azure|VPN down|
|Slow performance|Internet congestion|
|High latency|Using VPN instead of ExpressRoute|
|Cannot resolve hostname|DNS configuration|
|VM unreachable|NSG blocking traffic|
|Gateway disconnected|Incorrect shared key|
|Private service inaccessible|Private DNS missing|
|RDP not working|Use Azure Bastion|

---

# AZ-900 Exam Tips

## VPN Gateway

- Uses public Internet
- IPSec encrypted
- Cost effective
- Small and medium businesses

---

## ExpressRoute

- Private connection
- Lowest latency
- Highest reliability
- Enterprise workloads

---

## Azure DNS

- Public DNS
- Private DNS
- Name resolution

---

## Azure Load Balancer

- Layer 4
- TCP/UDP
- High availability

---

## Application Gateway

- Layer 7
- HTTP/HTTPS
- WAF
- URL routing

---

## Azure Firewall

- Central firewall
- Network security
- Threat protection

---

## Azure Bastion

- Secure RDP/SSH
- No public IP
- Browser-based access

---

# 30-Second Revision

- **VNet** → Private Azure network
- **Subnet** → Smaller network inside VNet
- **NSG** → Firewall rules for subnets/VMs
- **VPN Gateway** → Secure Internet connection
- **ExpressRoute** → Dedicated private connection
- **Azure DNS** → Domain name resolution
- **Private DNS** → Internal name resolution
- **Load Balancer** → Layer 4 traffic distribution
- **Application Gateway** → Layer 7 load balancing + WAF
- **Azure Firewall** → Managed network firewall
- **Azure Bastion** → Secure VM access without public IP
