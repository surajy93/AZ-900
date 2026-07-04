# AZ-900 Notes: Azure Monitoring, Alerts & Operational Excellence

## Azure Monitoring Overview

Azure provides several monitoring tools that help you:

- Monitor infrastructure
- Monitor applications
- Collect logs and metrics
- Detect failures
- Receive alerts
- Improve performance
- Optimize costs

Core monitoring services:

- Azure Monitor
- Log Analytics
- Application Insights
- Alerts
- Action Groups
- Azure Advisor
- Azure Service Health

---

# Azure Monitoring Architecture

```text
Users
   │
Applications
   │
Virtual Machines
   │
Azure Resources
   │
──────────────────────────
│     Metrics           │
│     Logs              │
│     Traces            │
──────────────────────────
        │
Azure Monitor
        │
 ├── Log Analytics
 ├── Application Insights
 ├── Alerts
 └── Dashboards
```

---

# Azure Monitor

Azure Monitor is the **central monitoring service** in Azure.

It collects:

- Metrics
- Logs
- Events
- Performance data

Example

```text
Virtual Machine

↓

CPU Usage

↓

Azure Monitor

↓

Alert
```

Azure Monitor can monitor:

- Virtual Machines
- Azure SQL
- Storage Accounts
- App Services
- AKS
- Networking

---

# Metrics

Metrics are **numerical measurements** collected over time.

Examples

- CPU %
- Memory Usage
- Disk IOPS
- Network Throughput
- Requests per Second

Example

```text
CPU Usage

10%

20%

45%

90%

95%
```

Metrics are:

- Lightweight
- Near real-time
- Ideal for alerts

---

# Logs

Logs contain **detailed records of events**.

Example

```text
2026-07-04

User Login

Status = Success

Location = Mumbai
```

Logs answer questions like:

- What happened?
- Who performed the action?
- When did it occur?

---

# Azure Log Analytics

Log Analytics stores and analyzes logs.

It uses **Kusto Query Language (KQL)**.

Example

```kusto
AzureActivity
| where ActivityStatus == "Failed"
```

Can analyze:

- VM logs
- Security logs
- Azure Activity Logs
- Diagnostic Logs

Benefits

- Powerful searching
- Troubleshooting
- Trend analysis

---

# Application Insights

Application Insights monitors applications.

Tracks:

- Requests
- Response time
- Exceptions
- Dependencies
- Availability

Example

```text
User

↓

Website

↓

Application Insights

↓

Request Time

↓

Database Calls

↓

Exceptions
```

Ideal for:

- Web applications
- APIs
- Microservices

---

# Azure Alerts

Alerts automatically notify administrators when conditions are met.

Example

```text
CPU > 80%

↓

Alert Triggered

↓

Email

↓

SMS

↓

Teams

↓

Webhook
```

Alerts can be based on:

- Metrics
- Logs
- Activity Logs

---

# Action Groups

Action Groups define **what happens after an alert**.

Example

```text
Alert

↓

Action Group

├── Email
├── SMS
├── Teams
├── Logic App
└── Webhook
```

One Action Group can be reused by many alerts.

---

# Azure Advisor

Azure Advisor provides **best practice recommendations**.

Categories

- Cost
- Security
- Performance
- Reliability
- Operational Excellence

Example Recommendations

- Resize idle VMs
- Enable backups
- Enable MFA
- Use Reserved Instances

Benefits

- Reduce costs
- Improve performance
- Increase reliability

---

# Azure Service Health

Service Health reports Azure platform issues.

Shows

- Regional outages
- Planned maintenance
- Service incidents
- Health advisories

Example

```text
Azure Region

↓

Storage Outage

↓

Azure Service Health

↓

Notification
```

Use it to determine if the problem is **Microsoft's infrastructure** rather than your application.

---

# Monitoring Strategy

## Scenario

An online shopping application.

Architecture

```text
Users

↓

Azure Front Door

↓

App Service

↓

Azure SQL Database

↓

Storage Account
```

Monitoring Strategy

### Azure Monitor

Monitor:

- CPU
- Memory
- Network
- Availability

---

### Application Insights

Track:

- Page Load Time
- API Calls
- Exceptions
- Failed Requests
- User Sessions

---

### Log Analytics

Store

- VM Logs
- Application Logs
- Security Logs

Analyze with KQL.

---

### Azure Alerts

Trigger alerts for:

- CPU > 80%
- Memory > 85%
- Failed Requests > 5%
- Database Unavailable

---

### Action Groups

Notify

- DevOps Team
- Operations Team
- SMS
- Email
- Microsoft Teams

---

### Azure Advisor

Review weekly

Recommendations

- Reduce VM size
- Improve security
- Optimize storage

---

### Azure Service Health

Monitor

- Regional outages
- Planned maintenance
- Azure incidents

---

# Complete Monitoring Flow

```text
Azure Resources

↓

Azure Monitor

↓

Metrics + Logs

↓

Application Insights

↓

Log Analytics

↓

Alert Rules

↓

Action Groups

↓

Operations Team
```

