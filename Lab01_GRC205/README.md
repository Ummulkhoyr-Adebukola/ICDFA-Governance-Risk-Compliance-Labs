# Incident Response Planning Assignment

![Status](https://img.shields.io/badge/Status-Completed-success)
![Domain](https://img.shields.io/badge/Domain-GRC%20%7C%20Incident%20Response-1f6feb)
![Framework](https://img.shields.io/badge/Framework-NIST%20SP%20800--61-blue)
![Exercise](https://img.shields.io/badge/Exercise-Ransomware%20Tabletop-orange)

## Overview

This repository contains my completed **Incident Response Planning Assignment** for the fictional **Northbridge Skills Institute**. The project presents a structured response to a critical ransomware incident involving suspected credential compromise, possible data exfiltration, encrypted systems, disrupted learning services, and an imminent online examination.

The assignment applies the incident response lifecycle taught in the course:

1. **Preparation**
2. **Detection and Analysis**
3. **Containment, Eradication, and Recovery**
4. **Post-Incident Activity**

It also aligns incident response activities with **NIST Cybersecurity Framework 2.0** and **NIST SP 800-61 Revision 3**.

> **Disclaimer:** Northbridge Skills Institute, the incident scenario, systems, users, contact details, and tabletop outcomes presented in this project are fictional and were used solely for academic purposes.

---

## Author

- **Name:** Ummulkhoyr Adebukola Shittu
- **Student ID:** 2025/GCR/12699
- **Programme:** Governance, Risk, and Compliance
- **Role in Scenario:** Incident Response Lead
- **Institution:** ICDFA

---

## Assignment Scenario

At **08:45 WAT on Day 0**, I assumed responsibility as Incident Response Lead after a ransomware attack affected the institute's environment.

### Confirmed or Observed Events

- A payroll attachment was opened on `FIN-PC07`.
- A finance user's Microsoft 365 account recorded an unfamiliar sign-in.
- The privileged `svc_backup` account logged on to `FS01` and `BAK01` outside its normal schedule.
- Approximately **1.2 GB** of data was uploaded from `FIN-PC07` to unfamiliar cloud storage.
- `FIN-PC07` and `FS01` displayed encrypted files and a ransom note.
- Learners could access the portal login page but could not open materials or submit work.
- The incident contact list stored on `FS01` became unavailable.
- An online examination for **100 learners** was due to begin within approximately two hours.

### Initial Classification

The incident was classified as **Critical** because it involved:

- Confirmed loss of availability and integrity
- Possible exposure of learner, assessment, admissions, and finance data
- Suspected account and privileged-service compromise
- Unverified backups and recovery capability
- A time-sensitive examination and major operational disruption

---

## Project Objectives

The response plan was designed to:

- Contain ransomware activity and prevent further spread
- Protect the institute's recovery path and disconnected backup
- Preserve volatile and non-volatile evidence
- Determine whether data exfiltration occurred
- Establish trusted, out-of-band communications
- Restore validated services in business-priority order
- Support legal, regulatory, executive, and stakeholder decisions
- Capture lessons learned through a structured tabletop exercise

---

## Scope of Work

The completed assignment includes six major tasks.

### 1. Classification and Initial Assessment

This section documents:

- A timeline of evidence records `E01` to `E08`
- Confirmed facts, working hypotheses, and unresolved questions
- Alternative explanations for suspicious activity
- Incident type, suspected attack vector, and severity
- Affected, degraded, potentially affected, and unverified assets
- Confidentiality, integrity, and availability impact
- Investigation priorities and decision-driven questions

### 2. Incident Response Plan and Team

This section defines:

- Mission, objectives, scope, declaration criteria, and escalation paths
- Authority to isolate systems, disable accounts, and block destinations
- Documentation and review requirements
- Integration with business continuity, BIA, RTO, and RPO processes
- CSIRT roles and deputies
- A RACI matrix covering detection, analysis, containment, evidence handling, communication, recovery, restoration approval, and closure
- Readiness improvements with owners and measurable checks

### 3. Playbook and Evidence Management

The response playbook contains a timed sequence of actions starting at **08:45 WAT**, including:

- Critical incident declaration and team activation
- Migration to trusted communication channels
- Isolation of `FIN-PC07` and `FS01`
- Protection of `BAK01` and the disconnected Friday backup
- Export of Microsoft 365, proxy, endpoint, and server logs
- Session revocation and credential resets
- Enterprise-wide scope assessment
- Executive escalation and examination go/no-go decision
- Forensic investigation, eradication, rebuilding, restoration, and monitoring

The evidence plan defines six initial evidence items:

- `EV-01`: `FIN-PC07` memory and disk image
- `EV-02`: `FS01` logs, ransom note, and encrypted-file samples
- `EV-03`: Microsoft 365 sign-in and audit logs
- `EV-04`: Proxy logs for the suspicious upload
- `EV-05`: `BAK01` configuration, logs, and service-account activity
- `EV-06`: Phishing email, headers, and attachment

Evidence handling controls include hashing, read-only collection, encrypted storage, restricted access, witnessed transfers, and chain-of-custody records.

### 4. Communication and Escalation

The communication plan covers:

- Learners
- Institute leadership
- IT and security teams
- All staff
- Technology service providers
- Legal and privacy advisers
- External incident response specialists
- Media and the public
- Regulators and law enforcement

It includes primary and alternative channels, communication owners, approval requirements, triggers, frequencies, an executive briefing, and a learner notification template.

### 5. Tabletop Exercise

A paper-based simulation was conducted to test:

- Decision-making authority
- Backup and restoration logic
- Alternative-channel communication
- Evidence handling during urgent containment

The exercise introduced five scenarios, including pressure to reopen the portal, an attacker data-theft claim, discovery of another affected endpoint, a failed backup restore, and media attention.

#### Exercise Outcome

- **2** success criteria were met
- **3** were partly met
- **1** was not met

The findings produced a measurable improvement plan covering offline contact lists, exam decision rules, backup isolation procedures, learner notification routes, communication templates, restore testing, server EDR coverage, and an external response retainer.

### 6. Case Study Analysis

The assignment compares the fictional Northbridge incident with a healthcare-sector ransomware case study. It evaluates:

- The value of verified offline backups
- Rapid team activation and network segmentation
- Detection gaps during attacker dwell time
- The difference between “no theft confirmed” and “no theft occurred”
- Critical-service restoration versus full recovery
- Lessons transferable to Northbridge Skills Institute

---

## Key Decisions

### Containment Before Convenience

The affected production environment would not be reopened simply to keep the examination on schedule. Network isolation, backup protection, and evidence preservation took priority.

### Backup Selection

The disconnected **Friday 17:00** backup was selected as the default recovery candidate because it clearly predated the suspected phishing event. It would only be used after isolated validation, malware scanning, integrity checks, and functional testing.

### Examination Decision

The preferred options were:

1. Launch a validated clean environment using a trusted backup; or
2. Postpone the examination if validation could not be completed safely.

Following the tabletop findings, the decision checkpoint was revised from **09:45** to **09:30**, with postponement as the default unless a validated environment was ready.

### Ransom Position

The default position was **not to pay or negotiate**. Any departure from that position would require executive authorization informed by legal counsel and external incident response advice.

---

## Recovery Strategy

### Proposed Restoration Order

1. Establish a clean and trusted recovery environment
2. Validate backup infrastructure and identity services
3. Restore `LMS01` and the required `FS01` learning content
4. Restore remaining `FS01` shares
5. Rebuild `FIN-PC07` and restore validated finance data
6. Restore other services according to business priority

### Provisional Recovery Targets

- **Critical services:** within 72 hours in a limited, monitored form
- **Full restoration:** within 7 days
- **Recovery point:** Friday at 17:00, subject to validation

### Acceptance Criteria

A restored service must have:

- No identified persistence
- Rebuilt or validated hosts
- Reset exposed credentials
- A verified clean backup
- Completed data-integrity checks
- Passed functional tests
- Active endpoint detection and response coverage
- Required legal and communications clearance
- Business-owner approval

Full production restoration also requires closure of the initial attack path and a defined monitoring window without recurrence.

---

## Frameworks and Guidance Applied

- **NIST SP 800-61 Revision 3**
- **NIST Cybersecurity Framework 2.0**
- **CISA, FBI, NSA, and MS-ISAC StopRansomware Guide**
- Course guidance on incident classification, CSIRT responsibilities, evidence handling, recovery, review, BIA, RTO, and RPO

---

## Key Skills Demonstrated

- Incident classification and severity assessment
- Ransomware response planning
- Timeline reconstruction and hypothesis management
- Incident command and CSIRT coordination
- RACI development
- Evidence preservation and chain of custody
- Microsoft 365 account-compromise response
- Backup validation and recovery planning
- Business continuity integration
- Crisis communication and stakeholder management
- Legal and privacy escalation awareness
- Tabletop exercise design and evaluation
- Corrective-action planning

---

## Repository Contents

```text
.
├── README.txt
└── Lab 22 GRC205.docx
```

> The repository file name references `GRC205`, while the assignment content identifies the course as `GRC105`. Both labels are retained as supplied in the completed assignment.

---

## How to Review This Project

1. Open `Lab 22 GRC205.docx` to read the completed assignment.
2. Review the incident timeline and severity rationale.
3. Examine the CSIRT structure and RACI matrix.
4. Follow the timed ransomware response playbook.
5. Review the evidence register and custody controls.
6. Assess the communication plan and decision records.
7. Compare the tabletop results with the improvement plan.

---

## Important Notes

- All times are expressed in **West Africa Time (WAT)**.
- Response targets are proposed for the fictional scenario and are not presented as official NIST requirements.
- No forensic hashes, acquisition times, or incident findings were invented.
- Data exfiltration remains a hypothesis unless supported by evidence.
- Legal jurisdiction and breach-notification deadlines must be confirmed by qualified counsel.
- The tabletop results are simulated and demonstrate planning rather than proof of operational capability.

---

## References

1. CISA, FBI, NSA, and MS-ISAC. (2023). *#StopRansomware Guide*. https://www.cisa.gov/resources-tools/resources/stopransomware-guide
2. ICDFA. (n.d.). *Incident Response Planning, GRC105 Week 20 Teaching Deck*.
3. ICDFA. (n.d.). *GRC105 Incident Response Planning Assignment: Scenario and Evidence Pack E01-E08*.
4. NIST. (2025). *SP 800-61 Revision 3: Incident Response Recommendations and Considerations for Cybersecurity Risk Management*. https://csrc.nist.gov/pubs/sp/800/61/r3/final
5. NIST. (n.d.). *Incident Response Project*. https://csrc.nist.gov/projects/incident-response

---

## Academic Integrity

This repository is intended to demonstrate my understanding of incident response planning, governance, risk, compliance, evidence management, recovery, and crisis communication. Any use or adaptation of this work should comply with applicable academic-integrity requirements.

---

## Contact

For professional or academic enquiries, connect with me through my GitHub profile.

---

<p align="center"><strong>Completed Incident Response Planning Project</strong></p>
