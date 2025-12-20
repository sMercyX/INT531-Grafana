# Host / Node Golden Signals Runbook

---

## Table of Contents
1. Availability
2. Saturation
3. General Response Guidelines

---

## 1. Availability

### Alert Name & Description
**Alert:** `HostDown`  
**Description:** Node exporter is unreachable (`up == 0`), indicating the host may be down or unreachable.

### Symptoms
- All services on the host are unreachable
- No metrics from node_exporter
- Sudden disappearance of host metrics

### Possible Causes
- Host power failure
- Kernel panic or OS crash
- Network outage
- Hypervisor or cloud provider failure

### Troubleshooting Steps
1. Ping the host or check SSH connectivity  
2. Verify VM or physical server status via hypervisor or cloud console  
3. Check provider or hypervisor health dashboard  

### Mitigation / Resolution Steps
- Restart host if possible
- Migrate workloads to another node
- Restore services from a healthy node or backup

### Escalation Path
- Infrastructure / Platform Team (Immediate)

### Rollback Instructions
- Not applicable (infrastructure-level incident)

### Post-mortem Link
- TBD / To be documented

---

## 2. Saturation

### Alert Name & Description
**Alert:** `HighCPUUsage` / `HighMemoryUsage` / `DiskSpaceLow`  
**Description:** Host resource utilization exceeds safe thresholds.

### Symptoms
- Slow response times across services
- Increased latency and error rates
- Disk write failures or out-of-memory events

### Possible Causes
- Traffic spike
- Resource leaks
- Log or data growth
- Mis-sized workloads

### Troubleshooting Steps
1. Check host resource dashboards (CPU, memory, disk)
2. Identify top resource-consuming processes
3. Review recent workload or traffic changes

### Mitigation / Resolution Steps
- Restart heavy services
- Scale workloads to other nodes
- Free disk space or rotate logs

### Escalation Path
- Infrastructure / SRE Team

### Rollback Instructions
- Roll back recent workload deployments if applicable

### Post-mortem Link
- TBD / To be documented

---

## 3. General Response Guidelines
- Assume all services on the host are impacted
- Prioritize recovery over root cause analysis during incident
- Perform post-mortem after stabilization
