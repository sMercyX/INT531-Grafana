# Host / Node Golden Signals Runbook

---

## Table of Contents
1. Availability
2. Saturation
3. General Response Guidelines

---

## Availability

### Alert: HostDown

**Severity:** Critical  
**Meaning:** Node exporter is unreachable (`up == 0`).

#### Immediate Checks
- Ping host or check cloud console
- Verify VM or physical server status
- Check hypervisor or provider health

#### Diagnosis
- Power failure
- Kernel panic
- Network outage

#### Mitigation
- Restart host if possible
- Migrate workloads
- Restore from backup node

#### Escalation
- Page infrastructure team immediately

---

## Saturation

### Alert: HighCPUUsage / HighMemoryUsage / DiskSpaceLow

**Severity:** Warning → Critical if unresolved  
**Meaning:** Host resources are under pressure.

#### Diagnosis
- Traffic spike
- Resource leaks
- Log or data growth

#### Mitigation
- Restart heavy services
- Scale workloads
- Free disk space

---

## General Response Guidelines
- Assume all services on host are impacted
- Prioritize recovery over root cause during incident
- Perform postmortem after stabilization
