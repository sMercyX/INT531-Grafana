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

## Availability

### Alert: ServiceDown

**Severity:** Critical  
**Meaning:** Prometheus cannot scrape the backend service (`up == 0`). The service is unavailable.

#### Immediate Checks
- Check Prometheus Targets page
- Verify backend pod / container / VM status
- Check recent deployments or crashes
- Validate network and ingress configuration

#### Diagnosis
- Application crash or panic
- Host failure
- Misconfigured health check
- Network or firewall issue

#### Mitigation
- Restart backend service
- Roll back recent deployment
- Restore network connectivity

#### Escalation
- Page backend on-call immediately
- Escalate to infrastructure team if host-related

---

## Traffic

### Alert: LowTraffic

**Severity:** Info (Contextual)  
**Meaning:** Backend is receiving unusually low request volume.

> ⚠️ Not critical by itself, but relevant during incidents.

---

## Latency

### Alert: HighLatency

**Severity:** Warning → Critical if persistent  
**Meaning:** P95 backend latency exceeds SLO threshold.

#### Immediate Checks
- Inspect latency (p50 / p95 / p99)
- Correlate with traffic and error rate
- Identify slow endpoints

#### Diagnosis
- Downstream dependency slowness
- CPU or memory saturation
- Inefficient queries or logic

#### Mitigation
- Scale backend replicas
- Restart unhealthy instances
- Reduce load if necessary

#### Escalation
- Page on-call if latency continues to increase

---

## Errors

### Alert: HighErrorRate

**Severity:** Critical  
**Meaning:** 5xx error rate exceeds SLO (1%).

#### Immediate Checks
- Check error rate dashboard
- Inspect backend logs
- Check database and downstream services

#### Diagnosis
- Application bug
- Dependency outage
- Invalid configuration

#### Mitigation
- Roll back deployment
- Restart service
- Disable failing features

#### Escalation
- Page backend team immediately

---

## Error Budget

### Alert: BackendErrorBudgetBurn

**Severity:** Critical  
**Meaning:** Error budget is burning rapidly.

#### Mitigation
- Freeze deployments
- Focus on reliability over new changes
- Reduce load

---

## Saturation

### Alert: BackendHighSaturation

**Severity:** Critical  
**Meaning:** Backend resources are saturated.

#### Mitigation
- Scale horizontally
- Increase resource limits
- Apply rate limiting

---

## General Response Guidelines
- Acknowledge critical alerts immediately
- Prefer rollback over risky fixes
- Capture metrics and timeline for postmortem
