# Crisis Communication and Stakeholder Management

![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Course-GRC205-1f6feb)
![Domain](https://img.shields.io/badge/Domain-Crisis%20Communication-6f42c1)
![Focus](https://img.shields.io/badge/Focus-Stakeholder%20Management-2ea44f)
![Scenario](https://img.shields.io/badge/Scenario-Suspected%20Cyber%20Incident-red)

## Overview

This repository contains my completed **Crisis Communication and Stakeholder Management** assignment for GRC205. The project is based on a simulated incident beginning at **08:15 on a Monday**, when several teams lose access to a critical file share, an unverified screenshot begins circulating in staff chats, a possible cyber incident is suspected, and Friday payroll may be affected.

Working as the **Communications Lead to the Incident Commander**, I developed a structured communication response that balances speed, accuracy, legal review, employee concerns, operational continuity, and stakeholder trust.

The central communication principle applied throughout the assignment is simple:

> Communicate a small, verified message quickly, distinguish facts from unknowns, and commit to the next update time.

> **Disclaimer:** The organisation, incident scenario, communication channels, contact details, and response decisions presented in this project are fictional and were created for academic purposes.

---

## Author

- **Name:** Ummulkhoyr Adebukola Shittu
- **Programme:** Governance, Risk, and Compliance
- **Course:** GRC205
- **Scenario Role:** Communications Lead to the Incident Commander
- **Institution:** ICDFA

---

## Scenario Summary

At approximately **08:15**, several teams were unable to access a critical file share. Security began investigating the disruption as a possible cyber incident. At the same time, an unverified screenshot circulated through staff chats and beyond, increasing the risk of misinformation and reputational damage.

The situation involved several communication challenges:

- The cause and extent of the disruption were unknown.
- Corporate email, staff chat, and the staff directory could be compromised.
- The circulating screenshot had not been verified.
- Friday payroll might depend on affected systems or data.
- Regulatory, contractual, and data-protection notification duties might apply.
- Customers, employees, executives, banks, partners, insurers, regulators, and the media required different information.
- Every message needed to be accurate enough to withstand legal, regulatory, and public scrutiny.

---

## Project Objectives

The assignment was designed to:

- Establish a credible source of truth during the first four hours
- Prevent rumours and leaked material from controlling the narrative
- Separate confirmed facts from assumptions and unknowns
- Define message approval and spokesperson responsibilities
- Prioritise stakeholders according to urgency and impact
- Develop employee, customer, partner, executive, and media communications
- Create resilient communication channels outside the corporate network
- Define escalation triggers for board and external engagement
- Address payroll uncertainty honestly without creating an unsupported promise
- Maintain a documented and auditable communication process

---

## Key Assumptions

| ID | Assumption | Verification Owner |
|---|---|---|
| A1 | The organisation has an Incident Commander, CISO, General Counsel, HR or Payroll Lead, and Communications Lead | Incident Commander |
| A2 | Corporate email, staff chat, and the directory may be compromised and should be treated as untrusted | CISO |
| A3 | Friday payroll may depend on systems or data connected to the affected file share | Payroll Lead |
| A4 | The bank has an unknown payroll cut-off, so Wednesday 12:00 is used as the decision point | Finance and Bank |
| A5 | Data-protection and contractual notification deadlines may apply | General Counsel |
| A6 | Bulk SMS, an externally hosted status page, and an offline contact sheet exist outside the corporate network | HR and IT |

---

## Communication Governance

### Approval Chain

Every message follows the same controlled process:

1. The Incident Commander confirms the operational facts.
2. Legal reviews the proposed wording.
3. The Incident Commander authorises release.
4. The Communications Lead distributes and records the message.

### Disclosure Rules

- Only named spokespeople may communicate externally.
- All other staff refer questions to the Communications Lead.
- Use **“possible cyber incident”** until Security confirms otherwise.
- Do not state “ransomware,” “breach,” or “attack” as confirmed facts without evidence.
- Do not repeat claims from an unverified screenshot.
- If information is not recorded in the approved fact log, it is not communicated.
- Unknowns are clearly labelled as under investigation.
- Each update states when the next update will be issued.

---

## First Four-Hour Communication Plan

| Time | Action | Owner | Output |
|---:|---|---|---|
| 08:30 | Incident command alignment using an out-of-band bridge | Incident Commander and Communications Lead | Fact log, named spokespeople, approval chain, and checkpoints |
| 08:45 | Verbal briefing to the CEO | Incident Commander | Leadership awareness of confirmed facts, unknowns, and timing |
| 08:45-09:25 | Draft employee and customer statements; obtain legal review; monitor screenshot spread | Communications Lead and Legal | Approved messages |
| 09:30 | Issue employee holding statement through SMS | Communications Lead | Staff message sent and receipt tracking started |
| 09:30-10:30 | Contain the screenshot, preserve evidence, remove internal copies, and monitor external spread | Communications Lead and Security | Leak log and preserved evidence copy |
| 10:45 | Update the fact log with the CISO | Incident Commander and CISO | Confirmed and unknown lists updated |
| 11:00 | Issue executive and board briefing | Communications Lead and Incident Commander | Decisions and approvals requested |
| 11:15-11:30 | Contact bank and payroll partners; send customer and partner update after approval | Finance Lead and Customer Lead | Calls logged and update issued |
| 12:00 | Review escalation triggers and the next draft | Incident Commander | Go or hold decision for the 12:30 update |
| 12:30 | Issue the second employee update | Communications Lead | First communication cycle completed |

### Why This Order Was Selected

Alignment comes first because conflicting messages and early speculation can create greater harm than a short delay. The CEO receives a verbal briefing before the workforce message. Employees are then contacted because the leak is spreading through staff channels and they need immediate instructions. Customers, partners, and external stakeholders receive updates after the facts and wording have been reviewed.

---

## Verification Gates

| Information | Verification Owner | Communication Requirement |
|---|---|---|
| Attacker identity | Security and external specialists | Must be verified and approved by the Incident Commander and Legal |
| Root cause and entry point | Forensics | Investigation must confirm the finding |
| Number of affected systems | Security | Asset assessment must be completed |
| Data exposure | Forensics and Legal | Evidence of access or exfiltration must exist |
| Recovery time | IT and vendors | A tested restoration plan must exist |
| Regulatory reporting duty | General Counsel | Legal must assess the facts against applicable law |
| Payroll status | Payroll Lead and bank | Systems must be confirmed safe and bank cut-off known |

---

## Stakeholder Prioritisation

| Stakeholder | Priority | Primary Need | Owner | Main Channel |
|---|---|---|---|---|
| Direct workforce | High | Clear instructions, payroll honesty, and a reporting route | Communications Lead with HR | SMS and external status page |
| Executive leadership and Board | High | Verified facts, unknowns, exposure, legal risk, and decisions | Incident Commander and Communications Lead | Phone and secure messaging |
| Key customers and B2B clients | High | Service continuity, accurate scope, named contact, and fraud warning | Customer Lead | Account-manager call and unaffected email domain |
| Regulators and Legal Counsel | High | Precise, privileged, and auditable records | General Counsel | Secure legal line and portal |
| Banking and payroll partners | High and time-critical | Cut-offs, transfer boundaries, and clean file-source assurance | Finance and Payroll Lead | Verified phone number and secure bank portal |
| Cyber insurer and law enforcement | Medium | Prompt notice, verified facts, and evidence access | General Counsel and CISO | Insurer hotline and official reporting route |
| Media and public | Initially low, potentially high | One approved line without speculation | Communications Lead | Reactive holding statement |

---

## Escalation Triggers

Any one of the following triggers moves the matter to the Board Chair, Legal-led external contact, and a formal decision meeting:

- Evidence that data left the organisation
- Evidence that the leaked screenshot contains personal or confidential information
- Payroll cannot be confirmed safe to run by Wednesday at 12:00
- Contact or a demand is received from the attacker
- A media or regulator enquiry is received
- The screenshot becomes publicly visible
- The primary incident-command channel fails

Only the Incident Commander and Legal may engage with an attacker.

---

## Communication Deliverables

### Employee Holding Statement

The employee statement:

- Confirms the file-share disruption
- Describes the matter as a possible cyber incident
- States that the screenshot is unverified
- Instructs employees not to forward or discuss it
- Directs staff to stop using the affected file share
- Warns against unexpected attachments and USB devices
- Prevents unapproved recovery attempts
- Directs external enquiries to the Communications Lead
- Treats payroll as a priority without promising an unverified outcome
- Commits to the next update at 12:30

### Customer and Partner Update

The customer message:

- Confirms a disruption affecting part of the internal file systems
- Explains that precautionary security measures have been taken
- Separates confirmed service status from unknown matters
- Provides a named contact for urgent transactions and deliverables
- Warns against fraudulent credential or payment requests
- Commits to another update by 14:00 or sooner if facts materially change

### Executive and Board Briefing

The executive briefing presents:

- Confirmed facts and operational assumptions
- Unknowns that must not be stated externally
- Payroll, legal, reputational, phishing, and spokesperson risks
- Decisions requiring executive approval
- Actions already in progress
- Scheduled update times and escalation conditions

---

## Channel-Resilience Plan

Corporate systems may be untrusted, so communication routes are designed to operate independently of the affected environment.

| Audience | Primary Channel | Fallback Channel | Confirmation Method |
|---|---|---|---|
| Incident command team | Dedicated bridge and separate-tenant secure messaging | Personal-mobile phone tree | Roll call at each checkpoint; absentees called within five minutes |
| Employees | External bulk SMS | Status page, line-manager cascade, and site notices | Staff reply “1”; target 90% acknowledgement by 10:30 |
| Executives and Board | Direct call from Incident Commander or CEO office | SMS and personal email through Company Secretary | Verbal acknowledgement recorded with time |
| Customers and B2B clients | Account-manager call and unaffected email domain | Status page and SMS | Call log, reply, or read receipt |
| Bank and payroll partners | Verified relationship-manager call | Secure bank portal or in-person visit | Call-back, reference number, and written out-of-band confirmation |
| Legal Counsel and regulators | Counsel's secure line and portal | External encrypted email | Contact time and reference recorded by Counsel |

### Readiness Measures

- Test the SMS provider without corporate login credentials.
- Confirm that the external status page remains accessible.
- Maintain offline contact lists.
- Use a pre-agreed code word for identity confirmation.
- Test the phone tree regularly.
- Record the time, owner, audience, content, and approval of every message.

---

## Key Communication Principles Demonstrated

### Accuracy Before Speculation

The response does not name an attacker, claim a breach, promise payroll, announce data safety, or confirm regulatory reporting before the relevant evidence and authorisation exist.

### Speed With Control

The first workforce message is issued within one hour of the alignment call, but only after fact confirmation and legal review.

### Fixed Update Cadence

Stakeholders receive updates at defined times, even when the facts have not materially changed. This reduces uncertainty and prevents silence from being interpreted as concealment.

### Audience-Specific Messaging

Employees need instructions and payroll clarity. Executives need risks and decisions. Customers need service facts and fraud warnings. Banks need cut-off and source-integrity assurance. Legal and regulators need precise, auditable information.

### Channel Resilience

The plan assumes that corporate email and chat may be unavailable or compromised and therefore uses SMS, phone calls, external portals, offline contact sheets, and separate communication tenants.

---

## Critical Reflection

The most difficult communication issue involved payroll. Employees need reassurance, but an unsupported promise that payroll will proceed normally could create greater harm if it later fails.

The selected approach was to:

- Recognise payroll as a priority
- State that timing remained unconfirmed
- Avoid both positive and negative speculation
- Commit to a specific update time
- Give employees clear actions they could take immediately

This approach protects credibility while acknowledging staff concerns. It also recognises that a reassuring statement may become a legal or employee-relations commitment if it is not carefully controlled.

---

## Risks Addressed

- Misinformation caused by an unverified screenshot
- Contradictory statements from multiple spokespeople
- Premature claims of ransomware, breach, or data loss
- Payroll uncertainty and employee anxiety
- Follow-on phishing and fraudulent payment requests
- Compromised corporate communication channels
- Missed regulatory or contractual notification duties
- Unauthorised attacker engagement
- Media escalation before facts are confirmed
- Loss of trust caused by missed update commitments

---

## Skills Demonstrated

- Crisis communication planning
- Stakeholder identification and prioritisation
- Incident-command communication
- Fact, assumption, and unknown separation
- Message approval governance
- Employee communication
- Customer and partner communication
- Executive and board briefing
- Legal and regulatory coordination
- Payroll-risk communication
- Media-response preparation
- Out-of-band communication planning
- Escalation-threshold development
- Communication logging and acknowledgement tracking
- Ethical communication under uncertainty

---

## Repository Contents

```text
.
├── README.md
└── GRC205 CRISIS COMMUNICATION & STAKEHOLDER MANAGEMENT.docx
```

---

## How to Review This Project

1. Review the scenario assumptions and verification owners.
2. Examine the first four-hour communication timeline.
3. Review the disclosure rules and verification gates.
4. Assess the stakeholder map, channels, owners, and update cadence.
5. Read the employee, customer, and executive communication drafts.
6. Examine the channel-resilience and acknowledgement approach.
7. Review the escalation triggers and critical reflection.

---

## Important Notes

- All incident details are part of a fictional academic scenario.
- The screenshot is treated as unverified, not genuine or false.
- The report does not confirm ransomware, a breach, data exfiltration, an attacker, or a root cause.
- Payroll timing is not promised because system safety and bank cut-offs remain unverified.
- Regulatory notification is treated as a Legal decision based on verified facts and applicable law.
- Placeholder contact details must be replaced only in an authorised operational version.
- This README summarises the completed assignment and does not replace the source report.

---

## Academic Integrity

This repository demonstrates my understanding of crisis communication, stakeholder management, incident-command coordination, channel resilience, message governance, and communication under uncertainty. Any reuse or adaptation should comply with applicable academic-integrity requirements.

---

## Contact

For professional or academic enquiries, please use the contact information available on my GitHub profile.

---

<p align="center"><strong>Completed GRC205 Crisis Communication and Stakeholder Management Project</strong></p>
