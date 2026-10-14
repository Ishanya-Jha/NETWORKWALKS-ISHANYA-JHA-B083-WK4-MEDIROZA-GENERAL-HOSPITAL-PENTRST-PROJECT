 <div align="center">

# Mediroza General Hospital

## Web Application Penetration Testing Assessment

### Black-Box Security Testing • Authentication Analysis • PDF Security • Information Disclosure • Remediation Engineering

<p>
<img src="https://img.shields.io/badge/Project-Networkwalks-0B5FFF?style=flat-square" alt="Networkwalks">
<img src="https://img.shields.io/badge/Batch-B083-1F6FEB?style=flat-square" alt="Batch B083">
<img src="https://img.shields.io/badge/Week-04-6A5ACD?style=flat-square" alt="Week 4">
<img src="https://img.shields.io/badge/Methodology-Black--Box-557C94?style=flat-square" alt="Black-box methodology">
<img src="https://img.shields.io/badge/Status-Completed-2D7D46?style=flat-square" alt="Completed">
</p>

**Author:** Ishanya Jha  
**Organization:** Networkwalks  
**Assessment Type:** Educational black-box web application security assessment  
**Target specified in assignment:** `https://medirozahospital.com`  
**Project:** Week 4 Penetration Testing Assignment  
**Repository Purpose:** Cybersecurity portfolio, technical documentation, evidence organization, and remediation analysis

</div>

---

## Quick Access

