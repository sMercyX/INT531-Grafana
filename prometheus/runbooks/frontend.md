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

## 1. Availability

### Alert Name & Description
**Alert:** `FrontendServiceDown`  
**Description:** Frontend service is unreachable and not responding to health checks.

### Symptoms
- Users cannot access the website
- HTTP request timeouts or connection refused
- Frontend health check endpoint is down

### Possible Causes
- Frontend container or service crashed
- Host VM is unreachable
- Networking or DNS misconfiguration
- Recent deployment caused service failure

### Troubleshooting Steps
1. Check frontend service status  
   - Verify frontend container is running  
   - Check Docker or orchestration status  

2. Check infrastructure  
   - Verify VM is reachable (ping / SSH)  
   - Check firewall and network rules  

3. Check logs  
   - Inspect frontend container logs  
   - Look for crash loops or startup errors  

### Mitigation / Resolution Steps
- Restart frontend service or container
- Roll back to previous stable frontend version
- Restore known-good configuration

### Escalation Path
- Frontend Team On-call
- DevOps / SRE On-call

### Rollback Instructions
- Re-deploy last stable frontend image
- Restore previous environment variables

### Post-mortem Link
- TBD / To be documented

---

## 2. Traffic

### Alert Name & Description
**Alert:** `FrontendTrafficDrop`  
**Description:** Sudden drop or spike in frontend request traffic.

### Symptoms
- Significant drop in page views
- Sudden change in request rate
- Users report blank pages or incomplete loads

### Possible Causes
- DNS or load balancer issues
- Backend API outage
- Misconfigured routing or CDN

### Troubleshooting Steps
1. Check traffic dashboards in Grafana  
2. Verify load balancer / ingress routing  
3. Confirm backend API availability  

### Mitigation / Resolution Steps
- Restore routing configuration
- Scale frontend replicas if traffic spikes
- Coordinate with network team

### Escalation Path
- Frontend Team
- Infrastructure / Network Team

### Rollback Instructions
- Revert recent routing or configuration changes

### Post-mortem Link
- TBD / To be documented

---

## 3. Latency

### Alert Name & Description
**Alert:** `FrontendHighLatency`  
**Description:** P95 frontend response latency exceeds the defined threshold.

### Symptoms
- Slow page loads
- Unresponsive UI interactions
- Elevated P95 / P99 latency metrics

### Possible Causes
- Backend API slowness
- Network congestion
- Heavy frontend rendering or blocking scripts

### Troubleshooting Steps
1. Check latency dashboards  
2. Identify slow endpoints  
3. Verify backend response times  

### Mitigation / Resolution Steps
- Scale frontend replicas
- Reduce frontend load temporarily
- Coordinate backend optimization

### Escalation Path
- Frontend Team
- Backend Team

### Rollback Instructions
- Roll back recent frontend changes impacting performance

### Post-mortem Link
- TBD / To be documented

---

## 4. Errors

### Alert Name & Description
**Alert:** `FrontendHighErrorRate`  
**Description:** High rate of 5xx or user-visible errors.

### Symptoms
- Users see error pages
- Increased 5xx error rate
- Failed API calls from frontend

### Possible Causes
- Backend API failures
- Broken frontend build or configuration
- Incorrect environment variables

### Troubleshooting Steps
1. Check error dashboards  
2. Inspect frontend and backend logs  
3. Verify backend dependencies  

### Mitigation / Resolution Steps
- Roll back frontend release
- Enable fallback UI or maintenance page
- Restart frontend service

### Escalation Path
- Frontend Team
- Backend Team

### Rollback Instructions
- Re-deploy previous stable frontend version

### Post-mortem Link
- TBD / To be documented

---

## 5. Error Budget

### Alert Name & Description
**Alert:** `FrontendErrorBudgetBurn`  
**Description:** Error budget burn rate is high; SLO violation imminent.

### Symptoms
- Rapid error budget consumption
- Frequent alerts across golden signals

### Possible Causes
- Unstable recent deployment
- Accumulated system issues
- Infrastructure instability

### Troubleshooting Steps
1. Review SLO and burn rate dashboards  
2. Correlate recent deployments and config changes  

### Mitigation / Resolution Steps
- Freeze new deployments
- Focus on system stability and reliability
- Address top error contributors

### Escalation Path
- SRE / Platform Team
- Engineering Lead

### Rollback Instructions
- Roll back recent changes contributing to instability

### Post-mortem Link
- TBD / To be documented

---

## 6. General Response Guidelines
- Communicate user impact clearly
- Prioritize customer-facing issues
- Coordinate across frontend, backend, and infrastructure teams
