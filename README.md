# Web Security Assessments

Practical web application security testing and reports by **Haroon Shahid**.

Each record explains the target, the tests, the evidence, the result and the limits of the conclusion.

## Reports

| Target | Coverage | Outcome | Public files |
| --- | --- | --- | --- |
| **Proantic** | Email and password changes: token validation, two-account checks, token reuse, reload behaviour and current-password checks | No CSRF vulnerability confirmed in the documented cases | [Assessment](Assessments/2026-11-csrf-account-management/) · [Illustrated PDF](Assessments/2026-11-csrf-account-management/Proantic_CSRF_Assessment.pdf) · [16 full-frame screenshots](Assessments/2026-11-csrf-account-management/evidence/) |
| **Loyal Hit** | Account-edit request: incorrect, empty, missing and substituted nonce values | No CSRF bypass observed; a successful valid-token replay control was not documented | [Assessment](Assessments/2026-11-loyalhit-csrf/) · [PDF](Assessments/2026-11-loyalhit-csrf/LoyalHit_CSRF_Assessment_Public.pdf) |

## Evidence status

The Proantic assessment publishes all 16 complete screenshot frames and the illustrated PDF. Sensitive fields in the public evidence were obscured before publication; the screenshots were not cropped.

The Loyal Hit PDF and request transcription are available. Sensitive cookie, email and token values use placeholders.

## Repository structure

| Folder | Contents |
| --- | --- |
| [Assessments/](Assessments/) | Tests with no confirmed vulnerability in the documented cases. |
| [Findings/](Findings/) | Confirmed vulnerabilities cleared for public disclosure. |

A failed bypass attempt is a documented assessment result, not proof that the entire application is secure.
