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

## 1. Availability

### Alert Name & Description
**Alert:** `DatabaseDown`  
**Description:** Database exporter is unreachable (`up == 0`), indicating database or host failure.

### Symptoms
- Application cannot connect to database
- No database metrics available
- Increased application errors

### Possible Causes
- Database crash
- Host down
- Disk full
- Network or credential misconfiguration

### Troubleshooting Steps
1. Check Prometheus targets page
2. Verify database process is running
3. Confirm host availability
4. Validate network connectivity and credentials

### Mitigation / Resolution Steps
- Restart database service
- Restart host if required
- Free disk space

### Escalation Path
- Database On-call (Immediate)

### Rollback Instructions
- Restore database from backup if necessary

### Post-mortem Link
- TBD / To be documented

---

## 2. Traffic

### Alert Name & Description
**Alert:** `DatabaseHighConnections`  
**Description:** Active database connections are near the configured limit.

### Symptoms
- New connections rejected
- Increased query latency
- Application connection errors

### Possible Causes
- Connection leaks
- Retry storms
- Connection pool misconfiguration

### Troubleshooting Steps
1. Check active connection metrics
2. Identify top connection sources
3. Review application connection pool settings

### Mitigation / Resolution Steps
- Restart offending applications
- Increase max connections temporarily

### Escalation Path
- Backend / Database Team

### Rollback Instructions
- Roll back recent application changes causing connection surge

### Post-mortem Link
- TBD / To be documented

---

## 3. Latency

### Alert Name & Description
**Alert:** `DatabaseHighLatency`  
**Description:** Database query latency exceeds acceptable thresholds.

### Symptoms
- Slow API responses
- Increased request timeouts
- High query execution times

### Possible Causes
- Missing indexes
- Lock contention
- Disk I/O bottlenecks

### Troubleshooting Steps
1. Identify slow or long-running queries
2. Check lock and I/O metrics
3. Review recent schema changes

### Mitigation / Resolution Steps
- Kill long-running queries
- Scale database resources
- Optimize queries after incident

### Escalation Path
- Database Team

### Rollback Instructions
- Roll back schema or migration changes

### Post-mortem Link
- TBD / To be documented

---

## 4. Errors

### Alert Name & Description
**Alert:** `DatabaseQueryErrors`  
**Description:** Database query failures detected.

### Symptoms
- Failed queries
- Application errors
- Permission or schema errors

### Possible Causes
- Invalid schema changes
- Permission misconfiguration
- Corrupt data

### Mitigation / Resolution Steps
- Roll back schema changes
- Fix permissions
- Restart database if required

### Escalation Path
- Database Team

### Rollback Instructions
- Restore previous schema or backup

### Post-mortem Link
- TBD / To be documented

---

## 5. Error Budget

### Alert Name & Description
**Alert:** `DatabaseErrorBudgetBurn`  
**Description:** Database SLO is at risk due to rapid error budget consumption.

### Mitigation / Resolution Steps
- Freeze deployments
- Reduce database load

### Escalation Path
- SRE / Engineering Lead

### Rollback Instructions
- Roll back recent changes contributing to instability

### Post-mortem Link
- TBD / To be documented

---

## 6. Saturation

### Alert Name & Description
**Alert:** `DatabaseHighSaturation`  
**Description:** CPU, memory, or disk I/O saturation detected.

### Mitigation / Resolution Steps
- Scale vertically
- Throttle workloads

### Escalation Path
- Database / Infrastructure Team

### Rollback Instructions
- Revert recent load-increasing changes

### Post-mortem Link
- TBD / To be documented

---

## 7. General Response Guidelines
- Treat database incidents as highest priority
- Communicate early with backend team
