# ☁️ AZ-900 Notes – Cloud Benefits, KPIs, and Trade-offs

---

# Why Do Companies Move to the Cloud?

Companies don't move to Azure just because it's "modern."

They move because it solves real business problems.

The five major cloud benefits are:

1. High Availability
2. Scalability
3. Reliability
4. Security
5. Manageability

---

# Example Business

Suppose a company owns an **Online Shopping Website**.

Current Setup (On-Premises)

```
Office

├── 2 Servers
├── Database
├── Network
└── Internet
```

Problems:

❌ Website goes down when server fails

❌ During sales, website becomes slow

❌ Hardware upgrades take weeks

❌ Manual software updates

❌ High maintenance cost

Let's see how Azure improves each area.

---

# 1. High Availability

## Definition

High Availability (HA) means **your application stays available even if something fails.**

The goal is to minimize downtime.

---

## On-Premises Example

```
Users
   |
Server

(Server crashes)

Website Down ❌
```

Only one server.

If it fails,

everything stops.

---

## Azure Example

```
Users

      |

----------------------

Server A

Server B

Server C

----------------------
```

If Server A fails,

Azure automatically routes traffic to Server B.

Users may not even notice.

---

## Real Example

Amazon during Diwali Sale.

If one server crashes,

customers should still be able to place orders.

---

## Azure Services

- Availability Zones
- Availability Sets
- Load Balancer

---

## Exam Tip

Keyword

"Application should continue working even if one server fails."

Answer

**High Availability**

---

# 2. Scalability

## Definition

Scalability means increasing or decreasing resources based on demand.

Cloud lets you add resources quickly.

---

## Types

### Vertical Scaling

Increase the power of one machine.

```
Before

4 CPU

↓

After

16 CPU
```

Same server.

More power.

---

### Horizontal Scaling

Add more servers.

```
Before

Server

↓

After

Server 1

Server 2

Server 3
```

More servers.

---

## Example

Normal Day

100 users

One server.

Black Friday Sale

100,000 users

Azure automatically creates more servers.

Sale ends

Azure removes extra servers.

You only pay while they're running.

---

## Exam Tip

Keyword

"Increase servers automatically during traffic spikes."

Answer

**Scalability**

---

# 3. Reliability

## Definition

Reliability means the system consistently performs correctly and recovers from failures.

Cloud providers use redundant infrastructure.

---

## Example

Suppose one Azure data center loses power.

