# Web Security Assessments

Practical web application security testing and reports by **Haroon Shahid**.

Each entry records what I tested, the evidence collected, the result and the limits of the assessment. Confirmed vulnerabilities and tests with no confirmed finding are kept in separate folders.

## Reports

| Assessment | Focus | Outcome | Report |
| --- | --- | --- | --- |
| [Account management CSRF assessment](Assessments/2026-11-csrf-account-management/) | Token validation, cross-account rejection, token lifecycle and password verification | No CSRF vulnerability identified in the tested scenarios | [PDF](Assessments/2026-11-csrf-account-management/CSRF_Account_Management_Assessment.pdf) |

## Repository structure

| Folder | Contents |
| --- | --- |
| [`Assessments/`](Assessments/) | Completed tests where no vulnerability was confirmed in the documented scenarios. |
| [`Findings/`](Findings/) | Confirmed vulnerability reports cleared for public disclosure. |

An assessment with no confirmed finding is a record of the tested behavior, not a claim that an application is completely secure. Future entries will use the same separation between observations, conclusions and untested areas.

## Publication

Published material excludes credentials, session identifiers and personal account information. This first assessment anonymizes the target and endpoint. Vulnerability reports belong here only after the applicable disclosure conditions have been met.
