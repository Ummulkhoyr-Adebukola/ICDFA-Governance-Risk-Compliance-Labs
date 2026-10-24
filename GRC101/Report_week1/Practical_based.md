# Linux Security and GRC Technical Lab Report

## Introduction to GRC and the Technical Landscape

![Status](https://img.shields.io/badge/Status-Completed-success)
![Course](https://img.shields.io/badge/Course-GRC101-1f6feb)
![Lab](https://img.shields.io/badge/Lab-Week%201-6f42c1)
![Platform](https://img.shields.io/badge/Platform-Linux-FCC624)
![Focus](https://img.shields.io/badge/Focus-GRC%20Technical%20Foundations-2ea44f)

---

## Document Control

| Field | Details |
|---|---|
| **Report title** | Linux Security and GRC Technical Lab Report |
| **Lab title** | Introduction to GRC and Technical Landscape |
| **Course** | GRC101 |
| **Week** | Week 1 |
| **Prepared by** | Shittu Ummulkhoyr Adebukola |
| **Registration number** | 2025/GRC/12699 |
| **Submission date** | 18 January 2026 |
| **Report type** | Practical laboratory report |
| **Status** | Completed |

> **Lab notice:** All commands, screenshots, IP addresses, observations, and findings in this report relate to the controlled learning environment used for the assignment. They should not be treated as findings from a production system.

---

## Executive Summary

This report documents a practical Linux laboratory completed as part of the Week 1 introduction to Governance, Risk, and Compliance. The lab developed foundational command-line skills that support security administration, compliance monitoring, evidence collection, and technical auditing.

The work covered three main technical areas:

1. Linux file-system navigation
2. File permissions and access security
3. Security-log analysis and extraction

A structured `audit_evidence` workspace was created to separate policies, confidential evidence, and copied log files. Linux permissions were applied using `chmod` to demonstrate least-privilege access. System logs were then reviewed with tools such as `head`, `tail`, `wc`, and `grep` to identify authentication failures, privileged commands, and other security-relevant events.

The recorded lab results included seven `sudo` events, four failed authentication attempts, two SSH logins within one minute from `192.168.1.101`, and invalid-user attempts associated with the exercise addresses `203.0.113.45` and `203.0.113.47`.

The practical demonstrated that Linux administration is relevant to GRC because technical evidence is required to support access-control reviews, audit trails, incident investigations, control testing, accountability, and compliance assurance.

---

## 1. Lab Purpose

The purpose of this lab was to build practical Linux skills that can be used during security reviews, compliance assessments, audit-evidence collection, and incident investigations.

The lab focused on understanding how to:

- Navigate the Linux file system
- Locate important system directories
- Distinguish absolute and relative paths
- Review file and directory permissions
- Apply least-privilege access settings
- Organise audit evidence
- Extract and filter security logs
- Interpret security-relevant events
- Document technical findings professionally

---

## 2. Learning Objectives

By completing the lab, the following objectives were addressed:

- Use essential Linux command-line tools confidently
- Understand the purpose of common Linux directories
- Create an organised workspace for compliance evidence
- Interpret symbolic and octal permission notation
- Apply suitable permissions to policy files, confidential evidence, and log directories
- Review user and group information
- Examine system and authentication logs
- Filter logs for errors, failed activity, authentication events, and `sudo` usage
- Relate technical findings to GRC responsibilities
- Produce an evidence-supported lab report

---

## 3. Lab Environment and Tools

### 3.1 Environment

The practical was completed in a Linux command-line environment. A working directory named `grc-lab-week1` was created in the user's home directory to organise the exercises and evidence.

### 3.2 Main Commands Used

| Command | Purpose |
|---|---|
| `pwd` | Display the current working directory |
| `ls -la` | List files, hidden items, ownership, and permissions |
| `cd` | Change the current directory |
| `mkdir -p` | Create directories and parent directories where required |
| `touch` | Create an empty file |
| `chmod` | Change file or directory permissions |
| `id` | Display the current user's identity and group details |
| `groups` | Display group memberships |
| `cat` | Display text-file contents |
| `head` | Display the beginning of a file |
| `tail` | Display the end of a file |
| `wc -l` | Count lines in a file or command output |
| `grep` | Search and filter text using a pattern |
| `cp` | Copy files into the evidence workspace |

---

## 4. Task 1: Linux File-System Navigation

### 4.1 Objective

The objective was to navigate the Linux file system and understand its directory structure.

### 4.2 Procedure

The task involved:

1. Verifying the current directory with `pwd`
2. Listing directory contents with `ls -la`
3. Navigating to `/home` and `/var/log`
4. Examining `/etc`, `/var`, `/home`, `/root`, and `/tmp`
5. Creating the working directory `~/grc-lab-week1`
6. Returning to the working directory and confirming its path

### 4.3 Commands Executed

```bash
pwd
ls -la
cd /home
ls -la
cd /var/log
pwd
ls -la /etc
ls -la /var
ls -la /home
ls -la /root
ls -la /tmp
mkdir -p ~/grc-lab-week1
cd ~/grc-lab-week1
pwd
```

### 4.4 Directory Reference

| Directory | Purpose | GRC Relevance |
|---|---|---|
| `/etc` | Stores system and application configuration files | Useful for configuration reviews and policy-compliance checks |
| `/var` | Stores variable data, including logs and databases | Important for monitoring, evidence collection, and audit trails |
| `/home` | Stores standard user home directories | Relevant to user-access and data-location reviews |
| `/root` | Root user's home directory | Relevant to privileged-access review |
| `/tmp` | Stores temporary files | May contain short-lived artefacts requiring security review |

### 4.5 Absolute and Relative Paths

- An **absolute path** begins at the root directory `/`, for example `/home/user/documents`.
- A **relative path** begins from the current working directory, for example `../logs` or `./file.txt`.

Understanding both path types helps analysts locate evidence accurately and document repeatable procedures.

### 4.6 Outcome

The task established a working understanding of the Linux directory hierarchy and showed where configuration files, user data, privileged-user files, temporary artefacts, and security logs may be located.

---

## 5. Task 2: File Permissions and Security

### 5.1 Objective

The objective was to understand Linux file permissions and their security implications for GRC activities.

### 5.2 Procedure

The task involved:

1. Creating an `audit_evidence` directory structure
2. Reviewing permissions on sensitive system files
3. Creating policy and confidential-evidence files
4. Applying specific permissions with `chmod`
5. Restricting access to the log directory
6. Reviewing user identity and group membership information

### 5.3 Evidence Structure

```text
grc-lab-week1/
└── audit_evidence/
    ├── policies/
    │   └── policy_draft.txt
    ├── evidence/
    │   └── confidential.txt
    └── logs/
        ├── syslog_sample.txt
        └── auth_sample.txt
```

> The source lab used the working directory `~/grc-lab-week1`. The tree above represents the intended evidence organisation: policies, confidential evidence, and copied logs are separated for clearer control and review.

### 5.4 Commands Executed

```bash
mkdir -p audit_evidence/policies audit_evidence/evidence audit_evidence/logs
ls -la /etc/passwd
ls -la /etc/shadow
ls -la /etc/sudoers
touch audit_evidence/policies/policy_draft.txt
chmod 644 audit_evidence/policies/policy_draft.txt
touch audit_evidence/evidence/confidential.txt
chmod 600 audit_evidence/evidence/confidential.txt
chmod 700 audit_evidence/logs
id
groups
cat /etc/passwd
cat /etc/group
```

### 5.5 Permission Notation

Linux permissions use:

- `r` for read
- `w` for write
- `x` for execute or directory access

### 5.6 Permission Configuration

| Mode | Owner | Group | Others | Intended Use |
|---:|---|---|---|---|
| `644` | Read and write | Read | Read | Policy draft that can be viewed but changed only by the owner |
| `600` | Read and write | No access | No access | Confidential evidence restricted to its owner |
| `700` | Read, write, and access | No access | No access | Restricted evidence or log directory |

### 5.7 Security Significance

Appropriate permissions support:

- Confidentiality of sensitive information
- Integrity of audit evidence
- Prevention of unauthorised changes
- Least-privilege access
- Clear access-control evidence
- Compliance with organisational security requirements

### 5.8 Outcome

The task demonstrated how permission settings can be used to separate general policy documents from confidential evidence and restricted logs. It also reinforced the importance of checking sensitive system files and reviewing user and group information during an audit.

---

## 6. Task 3: Log Analysis and Extraction

### 6.1 Objective

The objective was to extract and analyse system logs for security and compliance monitoring.

### 6.2 Procedure

The task involved:

1. Navigating to `/var/log`
2. Listing available log files
3. Reviewing the first and last 20 lines of `syslog`
4. Counting log entries
5. Filtering for errors, failures, `sudo` commands, and authentication events
6. Copying logs into the evidence directory
7. Counting selected events and reviewing failed activity

### 6.3 Commands Executed

```bash
cd /var/log
ls -la
head -20 syslog
tail -20 syslog
wc -l syslog
grep -i "error" syslog | head -10
grep -i "failed" syslog | head -10
grep -i "sudo" syslog | head -10
grep -i "authentication" syslog | head -10
cd ~/grc-lab-week1
cp /var/log/syslog audit_evidence/logs/syslog_sample.txt
cp /var/log/auth.log audit_evidence/logs/auth_sample.txt 2>/dev/null || echo "auth.log not available"
grep "sudo" audit_evidence/logs/syslog_sample.txt | wc -l
grep -i "failed" audit_evidence/logs/syslog_sample.txt | head -5
```

### 6.4 Recorded Findings

| Finding | Recorded Result | Security Relevance |
|---|---:|---|
| `sudo` command events | 7 | Supports review of privileged activity |
| Failed authentication attempts | 4 | May indicate mistyped credentials, misuse, or attempted unauthorised access |
| System errors in first filtered results | None observed | No error appeared in the first ten filtered lines reviewed |
| SSH login activity | Two logins within one minute from `192.168.1.101` | Requires contextual review to determine whether the activity was expected |
| Invalid-user attempts | `test user` and `admin` from `203.0.113.45` and `203.0.113.47` | Demonstrates how logs reveal attempted access using invalid accounts |

These results should be interpreted only within the context of the controlled lab dataset. The log entries alone do not prove that a security incident occurred.

### 6.5 GRC Relevance of Log Analysis

Log analysis supports:

- User-activity monitoring
- Privileged-access oversight
- Detection of unauthorised access attempts
- Incident investigation
- Audit-trail creation
- Control-effectiveness testing
- Accountability and traceability
- Compliance evidence

### 6.6 Outcome

The task demonstrated how basic Linux tools can be used to identify events that may require further investigation. It also showed the importance of copying relevant logs into an organised evidence location for later review.

---

## 7. Lab Report Preparation

The final stage involved compiling the procedures, commands, screenshots, findings, security observations, compliance implications, and conclusions into a structured report.

Good technical reporting should make it possible for another reviewer to understand:

- What was tested
- Which commands were used
- What evidence was collected
- What was observed
- Why the finding matters
- What limitations apply
- What action is recommended

---

## 8. Security Observations and Risks

### 8.1 Broad File Permissions

Some files may be readable by more users than necessary. World-readable access is not automatically a vulnerability, because some system files such as `/etc/passwd` are intentionally readable. However, confidential evidence, credential data, and sensitive configuration information should be restricted according to business need.

**Risk:** Unnecessary access may expose information or allow inappropriate use.

**Recommendation:** Review file ownership and permissions regularly, classify sensitive files, and apply least privilege.

### 8.2 Restricted Log Access

Certain logs require elevated privileges.

**Risk:** Analysts without approved access may be delayed during monitoring or incident response.

**Recommendation:** Provide controlled, role-based log access or centralised logging while preserving administrative separation and auditability.

### 8.3 Audit-Trail Gaps

Some authentication events may not contain enough information for complete forensic analysis.

**Risk:** Missing context can make it difficult to reconstruct events, identify the source of activity, and establish accountability.

**Recommendation:** Configure logging to retain relevant timestamps, accounts, source addresses, outcomes, system identifiers, and event details.

### 8.4 Evidence Integrity

Copying logs into an evidence directory improves organisation but does not by itself prove that the copies are unchanged.

**Risk:** Evidence may be questioned if collection, integrity, access, and retention are not controlled.

**Recommendation:** In a production process, record collection details, calculate cryptographic hashes, restrict access, define retention, maintain chain of custody where required, and document authorised disposal.

---

## 9. Compliance and Governance Implications

### 9.1 Access Control

The use of `600` and `700` permissions demonstrates the principle of limiting access to authorised users. This supports confidentiality and evidence-protection requirements.

### 9.2 Logging and Monitoring

System and authentication logs provide evidence of user activity, privileged actions, failed access attempts, and operational events. Effective monitoring depends on sufficient coverage, protected log storage, accurate time, useful context, and regular review.

### 9.3 Evidence Retention

The `audit_evidence` structure demonstrates how compliance artefacts can be organised. A complete organisational process would additionally require ownership, classification, retention periods, backup, access controls, integrity validation, and disposal procedures.

### 9.4 Accountability

User, group, permission, authentication, and `sudo` records help connect actions to accounts. This supports responsibility assignment, investigations, and assurance activities.

### 9.5 Regulatory and Framework Alignment

File-permission management, logging, monitoring, and evidence retention can contribute to organisational alignment with information-security frameworks and applicable legal obligations. The specific controls and retention requirements must be determined by the organisation's context, risks, contracts, and jurisdiction.

---

## 10. Skills Demonstrated

### Linux Administration

- File-system navigation
- Directory inspection
- Absolute and relative path usage
- File and directory creation
- User and group review
- File-permission interpretation
- Permission modification with `chmod`

### Security and Audit

- Least-privilege implementation
- Sensitive-file permission review
- Log extraction and filtering
- Authentication-event review
- Privileged-activity review
- Audit-evidence organisation
- Security observation and risk identification

### GRC

- Translating technical output into compliance evidence
- Connecting access controls to governance requirements
- Documenting findings and limitations
- Supporting accountability through audit trails
- Recognising evidence-integrity requirements
- Producing a structured technical report

---

## 11. Key Lessons Learned

1. Linux file-system knowledge helps auditors and security analysts locate configurations, logs, user data, and temporary artefacts.
2. Permissions must reflect data sensitivity and operational need.
3. Least privilege reduces unnecessary exposure and helps protect audit evidence.
4. Logs are essential for monitoring, investigation, accountability, and compliance.
5. A filtered result provides an investigative lead, not automatically proof of malicious activity.
6. Evidence organisation must be supported by integrity, retention, and access controls.
7. Technical observations should be translated into clear business, governance, and compliance implications.

---

## 12. Recommendations

- Review sensitive-file permissions regularly.
- Use role-based access for security logs.
- Centralise important logs where appropriate.
- Protect logs against unauthorised modification and deletion.
- Maintain accurate system time for event correlation.
- Define logging and retention requirements formally.
- Record evidence-collection details.
- Use cryptographic hashes for formal evidence validation.
- Monitor privileged commands and failed authentication events.
- Investigate repeated invalid-user and unusual SSH activity using contextual evidence.
- Document exceptions and obtain appropriate approval.
- Test monitoring and audit procedures periodically.

---

## 13. Report Limitations

- The exercise was completed in a controlled lab environment.
- The report reflects a limited evidence sample.
- The original assignment recorded no errors in the first ten filtered results, which does not prove that the complete log contained no errors.
- The recorded SSH and invalid-user events require contextual investigation before they can be classified as malicious.
- Screenshots provide visual evidence but are not a substitute for protected source logs and integrity records.
- Some system logs may differ across Linux distributions and logging configurations.

---

## 14. Conclusion

The Week 1 lab successfully established foundational Linux skills for GRC work. File-system navigation provided an understanding of where important configurations, user files, temporary data, and security logs are stored. Permission management demonstrated how access settings support confidentiality, integrity, and least privilege. Log analysis showed how simple command-line tools can reveal privileged activity, authentication failures, and events that may require investigation.

The most important outcome was the connection between technical activity and governance. Commands such as `ls`, `chmod`, and `grep` are not merely administrative tools. When used within a controlled process, they help produce the evidence required for access reviews, compliance assessments, incident response, risk decisions, and audit reporting.

---

## 15. Repository Structure

```text
.
├── README.md
├── GRC101_LINUX_SECURITY_MARKDOWN_REPORT.md
└── Week_01_GRC101_SHITTU UMMULKHOYR ADEBUKOLA.pdf
```

---

## 16. References

1. Linux.com. *The Linux Filesystem Explained*. https://www.linux.com/training-tutorials/linux-filesystem-explained/
2. Linux.com. *Understanding Linux File Permissions*. https://www.linux.com/learn/understanding-linux-file-permissions
3. Linux.com. *How to Analyse Linux Logs with Basic Commands*. https://www.linux.com/learn/how-analyze-linux-logs-basic-commands

---

## 17. Academic Integrity

This report presents a completed educational lab intended to demonstrate understanding of Linux administration, permission management, log analysis, evidence organisation, and their relevance to Governance, Risk, and Compliance. Any reuse or adaptation should follow applicable academic-integrity requirements.

---

<p align="center"><strong>Completed GRC101 Linux Security and GRC Technical Lab</strong></p>
<p align="center">Prepared by Shittu Ummulkhoyr Adebukola</p>
