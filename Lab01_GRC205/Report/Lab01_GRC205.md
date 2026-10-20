# Incident Response Planning Report

## Northbridge Skills Institute Ransomware Scenario

![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Course-GRC105-1f6feb)
![Domain](https://img.shields.io/badge/Domain-Incident%20Response-6f42c1)
![Severity](https://img.shields.io/badge/Severity-Critical-red)
![Framework](https://img.shields.io/badge/Framework-NIST%20SP%20800--61%20Rev.%203-blue)

---

## Document Control

| Field | Details |
|---|---|
| **Report title** | Incident Response Planning Report |
| **Organisation** | Northbridge Skills Institute, fictional |
| **Prepared by** | Ummulkhoyr Adebukola Shittu |
| **Student ID** | 2025/GCR/12699 |
| **Programme** | Governance, Risk, and Compliance |
| **Role** | Incident Response Lead |
| **Course** | GRC105 Incident Response Planning |
| **Incident start point** | Day 0, Monday, 08:45 WAT |
| **Report status** | Completed academic assignment |
| **Classification** | Academic use |

> **Repository note:** The source document is named `Lab 22 GRC205.docx`, while the assignment itself identifies the course as `GRC105`. This report preserves the course code stated in the assignment.

> **Scenario disclaimer:** Northbridge Skills Institute, its systems, people, contact details, incident records, and tabletop results are fictional and used solely for academic purposes.

---

## Executive Summary

This report presents a complete incident response plan for a critical ransomware incident affecting Northbridge Skills Institute. The incident disrupted access to learning materials and submissions, encrypted a finance workstation and file server, raised concerns about compromised Microsoft 365 and privileged service accounts, and created a possible data-exfiltration event involving approximately 1.2 GB of outbound traffic.

The incident was classified as **Critical** because it combined confirmed loss of system availability and integrity, possible exposure of learner and financial information, an unverified recovery environment, potential privileged-account misuse, and a time-sensitive online examination for 100 learners.

The response strategy prioritises:

1. Immediate containment of affected systems
2. Protection of backup and recovery assets
3. Preservation of forensic evidence
4. Investigation of suspected credential compromise and data theft
5. Activation of trusted, out-of-band communications
6. Validated restoration in business-priority order
7. Clear executive, legal, learner, and stakeholder communication
8. Post-incident learning through a structured tabletop exercise

The recommended recovery position is to avoid reopening the affected production environment. The disconnected Friday 17:00 backup is the preferred recovery candidate because it clearly predates the suspected phishing event. It must still pass isolated malware scanning, integrity verification, and functional testing before use.

The tabletop exercise showed that two success criteria were met, three were partly met, and one was not met. The most important gaps involved offline contact information, written backup-isolation procedures, independent learner-notification routes, timely evidence logging, restore testing, and server EDR coverage.

---

## 1. Assignment Context

### 1.1 Purpose

The purpose of this report is to demonstrate a structured, risk-based response to a ransomware incident using the incident response lifecycle:

1. **Preparation**
2. **Detection and Analysis**
3. **Containment, Eradication, and Recovery**
4. **Post-Incident Activity**

The report also aligns response activities with NIST Cybersecurity Framework 2.0 functions. Detect, Respond, and Recover form the core incident response activities, while Govern, Identify, and Protect support preparation and resilience.

### 1.2 Mission

Protect learner and staff information, preserve evidence, limit operational harm, and safely restore teaching and assessment services.

### 1.3 Objectives

- Contain malicious activity and prevent further spread
- Protect `BAK01`, the backup service account, and disconnected backup media
- Preserve volatile and non-volatile evidence
- Establish the scope of compromise
- Determine whether data exfiltration occurred
- Maintain accurate and trusted communications
- Support the examination go/no-go decision
- Restore verified services according to business priority
- Meet applicable legal and regulatory obligations
- Record lessons and corrective actions

### 1.4 Scope

The response covers:

- User endpoints
- `FIN-PC07`
- `FS01`
- `LMS01`
- `BAK01`
- Microsoft 365 identities and messaging
- Privileged and service accounts
- Network, proxy, endpoint, server, and cloud logs
- Third-party services holding learner information
- Learning, examination, admissions, and finance data
- Business continuity and stakeholder communications

---

## 2. Assumptions and Constraints

| ID | Assumption or Constraint |
|---|---|
| A1 | The applicable jurisdiction and data-protection law are not stated. Qualified legal counsel must confirm them. |
| A2 | Examination content and submissions are stored on `LMS01` and `FS01`. Some content may post-date the Friday backup. |
| A3 | The main learner contact list is on unavailable infrastructure, although tutors retain cohort phone numbers. |
| A4 | The institute has a Principal, Examinations Manager, Communications Officer, external legal adviser, three IT staff, and one security analyst. |
| A5 | Day -3 is Friday, Day -1 is Sunday, and all times are West Africa Time. |
| A6 | The IT staff comprise an operations lead, backup/infrastructure administrator, and helpdesk/endpoint technician. |
| A7 | The organisation has no incident response retainer at the start of the incident. |
| A8 | Proposed response times in this report are planning targets, not NIST-mandated deadlines. |

---

## 3. Incident Classification and Initial Assessment

### 3.1 Evidence Timeline

| ID | Time | Record | Assessment Status |
|---|---:|---|---|
| E01 | Day -1, 16:40 | Payroll attachment opened on `FIN-PC07` | Opening confirmed; execution remains a hypothesis |
| E02 | Day 0, 01:15 | Finance officer Microsoft 365 sign-in from unfamiliar IP and new device | Log confirmed; cause unresolved |
| E03 | 01:35 | `svc_backup` administrative logons to `FS01` and `BAK01` outside schedule | Log confirmed; misuse remains a hypothesis |
| E04 | 01:50 | Approximately 1.2 GB uploaded by HTTPS from `FIN-PC07` to unfamiliar cloud storage | Transfer confirmed; content unknown |
| E05 | 02:00 | Backup jobs for `FS01` and `LMS01` reported success | Report confirmed; recoverability unproven |
| E06 | 08:30 | Mass file changes on `FIN-PC07`; locked files and ransom note found on `FS01` | Confirmed |
| E07 | 08:40 | Portal login loads, but materials and submissions fail | Symptoms confirmed |
| E08 | 08:45 | Incident contact list on `FS01` inaccessible; phones operational | Confirmed |

### 3.2 Working Hypotheses

- **H1:** The payroll attachment executed and established the initial foothold.
- **H2:** The attacker obtained or reused the finance officer's credentials or session.
- **H3:** The attacker used `svc_backup` to access `FS01` and `BAK01`.
- **H4:** Data was transferred out of `FIN-PC07` before encryption.
- **H5:** `FIN-PC07` and `FS01` were encrypted, while the learning portal disruption is a dependency-related effect.

These hypotheses direct investigation but must not be treated as confirmed facts.

### 3.3 Alternative Explanations

| Event | Plausible Alternative | Verification Action |
|---|---|---|
| E02 | Legitimate remote work, a new device, or stolen token without password compromise | Review MFA, location history, device registration, session details, and user account activity |
| E03 | Planned maintenance, restore work, or a rescheduled job | Review change tickets, source address, commands, and administrator account activity |
| E04 | Cloud synchronisation, an update, or staff copying files to personal storage | Identify destination, transferred file types, historical traffic, and user intent |
| E05 | Backup succeeded but captured altered data, or the console was unreliable | Mount a restore point read-only in an isolated environment |
| E07 | Direct `LMS01` compromise or an unrelated technical fault | Inspect `LMS01`, dependencies, application logs, and network connectivity |

### 3.4 Unresolved Questions

- What data was included in the 1.2 GB transfer?
- What was the destination and who controlled it?
- Were E05 backups created before or after files were altered?
- Was `BAK01` modified or only accessed?
- Is `LMS01` compromised or dependent on unavailable content from `FS01`?
- Is the wider Microsoft 365 tenant compromised?
- Did the attacker establish persistence elsewhere?
- Are other endpoints or servers affected?

### 3.5 Incident Type and Suspected Vector

- **Incident type:** Ransomware with suspected data theft and account compromise
- **Suspected initial vector:** Phishing attachment opened on `FIN-PC07`
- **Potential lateral movement:** Misuse of `svc_backup`
- **Potential cloud compromise:** Unfamiliar Microsoft 365 sign-in
- **Potential exfiltration:** 1.2 GB outbound HTTPS transfer

### 3.6 Severity Matrix

| Level | Criteria | Response Expectation |
|---|---|---|
| **Critical** | Loss of availability, integrity, or confidentiality affecting critical services or sensitive data, with active spread, unproven recovery, or a fixed deadline at risk | Immediate full-team response and executive notification |
| **High** | Serious compromise of limited systems, spread stopped, and recovery proven | Rapid response within defined SLA and management notification |
| **Medium** | Isolated non-critical system, detected early, with no major outage or sensitive-data impact | Standard incident workflow |
| **Low** | Policy breach or blocked attempt with no material impact | Standard ticket and monitoring |

### 3.7 Selected Severity: Critical

The incident is classified as **Critical** because:

1. `FIN-PC07` and `FS01` are encrypted, learner services are disrupted, and an examination for 100 learners is imminent.
2. Learner, admissions, assessment, and finance information may be exposed.
3. A privileged service account may have been misused.
4. Backup integrity and recoverability have not been proven.
5. The Microsoft 365 environment and other hosts have not been cleared.
6. Server EDR coverage is incomplete, reducing confidence in scope assessment.

### 3.8 Asset Impact

| Category | Assets or Data |
|---|---|
| **Confirmed affected** | `FIN-PC07`, `FS01` |
| **Degraded** | `LMS01` and learner portal functionality |
| **Potentially affected** | `BAK01`, `svc_backup`, finance officer Microsoft 365 account, learner and finance data |
| **Trust unverified** | Microsoft 365 identity, email, network backups, privileged credentials |
| **Unknown** | Other endpoints and servers |
| **Priority protected asset** | Disconnected Friday 17:00 backup |

### 3.9 CIA Impact

- **Confidentiality:** Potentially affected, but data theft is not yet confirmed.
- **Integrity:** Confirmed affected on `FIN-PC07` and `FS01`; uncertain for backups, accounts, and `LMS01`.
- **Availability:** Confirmed affected across file and learning services.

---

## 4. Investigation Priorities

1. Stop encryption, lateral movement, and unauthorised access.
2. Protect `BAK01`, `svc_backup`, and the Friday backup.
3. Determine the examination decision before the revised 09:30 checkpoint.
4. Preserve evidence during containment.
5. Establish trusted communication routes.
6. Determine the full scope of affected systems and identities.
7. Investigate suspected data exfiltration.

### 4.1 Decision-Driven Investigation Questions

| Question | Evidence and Checks | Decision Impact |
|---|---|---|
| What data was taken? | Proxy data, destination ownership, EDR telemetry, file history, related traffic, user interview | Confirmed personal or financial data starts formal notification assessment |
| Was `svc_backup` misused and was `BAK01` changed? | Logon source, commands, job configuration, change tickets, administrator interview | Tampering shifts recovery to the disconnected Friday copy |
| Was the unfamiliar sign-in malicious and did the attachment execute? | Sign-in and MFA logs, mailbox rules, registered devices, message headers, EDR process tree | Confirmed compromise expands scope to Microsoft 365 and email trust |
| Is `LMS01` compromised? | Direct inspection, application logs, endpoint telemetry, dependency checks | A clean system may support a faster isolated learning service |
| Are other hosts affected? | EDR sweep, indicators of compromise, manual checks, privileged-account access history | Additional hosts expand containment, credential resets, and recovery work |

---

## 5. Incident Response Governance

### 5.1 Declaration

Anyone may report an incident. The security analyst validates and classifies it, while the Incident Manager formally declares the incident, records the time, and activates the appropriate response.

### 5.2 Escalation

- **Critical:** Activate the full CSIRT by phone and notify the executive sponsor immediately.
- **High:** Activate the Incident Manager, analyst, and IT operations; notify management within the defined SLA.
- **Medium/Low:** Manage through the standard ticketing process.
- Escalate immediately if scope grows, data theft is confirmed, an attacker issues threats, media enquiries are received, or recovery fails.

### 5.3 Emergency Authority

During a Critical or High incident:

- The Incident Manager may isolate systems, disable accounts, and block destinations without waiting for business approval.
- The analyst may isolate endpoints under delegated authority.
- The business owner must be consulted, but cannot delay urgent containment.
- Operational impact must be reported to the executive sponsor within one hour.

### 5.4 Documentation Requirements

The scribe maintains a WAT-timed incident log containing:

- Indicators and systems involved
- Actions performed
- Decisions and approvals
- Evidence and custody transfers
- Business impact
- Internal and external communications
- Recovery tests and acceptance decisions

### 5.5 Business Continuity Integration

A Critical incident affecting a critical function triggers coordination with the business owner and activation of continuity arrangements. The final BIA, RTO, and RPO should control restoration priorities. Until those values are formally approved, the report uses provisional recovery targets.

---

## 6. Cybersecurity Incident Response Team

| Role | Primary Responsibility | Deputy or Support |
|---|---|---|
| Incident Manager | Command, decisions, coordination, executive briefings | Named senior deputy |
| Security Analyst | Triage, threat analysis, EDR containment, hunting | IT Operations Lead |
| Forensics Specialist | Evidence collection, examination, chain of custody | Endpoint technician until external specialist arrives |
| IT Operations Lead | Network isolation, rebuilds, technical recovery | Cross-trained administrator |
| Backup Administrator | Protect `BAK01`, secure media, validate backups | IT Operations Lead |
| Business Owner | Business risk acceptance and return-to-service approval | Executive Sponsor |
| Legal and Privacy Adviser | Notification, regulatory, law-enforcement, and legal guidance | External counsel |
| Communications Lead | Staff, learner, public, and media communications | Trained deputy spokesperson |
| Executive Sponsor | Spending, external engagement, public statement, and ransom decisions | Designated executive deputy |
| Scribe | Chronology, evidence references, decision and action logs | Administrative support |

A handover rule should limit extended duty to approximately ten hours without relief.

### 6.1 RACI Matrix

**Key:** R = Responsible, A = Accountable, C = Consulted, I = Informed

| Activity | IM | SA | FS | ITO | BO | LP | CL | ES |
|---|---|---|---|---|---|---|---|---|
| Detection | A | R | I | R | I |  |  |  |
| Analysis | A | R | C | C | I | I |  | I |
| Containment | A/R | R | C | R | C | I | I | I |
| Evidence handling | A | C | R | C | I | C |  |  |
| Stakeholder communication | A | C |  | I | C | C | R | C |
| Reporting-obligation assessment | C | C | C |  | I | A/R | C | I |
| Eradication and recovery | A | R | C | R | C |  | I | I |
| Restoration approval | R | C | C | C | A/R | I | I | I |
| Closure and review | A/R | R | R | R | C | C | C | I |

---

## 7. Timed Incident Response Playbook

Actions 3 to 5 form a coordinated containment move at 08:55 to reduce the chance of alerting an active attacker before critical systems are isolated.

| Step | Time | Action | Owner | Approval or Check |
|---:|---|---|---|---|
| 1 | 08:45-08:50 | Declare Critical, open incident log, appoint scribe, phone CSIRT | IM | No prior approval; sponsor informed |
| 2 | 08:50-08:55 | Move to phones and voice bridge; avoid corporate email for incident details; instruct staff to stop using `FS01` and not shut down systems | CL and IM | IM |
| 3 | 08:55-09:00 | Isolate `FIN-PC07` through EDR, keep powered, photograph ransom note | SA | Confirm isolation and absence of proxy traffic |
| 4 | 08:55-09:05 | Export `svc_backup` logs, disable the account, isolate `BAK01`, pause jobs, secure Friday media | ITO and Backup Admin | IM; custody recorded |
| 5 | 08:55-09:05 | Network-isolate `FS01`; if isolation fails and files continue changing, power down and document evidence loss | ITO and Technician | IM |
| 6 | 09:05-09:20 | Export Microsoft 365 logs, revoke sessions, reset finance account from a clean device, block suspicious IP and destination, review rules and MFA | SA and ITO | IM |
| 7 | 09:10-09:30 | Create evidence register in volatility order | FS | IM |
| 8 | 09:15-09:40 | Conduct enterprise scope sweep and classify hosts as confirmed, suspected, clean, or unchecked | SA | IM |
| 9 | 09:30 | Brief executive, engage legal adviser, request external response support | IM and CL | ES |
| 10 | 09:30 | Revised examination go/no-go checkpoint; issue learner notice within 10 minutes | BO, advised by IM | BO; sponsor informed |
| 11 | 09:45-14:00 | Analyse endpoint evidence and attachment; identify malware; test hypotheses H1-H5 | FS and SA | IM |
| 12 | 12:00-17:00 | Reset privileged credentials, replace service account, segment critical servers, block phishing pattern, patch, expand EDR | ITO | IM |
| 13 | 14:00-20:00 | After verified imaging, rebuild affected systems from known-good images and remove persistence elsewhere | ITO and SA | IM |
| 14 | 15:00-Day 1 06:00 | Select and validate backup in isolation; restore `LMS01` and required `FS01` content first | Backup Admin and SA | IM |
| 15 | Day 1 06:00-08:45 | Begin phased return with enhanced monitoring | SA and BO | BO against acceptance criteria |
| 16 | Hour 24 | Produce status report, verify custody, set review date; keep incident open until full restoration | IM | Sponsor informed |

---

## 8. Evidence Management Plan

### 8.1 Evidence Register

| ID | Source | Collection Method | Collector | Integrity Control | Storage |
|---|---|---|---|---|---|
| EV-01 | `FIN-PC07` memory and disk | Memory capture while isolated, then forensic image | FS or interim technician | Hash at acquisition and verify every copy | Encrypted drive in locked cabinet |
| EV-02 | `FS01` logs, ransom note, and locked-file samples | Read-only export | FS | Hash each file | Same evidence store |
| EV-03 | Microsoft 365 sign-in and audit logs | Native export before session revocation | SA | Hash export | Same evidence store |
| EV-04 | Proxy logs for E04 transfer | Export relevant time window | SA | Hash export | Same evidence store |
| EV-05 | `BAK01` logs, configuration, and service-account activity | Read-only export; image after isolation | FS with Backup Admin | Hash export and image | Same store; `BAK01` remains offline |
| EV-06 | Phishing email, headers, and attachment | Native export with headers; never open in production | SA | Hash files | Locked and encrypted store |

### 8.2 Custody and Access Controls

- Record the actual acquisition date and time in WAT.
- Record hash algorithm and value at collection.
- Document every transfer with source, recipient, time, purpose, and signatures.
- Limit original-evidence access to the Incident Manager, Forensics Specialist, and named deputy.
- Require analysts to work from verified copies.
- Store evidence away from `FS01` in encrypted media.
- Log all access and witness physical transfers.
- Never invent missing collection times, hashes, or findings.

### 8.3 Containment Versus Evidence

The default approach is to isolate at the network layer, keep systems powered, and capture volatile evidence afterwards. Shutdown is a last resort when network isolation is impossible and encryption or attacker control continues.

Any evidence loss or operational disruption must record:

- What was lost or altered
- Why the decision was necessary
- Who approved it
- The time of the action
- The expected investigative effect

---

## 9. Eradication and Credential Security

### 9.1 Eradication Actions

- Remove malicious files, tasks, registry entries, services, and persistence.
- Hunt for unauthorised accounts, mailbox rules, MFA methods, remote tools, and scheduled tasks.
- Remove the phishing email from all mailboxes.
- Block the sender pattern, attachment indicators, IP addresses, and destinations.
- Rebuild systems rather than relying only on malware cleaning.
- Validate rebuilt systems with more than one security tool.
- Patch confirmed exploited weaknesses.
- Expand EDR and central logging to all servers.

### 9.2 Credential Response

Treat the following as exposed until proven otherwise:

- Finance officer Microsoft 365 identity
- `svc_backup`
- Accounts used on `FIN-PC07`, `FS01`, or `BAK01`
- Privileged identities that authenticated during the compromise window

Export necessary logs first, then revoke sessions and reset credentials from a known-clean device. Replace the service account, enforce least privilege, prohibit interactive logon, and store credentials in a secure vault.

---

## 10. Recovery Strategy

### 10.1 Examination Decision

The affected portal must not be reopened merely to preserve the examination schedule.

Available routes:

- **Route A:** Postpone the examination.
- **Route B:** Use a clean, isolated environment restored from a validated pre-incident backup.

The tabletop finding revises the checkpoint from 09:45 to **09:30**, with postponement as the default unless a validated environment is ready. Content created after the Friday backup may only be introduced from a verified clean source.

### 10.2 Restoration Order

1. Establish a trusted clean recovery environment.
2. Validate identity, `BAK01`, and recovery tooling.
3. Restore `LMS01` and required `FS01` learning content.
4. Restore remaining `FS01` shares.
5. Rebuild `FIN-PC07` and restore validated finance data.
6. Restore other services according to business priority.

### 10.3 Provisional Recovery Targets

| Target | Provisional Value |
|---|---|
| Critical-services recovery | Within 72 hours in limited and monitored form |
| Full restoration | Within 7 days |
| Recovery point | Friday at 17:00, approximately 63 hours 45 minutes before incident command began |
| Enhanced monitoring | At least 24 hours without recurrence before full confidence |

These values are provisional until supported by a formal Business Impact Analysis.

### 10.4 Backup Selection

The default recovery candidate is the disconnected Friday 17:00 backup because it predates E01 by approximately 47 hours 40 minutes and is separated from the affected environment. A more recent network backup may only be considered if it clearly predates E01 and passes the same validation procedure.

### 10.5 Backup Validation

Validation must occur in an isolated network:

1. Confirm backup provenance, timestamps, ownership, and custody.
2. Mount or restore read-only where possible.
3. Scan with multiple tools for ransomware artefacts, locked files, notes, and persistence.
4. Compare expected file counts and sizes.
5. Open representative samples.
6. Test user authentication.
7. Test access to learning materials.
8. Submit a test assessment.
9. Record results and obtain sign-off.

### 10.6 Acceptance Criteria

A limited or fully restored service requires:

- No identified persistence
- Rebuilt or independently validated hosts
- Reset exposed credentials
- Verified clean backup
- Completed integrity checks
- Successful functional testing
- Active EDR on restored servers
- Required legal and communication clearance
- Business-owner sign-off

Full production also requires closure of the initial entry route and a defined observation period without recurrence.

---

## 11. Communication and Escalation Plan

Corporate email is treated as potentially untrusted, so every stakeholder has an alternative channel.

| Stakeholder | Trigger | Owner | Primary / Alternative Channel | Approval | Frequency |
|---|---|---|---|---|---|
| Learners | Examination decision or service change | CL | SMS or email / tutor phone tree, website, notice board, official social page | ES, with BO for exam content | At decision, every 4 hours on Day 0, then daily |
| Management and sponsor | Critical declaration | IM | Phone then written note / voice bridge | IM | Hourly until containment, then every 4 hours |
| IT and security | Declaration or new instruction | IM | Voice bridge / in person | IM | Hourly |
| All staff | Stop-work or safety instruction | CL | SMS and phone tree / supervisors | IM | At declaration, then twice daily |
| Service providers | Tenant, log, product, or connectivity assistance | ITO | Verified support portal or phone / account manager | IM | Per ticket, with daily check |
| Legal and privacy | Critical declaration or personal-data concern | IM | Phone and secure external sharing | IM | Every 2 hours and on material findings |
| External response firm | Sponsor approval | IM | Verified phone and secure transfer / courier | ES | At engagement and agreed cadence |
| Media and public | Enquiry or public post | CL | Holding statement / official social page | ES with Legal | When facts materially change |
| Regulators and law enforcement | Legal advice or statutory trigger | LP | Official channel | ES | As legally required |

### 11.1 Executive Briefing

> **Time:** 09:30 WAT, Day 0  
> **Classification:** Critical ransomware incident
>
> **Confirmed:** `FIN-PC07` and `FS01` contain encrypted files and a ransom note. Learners cannot open materials or submit work. The contact list is unavailable. The two confirmed affected systems are isolated, and `svc_backup` is disabled to protect backup infrastructure.
>
> **Uncertain:** The initial access method, the content of the 1.2 GB upload, the safety of network backups, and the extent of wider compromise remain under investigation. The Friday disconnected backup is secured but untested.
>
> **Decisions required:** Approve an external forensic and incident response firm; approve legal involvement; note that the current portal must not host the 11:00 examination. The revised go/no-go recommendation is due by 09:30.
>
> **Next update:** 10:15 WAT by phone, then hourly. All external enquiries must go to the Communications Lead.

### 11.2 Learner Notice

> ## Important Notice for Learners
>
> We are responding to a security incident affecting some institute systems. The learning portal is unreliable, and some materials and submissions are currently unavailable.
>
> **Examination update:** The 11:00 online examination will not proceed as planned. Please do not attempt to log in for the examination. A revised date will be communicated by 14:00 today.
>
> **What you should do:** Do not open attachments or follow links about the incident or examination unless they come through the institute's official channels. The institute will never ask for your password.
>
> We are assessing whether personal information is affected and will contact impacted individuals directly if required.
>
> **Official updates:** Institute website, SMS, notice boards, and verified social channels.  
> **Fictional helpline:** 0800 000 0000

### 11.3 Notification Principles

- Operational notices are separate from formal personal-data breach notifications.
- Public statements must not exceed verified evidence.
- Legal counsel confirms jurisdiction, applicable law, notification recipients, awareness time, and deadlines.
- No statutory deadline is asserted because the scenario does not specify jurisdiction.
- The attacker's 12-hour publication threat is not a legal deadline.
- Law-enforcement contact proceeds through legal counsel and the executive sponsor.
- The default position is not to pay or negotiate.

---

## 12. Tabletop Exercise Report

### 12.1 Exercise Objectives

- Test authority and decision-making
- Test backup selection and restoration logic
- Test alternative-channel communication
- Test evidence handling during urgent containment

### 12.2 Participants

The exercise simulates all ten roles in the response team. It was conducted individually on paper, with the author speaking for each role in turn.

### 12.3 Agenda

| Exercise Time | Activity |
|---|---|
| Minutes 0-10 | Opening brief and coordinated containment call |
| Minute 10 | Inject 1: pressure to reopen portal |
| Minute 20 | Inject 2: attacker claims data theft |
| Minute 28 | Inject 5: additional affected endpoint |
| Minute 35 | Inject 3: network backup restore failure |
| Minute 45 | Inject 4: social-media rumour and journalist enquiry |
| Minutes 50-60 | Hot debrief |

### 12.4 Success Criteria

| ID | Criterion |
|---|---|
| SC1 | Incident declared and all roles reached, or deputies named, within 10 minutes |
| SC2 | `svc_backup` disabled and `BAK01` isolated within 20 minutes |
| SC3 | Examination decision with named approver and rationale before 09:45 |
| SC4 | Learner notice issued within 15 minutes of the decision |
| SC5 | Evidence-altering decisions logged within 30 minutes |
| SC6 | Holding statement approved within 10 minutes of media inject |

### 12.5 Injects and Decisions

#### Inject 1: Management Requests Portal Reopening

The Incident Manager refuses to reopen the affected production environment. `LMS01` lacks EDR coverage, network backups are unverified, and a safe restore is unlikely before the examination. The business owner accepts postponement if learners receive early notice.

#### Inject 2: Attacker Claims Theft of 1,800 Records

The claim is preserved as evidence but treated as unverified. The analyst compares the claim with file listings, logs, and forensic findings. The sponsor does not authorise payment or direct engagement.

#### Inject 5: Additional Endpoint Detected

A fictional endpoint, `ADM-PC12`, shows the same process, a suspicious scheduled task, and use of the finance officer's credentials. It is isolated, added to the evidence register, and used to expand the scope to admissions information.

#### Inject 3: Network Backup Restore Fails

The backup administrator stops retrying in production and preserves logs. `BAK01` remains untrusted and offline. The Friday disconnected backup becomes the only candidate, accepting an estimated 63 hours 45 minutes of potential data loss.

#### Inject 4: Social Post and Media Enquiry

The Communications Lead issues a holding statement through the approved spokesperson. The statement neither confirms nor denies data exposure because evidence is not yet sufficient.

### 12.6 Decision Log

| ID | Inject | Decision | Owner | Rationale | Effect |
|---|---|---|---|---|---|
| D1 | 1 | Do not reopen production; retain two recovery routes | IM advises, BO decides | Untrusted backup, possible compromise, no recent restore test | Friday backup becomes the recovery focus |
| D2 | 2 | Treat claim as unverified; no engagement or payment | ES with LP | Authenticity unknown | Add formal evidence review checkpoint |
| D3 | 5 | Isolate `ADM-PC12`, expand sweep, reset exposed accounts | IM | Second endpoint increases scope | Admissions data enters scope |
| D4 | 3 | Reject network backup and keep `BAK01` offline | IM | Failed restore plus suspicious access | Friday copy becomes sole candidate |
| D5 | 3 and 4 | Postpone examination and move decision to 09:25 | BO | No validated environment by 11:00 | Earlier learner notice |
| D6 | 4 | Issue neither-confirm-nor-deny holding statement | ES approves; CL delivers | Evidence supports neither public claim | Avoids contradiction and speculation |

### 12.7 Evaluation Results

| Criterion | Result | Rating |
|---|---|---|
| SC1 | Critical declared at 08:50; 8 of 10 roles reached by 08:55; legal reached at 09:08 because contact details were unavailable | Partly met |
| SC2 | `svc_backup` disabled at 09:00; `BAK01` isolated at 09:08 without a written procedure | Partly met |
| SC3 | Examination decision made at 09:25 with named owner and rationale | Met |
| SC4 | Notice issued at 09:42, 17 minutes after decision | Not met |
| SC5 | Three of four evidence-altering decisions logged on time; one memory-related entry was about 40 minutes late | Partly met |
| SC6 | Holding statement approved at 09:38, eight minutes after media inject | Met |

### 12.8 Overall Exercise Outcome

- **Met:** 2
- **Partly met:** 3
- **Not met:** 1

The results are a simulation and a learning guide, not proof of operational readiness.

---

## 13. Corrective Action Plan

| ID | Improvement | Priority | Owner | Target | Success Measure |
|---:|---|---|---|---|---|
| 1 | Create offline contact list including counsel and external response support | High | IM | Day 3 | Call test reaches every role within 15 minutes |
| 2 | Approve examination rule with 09:30 checkpoint and default postponement | High | BO | Day 7 | Signed procedure |
| 3 | Create `BAK01` and `svc_backup` isolation runbook | High | ITO and Backup Admin | Day 7 | Timed drill completes within 10 minutes |
| 4 | Establish learner-notification route independent of `FS01` and email | High | CL | Day 14 | Test reaches 50 people within 30 minutes |
| 5 | Create holding-statement and evidence-loss log templates | Medium | CL and FS | Day 7 | Templates used successfully in a drill |
| 6 | Implement quarterly restore testing | High | Backup Admin | First test Day 30 | Signed report with timing and integrity checks |
| 7 | Deploy EDR to all servers and centralise logs | High | SA | Day 30 | Complete coverage report and test alert per server |
| 8 | Engage an external incident response firm on retainer | Medium | ES | Day 30 | Signed agreement and verified call procedure |
| 9 | Reduce `svc_backup` privilege and prohibit interactive use | High | ITO | Day 14 | Access review plus failed interactive-logon test |
| 10 | Conduct twice-yearly tabletop exercises and finance phishing training | Medium | IM | Within 90 days | Attendance records and measurable reporting rate |

---

## 14. Case Study Analysis

### 14.1 Strengths Observed

The course case study describes a healthcare organisation affected by a Ryuk ransomware variant following a phishing attachment. Its strongest controls were:

- Verified offline backups supported recovery without paying a ransom.
- Rapid team activation and network segmentation limited further spread.
- A review after recovery updated the plan, scheduled training, and shared intelligence.

### 14.2 Limitations Observed

- Malware remained undetected for approximately 72 hours before encryption.
- “No patient data exfiltration confirmed” does not prove that no exfiltration occurred.
- The case mentions backup-restoration gaps but provides limited detail on how they were closed.

### 14.3 Lessons for Northbridge

1. A disconnected backup is useful only when it is regularly restored and verified.
2. EDR and central logging must include servers, especially file and backup systems.
3. Segmentation should separate user networks, learning systems, file servers, identities, and backup infrastructure.
4. Claims about data theft must reflect the strength and completeness of available evidence.
5. Restoring critical service does not mean the incident is closed.

### 14.4 Evidence Needed Before Claiming No Data Theft

- Complete outbound traffic records for the suspected dwell period
- Cloud audit and sign-in logs
- EDR and file-access records from affected systems
- Evidence showing no staging, compression, or archive creation
- Review of the suspicious cloud destination
- Leak-site and exposure checks
- Confirmation that relevant logs are complete and trustworthy

Where logs are incomplete, the defensible wording is **“no evidence of theft was identified”**, not **“no data was stolen.”**

---

## 15. Readiness Improvements

### 15.1 Technology

- Immutable or offline backups for `FS01` and `LMS01`
- Quarterly restore tests
- EDR across all servers and endpoints
- Centralised and protected security logging
- Network segmentation for backup and critical servers
- Secure privileged-access management
- MFA and conditional access

### 15.2 Process

- Offline contact directory
- Written isolation runbooks
- Pre-approved examination decision rules
- Evidence collection kit and forms
- Legal and privacy escalation procedure
- Alternative learner-notification mechanism
- Recovery acceptance checklist

### 15.3 People

- Role-specific incident response training
- Twice-yearly tabletop exercises
- Phishing awareness for finance and administrative staff
- Cross-training to support handovers
- Named deputies for every critical role
- External incident response retainer

---

## 16. Risk and Decision Principles

- Containment takes priority over convenience.
- Evidence preservation occurs alongside, not instead of, containment.
- A reported successful backup is not assumed recoverable.
- An attacker claim is not treated as confirmed evidence.
- Absence of evidence is not evidence of absence.
- Production access is restored only after security and business acceptance criteria are met.
- Communications distinguish confirmed facts, hypotheses, and unknowns.
- Legal counsel confirms notification obligations.
- The default ransom position is not to pay or negotiate.
- The incident remains open until recovery, monitoring, documentation, and corrective actions are appropriately addressed.

---

## 17. Review and Closure

A blame-free review should occur within two weeks of incident closure. The review should use the five-whys technique and attack-chain analysis to determine:

- How initial access occurred
- Why the affected activity was not detected earlier
- How privileged access was obtained or misused
- Why server visibility and backup assurance were insufficient
- Whether communication and decision pathways performed as intended
- Which controls prevented greater harm

The Incident Manager may close a corrective action only when evidence of completion is attached. Overdue or risk-accepted actions must be escalated to the executive sponsor.

### 17.1 Incident Closure Criteria

- Scope is sufficiently understood
- Malicious access and persistence are removed
- Affected systems are rebuilt or validated
- Exposed credentials are reset
- Services meet acceptance criteria
- Required notifications are completed
- Evidence and custody records are complete
- Monitoring shows no recurrence during the agreed observation period
- Lessons learned are documented
- Corrective actions have owners and deadlines

---

## 18. Skills Demonstrated

- Incident classification and severity assessment
- Ransomware response planning
- Timeline and hypothesis development
- CSIRT design and incident command
- RACI development
- Evidence handling and chain of custody
- Microsoft 365 account-compromise response
- Privileged account and backup protection
- Business continuity and recovery planning
- Crisis communication
- Legal and privacy escalation awareness
- Tabletop exercise design and evaluation
- Corrective-action management
- Technical and executive report writing


---

## 20. References

1. CISA, FBI, NSA, and MS-ISAC. (2023). *#StopRansomware Guide*. https://www.cisa.gov/resources-tools/resources/stopransomware-guide
2. ICDFA. (n.d.). *Incident Response Planning: GRC105 Week 20 Teaching Deck*.
3. ICDFA. (n.d.). *GRC105 Incident Response Planning Assignment: Scenario and Evidence Pack E01-E08*.
4. National Institute of Standards and Technology. (2025). *SP 800-61 Revision 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management*. https://csrc.nist.gov/pubs/sp/800/61/r3/final
5. National Institute of Standards and Technology. (n.d.). *Incident Response Project*. https://csrc.nist.gov/projects/incident-response

---

## 21. AI Use and Academic Integrity Statement

An AI assistant was used as a research and learning aid to support understanding of incident response plan structure, templates, and course concepts. The assignment was then written and completed by the student using the course materials and the NIST and CISA references listed above.

This repository is intended to demonstrate understanding of incident response planning, governance, risk, compliance, evidence management, recovery, and crisis communication. Reuse should comply with applicable academic-integrity requirements.

---

**Ummulkhoyr Adebukola Shittu**  
Governance, Risk, and Compliance Trainee  
Student ID: `2025/GCR/12699`

---

<p align="center"><strong>Completed GRC Incident Response Planning Report</strong></p>
<p align="center">Northbridge Skills Institute Ransomware Scenario</p>
