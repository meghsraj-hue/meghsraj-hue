# Detailed Technical Case Studies

> **Evidence note:** Historical experience, illustrative technical design exercises, and suggested evidence are explicitly distinguished below. This document does not claim that illustrative configurations were deployed at ICICI Bank.


### Enterprise Infrastructure & Technology Delivery

TECHNICAL CASE STUDIES | DESIGN DECISIONS | TROUBLESHOOTING | BUSINESS IMPACT  
Meghna Shah  •  Enterprise IT / Technical Program Management  •  Fremont, California  •  github.com/meghsraj-hue  

### Evidence standard: actual work versus technical demonstration

This is a technical case-study portfolio, not a resume. “Documented experience” sections are grounded in the supplied ICICI Bank master resume. “Illustrative design exercise” sections show how a technical program manager would evaluate a scenario; values and configurations in these exercises are examples, NOT claims about ICICI Bank production systems. Specific server models, RAM, cores, storage TB, firewall brands, switch speeds, vendor contract amounts and the exact AI tools used in microcredential courses were not supplied. They must be confirmed before being presented as historical facts.  

## CASE STUDY 01 | Enterprise backup recovery: 65% → 99% success


### Business incident / problem

Documented experience (ICICI Bank, 2008–2013): mission-critical Oracle and other enterprise workloads faced recurring backup failures and recovery exposure. Veritas NetBackup and EMC Data Domain were used in enterprise data protection; backup success improved from approximately 65% to 99%.  

### Technical investigation and decision chain

- Classify failed jobs by client, policy, schedule, backup window, operating system, database type and failure reason; correlate NetBackup job logs with server, storage and network events.
- Check media/master/client compatibility, NetBackup agent versions, Oracle backup integration, DNS resolution, TCP reachability, credentials, filesystem capacity, storage mount paths and backup concurrency.
- Determine whether the bottleneck is source disk throughput, client CPU/RAM, network bandwidth, backup appliance ingest, retention/cleanup, or overlapping job schedules.
- Review EMC Data Domain deduplication, retention policy, projected growth, restore throughput, replication/DR needs and vendor support matrix before approving changes.
- Execute controlled changes, rerun failed policies, test sample restores, record evidence, assign vendor actions, and monitor post-change job-success trends.

### Concrete technical proof to attach

Business outcome: documented improvement is +34 percentage points in backup success (65% to 99%). This reduces the proportion of unsuccessful backup jobs from 35% to 1%; it is NOT proof of a particular dollar amount of avoided loss.  

## CASE STUDY 02 | Server sizing and storage selection for a high-availability service

Documented experience: requirements gathering, capacity planning, storage/server compatibility, Oracle workload analysis, backup growth, recovery objectives and cross-team infrastructure readiness. Exact historic hardware specifications are not recorded.  

### Illustrative design exercise — explicitly NOT an ICICI configuration

Example requirement: an application must support 10,000 concurrent sessions, 99.95% availability target, 2 TB of active database data, 20% annual growth, 4-hour RTO and 15-minute RPO. These are fictional design inputs for demonstrating method, not historical figures.  

### Capacity calculation hiring managers can challenge

Illustrative only: 2 TB × (1.20)^3 = 3.456 TB after 3 years before indexing, logs, replicas and free-space headroom. With 30% planning headroom, target usable capacity ≈ 4.49 TB. For a 1 TB full backup over a dedicated effective 1 Gbps link, theoretical transfer floor ≈ 2.22 hours before protocol overhead, deduplication and contention. Validate actual measured throughput rather than sizing from link speed alone.  

### Vendor / project coordinator ownership

Build an RFP comparison using supported CPU/RAM configurations, usable-versus-raw storage, SAN/NAS interoperability, vendor HCL, support SLAs, rack units, power draw, dual PSU, lead time, warranty, renewal cost and migration downtime. Coordinate architecture signoff, PO/contract owners, delivery, rack/stack readiness, security, integration tests and production acceptance; do not claim procurement signatory authority unless verified.  

## CASE STUDY 03 | Networking, firewall, patching and compatibility gates

Documented experience: network readiness, infrastructure coordination, production incidents and upgrade/patch governance. Exact switch/router/firewall product names and personally configured network devices are not established.  

### Illustrative network path and fault isolation

User → DNS → edge/WAF or firewall → load balancer → application tier → database tier → backup/monitoring networks. Review copper Ethernet (Cat6/6A), fiber (multimode/single-mode), access vs aggregation switches, L2 VLANs, L3 routing, WAN connectivity, redundant uplinks, 1/10/25/40/100GbE as applicable; these are technology options, not claimed historic installations.  
- Create source–destination–protocol–port matrix; confirm business owner, least-privilege rule, network zone, change ticket, expiry and rollback.
- Test DNS, TCP handshake, TLS certificates, time synchronization, routing/ACLs, load-balancer health probes and asymmetric-path issues with engineering.
- Compare OS, firmware, hypervisor, Oracle DB, middleware, backup agent, OEM agent and vendor interoperability matrices before patching.
- Review vulnerability scan findings, patch severity, compensating controls, maintenance window, backup/snapshot readiness and post-patch smoke tests.
- Capture evidence: traceroute or mtr (where permitted), nslookup/dig, curl or test connection, firewall change ID, packet capture owned by network team, before/after latency.
Business impact logic: prevent avoidable release failures, reduce incident duration and maintain secure access to customer-facing systems. Quantify only with incident logs, downtime minutes and change success records.  

