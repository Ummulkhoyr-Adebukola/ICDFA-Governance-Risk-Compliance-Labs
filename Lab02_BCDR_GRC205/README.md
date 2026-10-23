# Business Continuity and Disaster Recovery Plan

## Northbridge Skills Institute Flood and Power-Failure Scenario

![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Course-GRC205-1f6feb)
![Domain](https://img.shields.io/badge/Domain-BC%2FDR-6f42c1)
![Framework](https://img.shields.io/badge/Framework-NIST%20SP%20800--34-blue)
![Standard](https://img.shields.io/badge/Standard-ISO%2022301-orange)

## Overview

This repository contains my completed **Business Continuity and Disaster Recovery assignment** for the fictional **Northbridge Skills Institute**. The project examines a major flood and power failure that makes the institute's main site and local systems unavailable for up to 72 hours.

Working as the **Business Continuity and Disaster Recovery Coordinator**, I developed a risk-based plan to maintain essential services, recover critical systems, protect backup integrity, communicate with stakeholders, and support a controlled return to normal operations.

The project combines business impact analysis, recovery objectives, backup design, recovery-site selection, continuity procedures, disaster recovery scheduling, tabletop testing, governance, and performance measurement.

> **Disclaimer:** Northbridge Skills Institute, its systems, personnel, costs, recovery estimates, and exercise outcomes are fictional and were used solely for academic purposes.

---

## Author

- **Name:** Ummilkhoyr Adebukola Shittu
- **Student ID:** 2025/GCR/12699
- **Programme:** Governance, Risk, and Compliance
- **Course:** GRC205 Business Continuity and Disaster Recovery
- **Scenario Role:** Business Continuity and Disaster Recovery Coordinator
- **Institution:** ICDFA

---

## Scenario Summary

At **08:00 WAT on Day 0**, flooding and a power failure made the main site and local systems unavailable. The disruption affected teaching and assessment, fees and finance, admissions, payroll, and records services.

The scenario included several time-sensitive business requirements:

- An examination for 120 learners scheduled for 11:00
- Fee confirmations required by 16:00
- Admissions closing at 18:00
- Payroll submission due by 12:00 on Day 1
- Records-service commitments due within 48 hours

The response therefore required both technical recovery and temporary business procedures. Restoring systems alone was not considered sufficient. Each service also required business-owner validation, reconciliation of temporary records, and restoration of the necessary controls.

---

## Project Objectives

The assignment was designed to:

- Identify and prioritise critical business functions
- Quantify the financial effect of disruption
- Evaluate non-financial consequences such as learner welfare, trust, and data integrity
- Define realistic RTO, RPO, and MTD values
- Design a resilient backup and restoration strategy
- Compare cold, warm, and hot recovery options
- Recommend a recovery approach within the available budget
- Develop temporary procedures for a 72-hour outage
- Build a dependency-aware disaster recovery runbook
- Test the plan through a tabletop exercise
- Establish governance, testing, training, and performance measures

---

## Scope of Work

The completed assignment contains six major tasks.

### 1. Business Impact Analysis

The Business Impact Analysis evaluates five critical functions:

| Priority | Function | Owner | Key Deadline |
|---:|---|---|---|
| 1 | Teaching and assessment | Exams Manager | Examination at 11:00 |
| 2 | Fees and finance | Finance Manager | Confirmations by 16:00 |
| 3 | Admissions | Registrar | Applications close at 18:00 |
| 4 | Payroll | HR Manager | Bank submission by 12:00 on Day 1 |
| 5 | Records and certificates | Records Officer | Service commitment within 48 hours |

The analysis identifies users, resources, suppliers, information, system dependencies, minimum acceptable service levels, and disruption consequences for each function.

### 2. Recovery Objectives and Backup Design

The project defines recovery objectives using:

- **Recovery Time Objective (RTO):** Maximum acceptable downtime
- **Recovery Point Objective (RPO):** Maximum acceptable data loss measured in time
- **Maximum Tolerable Downtime (MTD):** Absolute outage limit before unacceptable harm

| Function | Tier | RTO | RPO | MTD |
|---|---|---:|---:|---:|
| Teaching and assessment | T1 | 4 hours | 1 hour | 8 hours |
| Fees and finance | T1 | 4 hours | 1 hour | 8 hours |
| Admissions | T2 | 5 hours | 1 hour | 10 hours |
| Payroll | T2 | 8 hours | 4 hours | 24 hours |
| Records and certificates | T3 | 24 hours | 24 hours | 48 hours |

The backup design applies the **3-2-1 principle**, supported by an additional independent immutable or offline copy. Controls include separate administrator identities, MFA, least privilege, dual approval for deletion, encryption, integrity validation, monthly sample restores, quarterly full-chain tests, and annual parallel testing.

### 3. Recovery Strategy and Budget

Three recovery options were assessed:

| Option | Annual Cost | Recovery Estimate | Assessment |
|---|---:|---|---|
| Cold site | NGN 1,200,000 | 24 to 48 hours | Fails several RTOs and MTDs |
| Warm site | NGN 2,100,000 | 3 to 5 hours | Recommended |
| Hot site | NGN 3,000,000 | Approximately 1 hour | Meets targets but uses the full budget |

The **warm-site option** was recommended because it meets all MTDs, supports the recovery objectives, includes independent protected backups and training, and leaves **NGN 900,000** in budget headroom.

The recommendation recognises that the warm site cannot restore the learning platform before the 11:00 examination. A temporary assessment procedure is therefore required even when technical recovery proceeds successfully.

### 4. Business Continuity and Disaster Recovery Plan

The plan defines:

- Scope and activation criteria
- Authority and escalation paths
- Incident command and team coordination
- RACI responsibilities
- Temporary procedures for each business function
- Minimum staffing, equipment, facility, and supplier requirements
- A technical disaster recovery runbook
- Business acceptance and rollback rules
- Stakeholder communication procedures
- Incident response triggers
- Safe return-to-site and final sign-off requirements

Temporary operating procedures cover controlled assessments, manual finance reconciliation, temporary admissions intake, protected payroll processing, and logged records requests.

### 5. Recovery Schedule and Tabletop Exercise

The baseline technical recovery schedule uses two technicians and respects system dependencies.

| Service or System | Planned Availability |
|---|---:|
| Recovery network | 08:30 |
| AUTH01 | 09:00 |
| Security and backup checks | 09:30 |
| FS01 | 10:30 |
| DB01 | 11:00 |
| FIN01 | 11:30 |
| LMS01 | 11:45 |
| HR01 | 12:10 |
| REG01 | 12:15 |

The critical path is:

`Recovery network -> AUTH01 -> security and backup checks -> DB01 -> LMS01`

Its total duration is **225 minutes**, making 11:45 the earliest planned restoration time for the assessment platform. Because the examination begins at 11:00, the continuity workaround remains necessary.

The tabletop exercise tested:

- Extension of the site closure from 72 hours to five days
- Reduction of available workstations from 25 to 15
- Failure of a DB01 incremental backup integrity check
- Detection of an unexpected backup-administrator logon
- Missing finance transactions after restoration

The exercise produced decisions on extended resourcing, learner prioritisation, equivalent examination sessions, incident response activation, backup fallback, credential replacement, and finance reconciliation.

### 6. Governance and Performance Measures

The governance model includes:

- Executive Steering Committee oversight
- Executive Sponsor approval
- BC/DR Coordinator ownership
- Version control and controlled distribution
- Quarterly risk-based testing
- Monthly sample restores
- Role-based training and onboarding
- Review triggers after incidents, exercises, system changes, supplier changes, audit findings, and flood-season preparation

Performance is tracked through the following KPIs:

- Percentage of functions restored within RTO
- Actual recovered data age compared with RPO
- Annual restoration-test coverage
- Corrective actions completed by target date
- Staff training completion
- Percentage of backups passing integrity checks first time

---

## Business Impact Calculations

The assignment estimates a combined disruption rate of **NGN 135,000 per hour** across the five functions.

| Period | Hourly Impact | Examination Rescheduling | Total Estimated Impact |
|---|---:|---:|---:|
| 8 hours | NGN 1,080,000 | NGN 120,000 | **NGN 1,200,000** |
| 24 hours | NGN 3,240,000 | NGN 120,000 | **NGN 3,360,000** |

The financial model is treated as an exercise estimate rather than an observed loss. It does not fully represent learner welfare, accessibility, institutional trust, assessment integrity, payroll errors, or corrupted records.

---

## Recommended Solution

The recommended solution is a **warm recovery site** supported by:

- Hourly DB01 incremental backups
- Daily differential and weekly full backups
- Frequent AUTH01 snapshots
- Independent encrypted offsite storage
- A weekly immutable or offline copy
- Separate and monitored backup-administrator credentials
- Regular integrity checks and restoration tests
- Temporary business procedures for deadline-driven services
- A pre-built recovery network to shorten the critical path

The warm-site strategy balances cost, recovery speed, operational practicality, and resilience. It also preserves budget capacity for contingencies and future improvements.

---

## Key Risks Identified

- Shared production and backup administrator identity
- Unverified independence of the offsite backup provider
- Dependence on a single local directory service
- DB01 as a shared dependency for four business functions
- Only two technicians available for recovery
- Limited alternate-facility workstation capacity
- Dependence on mobile internet and Microsoft 365
- Recovery-site exposure to the same flood or power risks
- One-hour RPO with no safety margin for key functions
- Possibility that live replication could reproduce corruption or malicious changes

---

## Corrective Actions

Priority improvements include:

1. Separate backup administration from production administration.
2. Enable MFA, least privilege, and administrator-logon alerts.
3. Test offsite-provider access independence.
4. Create and restore from an immutable or offline weekly copy.
5. Automate backup integrity and incremental-chain validation.
6. Maintain an exam-bank copy outside LMS01.
7. Formalise temporary assessment procedures.
8. Contract for a defined number of working recovery-site workstations.
9. Pre-build the recovery network to reduce restoration time.
10. Re-run the exercise and verify that corrective actions work as intended.

---

## Framework and Standards Alignment

The assignment is aligned with:

- **NIST SP 800-34 Revision 1**, covering policy, BIA, preventive controls, contingency strategies, plan development, testing, training, exercises, and maintenance
- **ISO 22301:2019**, covering organisational context, leadership, planning, support, operations, performance evaluation, and improvement
- **ISO 22301:2019/Amd 1:2024**, considering whether climate change is relevant to the organisation and its interested parties

Flood risk was treated as relevant because the scenario begins with an actual flood event. Proposed controls include locating recovery resources in a different flood zone and power grid, raising equipment above floor level, monitoring early-warning triggers, and conducting pre-flood-season reviews.

---

## Key Skills Demonstrated

- Business impact analysis
- Critical-function prioritisation
- RTO, RPO, and MTD definition
- Dependency and critical-path analysis
- Backup architecture and restoration planning
- Recovery-site evaluation and budgeting
- Business continuity procedure design
- Disaster recovery runbook development
- RACI matrix development
- Crisis communication planning
- Tabletop exercise design
- Corrective-action management
- Governance and KPI development
- NIST and ISO control mapping
- Climate-related continuity planning

---

## Repository Contents

```text
.
├── README.md
└── LAB02 BCD GRC205.docx
```

---


## Important Notes

- All times are expressed in **West Africa Time (WAT)**.
- All costs and operational figures are fictional exercise estimates.
- Items not confirmed by the assignment case are marked as assumptions or unverified in the full report.
- System recovery is not treated as business recovery until technical checks, reconciliation, control restoration, and business-owner acceptance are completed.
- The baseline recovery schedule is a model based on provided drill timings, not the result of a live recovery test.
- The maturity rating is an assessment based only on the fictional case data.

---

## References

1. ICDFA. (n.d.). *Business Continuity and Disaster Recovery, GRC205 Week 21 Teaching Deck*.
2. ICDFA. (n.d.). *GRC205 Business Continuity and Disaster Recovery Assignment Case Data*.
3. National Institute of Standards and Technology. (2010). *SP 800-34 Revision 1: Contingency Planning Guide for Federal Information Systems*. https://csrc.nist.gov/pubs/sp/800/34/r1/upd1/final
4. International Organization for Standardization. (2019). *ISO 22301:2019 Security and Resilience, Business Continuity Management Systems*. https://www.iso.org/standard/75106.html
5. International Organization for Standardization. (2024). *ISO 22301:2019/Amd 1:2024 Climate Action Changes*. https://www.iso.org/standard/88412.html

---

## Academic Integrity

This repository is intended to demonstrate my understanding of business continuity, disaster recovery, governance, risk management, backup resilience, crisis communication, and operational recovery. Any reuse or adaptation should comply with the applicable academic-integrity requirements.

---

<p align="center"><strong>Completed GRC205 Business Continuity and Disaster Recovery Project</strong></p>
