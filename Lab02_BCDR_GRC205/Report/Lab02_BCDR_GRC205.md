# Business Continuity and Disaster Recovery Report

## Northbridge Skills Institute Flood and Power-Failure Scenario

![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Course-GRC205-1f6feb)
![Focus](https://img.shields.io/badge/Focus-Business%20Continuity%20%26%20Disaster%20Recovery-6f42c1)
![Framework](https://img.shields.io/badge/Framework-NIST%20SP%20800--34-blue)
![Standard](https://img.shields.io/badge/Standard-ISO%2022301-orange)

---

## Document Control

| Field | Details |
|---|---|
| **Report title** | Business Continuity and Disaster Recovery Report |
| **Organisation** | Northbridge Skills Institute, fictional |
| **Prepared by** | Ummilkhoyr Adebukola Shittu |
| **Student ID** | 2025/GCR/12699 |
| **Programme** | Governance, Risk, and Compliance |
| **Course** | GRC205 Business Continuity and Disaster Recovery |
| **Scenario role** | Business Continuity and Disaster Recovery Coordinator |
| **Disruption time** | Day 0, Monday, 08:00 WAT |
| **Report status** | Completed academic assignment |
| **Classification** | Academic use |

> **Scenario disclaimer:** Northbridge Skills Institute, its systems, personnel, costs, assumptions, recovery estimates, and exercise outcomes are fictional and were used solely for academic purposes.

---

## Executive Summary

This report presents a Business Continuity and Disaster Recovery plan for Northbridge Skills Institute following a flood and power failure that made the main site and local systems unavailable. The scenario placed several deadline-sensitive services at risk, including an examination for 120 learners at 11:00, fee confirmations by 16:00, admissions closure at 18:00, payroll submission by 12:00 on Day 1, and records services within 48 hours.

The analysis prioritised five business functions: teaching and assessment, fees and finance, admissions, payroll, and records and certificates. Their combined estimated disruption rate was **NGN 135,000 per hour**. With examination rescheduling included, the estimated impact was **NGN 1,200,000 after eight hours** and **NGN 3,360,000 after 24 hours**.

Recovery objectives were established using RTO, RPO, and MTD values. A warm recovery site costing **NGN 2,100,000 per year** was selected over cold and hot alternatives. It met the proposed tolerable downtime limits, supported the recovery objectives, and retained **NGN 900,000** of the available budget. However, the modelled recovery schedule showed that LMS01 could not return before 11:45, making a temporary assessment procedure necessary for the 11:00 examination.

The plan also introduced protected backups, temporary business procedures, a dependency-aware runbook, a stakeholder communication model, a tabletop exercise, governance controls, corrective actions, and measurable performance indicators. The overall goal was not merely to restore technology, but to resume controlled business services with validated data, reconciled temporary records, restored safeguards, and formal business-owner acceptance.

---

## 1. Purpose, Scope, and Assumptions

### 1.1 Purpose

The purpose of this report is to define how Northbridge Skills Institute can maintain essential services during a prolonged site outage and restore its systems in a controlled, secure, and prioritised manner.

### 1.2 Scope

The plan covers:

- Teaching and assessment
- Fees and finance
- Admissions
- Payroll
- Records and certificates
- Local infrastructure and application systems
- Backup and restoration arrangements
- Alternate facilities and recovery suppliers
- Temporary business procedures
- Stakeholder communication
- Incident response integration
- Return to the primary site

### 1.3 Key Assumptions

| ID | Assumption |
|---|---|
| A1 | DB01 incremental backups are taken hourly through 07:00. This is unverified. |
| A2 | The baseline assumes a complete DB01 backup chain and clean AUTH01 and FS01 recovery points. |
| A3 | Fictional role titles are used for plan ownership and accountability. |
| A4 | Examination papers can be obtained outside LMS01. This is unverified. |
| A5 | The alternate facility can support the required learners through workstations and controlled BYOD use. This is unverified. |
| A6 | Tabletop exercise minutes are mapped to scenario time through facilitator advancement. |

All financial figures and operational outcomes are exercise estimates. Items not confirmed by the case are labelled as assumptions or unverified.

---

## 2. Business Impact Analysis

### 2.1 Critical Functions

| Priority | Function | Business Owner | Deadline or Key Impact |
|---:|---|---|---|
| 1 | Teaching and assessment | Exams Manager | Examination at 11:00 |
| 2 | Fees and finance | Finance Manager | Fee confirmations by 16:00 |
| 3 | Admissions | Registrar | Applications close at 18:00 |
| 4 | Payroll | HR Manager | Bank submission by 12:00 on Day 1 |
| 5 | Records and certificates | Records Officer | Service commitment within 48 hours |

### 2.2 Dependencies and Minimum Services

| Function | Main Dependencies | Minimum Acceptable Service |
|---|---|---|
| Teaching and assessment | Recovery network, AUTH01, DB01, LMS01, exam bank, invigilators | Controlled temporary assessment with identity checks, invigilation, secured submissions, timed release, and attendance records |
| Fees and finance | Recovery network, AUTH01, DB01, FIN01, payment provider | Temporary ledger using provider exports, dual approval, controlled confirmations, and temporary receipt numbers |
| Admissions | Recovery network, AUTH01, DB01, REG01 | Temporary online intake, acknowledgement of applications, and Registrar-approved changes |
| Payroll | Recovery network, AUTH01, DB01, HR01, bank portal | Last approved payroll run plus approved changes, two-person approval, and submission log |
| Records and certificates | Recovery network, AUTH01, FS01 | Logged requests, identity checks, Registrar approval, and confirmed access restrictions |

### 2.3 Financial Impact

| Function | Rate per Hour | Eight Hours | Twenty-Four Hours |
|---|---:|---:|---:|
| Teaching and assessment | NGN 60,000 | NGN 480,000 | NGN 1,440,000 |
| Fees and finance | NGN 40,000 | NGN 320,000 | NGN 960,000 |
| Admissions | NGN 20,000 | NGN 160,000 | NGN 480,000 |
| Payroll | NGN 10,000 | NGN 80,000 | NGN 240,000 |
| Records and certificates | NGN 5,000 | NGN 40,000 | NGN 120,000 |
| **Hourly-impact subtotal** | **NGN 135,000** | **NGN 1,080,000** | **NGN 3,240,000** |
| Examination rescheduling | One-off | NGN 120,000 | NGN 120,000 |
| **Total estimated impact** |  | **NGN 1,200,000** | **NGN 3,360,000** |

The model is linear and does not fully capture deadline spikes, learner welfare, accessibility, institutional trust, assessment integrity, payroll errors, or data corruption. Business priority is therefore based on deadline and consequence as well as financial cost.

### 2.4 Key Dependency Risks

- Production and backup administration share an identity.
- Offsite-provider access independence is undocumented.
- AUTH01 is a single shared directory dependency.
- DB01 supports four critical functions.
- Only two technicians are available for recovery.
- Alternate-site workstation capacity is limited.
- Identity, email, and communications rely on mobile internet and Microsoft 365.

---

## 3. Recovery Objectives

### 3.1 Definitions

- **Recovery Time Objective (RTO):** Maximum acceptable time from disruption to restoration.
- **Recovery Point Objective (RPO):** Maximum acceptable data loss measured in time.
- **Maximum Tolerable Downtime (MTD):** Absolute outage limit before the harm becomes unacceptable.

### 3.2 Objective Matrix

| Function | Tier | RTO | RPO | MTD | MTD Buffer |
|---|---:|---:|---:|---:|---:|
| Teaching and assessment | T1 | 4 hours | 1 hour | 8 hours | 4 hours |
| Fees and finance | T1 | 4 hours | 1 hour | 8 hours | 4 hours |
| Admissions | T2 | 5 hours | 1 hour | 10 hours | 5 hours |
| Payroll | T2 | 8 hours | 4 hours | 24 hours | 16 hours |
| Records and certificates | T3 | 24 hours | 24 hours | 48 hours | 24 hours |
| AUTH01 shared service | T1 | Aligned with F1 | 12 hours | Not applicable | Not applicable |

A service is declared recovered only after the application is restored from a validated point, technical and data checks pass, the business owner accepts the minimum service, and temporary records are reconciled or covered by a dated reconciliation plan.

### 3.3 Recovery-Point Assessment at 08:00

| Item | Available Point | Age | Functions | Proposed RPO | Result |
|---|---|---:|---|---:|---|
| DB01 full plus incrementals | 07:00 Day 0 | 1 hour | F1 to F4 | 1 hour for F1-F3; 4 hours for F4 | Meets, with no margin for F1-F3 |
| AUTH01 snapshot | 00:00 Day 0 | 8 hours | All | 12 hours | Meets with 4-hour margin |
| FS01 backup | 23:00 Day -1 | 9 hours | F5 | 24 hours | Meets with 15-hour margin |
| Disconnected full backup | 17:00 Day -3 | 63 hours | All, as fallback | Outside normal RPOs | Emergency fallback only |

The disconnected backup is valuable as an independent recovery option but falls far outside every proposed RPO.

---

## 4. Backup and Recovery Design

### 4.1 Backup Schedule

| Data Set | Full Backup | Differential or Incremental | Retention | Independent Copy |
|---|---|---|---|---|
| DB01 | Weekly, Sunday 23:00 | Daily differential at 23:00 and hourly incrementals | Four weekly fulls, 14 daily differentials, seven days of incrementals | Encrypted provider copy plus weekly immutable copy |
| AUTH01 | Snapshot every six hours and after major changes | Not applicable | 14 days | Protected offsite copy |
| FS01 | Weekly, Sunday 23:00 | Daily differential at 23:00 | Four weekly and 12 monthly copies | Protected offsite copy |

### 4.2 DB01 Restoration Chain

The DB01 restore sequence is:

1. Latest full backup
2. Latest differential backup
3. Every subsequent hourly incremental in order
4. Final integrity, consistency, and transaction checks

A missing or failed incremental makes all later increments unusable until an alternative valid chain is selected.

### 4.3 Backup Protection Controls

- Three production and backup copies plus an independent immutable or offline copy
- Two storage media types
- One offsite copy in a different flood zone and power grid
- Separate backup-administrator identity
- MFA and least privilege
- Two-person approval for deletion and retention changes
- Alerts for administrator logons
- Encryption in transit and at rest
- Encryption keys stored outside AUTH01 and offline
- Monthly sample restores
- Quarterly timed full-chain restores
- Annual parallel testing at the warm site

### 4.4 Validation Requirements

**Integrity checks**

- Catalogue and checksum verification
- Complete-chain and sequence validation
- Malware scanning in an isolated environment

**Access-independence checks**

- Confirm production credentials cannot modify offsite copies
- Confirm backup credentials cannot delete immutable copies
- Obtain written confirmation from the provider

**Usability checks**

- Restore into isolation
- Run database consistency checks
- Start applications
- Compare record counts and financial totals
- Obtain sample validation from business owners

---

## 5. Recovery Strategy and Budget

### 5.1 Option Comparison

| Option | Annual Base | Protected Backups | Training and Tests | Total Annual Cost | Budget Headroom | Recovery Estimate |
|---|---:|---:|---:|---:|---:|---|
| Cold site | NGN 600,000 | NGN 400,000 | NGN 200,000 | **NGN 1,200,000** | NGN 1,800,000 | 24 to 48 hours |
| Warm site | NGN 1,500,000 | NGN 400,000 | NGN 200,000 | **NGN 2,100,000** | NGN 900,000 | 3 to 5 hours |
| Hot site | NGN 2,400,000 | NGN 400,000 | NGN 200,000 | **NGN 3,000,000** | NGN 0 | Approximately 1 hour |

### 5.2 Recommended Option

The recommended solution is the **warm site** at **NGN 2,100,000 annually**.

It was selected because it:

- Meets all proposed MTD values
- Supports the proposed RTOs under the baseline schedule
- Includes protected offsite backups and training
- Retains NGN 900,000 for contingencies and improvements
- Avoids the unacceptable recovery delay of the cold site
- Avoids committing the entire budget to a hot site
- Reduces the risk that real-time replication will copy corruption or malicious changes

### 5.3 Limitation of the Warm Site

The warm-site strategy cannot restore LMS01 by the 11:00 examination. A temporary assessment procedure is therefore required. Its one-hour RPO also depends on the planned hourly DB01 backup schedule being delivered and verified.

### 5.4 Estimated Benefit

Under the baseline warm-site schedule, the estimated outage cost is approximately NGN 505,000 before examination rescheduling and NGN 625,000 after including the NGN 120,000 one-off cost. Compared with the 24-hour no-measure estimate of NGN 3,360,000, the estimated avoided loss is approximately NGN 2,735,000.

This comparison is not a complete ROI calculation because a true ROI assessment also requires outage probability, multi-year cost, operational overhead, and evidence of the option's actual performance.

---

## 6. Business Continuity Plan

### 6.1 Activation Criteria

The plan activates when:

- The main site or local systems are expected to remain unavailable for more than four hours
- Any critical function is at risk of exceeding its RTO
- Backup or system compromise is suspected
- Safety, regulatory, or material stakeholder concerns arise

### 6.2 Authority and Escalation

- The Director of Operations acts as Incident Commander.
- The Principal acts as Executive Sponsor and approves plan activation.
- The Head of Academic Services acts as deputy when the Incident Commander is unavailable.
- The BC/DR Coordinator escalates within 15 minutes.
- Additional escalation occurs when an RTO or MTD is threatened, compromise is suspected, safety is affected, or media enquiries are received.

### 6.3 Command Structure

- Facilities establishes site safety and return conditions.
- Function owners operate continuity procedures.
- The technical recovery team executes the runbook.
- The incident response lead screens backups and suspicious activity.
- A shared incident log and hourly joint briefings maintain common situational awareness.

### 6.4 RACI Matrix

**Key:** R = Responsible, A = Accountable, C = Consulted, I = Informed

| Activity | Incident Commander | Executive Sponsor | BC/DR Coordinator | Technical Lead | Technicians | Function Owners | Facilities | Communications | IR Lead |
|---|---|---|---|---|---|---|---|---|---|
| Plan activation | R | A | C | I | I | I | I | I | I |
| Temporary assessment | I | I | C | C | R | A/R | C | C | I |
| Backup validation | I | I | I | A | R | C | I | I | R |
| Restoration | I | I | I | A/R | R | I | I | I | C |
| Business acceptance | I | I | C | R | C | A/R | I | I | C |
| Stakeholder communication | A | C | C | C | I | C | I | R | C |
| Return to primary site | R | A | C | R | R | R | R | I | C |
| Compromise assessment | I | I | C | C | C | I | I | C | A/R |

---

## 7. Temporary Operating Procedures

### 7.1 Teaching and Assessment

- Use an approved examination paper obtained outside LMS01.
- Release papers only at the scheduled start time.
- Require learners to sign in with their own accounts.
- Conduct identity and attendance checks.
- Prioritise alternate-site workstations for learners requiring adjustments or without devices.
- Use a controlled BYOD arrangement where approved.
- Schedule an equivalent second session for learners who cannot be accommodated.
- Store submissions in a restricted location.
- Record marks in a controlled sheet and reconcile them to LMS01 later.
- Delete temporary copies after validated import and reconciliation.

### 7.2 Fees and Finance

- Build a restricted temporary ledger from payment-provider exports.
- Use one preparer and one approver for each confirmation.
- Issue temporary receipt numbers.
- Do not manually edit wallet balances.
- Reconcile the temporary ledger after FIN01 is restored.

### 7.3 Admissions

- Use a temporary online form with mandatory fields.
- Send an acknowledgement for every application.
- Require Registrar approval for registration changes.
- Enter temporary applications into REG01 after restoration.
- Use a second-person check and reconcile form counts to system records.

### 7.4 Payroll

- Freeze payroll to the last approved run plus approved changes.
- Require HR preparation and Finance approval.
- Use a submission log to prevent duplicate bank instructions.
- Reconcile any changes created after the recovery point.

### 7.5 Records and Certificates

- Log every request.
- Verify identity.
- Require Registrar approval.
- Release nothing until FS01 access restrictions have been validated.
- Track the 48-hour commitment from the logged request time.

---

## 8. Disaster Recovery Runbook

| Step | Action | Prerequisite | Owner | Completion Check | Failure Response |
|---:|---|---|---|---|---|
| 1 | Activate plan, screen for compromise, and assemble teams | Disruption confirmed | Incident Commander and BC/DR Coordinator | Activation logged and teams reached | Deputy takes over; use phone tree |
| 2 | Select DB01, AUTH01, and FS01 recovery points; hold disconnected copy as fallback | Catalogue access | Technical Lead | Timestamps listed and chain contiguous | Contact provider or use fallback |
| 3 | Build recovery network | None | Technician 1 | Isolated network reaches required services | Contact provider and escalate |
| 4 | Restore AUTH01 | Recovery network | Technician 1 | Directory starts and test logons succeed | Use earlier snapshot and hold dependants |
| 5 | Perform security and backup checks | AUTH01 | Technician 1 and IR Lead | Integrity, malware, and logon checks pass | Stop, escalate, and select valid fallback |
| 6 | Restore DB01 | Successful checks | Technician 1 | Consistency check passes and recovery point is confirmed | Preserve failed image and rebuild from alternate chain |
| 7 | Restore FS01 | AUTH01 and successful checks | Technician 2 | File counts, permissions, and samples pass | Re-restore from validated backup |
| 8 | Restore LMS01, FIN01, HR01, and REG01 | DB01 | Technical team | Application and record-count tests pass | Roll back to previous validated state |
| 9 | Obtain business acceptance | Application restoration | Function owners | Signed acceptance | Remain on temporary procedure |
| 10 | Declare recovery | Business acceptance | Incident Commander | Declaration logged | Continue recovery and remediation |

Technology is considered restored after technical and data checks. A business service resumes only after the owner accepts it, temporary records are reconciled, and the required controls are active.

---

## 9. Baseline Recovery Schedule

| Action | Technician | Start | Finish | Dependency |
|---|---:|---:|---:|---|
| Recovery network | 1 | 08:00 | 08:30 | None |
| AUTH01 | 1 | 08:30 | 09:00 | Recovery network |
| Security and backup checks | 1 | 09:00 | 09:30 | AUTH01 |
| DB01 | 1 | 09:30 | 11:00 | Security and backup checks |
| FS01 | 2 | 09:30 | 10:30 | AUTH01 and checks |
| LMS01 | 1 | 11:00 | 11:45 | DB01 |
| FIN01 | 2 | 11:00 | 11:30 | DB01 |
| HR01 | 2 | 11:30 | 12:10 | DB01 |
| REG01 | 1 | 11:45 | 12:10 | DB01 |

### 9.1 Critical Path

`Recovery network -> AUTH01 -> security and backup checks -> DB01 -> LMS01`

The critical path is **225 minutes**, making **11:45** the earliest planned restoration time for LMS01. This is 45 minutes after the examination start.

### 9.2 Performance Against Objectives

| Function | Planned Restoration | Elapsed | RTO | RTO Result | MTD | Data Point Versus RPO |
|---|---:|---:|---:|---|---:|---|
| Teaching and assessment | 11:45 | 3h 45m | 4h | Met with 15-minute margin | 8h | 1h versus 1h, met with no margin |
| Fees and finance | 11:30 | 3h 30m | 4h | Met with 30-minute margin | 8h | 1h versus 1h, met with no margin |
| Admissions | 12:10 | 4h 10m | 5h | Met | 10h | 1h versus 1h, met with no margin |
| Payroll | 12:10 | 4h 10m | 8h | Met | 24h | 1h versus 4h, met |
| Records and certificates | 10:30 | 2h 30m | 24h | Met | 48h | 9h versus 24h, met |

F1 has a thin RTO margin and still misses the 11:00 examination start, so its temporary procedure remains mandatory.

---

## 10. Communication Plan

| Stakeholder | Trigger | Owner | Primary and Alternative Channels | Approver | Frequency |
|---|---|---|---|---|---|
| Learners | Activation or service change | Communications Lead | Email and SMS; tutor phone tree and website | Incident Commander | Every four hours |
| Staff | Activation and instructions | Communications Lead | Email; SMS tree | Incident Commander | Twice daily |
| Executive Sponsor and Steering Committee | Activation and decisions | BC/DR Coordinator | Phone and written note; voice bridge | Incident Commander | Hourly |
| Alternate facility and warm-site provider | Activation | Technical Lead | Phone; account manager | Incident Commander | As required |
| Payment provider | Reconciliation | Finance Manager | Support line; account manager | Incident Commander | Daily |
| Offsite backup provider | Catalogue access and validation | Technical Lead | Phone; provider portal | Technical Lead | As required |
| Legal and incident response | Suspected compromise | Incident Commander | Phone | Incident Commander | As required |
| Media | Enquiry | Communications Lead | Approved holding statement | Executive Sponsor | When verified facts change |

### 10.1 Initial Learner Notice

> **Important notice for learners, Monday 08:45 WAT**
>
> Northbridge Skills Institute's main site is closed because of flooding and a power failure. It is expected to remain inaccessible for up to 72 hours. Some systems are affected, but Microsoft 365 accounts and email remain available.
>
> Do not travel to the main site for today's 11:00 examination. A separate message will be sent by 09:30 explaining where and how the examination will take place. Learners who require a centre workstation or adjustment should reply with **EXAM SUPPORT** in the subject line.
>
> Payments can continue through the payment provider, with confirmations issued manually. Applications can be submitted through the temporary admissions form. Please retain a copy of anything submitted. The institute will never ask for your password. Updates will follow every four hours.

---

## 11. Incident Response Integration

Incident response is activated when any of the following occurs:

- Unexpected backup-administrator logon
- Backup-integrity failure without an explained hardware cause
- Unexplained data differences
- Unexpected accounts after AUTH01 restoration
- Ransom message or other evidence of malicious activity

The IR Lead may pause an affected backup, preserve evidence, replace exposed credentials, and screen restored systems. Business continuity procedures continue while the technical investigation proceeds.

---

## 12. Tabletop Exercise

### 12.1 Exercise Purpose

The 45-minute simulation tested:

- Authority under changing conditions
- Backup-selection logic
- Resource limitations
- Incident response integration
- Business reconciliation

### 12.2 Exercise Injects and Decisions

| Inject | Decision | Owner | Operational Effect |
|---|---|---|---|
| Site closure extends from 72 hours to five days | Extend alternate-site use, introduce remote teaching, establish technician rota, and request extra technical support | Incident Commander | Recovery schedule remains, but resourcing and continuity requirements increase |
| Alternate site offers only 15 workstations | Prioritise learners needing adjustments, use controlled BYOD, schedule equivalent later sessions, and retain Day 1 deferral as fallback | Exams Manager | Some learners are delayed while accessibility and assessment integrity are protected |
| DB01 incremental fails and unexpected admin logon appears | Stop the chain, activate IR, replace the shared credential, preserve logs, validate other backups, and apply a time-bounded decision rule | Technical and IR Leads | A 60-minute investigation hold delays application availability and increases reconciliation work |
| Provider shows successful payments missing from FIN01 | Treat provider records as authoritative for post-07:00 payments, reconcile totals, require dual approval, and escalate unexplained gaps | Finance Manager | Technical recovery remains complete only when business reconciliation is accepted |

### 12.3 Key Exercise Findings

- Extended outages require fatigue management and supplier capacity commitments.
- Workstation shortages must be addressed through accessibility-based prioritisation and equivalent sessions.
- A failed incremental backup can invalidate later points in the chain.
- Shared backup-administrator identities create unacceptable recovery and security risk.
- Technical restoration does not equal financial-service recovery until payment reconciliation is complete.

---

## 13. Corrective Action Plan

| No. | Action | Priority | Owner | Target | Completion Evidence |
|---:|---|---|---|---|---|
| 1 | Separate backup administration from production administration; add MFA and logon alerts | High | IT Lead | Day 14 | Access review and rejected production-credential test |
| 2 | Document and test offsite-provider access independence | High | BC/DR Coordinator | Day 30 | Provider statement and successful independence test |
| 3 | Create a weekly immutable or offline copy and complete a timed restore | High | Backup Administrator | Day 30 | Restore record and validated recovery evidence |
| 4 | Automate integrity and chain validation for all incrementals | High | Backup Administrator | Day 30 | Automated checks and alert records |
| 5 | Maintain an exam-bank copy outside LMS01 and approve the temporary assessment procedure | High | Exams Manager | Day 21 | Signed procedure and successful exercise |
| 6 | Add guaranteed workstation and five-day availability requirements to the facility contract | Medium | Facilities Manager | Day 30 | Signed contract amendment and workstation test |
| 7 | Pre-build the recovery network to shorten the critical path | Medium | Technical Recovery Lead | Day 60 | Timed drill demonstrates a 30-minute improvement |

---

## 14. Governance and Maintenance

### 14.1 Ownership and Approval

- The BC/DR Coordinator owns the plan.
- The Executive Steering Committee provides oversight and approves the budget.
- The Principal acts as Executive Sponsor and signs each version.
- The Steering Committee meets quarterly.

### 14.2 Version Control and Distribution

- Use major.minor version numbering.
- Maintain a change log, approval date, and next-review date.
- Keep controlled copies in a restricted Microsoft 365 location.
- Provide command members with encrypted offline copies.
- Store printed copies offsite.
- Withdraw superseded copies.

### 14.3 Testing Calendar

| Quarter | Test |
|---|---|
| Q1 | Flood and main-site-loss tabletop |
| Q2 | Runbook walkthrough and timed full-chain restore |
| Q3 | Backup-compromise tabletop |
| Q4 | Warm-site simulation with parallel testing |

Monthly sample restores support the quarterly programme. Review is also triggered by actual incidents, exercises, system changes, supplier changes, audit findings, staff changes, and the beginning of the local flood season.

### 14.4 Training

- Annual awareness training for all staff
- Role-specific training for command members and technicians
- Onboarding within 30 days
- Refresher training after material plan changes

---

## 15. Performance Measures

| KPI | Measurement | Target | Frequency | Owner |
|---|---|---|---|---|
| Recovery performance | Functions restored within RTO divided by functions tested; actual data age compared with RPO | 100% of T1 functions within RTO and RPO | After each test and quarterly reporting | Technical Recovery Lead |
| Restoration-test coverage | Systems and data sets with successful full restores in the last 12 months | 100% annually | Monthly tracking | Backup Administrator |
| Corrective-action closure | Actions closed by target date divided by actions due | At least 90% | Monthly | BC/DR Coordinator |
| Training completion | Required staff with current training divided by required staff | 95% overall; 100% for command and technical roles | Quarterly | HR Manager |
| Backup integrity | Backups passing first-time integrity checks divided by all backups | At least 99% | Weekly | Backup Administrator |

---

## 16. Framework Alignment

### 16.1 NIST SP 800-34 Revision 1

| Planning Element | Project Output |
|---|---|
| Policy statement | Ownership, approval, maintenance, and distribution |
| Business Impact Analysis | Critical-function analysis and impact calculations |
| Preventive controls | Immutable copy, separate administration, MFA, monitoring, and integrity checks |
| Contingency strategies | Cold, warm, and hot option comparison |
| Contingency plan | Activation, RACI, temporary procedures, runbook, and communications |
| Testing, training, and exercises | Tabletop exercise and annual testing calendar |
| Plan maintenance | Version control, review triggers, corrective actions, and KPIs |

### 16.2 ISO 22301 Themes

| Theme | Project Output |
|---|---|
| Context | Flood exposure, stakeholders, assumptions, and communication needs |
| Leadership | Steering Committee, Executive Sponsor, and activation authority |
| Planning | RTO, RPO, MTD, and residual-risk decisions |
| Support | Resources, competence, training, communications, and controlled information |
| Operation | BIA, recovery strategy, temporary procedures, and technical runbook |
| Performance evaluation | KPIs, tests, exercises, and recovery results |
| Improvement | Corrective-action register and plan updates |

### 16.3 Climate and Flood Consideration

Flood risk is treated as a relevant continuity issue because the disruption begins with an actual flood. Recommended controls include:

- Assessing the main site's flood exposure
- Locating recovery resources in a different flood zone and power grid
- Raising critical equipment above floor level
- Monitoring flood-warning triggers
- Conducting pre-flood-season reviews
- Confirming supplier and offsite-storage resilience against correlated events

---

## 17. Maturity Assessment

Northbridge is assessed at **Level 2: Developing**.

Existing strengths include backups, an offsite catalogue, a disconnected copy, and modelled recovery timings. Weaknesses include the absence of a previously formalised BIA, limited evidence of recurring tests, shared administrative identity, and unverified offsite independence.

The realistic 12-month target is **Level 3: Defined**, demonstrated through documented procedures, completed tests, formal governance, repeatable recovery performance, and at least two quarters of KPI evidence.

---

## 18. Key Conclusions

1. Teaching and assessment is the highest business priority, but technical dependencies require recovery of network, identity, security checks, and DB01 before LMS01.
2. The 11:00 examination cannot rely on technical restoration because LMS01 is not planned to return until 11:45.
3. The warm site provides the strongest balance between recovery capability and cost.
4. A one-hour DB01 RPO can be met only when hourly incrementals are complete, valid, protected, and tested.
5. Shared backup and production administration is a material risk and must be corrected.
6. An offsite or replicated copy is not sufficient without independent access controls and successful restoration tests.
7. Technology restoration becomes business recovery only after validation, reconciliation, restored controls, and owner acceptance.
8. Regular exercises, measurable KPIs, corrective-action tracking, and governance are required to move from developing to defined continuity maturity.

---

## 19. References

1. ICDFA. (n.d.). *Business Continuity and Disaster Recovery, GRC205 Week 21 Teaching Deck*.
2. ICDFA. (n.d.). *GRC205 Business Continuity and Disaster Recovery Assignment Case Data*.
3. National Institute of Standards and Technology. (2010). *SP 800-34 Revision 1: Contingency Planning Guide for Federal Information Systems*. https://csrc.nist.gov/pubs/sp/800/34/r1/upd1/final
4. International Organization for Standardization. (2019). *ISO 22301:2019 Security and Resilience, Business Continuity Management Systems*. https://www.iso.org/standard/75106.html
5. International Organization for Standardization. (2024). *ISO 22301:2019/Amd 1:2024 Climate Action Changes*. https://www.iso.org/standard/88412.html

---

## 20. Artificial Intelligence Use Statement

Generative AI was used as a learning and writing-support tool during the preparation of this assignment. It assisted with organising the report structure, improving clarity and grammar, and presenting selected concepts in a professional format.

The assignment was reviewed, edited, and completed by the student using the provided course materials and referenced standards. The student remains responsible for the accuracy, analysis, conclusions, and final submitted work.

---

## 21. Academic Integrity

This report demonstrates understanding of business continuity, disaster recovery, governance, business impact analysis, backup resilience, crisis communication, operational recovery, testing, and continuous improvement. Any reuse or adaptation should comply with applicable academic-integrity requirements.

---

<p align="center"><strong>Completed GRC205 Business Continuity and Disaster Recovery Report</strong></p>
<p align="center">Northbridge Skills Institute Flood and Power-Failure Scenario</p>
