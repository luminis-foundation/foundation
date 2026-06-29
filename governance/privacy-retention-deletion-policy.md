# Luminis Foundation — Privacy, Retention, and Deletion Policy

> Status: Draft — pending Board review and adoption
> Last updated: 2026-06-29
> Author: Carlos Garcia, President / Research Director
> File: governance/privacy-retention-deletion-policy.md
>
> **This is a draft policy.** It is not operative until reviewed and adopted by the Board of Directors. It is
> not legal advice; before relying on the GDPR/HIPAA applicability conclusions below, confirm them with a
> qualified attorney for any jurisdiction in which the Foundation actually collects personal data.

---

## Guiding Principle

> **Collect the minimum. Keep it the shortest defensible time. Delete on request where the law allows.**

This policy complements the Foundation's data-handling rule **"Private by default. Public by proof."**
(`research/data-management-security-brainstorm.md`). That brainstorm covers *research* data; this policy
covers *personal* data about people — website visitors, volunteers, contributors, collaborators, and
individuals named in research records.

---

## 1. Scope

This policy applies to personal data the Foundation collects or holds about identifiable people, including:

- Website contact-form submissions and email correspondence
- Volunteer and contributor records (names, emails, roles, contributions)
- Collaborator and partner contact details
- Donor records (handled jointly with `governance/financial-controls-policy.md`)
- Any individual identifiable within research records, field notes, or photographs

It does **not** govern non-personal research/sensor data (see `research/data-management-plan.md`) except
where that data can identify a person or a sensitive site.

---

## 2. Categories of Personal Data and Lawful Basis

| Category | Examples | Default lawful basis | Default visibility |
|---|---|---|---|
| Contact-form data | Name, email, message | Consent (user initiated contact) | Private |
| Volunteer/contributor data | Name, email, GitHub handle, contributions | Legitimate interest / agreement | Public handle only if user-published; rest private |
| Collaborator/partner data | Name, org, contact | Legitimate interest / agreement | Private unless partner consents |
| Donor data | Name, amount, contact | Legal obligation (financial records) | Private — never public |
| Research-embedded personal data | People in photos, named field contacts | Consent | Private; redact before any release |

The Board confirms the lawful basis at adoption; bases above are drafting defaults.

---

## 3. Data Minimization

- Collect only what is needed for the stated purpose.
- The website should collect the **minimum** contact fields (e.g., name + email + message) and state why.
- Do not collect special-category data (health, ethnicity, biometrics, precise location of individuals)
  unless there is a specific, documented, consented purpose.
- Prefer public GitHub handles over personal emails for contributor coordination where practical.

---

## 4. Retention Schedule

| Data type | Retention period | Trigger for deletion |
|---|---|---|
| Contact-form submissions | [TBD — proposed: 24 months] after last contact | No active relationship |
| Volunteer/contributor records | Duration of involvement + [TBD — proposed: 3 years] | End of involvement + period |
| Collaborator/partner contacts | Duration of relationship + [TBD — proposed: 3 years] | End of relationship + period |
| Donor records | Per IRS retention — see financial policy ([TBD — proposed: 7 years]) | Statutory minimum elapsed |
| Research-embedded personal data | Per `research/data-management-plan.md` retention | Project closure / consent withdrawal |
| Email correspondence | [TBD — proposed: 24 months] for routine; longer if legally required | Routine retention elapsed |

Retention periods are drafting proposals; the Board confirms them at adoption. Where a legal obligation
(e.g., IRS donor records) requires longer retention, the legal obligation governs.

---

## 5. Deletion and Erasure Requests

Any individual may request deletion of their personal data.

**Procedure:**
1. Request is received (email to the address on the Foundation's GitHub profile, or contact form).
2. Carlos Garcia (or designated officer) verifies the requester's identity sufficiently to avoid wrongful
   disclosure or deletion.
3. The officer identifies all locations holding the person's data (email, contributor records, website
   backend, research records).
4. Data is deleted or anonymized **unless** a legal obligation requires retention (e.g., donor records for
   IRS purposes) — in which case the requester is told what is retained and why.
5. The request and the action taken are logged (date, requester, scope, outcome) in private records.
6. Target turnaround: [TBD — proposed: 30 days].

> **Public-repo caveat:** personal data accidentally committed to a public repo cannot simply be deleted —
> Git history must be rewritten. Treat any such exposure as an incident under
> `operations/incident-response-plan.md`.

---

## 6. Disclosure and Sharing

- Personal data is not sold, rented, or shared with third parties for marketing.
- It is shared only with service providers strictly necessary to operate (e.g., email/hosting) and only the
  minimum required.
- External collaborators receive only the personal data needed for approved work, under the access rules in
  `research/data-management-security-brainstorm.md` Section 7.

---

## 7. Security of Personal Data

Personal data is protected under the same controls as other Foundation data — see
`research/data-security-policy.md` and `operations/github-access-and-branch-protection-policy.md`:

- No personal data in public repositories.
- Encryption at rest for stored personal data; MFA on accounts that can access it.
- Least-privilege access; access reviewed at least annually.

---

## 8. Regulatory Applicability Memo (GDPR / HIPAA)

> **Not legal advice.** A working applicability assessment to be confirmed by counsel.

### HIPAA
**Likely not applicable.** HIPAA governs Protected Health Information held by covered entities (health plans,
clearinghouses, providers) and their business associates. The Foundation does not provide healthcare, bill
for it, or process clinical health records. HIPAA would only become relevant if the project began handling
individually identifiable health/clinical data — which is not part of the current MycoSense or research
program. **Action:** re-assess if any health/clinical data is ever introduced.

### GDPR (and similar privacy laws)
**Potentially applicable** if the Foundation collects personal data of individuals in the EU/EEA/UK — for
example, an EU collaborator, volunteer, or website contact-form submission from the EU. GDPR can apply to a
US nonprofit that offers services to, or monitors, people in the EU. Where applicable, the Foundation should
honor data-subject rights (access, rectification, erasure, portability), have a lawful basis (Section 2),
and minimize data (Section 3). **Action:** if/when the Foundation knowingly collects EU personal data,
confirm obligations with counsel and, if needed, add a website privacy notice and consent mechanism.

### US state privacy laws (e.g., CCPA/CPRA)
Generally apply to for-profit businesses meeting revenue/volume thresholds and typically exempt nonprofits,
but several states are expanding scope. **Action:** re-assess if the Foundation grows or collects data at
scale.

### Practical conclusion
At current scale (no health data; minimal, mostly US, voluntary contact data) the binding obligations are
limited, but the Foundation should adopt privacy-by-design now (minimize, retain briefly, honor deletion) so
it is ready before any EU data or larger-scale collection occurs. A public **privacy notice** on the website
is recommended regardless (see `operations/next-actions.md` "Add privacy policy to Foundation website").

---

## 9. Website Privacy Notice (Recommended Companion)

If the website collects any personal data (e.g., a contact form), publish a short privacy notice covering:
what is collected, why, how long it is kept, who to contact for deletion, and that data is not sold. This
policy is the internal source for that public notice.

---

## 10. Annual Review

This policy is reviewed by the Board at least annually (see `governance/compliance-calendar.md`) and whenever
the Foundation begins collecting a new category of personal data.

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| Counsel review of applicability memo | ⬜ Recommended before reliance |
| Board review | ⬜ Pending |
| Board adoption date | ⬜ Not yet adopted |
| Effective date | ⬜ Upon Board adoption |

*Not operative until adopted by the Board. The applicability memo is a working assessment, not legal advice.*
