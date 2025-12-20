# Database Golden Signals Runbook

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

### Alert: DatabaseDown

**Severity:** Critical  
**Meaning:** Database exporter is unreachable (`up == 0`).

#### Immediate Checks
- Check Prometheus Targets
- Verify database process
- Check host availability
- Validate network and credentials

#### Diagnosis
- Database crash
- Host down
- Disk full
- Network misconfiguration

#### Mitigation
- Restart database
- Restart host if required
- Free disk space

#### Escalation
- Page database on-call immediately

---

## Traffic

### Alert: DatabaseHighConnections

**Severity:** Critical  
**Meaning:** Active connections are near limit.

#### Diagnosis
- Connection leaks
- Retry storms
- Pool misconfiguration

#### Mitigation
- Restart offending apps
- Increase max connections temporarily

---

## Latency

### Alert: DatabaseHighLatency

**Severity:** Critical  
**Meaning:** Query latency exceeds acceptable limits.

#### Diagnosis
- Missing indexes
- Lock contention
- Disk I/O bottleneck

#### Mitigation
- Kill long-running queries
- Scale resources
- Optimize queries post-incident

---

## Errors

### Alert: DatabaseQueryErrors

**Severity:** Critical  
**Meaning:** Query failures detected.

#### Mitigation
- Roll back schema changes
- Fix permissions
- Restart database if needed

---

## Error Budget

### Alert: DatabaseErrorBudgetBurn

**Severity:** Critical  
**Meaning:** Database SLO at risk.

#### Mitigation
- Freeze deployments
- Reduce load

---

## Saturation

### Alert: DatabaseHighSaturation

**Severity:** Critical  
**Meaning:** CPU / memory / disk I/O saturation.

#### Mitigation
- Scale vertically
- Throttle workloads

---

## General Response Guidelines
- Treat DB incidents as highest priority
- Communicate early with backend team

