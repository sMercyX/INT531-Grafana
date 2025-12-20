# Backend API Golden Signals Runbook

---

## Table of Contents
1. Availability
2. Traffic
3. Latency
4. Errors
5. Error Budget
6. Saturation
7. General Response Guidelines

---

## 1. Availability

### Alert Name & Description
**Alert:** `ServiceDown`  
**Description:** Prometheus cannot scrape the backend service (`up == 0`).

### Symptoms
- API endpoints unreachable
- Increased frontend errors
- No backend metrics available

### Possible Causes
- Application crash or panic
- Host failure
- Misconfigured health check
- Network or firewall issue

### Troubleshooting Steps
1. Check Prometheus targets page
2. Verify backend container or VM status
3. Review recent deployments
4. Validate network and ingress configuration

### Mitigation / Resolution Steps
- Restart backend service
- Roll back recent deployment
- Restore network connectivity

### Escalation Path
- Backend On-call
- Infrastructure Team (if host-related)

### Rollback Instructions
- Re-deploy previous stable backend version

### Post-mortem Link
- TBD / To be documented

---

## 2. Traffic

### Alert Name & Description
**Alert:** `LowTraffic`  
**Description:** Backend receives unusually low request volume.

### Symptoms
- Drop in request rate
- Reduced frontend activity

### Possible Causes
- Upstream routing issues
- Frontend outage
- Load balancer misconfiguration

### Mitigation / Resolution Steps
- Verify upstream components
- Restore routing

### Post-mortem Link
- TBD / To be documented

---

## 3. Latency

### Alert Name & Description
**Alert:** `HighLatency`  
**Description:** P95 backend latency exceeds SLO threshold.

### Symptoms
- Slow API responses
- Increased frontend latency

### Possible Causes
- Downstream dependency slowness
- CPU or memory saturation
- Inefficient queries or logic

### Troubleshooting Steps
1. Inspect latency percentiles
2. Identify slow endpoints
3. Check dependency health

### Mitigation / Resolution Steps
- Scale backend replicas
- Restart unhealthy instances
- Reduce load if required

### Escalation Path
- Backend On-call

### Rollback Instructions
- Roll back performance-impacting changes

### Post-mortem Link
- TBD / To be documented

---

## 4. Errors

### Alert Name & Description
**Alert:** `HighErrorRate`  
**Description:** Backend 5xx error rate exceeds SLO.

### Symptoms
- API failures
- Frontend error pages

### Possible Causes
- Application bug
- Dependency outage
- Invalid configuration

### Mitigation / Resolution Steps
- Roll back deployment
- Restart service
- Disable failing features

### Escalation Path
- Backend Team (Immediate)

### Rollback Instructions
- Restore last stable backend version

### Post-mortem Link
- TBD / To be documented

---

## 5. Error Budget

### Alert Name & Description
**Alert:** `BackendErrorBudgetBurn`  
**Description:** Error budget is being consumed rapidly.

### Mitigation / Resolution Steps
- Freeze deployments
- Focus on reliability
- Reduce load

### Escalation Path
- SRE / Engineering Lead

### Rollback Instructions
- Roll back recent changes

### Post-mortem Link
- TBD / To be documented

---

## 6. Saturation

### Alert Name & Description
**Alert:** `BackendHighSaturation`  
**Description:** Backend resources are saturated.

### Mitigation / Resolution Steps
- Scale horizontally
- Increase resource limits
- Apply rate limiting

### Escalation Path
- Backend / Platform Team

### Rollback Instructions
- Revert load-increasing changes

### Post-mortem Link
- TBD / To be documented

---

## 7. General Response Guidelines
- Acknowledge critical alerts immediately
- Prefer rollback over risky fixes
- Capture metrics and timeline for post-mortem