[📋 Assessment Overview](#-assessment-overview) · [🎯 Objectives](#-assessment-objectives) · [🔎 Methodology](#-assessment-methodology) · [🚨 Findings](#-findings-summary) · [🛠️ Remediation](#️-remediation-strategy) · [📸 Evidence](#-evidence-gallery) · [📁 Repository Structure](#-repository-structure) · [🏁 Conclusion](#-project-completion-summary)

---

## ⚠️ Responsible Use and Authorization

This repository documents an educational security assessment completed as part of the Networkwalks training program.

All security testing must remain within the scope of explicit authorization. The public portfolio version is intended to communicate methodology, findings, security impact, and remediation without exposing sensitive assessment artifacts.

**Sensitive information is intentionally excluded**, including recovered passwords, session tokens, raw database records, staff salary details, shareholder information, and confidential document contents.

The findings below reflect the supplied assignment results and should not be interpreted as an independent verification of the target's current security posture.

---

# 📌 Assessment Overview

This project examined the security of the Mediroza General Hospital web application through a black-box testing approach.

The assessment focused on how externally observable application behavior, authentication weaknesses, insufficient document protection, metadata exposure, and publicly accessible backup files could affect information confidentiality.

Rather than treating each issue as an isolated technical observation, the project examined the broader security implications of the reported weaknesses and documented appropriate remediation measures.

### Assessment at a glance

| Attribute | Details |
|---|---|
| Training organization | Networkwalks |
| Batch | B083 |
| Assignment | Week 4 |
| Author | Ishanya Jha |
| Assessment approach | Black-box security testing |
| Primary focus | Web application security |
| Additional focus | PDF protection and information disclosure |
| Deliverable | Technical findings and remediation documentation |
| Project status | Completed |

## Key Assessment Areas

- External reconnaissance and application resource discovery
- Authentication behavior and username enumeration
- SQL injection and authentication-bypass risks
- PDF document protection and password strength
- Document metadata analysis
- Directory listing and exposed backup files
- Confidential information exposure
- Risk classification and remediation planning

---

# 🎯 Assessment Objectives

The assignment was organized into four principal milestones.

## M1: Reconnaissance and Authentication Analysis

**Objective:** Examine the application's externally visible structure and evaluate authentication-related weaknesses.

Activities included:

- Reviewing publicly accessible resources and application paths.
- Examining login behavior and error responses.
- Investigating username enumeration risks.
- Evaluating reported SQL injection behavior.
- Documenting the potential consequences of authentication bypass.

## M2: PDF Security and Password Analysis

**Objective:** Evaluate the security implications of password-protected PDF reports.

Activities included:

- Reviewing the PDF documents referenced in the assignment.
- Examining document protection and password-strength weaknesses.
- Studying the assigned password-analysis workflow.
- Evaluating the confidentiality risks associated with weak document passwords.

## M3: Metadata and Information Disclosure

**Objective:** Investigate whether document metadata, directory configuration, and exposed backup files could reveal sensitive information.

Activities included:

- Examining document metadata.
- Reviewing the reported directory-listing exposure.
- Assessing the implications of an accessible database backup.
- Evaluating potential staff, shareholder, and organizational data exposure.

## M4: Security Reporting and Remediation

**Objective:** Consolidate the assessment results into structured technical documentation.

Activities included:

- Documenting the reported findings.
- Classifying findings by severity.
- Explaining potential security impact.
- Identifying underlying control weaknesses.
- Recommending remediation and future verification measures.

---

# 🧭 Assessment Methodology

The assessment followed a structured workflow from reconnaissance through findings documentation.

```text
External Reconnaissance
         |
         v
Application Surface Discovery
         |
         v
Authentication Behavior Analysis
         |
         v
SQL Injection Risk Assessment
         |
         v
PDF Security and Password Analysis
         |
         v
Metadata and Backup Exposure Review
         |
         v
Finding Classification
         |
         v
Remediation Recommendations
         |
         v
Technical Documentation
```

The methodology emphasizes the relationship between a reported weakness, its potential impact, and the controls required to mitigate the risk.

---

# 🔎 Reconnaissance and Attack-Surface Analysis

Initial reconnaissance examined publicly accessible application resources and paths identified in the assignment.

The supplied solution describes `robots.txt` entries referencing patient, staff, and legacy application directories. These entries provided useful discovery clues but did not constitute access controls.

### Areas examined

| Area | Assessment purpose |
|---|---|
| Public resources | Identify application structure |
| `robots.txt` | Review publicly disclosed path references |
| Login endpoints | Examine authentication behavior |
| HTTP responses | Understand application error handling |
| PDF resources | Evaluate document access and protection |
| Directory listings | Identify potential information disclosure |
| Backup files | Assess the risks of public backup exposure |

### Security observation

Publicly disclosed paths can reduce the effort required to discover sensitive application surfaces. However, hiding a path is not a substitute for authentication, authorization, or appropriate server configuration.

---

# 🔐 Authentication and SQL Injection Assessment

The supplied assignment results report authentication weaknesses, including username enumeration and a SQL injection-related authentication bypass.

## Reported observations

| Observation | Potential security implication |
|---|---|
| Different login responses | May reveal whether usernames exist |
| Database-related errors | May disclose backend implementation details |
| SQL injection-related behavior | May allow unintended manipulation of authentication queries |
| Authentication bypass | May expose protected application functionality |

## Root-cause considerations

The reported behavior is consistent with weaknesses that can arise when applications:

- Construct database queries using untrusted input.
- Fail to use parameterized database operations.
- Return detailed internal errors to users.
- Rely on incomplete authentication or authorization checks.

## Recommended controls

- Use parameterized queries and prepared statements.
- Return consistent authentication failure messages.
- Validate input on the server.
- Avoid exposing database errors in production responses.
- Apply rate limiting and appropriate authentication monitoring.
- Verify authorization for every protected application resource.

---

# 📄 PDF Document Security

The assignment included analysis of three PDF reports and the security implications of weak document passwords.

## Assessment focus

- Document protection and encryption characteristics
- Password-strength risks
- Password-analysis workflow
- Confidentiality implications of weak passwords
- Secure handling of document artifacts

### Key lesson

Encryption does not guarantee effective confidentiality when the password protecting a document is weak or predictable.

## Recommended controls

- Apply strong, unique document passwords where appropriate.
- Use suitable modern encryption settings.
- Restrict document access through server-side authorization.
- Avoid publicly exposing confidential reports.
- Review access permissions and maintain appropriate audit logs.
- Keep sensitive documents in controlled storage.

Recovered passwords and confidential report contents are not included in this public README.

---

# 🧾 Metadata and Information Disclosure

The supplied assignment results describe document metadata exposure, directory listing, and an accessible database backup containing sensitive organizational information.

## Reported observations

| Area | Security implication |
|---|---|
| Document metadata | May reveal internal identities or operational details |
| Directory listing | May disclose filenames and application resources |
| Public backup file | May expose confidential database contents |
| Sensitive organizational records | May create privacy, confidentiality, and business risks |

## Recommended controls

- Remove unnecessary metadata before document publication.
- Disable directory listing where it is not required.
- Store backups outside the public web root.
- Apply restrictive file permissions.
- Encrypt sensitive backups and protect their storage locations.
- Establish appropriate backup-retention and secure-deletion policies.
- Review server logs for possible unauthorized access.

---

# 🚨 Findings Summary

The following table summarizes the findings reported in the supplied assignment solution. Severity labels are reproduced from that assignment and have not been independently recalculated.

| ID | Finding | Reported severity |
|---|---|---|
| F-01 | Username enumeration | Medium |
| F-02 | SQL injection and authentication bypass | Critical |
| F-03 | Access to PDF reports following authentication bypass | High |
| F-04 | Weak PDF passwords | High |
| F-05 | Sensitive document metadata exposure | Medium |
| F-06 | Exposed backup directory listing | Critical |
| F-07 | Confidential information reportedly exposed through the backup | Critical |

### Risk interpretation

The findings illustrate how multiple weaknesses can compound:

1. Authentication weaknesses may undermine access restrictions.
2. Weak document passwords may reduce the confidentiality of obtained files.
3. Metadata may disclose internal context.
4. Public backup exposure may reveal sensitive organizational information.

The actual impact of each issue depends on the affected environment, the information involved, and the validity of the reported evidence.

---

# 🛠️ Remediation Strategy

The following recommendations address the reported security weaknesses.

| Priority | Recommended remediation | Related findings |
|---|---|---|
| Critical | Correct unsafe SQL query construction and verify authentication controls | F-02 |
| Critical | Remove exposed backups from public access and restrict backup storage | F-06, F-07 |
| High | Enforce authorization checks for confidential document access | F-03 |
| High | Strengthen PDF encryption and password policies | F-04 |
| Medium | Standardize login errors and monitor authentication attempts | F-01 |
| Medium | Remove unnecessary metadata from published documents | F-05 |
| High | Review potentially exposed information and access logs | F-03, F-06, F-07 |

These are proposed remediation measures. The completion of the educational assignment does not, by itself, establish that changes were implemented on the target system.

## Recommended security architecture

```text
                 Incoming Request
                        |
                        v
              Server-Side Validation
                        |
                        v
             Authentication Controls
                        |
                        v
            Authorization Verification
                        |
                        v
             Parameterized SQL Queries
                        |
                        v
               Controlled Data Access
                        |
                        v
              Secure Document Storage
                        |
                        v
             Logging and Monitoring
```

A layered approach reduces reliance on any single security control and makes weaknesses less likely to combine into a broader compromise.

---

# 📸 Evidence Gallery

The following paths are suggested locations for sanitized screenshots. Add the corresponding image files to your repository before expecting them to render on GitHub.

## 1. Reconnaissance

![Reconnaissance evidence](screenshots/01-reconnaissance.png)

*Suggested evidence: publicly observable application resources and discovery results.*

## 2. Authentication Analysis

![Authentication assessment evidence](screenshots/02-authentication.png)

*Suggested evidence: sanitized authentication behavior or error-response analysis.*

## 3. PDF Security

![PDF security analysis evidence](screenshots/03-pdf-security.png)

*Suggested evidence: document security analysis with passwords and confidential content excluded.*

## 4. Metadata Analysis

![Metadata analysis evidence](screenshots/04-metadata-analysis.png)

*Suggested evidence: redacted document metadata.*

## 5. Information Disclosure

![Information disclosure evidence](screenshots/05-information-disclosure.png)

*Suggested evidence: sanitized directory-configuration or exposure analysis.*

## 6. Final Technical Report

![Final report evidence](screenshots/06-final-report.png)

*Suggested evidence: a screenshot of the completed report's findings or remediation summary.*

**Evidence handling:** Do not publish recovered passwords, session cookies, raw database records, personal identifiers, staff salary details, shareholder information, or confidential medical records.

---

# 🧰 Tools and Technologies

The tools below are associated with the supplied assignment workflow. Retain only those that you personally used and can explain during a technical review.

| Tool or technology | Purpose |
|---|---|
| Kali Linux | Security assessment environment |
| Web browser and developer tools | Application inspection |
| cURL | HTTP request and response analysis, if used |
| ExifTool | Document metadata analysis |
| John the Ripper | Password-analysis workflow, if used |
| qpdf | PDF inspection and validation, if used |
| Networkwalks Hash Calculator | Hash-related analysis in the assigned workflow |
| Networkwalks Password Cracker | Password-analysis exercise in the assigned workflow |
| Markdown | Technical documentation |
| Git and GitHub | Version control and project presentation |

---

# 📁 Repository Structure

```text
NETWORKWALKS-ISHANYA-JHA-B083-WK4-MEDIROZA-GENERAL-HOSPITAL-PENTRST-PROJECT/
│
├── README.md
│
├── screenshots/
│   ├── 01-reconnaissance.png
│   ├── 02-authentication.png
│   ├── 03-pdf-security.png
│   ├── 04-metadata-analysis.png
│   ├── 05-information-disclosure.png
│   └── 06-final-report.png
│
├── report/
│   └── penetration-testing-report.pdf
│
└── notes/
    └── remediation-summary.md
```

This is a suggested structure. Keep only files that actually exist in your repository and ensure that all publicly available evidence is appropriately sanitized.

---

# 📚 Key Learning Outcomes

This project strengthened my understanding of:

- Black-box web application security assessment
- Reconnaissance and application resource discovery
- Authentication weaknesses and username enumeration
- SQL injection risks and secure database queries
- PDF password security and document confidentiality
- Metadata analysis and information disclosure
- Directory listing and backup-file exposure
- Vulnerability severity classification
- Technical reporting and remediation planning
- Responsible evidence handling

---

# 🏁 Project Completion Summary

The Week 4 Mediroza General Hospital web application penetration testing assignment was completed as part of the Networkwalks B083 cybersecurity training program.

The assessment covered reconnaissance, authentication security, SQL injection risks, PDF document protection, metadata analysis, and information disclosure. The reported findings were organized by severity, their potential security implications were documented, and remediation recommendations were prepared.

### Project Deliverables

- Completed educational security assessment
- Documented findings and severity classifications
- Analysis of document security and information disclosure risks
- Technical remediation recommendations
- Supporting project documentation and evidence structure

### Conclusion

This project provided practical experience in black-box security testing, vulnerability analysis, risk evaluation, and technical reporting. It reinforced the importance of secure authentication, server-side authorization, appropriate document protection, metadata sanitization, and secure backup management.

**Project Status:** Completed  
**Organization:** Networkwalks  
**Batch:** B083  
**Assignment:** Week 4  
**Author:** Ishanya Jha

---

<div align="center">

### Mediroza General Hospital

**Web Application Security Assessment**

*Networkwalks • Batch B083 • Week 4*

</div>
