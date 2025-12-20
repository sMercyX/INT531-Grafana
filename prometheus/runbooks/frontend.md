# Frontend Golden Signals Runbook

---

## Table of Contents
1. Availability
2. Traffic
3. Latency
4. Errors
5. Error Budget
6. General Response Guidelines

---

## Availability

### Alert: FrontendServiceDown

**Severity:** Critical  
**Meaning:** Frontend service is unreachable.

#### Immediate Checks
- Check frontend service status
- Verify hosting / container platform
- Check DNS and networking

#### Mitigation
- Restart frontend
- Roll back recent deployment

#### Escalation
- Page frontend or DevOps on-call

---

## Latency

### Alert: FrontendHighLatency

**Severity:** Warning → Critical if sustained  
**Meaning:** P95 frontend latency exceeds threshold.

#### Diagnosis
- Backend slowness
- Network issues
- Heavy frontend rendering

#### Mitigation
- Verify backend health
- Scale frontend replicas

---

## Errors

### Alert: FrontendHighErrorRate

**Severity:** Critical  
**Meaning:** Frontend returning high rate of 5xx errors.

#### Diagnosis
- Backend API failures
- Broken frontend build

#### Mitigation
- Roll back frontend release
- Enable fallback or maintenance page

---

## Error Budget

### Alert: FrontendErrorBudgetBurn

**Severity:** Critical  
**Meaning:** Frontend SLO violation imminent.

#### Mitigation
- Freeze releases
- Focus on stability

---

## General Response Guidelines
- Communicate user impact clearly
- Coordinate with backend team