Azure can run your application from another region or availability zone (depending on how you've designed it).

Users continue using the application.

---

## Difference Between Reliability and Availability

Availability

Can users access the application?

Reliability

Does the application continue working correctly over time, including during failures?

---

## Exam Tip

Keyword

"System continues operating despite failures."

Answer

**Reliability**

---

# 4. Security

## Definition

Security protects systems, applications, and data from threats.

Azure provides many built-in security features.

---

## Examples

Identity Protection

Azure Active Directory

Encryption

Data encrypted at rest and in transit.

Firewall

Blocks unauthorized access.

DDoS Protection

Protects against denial-of-service attacks.

Role-Based Access Control (RBAC)

Only authorized users can perform specific actions.

---

## Example

Without Cloud

Company hires security team.

Maintains firewall.

Manages updates.

---

With Azure

Microsoft secures the physical infrastructure.

Customer secures applications, identities, and data according to the shared responsibility model.

---

## Exam Tip

Keyword

"Protect company data."

Answer

**Security**

---

# 5. Manageability

## Definition

Manageability means how easy it is to monitor, configure, update, and operate cloud resources.

---

## Example

Without Cloud

Administrator visits every server.

Installs updates manually.

Checks logs manually.

---

Azure

Administrator manages everything from the Azure Portal, Azure CLI, or PowerShell.

Automation can deploy resources and apply updates.

---

## Example

Deploy 50 Virtual Machines.

Without Cloud

Several days.

Azure

Automated deployment in minutes.

---

## Azure Services

- Azure Portal
- Azure CLI
- Azure PowerShell
- Azure Resource Manager (ARM)
- Azure Monitor

---

# Summary of Cloud Benefits

| Benefit | Meaning | Example |
|----------|---------|---------|
| High Availability | Minimize downtime | Backup server takes over |
| Scalability | Add/remove resources | Add servers during sales |
| Reliability | Continue operating during failures | Workloads survive hardware failures |
| Security | Protect systems and data | Encryption, firewall, RBAC |
| Manageability | Easier administration | Azure Portal and automation |

---

# KPI Dashboard for Cloud Adoption

A KPI (Key Performance Indicator) measures whether moving to the cloud is delivering value.

---

## Technical KPIs

### Availability

Target

99.99%

Meaning

Website is available almost all the time.

---

### Downtime

Measure

Minutes of downtime each month.

Lower is better.

---

### Response Time

How quickly pages load.

Example

Before Cloud

5 seconds

After Cloud

1.2 seconds

---

### CPU Utilization

Average CPU usage.

Shows whether servers are underused or overloaded.

---

### Auto Scaling Success

Did Azure automatically add servers during high traffic?

---

### Backup Success Rate

Percentage of successful backups.

Target

100%

---

### Security Incidents

Number of attacks detected.

Goal

Reduce incidents over time.

---

# Business KPIs

### Infrastructure Cost

Compare

Before Azure

₹10,00,000/month

After Azure

₹7,50,000/month

---

### Deployment Time

Before

3 days

After

20 minutes

---

### Customer Satisfaction

Measure

- Reviews
- Ratings
- Support tickets

---

### Revenue

Did faster website performance increase sales?

---

### Employee Productivity

Developers spend less time managing servers and more time building features.

---

# Example Dashboard

| KPI | Before Cloud | After Cloud |
|------|--------------|-------------|
| Availability | 98% | 99.99% |
| Downtime | 6 hours/month | 10 minutes/month |
| Deployment Time | 3 days | 20 minutes |
| Infrastructure Cost | ₹10L | ₹7.5L |
| Customer Satisfaction | 82% | 95% |
| Response Time | 5 sec | 1 sec |

---

# Cloud Trade-offs

Cloud has many advantages, but it isn't perfect.

Understanding these trade-offs is important for AZ-900.

---

# 1. Cost Trade-offs

Cloud usually reduces upfront costs (CapEx), but costs can grow if resources aren't managed.

Example

Create 100 Virtual Machines.

Forget to delete them.

Azure continues billing.

---

### Common Cost Challenges

- Idle Virtual Machines
- Unused Storage
- High outbound network traffic
- Overprovisioned resources

---

### Solution

- Monitor costs
- Use Azure Cost Management
- Delete unused resources
- Use budgets and alerts

---

# 2. Governance Complexity

As cloud environments grow,

managing resources becomes more difficult.

Example

500 Developers

Everyone creates resources.

Problems

- Duplicate resources
- Inconsistent naming
- Security risks
- Unexpected costs

---

### Azure Solutions

- Azure Policy
- RBAC
- Management Groups
- Resource Tags

---

# 3. Sustainability Constraints

Cloud providers use energy-efficient data centers.

However,

cloud resources still consume electricity.

Example

Running hundreds of idle Virtual Machines wastes energy and money.

---

### Best Practices

- Delete unused resources
- Auto-scale resources
- Shut down development VMs after office hours
- Use efficient architectures

---

# 4. Vendor Lock-in

Building everything with one cloud provider's proprietary services can make migration difficult.

Example

Company uses many Azure-specific services.

Moving later to AWS may require redesigning applications.

---

# 5. Compliance & Data Residency

Some countries require certain data to remain within national borders.

Organizations must choose cloud regions carefully and comply with regulations.

---

# Best Practices

✅ Use auto-scaling

✅ Monitor costs regularly

✅ Apply governance policies

✅ Automate deployments

✅ Enable backups

✅ Use least-privilege access (RBAC)

✅ Monitor security continuously

---

# AZ-900 Exam Keywords

| Keyword | Answer |
|----------|--------|
| Keep application running during failures | High Availability |
| Add servers automatically | Scalability |
| Consistent operation despite failures | Reliability |
| Protect systems and data | Security |
| Easy monitoring and automation | Manageability |
| Measure cloud success | KPI |
| Unexpected monthly bill | Cost Management |
| Control cloud resources | Governance |
| Energy-efficient usage | Sustainability |
| Follow legal/regulatory requirements | Compliance |

---

# Memory Tricks

🏥 **High Availability** → Hospital is always open

📈 **Scalability** → Add more checkout counters when customers increase

🔄 **Reliability** → Even if one machine fails, the business continues

🔒 **Security** → Lock the doors and verify identity

🛠️ **Manageability** → One dashboard to manage everything

📊 **KPI** → Report card showing whether cloud adoption is successful

💰 **Cost Trade-off** → Pay only for what you use—but remember to stop paying for what you don't use

🏛️ **Governance** → Rules that keep everyone using the cloud consistently and securely
