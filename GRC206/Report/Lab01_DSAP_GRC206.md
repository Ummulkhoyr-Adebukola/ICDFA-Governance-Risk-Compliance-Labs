# Security Awareness Program Design Report

## Northbridge Logistics: 12-Month Human-Risk Reduction Programme

![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Course-GRC206-1f6feb)
![Focus](https://img.shields.io/badge/Focus-Security%20Awareness-6f42c1)
![Duration](https://img.shields.io/badge/Duration-12%20Months-2ea44f)
![Workforce](https://img.shields.io/badge/Workforce-800%20Employees-orange)

---

## Document Control

| Field | Details |
|---|---|
| **Report title** | Security Awareness Program Design Report |
| **Organisation** | Northbridge Logistics, fictional |
| **Prepared by** | Ummulkhoyr Adebukola Shittu |
| **Registration number** | 2025/GCR/12699 |
| **Course** | GRC206 |
| **Programme horizon** | 12 months |
| **Workforce scope** | 800 employees across head office, warehouses, remote sales, and IT administration |
| **Report status** | Completed academic assignment |
| **Classification** | Academic use |

> **Scenario disclaimer:** Northbridge Logistics, its workforce profile, incidents, programme assumptions, baselines, and targets are part of an academic scenario. All performance targets are proposed planning objectives and not existing organisational results.

---

## Executive Summary

This report presents a practical 12-month security awareness programme for Northbridge Logistics, a fictional logistics organisation with 800 employees working across a head office, warehouse locations, remote sales roles, and IT administration.

The programme addresses three priority human-driven risks: Business Email Compromise and invoice fraud, password reuse and weak credential hygiene, and phishing across a dispersed workforce using different devices and communication channels.

Rather than applying one generic training package to all staff, the programme segments the workforce into four audiences and assigns each group suitable content, delivery formats, reporting routes, and performance measures. Head-office and Finance teams receive deeper training on invoice fraud and regulated data. Warehouse employees receive short, visual, shift-based content. Remote sales personnel receive mobile-first training. IT administrators receive technical guidance on MFA, privileged access, and incident triage.

The programme establishes three measurable objectives:

1. Reduce the simulated-phishing click rate to below 10% within six months and below 5% within 12 months.
2. Increase suspicious-email reporting to at least 25% within six months and 40% within 12 months.
3. Achieve 90% onboarding-training completion within a new employee's first 30 days and 95% annual-refresher completion by Month 9.

The design intentionally uses low-cost tools, including existing email-gateway logs, a basic survey platform, printed materials, and spreadsheet tracking. This reflects the assumed capacity of a two-to-three-person security team without a dedicated phishing-simulation platform.

Four core measures are reported through a quarterly dashboard: training completion, phishing click rate, phishing report rate, and fraud-attempt incidents. The programme also promotes a no-blame reporting culture, immediate supportive coaching, learner feedback, quarterly improvement reviews, and recognition of positive security behaviour.

---

## 1. Organisational Context

Northbridge Logistics operates through multiple work environments:

- A head office supporting Finance, Procurement, Human Resources, and Administration
- Warehouse operations using shared terminals and handheld devices
- Remote sales personnel using mobile devices and public networks
- IT and system-administration teams with elevated access

This mixed workforce creates different patterns of exposure. A standard annual presentation would not adequately address the judgement required for invoice verification, the limited desk time available to warehouse employees, mobile phishing risks affecting remote workers, or privileged-access risks affecting administrators.

### 1.1 Programme Assumptions

- The security function consists of approximately two to three people.
- No dedicated phishing-simulation platform is available at the beginning of Year 1.
- Existing email-gateway logs can support basic simulation analysis.
- A free or low-cost survey tool is available.
- MFA exists through the identity provider but is not fully enforced.
- HR has an onboarding checklist to which a security module can be added.
- Manual spreadsheet tracking is acceptable during the first year.
- Proposed targets are planning choices rather than measured historical results.

---

## 2. Human-Risk Assessment

### 2.1 Priority Risk 1: Invoice and Payment Fraud

Recent invoice-fraud attempts indicate that Finance and Procurement are active targets. Attackers may impersonate executives, suppliers, or internal staff and request urgent payments or changes to bank details.

**Potential consequences:**

- Direct financial loss
- Supplier-payment diversion
- Operational disruption
- Fraud investigation costs
- Reputational damage
- Weaknesses in approval and verification controls

**Primary controls:**

- Mandatory verbal callback using independently verified contact details
- Dual approval for payment-detail changes
- BEC and impersonation awareness
- Clear escalation route for urgent or unusual requests

### 2.2 Priority Risk 2: Password Reuse and Weak Credential Hygiene

The scenario records password reuse by two employees following a breach. Reused credentials may allow attackers to access corporate accounts through credential stuffing or password spraying.

**Potential consequences:**

- Account takeover
- Unauthorised access to regulated customer information
- Compromised email used for further fraud
- Privileged-account compromise
- Wider lateral movement

**Primary controls:**

- MFA enrolment and enforcement
- Unique passwords or approved password managers
- Privileged-account separation
- Immediate password changes after suspected exposure
- Technical monitoring and supportive awareness training

### 2.3 Priority Risk 3: Phishing and Suspicious-Link Handling

Northbridge staff use desktop email, shared warehouse terminals, and mobile devices. This creates exposure to email phishing, smishing, malicious links, fake login pages, QR-code lures, and social engineering.

**Potential consequences:**

- Credential theft
- Malware execution
- Fraudulent payments
- Data exposure
- Device compromise
- Delayed incident reporting

**Primary controls:**

- Role-relevant training
- Quarterly simulations or equivalent exercises
- Simple reporting routes
- Immediate supportive feedback
- Reinforcement through short, repeated learning activities

---

## 3. Audience Segmentation

| Audience | Access and Work Pattern | Distinct Training Need |
|---|---|---|
| Head Office, Finance, Procurement, HR, and Admin | Desk-based, regular email and invoicing access, handles regulated information | BEC, invoice-fraud red flags, callback verification, and secure data handling |
| Warehouse Operations | Shared terminals, handheld scanners, limited desk time, and higher turnover | Short visual content, shared-terminal hygiene, physical social engineering, badge and visitor reporting |
| Remote Sales | Mobile-first, personal or corporate devices, public Wi-Fi, and travel | Smishing, secure remote access, device protection, and lost-device reporting |
| IT and System Administrators | Elevated and privileged access | MFA enforcement, credential hygiene, privileged-account protection, and basic incident triage |

### 3.1 Segmentation Rationale

The segmentation recognises that employees face different risks and have different opportunities to learn. Warehouse staff may not have individual email accounts or reliable desk time, while Finance teams need practice evaluating realistic payment requests. Remote sales personnel need mobile-friendly content, and administrators require greater technical depth.

---

## 4. Pre-Launch Baseline

A reliable baseline is required before programme performance can be evaluated.

### 4.1 Phishing Susceptibility

Conduct one unannounced, benign simulated-phishing exercise before programme launch. Record click and report rates by audience using available email-gateway logs.

### 4.2 Credential Hygiene

Use a short anonymous survey to assess password reuse and security habits. Where available, compare the results with MFA-enrolment reports from the identity provider.

Self-reported results must be treated cautiously because respondents may forget, misunderstand, or underreport insecure behaviour.

### 4.3 Incident History

Review 12 months of:

- Helpdesk tickets involving suspicious email
- Finance records of attempted invoice or payment fraud
- Lost-device reports
- Account-compromise records
- Security reports submitted by employees

The baseline should establish counts, trends, affected audiences, and available financial values without assuming that all incidents were detected or reported.

---

## 5. Programme Objectives

| Objective | Six-Month Target | Twelve-Month Target | Measurement Source |
|---|---:|---:|---|
| Reduce simulated-phishing click rate | Below 10% | Below 5% | Quarterly simulation and email-gateway logs |
| Increase suspicious-email report rate | At least 25% | At least 40% | Report-button or reporting-route logs |
| Improve training completion | 90% of new hires within 30 days | 95% annual-refresher completion by Month 9 | HR and training tracker |

### 5.1 Objective Design

The objectives measure reach and behaviour rather than attendance alone. Training completion shows whether staff were reached, while click and report rates indicate whether behaviour is changing. Fraud-attempt incidents provide a business-outcome measure but must be interpreted carefully because improved reporting can initially increase recorded incident numbers.

---

## 6. Governance and Ownership

| Role | Primary Responsibility |
|---|---|
| Executive Sponsor, such as the COO | Approves resources, visibly supports the programme, and reviews performance |
| Security or IT Manager | Owns programme design, scheduling, content, measurement, and reporting |
| Finance Manager | Champions participation and owns invoice-fraud controls within Finance |
| Warehouse Operations Manager | Fits learning into shifts and supports warehouse reporting routes |
| Sales Director | Promotes completion and mobile-security practices within Remote Sales |
| IT Systems Lead | Owns administrator training, MFA enforcement, and privileged-access topics |
| Human Resources | Embeds awareness into onboarding and tracks required completion |

### 6.1 Governance Cycle

- Monthly onboarding-completion review
- Quarterly simulation or equivalent exercise
- Quarterly dashboard and 60-minute review meeting
- Up to three corrective actions per review, each with an owner and target date
- Annual report to leadership at the end of Month 12
- Off-cycle updates following incidents, near-misses, new scam patterns, or process changes

---

## 7. Role-Based Content Plan

### 7.1 Head Office and Finance

- BEC and invoice-fraud warning signs
- Supplier-bank-detail verification
- Mandatory verbal callback procedures
- Urgent-request and executive-impersonation tactics
- Regulated-customer-data handling
- Suspicious-message reporting

### 7.2 Warehouse Operations

- Logging out of shared terminals
- Prohibition on shared user credentials
- Recognising loading-dock and visitor social engineering
- Lost-badge and suspicious-visitor reporting
- QR-code and handheld-device risks
- Simple in-person reporting methods

### 7.3 Remote Sales

- Smishing and mobile phishing
- Safe use of devices on public networks
- Lost or stolen device reporting
- Mobile-app and QR-code caution
- Secure remote access
- Credential and MFA protection

### 7.4 IT and Administrators

- Privileged-account separation
- Unique administrator credentials
- MFA enforcement
- Credential-vault and password-manager practices
- Basic incident triage
- Escalation of suspicious authentication activity

---

## 8. Delivery Strategy

| Audience | Delivery Format | Why It Fits |
|---|---|---|
| Head Office and Finance | Quarterly 90-minute workshop plus monthly five-minute micro-video | Supports interactive discussion of realistic invoice and judgement scenarios |
| Warehouse Operations | Short shift-start toolbox talks, posters, and laminated reference cards | Fits shift culture and limited computer access |
| Remote Sales | Monthly three-to-five-minute mobile learning plus quarterly virtual call-in | Works for mobile-first employees who rarely share one office |
| IT and Administrators | Biannual technical briefing and ad-hoc advisories | Provides focused depth for a small technical audience |

### 8.1 Onboarding

A 30-to-45-minute role-tailored module is delivered during the first week of employment and completed before system credentials are issued. HR tracks completion. The module covers the three priority risks and the appropriate reporting route.

### 8.2 Phishing Simulations

Quarterly campaigns are delivered to email-enabled staff. Warehouse employees without individual email access complete an equivalent paper- or poster-based “spot the scam” exercise.

Employees who click receive an immediate, friendly two-minute explainer. Results are not used for disciplinary action. Employees with three or more simulation clicks within a year are offered a supportive check-in to identify barriers rather than being publicly identified or shamed.

### 8.3 No-Blame Reporting

The programme provides:

- A single report button or address for suspicious emails
- Automatic acknowledgement after a report is submitted
- A verbal route through warehouse supervisors or the security team
- A phone or app route for remote employees reporting lost devices
- Clear assurance that prompt reporting of mistakes is welcomed

Only deliberate circumvention of controls is referred through normal HR procedures.

---

## 9. Measurement Framework

| Metric | Type | Calculation | Source | Owner | Review Cycle |
|---|---|---|---|---|---|
| Training completion rate | Reach | Completed divided by required | HR and training tracker | HR | Monthly for onboarding and quarterly for refresher |
| Phishing click rate | Behaviour | Clicked divided by recipients | Simulation or email-gateway logs | Security or IT Manager | After each quarterly campaign |
| Phishing report rate | Behaviour | Reported divided by recipients | Reporting-route logs | Security or IT Manager | After each campaign and monthly |
| Fraud-attempt incidents | Outcome | Count and financial value per quarter compared with baseline | Finance incident log | Finance Manager | Quarterly |

### 9.1 Quarterly Dashboard

The one-page dashboard should show:

- Current result
- Pre-launch baseline
- Six-month target
- Twelve-month target
- Audience-level breakdown where sample size is meaningful
- Short explanation of movement
- Risks and limitations
- Corrective actions
- Resources or decisions required from leadership

### 9.2 Measurement Limitations

- Small audience groups may produce unstable percentages.
- Self-report surveys are affected by recall and social-desirability bias.
- Fraud data is a lagging measure.
- An increase in reporting may initially increase recorded incidents.
- Email-gateway logs may not provide the same detail as a dedicated simulation platform.
- Manual spreadsheet tracking introduces data-quality and administrative risks.

---

## 10. Twelve-Month Programme Calendar

| Month | Head Office and Finance | Warehouse | Remote Sales | IT and Admin | Programme-Wide Activity |
|---:|---|---|---|---|---|
| 1 | Baseline survey | Baseline survey | Baseline survey | Programme finalised | Pre-launch baseline captured |
| 2 | Launch and Workshop 1 on BEC | Posters, cards, and Toolbox Talk 1 | Micro-learning 1 | Technical Briefing 1 | Full programme launch |
| 3 | Micro-learning | Toolbox Talk 2 | Micro-learning 2 | No scheduled event | Q1 simulation, warehouse quiz, and Review 1 |
| 4 | No scheduled event | Toolbox Talk 3 | Micro-learning 3 | No scheduled event | Content refreshed using Q1 feedback |
| 5 | Workshop 2 | Toolbox Talk 4 | Virtual Call-In 1 | No scheduled event | Feedback survey cycle |
| 6 | Micro-learning | Toolbox Talk 5 | Micro-learning 4 | No scheduled event | Q2 simulation and six-month Review 2 |
| 7 | No scheduled event | Toolbox Talk 6 | Micro-learning 5 | Technical Briefing 2 | Monthly recognition programme begins |
| 8 | Workshop 3 | Toolbox Talk 7 | Virtual Call-In 2 | No scheduled event | Feedback survey cycle |
| 9 | Annual refresher | Annual refresher | Annual refresher | Annual refresher | Q3 simulation and Review 3 |
| 10 | No scheduled event | Toolbox Talk 8 | Micro-learning 6 | No scheduled event | Refresher completion tracking |
| 11 | Workshop 4 | Toolbox Talk 9 | Virtual Call-In 3 | Advisory if required | Feedback survey cycle |
| 12 | Micro-learning | Toolbox Talk 10 | Micro-learning 7 | No scheduled event | Q4 simulation, Review 4, and annual leadership report |

---

## 11. Continuous Improvement and Sustainability

### 11.1 Quarterly Review

The programme owner, executive sponsor, and four audience owners meet for 60 minutes each quarter. They review the dashboard, learner feedback, incident trends, and delivery challenges. The group agrees no more than three priority actions, each with a named owner and due date.

### 11.2 Learner Feedback

Each training activity includes a two-to-three-question anonymous survey delivered through an audience-appropriate channel:

- QR code on warehouse posters
- End-of-session poll for workshops
- Email link for head-office staff
- Mobile link for remote sales

Feedback is used to adjust timing, format, language, accessibility, and relevance.

### 11.3 Positive Recognition

- A monthly **Great Catch** feature recognises, with consent, a person or team whose report helped stop a real threat.
- Line managers may provide a small, discreet token of recognition for genuine near-miss reporting.
- Employees who report their own mistakes are included, reinforcing that prompt reporting is more valuable than pretending to be perfect.
- Simulation results are never used for public ranking or humiliation.

### 11.4 Off-Cycle Updates

Content is updated outside the quarterly schedule when:

- A new scam pattern appears
- A confirmed incident or near-miss occurs
- A business process changes
- A new payment system is introduced
- A recurring simulation weakness is identified
- A legal, contractual, or technical requirement changes

---

## 12. Resource and Tooling Model

The first-year design prioritises sustainability over sophistication.

### Existing or Low-Cost Resources

- Email-gateway logs for campaign measurement
- Identity-provider MFA reports
- Spreadsheet-based tracking
- Free or low-cost survey tools
- Existing HR onboarding processes
- Printed posters and laminated cards
- Short internally produced videos
- Finance incident logs and helpdesk tickets

### Control Requirements for Manual Tracking

- Restrict access to the tracker
- Define one data owner
- Use consistent audience and metric definitions
- Protect employee-level data
- Retain only necessary information
- Validate formulas before quarterly reporting
- Keep version history and backup copies

### Future Maturity Option

If the first-year programme demonstrates value and manual administration becomes burdensome, leadership may consider a dedicated awareness and phishing-simulation platform. Any procurement decision should assess workforce size, required integrations, data-protection terms, reporting capability, accessibility, and total annual cost.

---

## 13. Framework Alignment

### 13.1 NIST SP 800-50

The project follows the general lifecycle of building and maintaining a security awareness and training programme:

- Assess organisational needs and risks
- Define roles and responsibilities
- Develop audience-specific learning
- Deliver training and awareness activities
- Measure effectiveness
- Improve and sustain the programme

### 13.2 SANS Security Awareness Maturity Model

The design supports movement from ad-hoc activity toward a structured and measurable programme through:

- Defined ownership
- Role-based content
- Regular campaigns
- Behavioural metrics
- Management reporting
- Quarterly review
- Continuous improvement

---

## 14. Ethical, Privacy, and Cultural Considerations

- Simulation results should be used for improvement rather than punishment.
- Employee-level results should be restricted to authorised personnel.
- Reports to leadership should favour aggregate trends unless individual intervention is necessary.
- Training must be accessible to different literacy levels, devices, languages, and work patterns.
- Recognition requires employee consent before names are published.
- Simulations should avoid highly distressing themes or deceptive requests involving personal emergencies.
- Reporting channels should acknowledge employees promptly and protect them from retaliation.
- The programme should reward early reporting, including reports submitted after a genuine mistake.

---

## 15. Key Risks to Programme Success

| Risk | Potential Effect | Mitigation |
|---|---|---|
| Limited security-team capacity | Cancelled campaigns or weak analysis | Keep the metric set small and use a fixed quarterly cycle |
| Generic training content | Low relevance and poor behaviour change | Maintain audience segmentation and role-based examples |
| Punitive response to mistakes | Under-reporting and hidden incidents | Apply a documented no-blame reporting approach |
| Manual spreadsheet errors | Incorrect dashboard results | Assign one owner, validate formulas, and retain version history |
| Low warehouse access to digital learning | Incomplete coverage | Use toolbox talks, posters, cards, and supervisor routes |
| Leadership disengagement | Weak completion and limited resources | Use visible executive sponsorship and quarterly decisions |
| Simulation fatigue | Reduced engagement and gaming | Vary scenarios and combine simulations with practical coaching |
| Overreliance on click rate | Incomplete view of risk | Include report rate, completion, and business incident measures |

---

## 16. Critical Reflection

The most difficult part of the design was the measurement plan rather than the training content. Northbridge's modest budget means that the programme cannot initially depend on a dedicated simulation platform or mature analytics dashboard. Metrics must instead be built from logs, spreadsheets, and a basic survey tool.

This creates a trade-off between a sophisticated adaptive programme and one that a two-to-three-person security team can operate consistently. Rich segmentation and continuous micro-simulations could produce faster feedback, but they would also create a heavy administrative burden and may not be sustainable throughout the year.

The design resolves this by limiting the dashboard to four core measures and reviewing them quarterly. This accepts slower feedback in exchange for realistic delivery, consistent interpretation, and a greater likelihood that the programme will remain active for the full 12 months.

---

## 17. Recommendations

1. Capture the pre-launch baseline before delivering training.
2. Enforce MFA progressively, beginning with privileged and high-risk roles.
3. Implement verbal callback verification for payment-detail changes.
4. Create one simple reporting route for suspicious email and separate routes for warehouse and mobile workers.
5. Maintain quarterly simulations without using results for punishment.
6. Track click and report rates together rather than treating click rate as the only success measure.
7. Embed role-specific security training into HR onboarding before credentials are issued.
8. Use aggregate reporting to protect employee privacy.
9. Limit each quarterly review to three priority actions with owners and dates.
10. Reassess dedicated awareness-platform procurement after the first year using evidence of workload and programme value.

---

## 18. Skills Demonstrated

- Human-risk assessment
- Audience segmentation
- Role-based security-awareness design
- Business Email Compromise risk treatment
- Phishing-simulation planning
- No-blame reporting design
- Security metrics and KPI development
- Programme governance and ownership
- Twelve-month campaign planning
- Learner-feedback design
- Positive security-culture development
- Continuous improvement planning
- Ethical use of simulation data
- Resource-constrained programme design

---

## 19. Conclusion

The Northbridge Logistics Security Awareness Programme translates human-risk priorities into a practical and measurable 12-month plan. It recognises that security awareness is not a one-time annual presentation and that different employee groups require different content and delivery methods.

The design balances behavioural ambition with organisational capacity. It uses measurable targets, role-based delivery, quarterly simulations, no-blame reporting, positive recognition, and four focused metrics. Its low-cost operating model is suitable for a small security team while still creating a path toward a more mature programme.

The programme's success should ultimately be judged by safer decisions, earlier reporting, stronger credential practices, fewer successful fraud attempts, and sustained leadership support rather than training attendance alone.

---

## 20. Repository Structure

```text
.
├── README.md
├── GRC206_SECURITY_AWARENESS_PROFESSIONAL_MARKDOWN_REPORT.md
└── GRC 206 Design a Security Awareness Program.docx
```

---

## 21. References

1. National Institute of Standards and Technology. *NIST SP 800-50: Building an Information Technology Security Awareness and Training Program*.
2. SANS Institute. *Security Awareness Maturity Model*.
3. ICDFA. *GRC206 Design a Security Awareness Program assignment brief and course materials*.

---

## 22. Artificial Intelligence Use Statement

Generative AI was used as a learning and writing-support tool during the professional organisation and Markdown formatting of this report. It assisted with report structure, clarity, grammar, and presentation.

The assignment was reviewed, edited, and completed by the student using the provided course materials and scenario requirements. The student remains responsible for the accuracy, analysis, conclusions, and final submitted work.

---

## 23. Academic Integrity

This report demonstrates understanding of security awareness programme design, human-risk reduction, audience segmentation, behaviour measurement, stakeholder engagement, and continuous improvement. Any reuse or adaptation should comply with applicable academic-integrity requirements.

---

<p align="center"><strong>Completed GRC206 Security Awareness Program Design Report</strong></p>
<p align="center">Prepared by Ummulkhoyr Adebukola Shittu</p>