---

# Outage Scenario

## Problem

Users report:

> Website is unavailable.

---

## Step 1

Check

✅ Azure Service Health

Question

Is Azure experiencing an outage?

If Yes

Problem is Microsoft's infrastructure.

Wait for Azure recovery or fail over to another region.

---

## Step 2

If Azure is healthy

Check

✅ Azure Monitor

Look for

- CPU
- Memory
- Network
- Availability

Question

Is infrastructure overloaded?

---

## Step 3

Infrastructure looks healthy

Check

✅ Application Insights

Look for

- Failed Requests
- Slow Responses
- Exceptions

Question

Is the application failing?

---

## Step 4

Need detailed investigation

Open

✅ Log Analytics

Run KQL queries.

Look for

- Error messages
- Failed logins
- Dependency failures

---

## Step 5

Determine root cause

Examples

- Database unavailable
- Disk full
- High CPU
- Network timeout

---

## Step 6

Alerts notify engineers automatically.

Action Groups

↓

Email

↓

SMS

↓

Teams

↓

Webhook

---

## Step 7

After recovery

Review

✅ Azure Advisor

Implement recommendations to prevent recurrence.

---

# Which Tool Should I Check First?

| Situation | Tool |
|------------|------|
| Azure regional outage | Azure Service Health |
| High CPU | Azure Monitor |
| Slow website | Application Insights |
| Error logs | Log Analytics |
| Best practices | Azure Advisor |
| Automatic notifications | Azure Alerts |

---

# Alert Severity Levels

| Severity | Meaning | Example |
|----------|----------|----------|
| Sev 0 | Critical | Entire application unavailable |
| Sev 1 | High | Database offline |
| Sev 2 | Medium | CPU above 90% |
| Sev 3 | Low | Disk usage above 75% |
| Sev 4 | Informational | Backup completed |

---

# Example Alert Rules

## CPU Alert

Condition

```text
CPU > 80%

Duration

5 Minutes
```

Action

Notify Operations Team

---

## Disk Alert

Condition

```text
Disk Usage > 90%
```

Action

Create Support Ticket

---

## Website Availability

Condition

```text
Availability < 99%
```

Action

Notify DevOps Team

---

## Database Alert

Condition

```text
Connection Failures > 10
```

Action

Escalate immediately

---

# Escalation Model

```text
Alert

↓

Operations Engineer

↓

No Response (15 min)

↓

Senior Engineer

↓

No Response (30 min)

↓

Cloud Architect

↓

No Response (1 hour)

↓

IT Manager
```

---

# Production Alerting Model

## Critical (Sev 0)

Examples

- Website down
- Database unavailable
- Region outage

Notify

- SMS
- Phone
- Teams
- Email

Immediate escalation

---

## High (Sev 1)

Examples

- High latency
- VM failures

Notify

- Operations Team
- DevOps Team

Escalate after 15 minutes

---

## Medium (Sev 2)

Examples

- CPU > 85%
- Memory > 90%

Notify

- Email
- Teams

Review during business hours

---

## Low (Sev 3)

Examples

- Storage reaching 75%
- SSL certificate expires in 30 days

Notify

Email only

---

## Informational (Sev 4)

Examples

- Backup completed
- VM restarted
- Deployment finished

Store in logs

No escalation

---

# Azure Monitoring Comparison

| Tool | Primary Purpose |
|------|-----------------|
| Azure Monitor | Collect metrics and logs |
| Log Analytics | Query and analyze logs |
| Application Insights | Monitor applications |
| Azure Alerts | Trigger notifications |
| Action Groups | Execute alert actions |
| Azure Advisor | Optimization recommendations |
| Azure Service Health | Azure platform health |

---

# AZ-900 Exam Tips

## Azure Monitor

- Central monitoring platform
- Collects metrics and logs

---

## Log Analytics

- Stores logs
- Uses KQL
- Root cause analysis

---

## Application Insights

- Application performance monitoring
- Exceptions
- Dependencies
- Availability

---

## Azure Alerts

- Metric alerts
- Log alerts
- Activity log alerts

---

## Action Groups

- Email
- SMS
- Webhooks
- Teams
- Logic Apps

---

## Azure Advisor

Provides recommendations for:

- Cost
- Security
- Reliability
- Performance
- Operational Excellence

---

## Azure Service Health

Shows:

- Service outages
- Planned maintenance
- Regional incidents

---

# 30-Second Revision

- **Azure Monitor** → Central monitoring platform
- **Metrics** → Numerical performance data
- **Logs** → Detailed event records
- **Log Analytics** → Query logs with KQL
- **Application Insights** → Monitor web apps and APIs
- **Azure Alerts** → Trigger notifications
- **Action Groups** → Define alert responses
- **Azure Advisor** → Best practice recommendations
- **Azure Service Health** → Azure platform status
- **Severity Levels** → Sev 0 (Critical) → Sev 4 (Informational)