## CASE STUDY 04 | Oracle Enterprise Manager: 300+ database monitoring

Documented experience (ICICI Bank, 2013–2016): deployed and operated Oracle Enterprise Manager across approximately 250–300 production databases; installed/upgraded/patched OEM agents and management servers; analyzed CPU, memory, tablespace growth, storage, listener health and thresholds. Master resume reports improvement in enterprise availability from 98.5% to 99.95% in the monitoring period.  

### Example diagnostic sequence: tablespace exhaustion risk

- OEM alert flags accelerating tablespace growth; validate alert threshold against actual utilization, autoextend settings and growth rate.
- Correlate database activity, filesystem/ASM capacity, SAN free space, batch schedules and application deployment history with DBAs and storage owners.
- Forecast time-to-full using growth slope; compare adding capacity, cleanup/archival, index maintenance and application-side remediation.
- Raise capacity/change request; assign DBA/storage/network/vendor tasks; plan maintenance and rollback; test application connectivity after remediation.
- Tune actionable alerts and runbooks, confirm incident routing and track recurrence over subsequent cycles.
Proof artifacts: anonymized OEM metric trend, threshold policy, capacity forecast, incident RCA, agent compatibility checklist, post-change health report. Note: 99.95% is a reported broader platform metric; do not attribute all of it solely to one alert.  

## CASE STUDY 05 | Customer-service platform reliability: IVR, WFM and Genesys

Documented experience (ICICI Bank, 2016–2022): technology delivery for enterprise customer-service platforms; Genesys contact center, IVR, workforce management, call recording, Oracle databases, application infrastructure and external vendors. Portfolio outcomes: 99.95% availability; MTTR reduced 45%; SLA compliance 92% → 99%; customer wait time reduced 18%; CSAT improved 10%.  
Example production problem: call-routing / application integration degradation  
Illustrative incident narrative based on documented platform responsibilities, not a verified single historical incident: customers experience longer IVR waits after a release. Separate symptoms by telephony carrier/SIP trunk, IVR routing, application API, Oracle database latency, Genesys service health, WFM staffing assumptions and network packet loss. Convene bridge with owner per tier; use correlated timestamps and synthetic calls to isolate the failure domain.  

### Cross-functional execution and UAT

- Define customer journey acceptance: incoming call → IVR menu → authentication → queue selection → agent transfer → CRM/call recording completion.
- Test positive, negative, timeout, retry, failover, peak concurrency and integration scenarios; validate PII masking and role-based access.
- Review dependency matrix across Genesys, IVR, WFM, Oracle, app servers, network, firewall, monitoring and support vendors.
- Schedule release with change advisory approval; confirm cutover steps, rollback trigger, communications, staffing and hypercare coverage.
- Track first-call resolution, abandoned calls, queue wait time, agent availability, MTTR, SLA, CSAT and production defects.

### Availability math — separate illustrative calculation

99.95% availability corresponds to approximately 21.6 minutes of downtime per 30-day month, assuming continuous 24×7 service and a simple uptime calculation. It is NOT proof of actual measured monthly downtime without the underlying monitoring logs.  
Business value: service reliability supports customer access, employee productivity, transaction continuity and operational resilience.  

## CASE STUDY 06 | Vendor management and IT project coordinator operating model

Documented experience: external vendor engagement, technical escalations, service readiness, requirements, cross-team coordination, executive communication, release governance and 24×7 operations. The following deliverables turn those responsibilities into auditable project evidence.  

### Vendor escalation example — illustrative

Issue: a storage/backup appliance upgrade cannot proceed because the deployed backup-client version is absent from the vendor compatibility matrix. Action: pause change; request vendor written support position; coordinate version inventory and staging test; identify patch sequence and rollback; rebaseline milestone; obtain approval and execute validation. Result to measure: avoided failed change, time-to-resolution, and confirmed supportability. Do not claim this exact event occurred unless backed by a ticket.  

## CASE STUDY 07 | UAT → production timeline and release quality

Documented experience: coordinated QA/UAT, integration testing, release readiness, change governance, production deployment and hypercare across applications and infrastructure.  
Sample traceability record: REQ-014 “agent can retrieve customer interaction” → UAT-014a valid customer → UAT-014b unauthorized role denied → UAT-014c database timeout handled → linked defects → owner → evidence → business signoff. All IDs and scenarios are illustrative.  

## CASE STUDY 08 | Hands-on AWS/DevOps projects: reproducible technical proof

The supplied Cloud Project Report documents 20 hands-on implementations completed separately from the ICICI Bank historical roles. These are real project write-ups; they should be published with sanitized configurations, source code, screenshots, test results and troubleshooting notes when available.  
Do not publish secrets, access keys, client/customer data, bank architecture diagrams or copied employer intellectual property.  

## CASE STUDY 09 | AI microcredentials: tools and business impact

Confirmed credentials from supplied screenshot: AI for Scrum Masters; AI for Product Owners; Get Started with AI Prompt Engineering; AI for Product Discovery and Strategy. Exact tool names taught in each course are not present in the screenshot or the supplied project documents. The list below is a TOOL-VALIDATION WORKSHEET, not a claim that each brand was taught or used.  


