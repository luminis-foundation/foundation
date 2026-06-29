# Luminis Foundation — Compliance Calendar

> Status: Draft — pending Board review and confirmation of dates
> Last updated: 2026-06-29
> Owner: Carlos Garcia (President), Adam Kimble (Treasurer)
> File: governance/compliance-calendar.md
>
> **This calendar consolidates known recurring obligations.** Exact statutory due dates depend on the
> Foundation's fiscal year and the IRS determination outcome and must be confirmed against the relevant
> agency before relying on any date here. Several rows are conditional on the pending 501(c)(3) determination.

---

## Purpose

The Foundation has recurring legal, financial, and governance obligations across multiple agencies (NM SOS,
IRS, NM-COROS) plus internal annual reviews. Missing a deadline risks loss of good standing, tax-exempt
jeopardy, and funder distrust. This calendar is the single source of truth for *when* each obligation is due,
*who* owns it, and *where* the evidence is filed.

This formalizes the "create compliance calendar" action tracked in `operations/next-actions.md` and risk #1
in `risk/attack-surface-analysis.md`.

---

## Foundation Reference Facts

| Item | Value |
|---|---|
| Entity | Luminis Foundation, NM domestic nonprofit corporation |
| NM Entity ID | 0008089293 |
| Date of incorporation | 2026-03-16 |
| 501(c)(3) application | Form 1023-EZ filed 2026-06-09 — determination pending |
| Fiscal year | [TBD — confirm calendar year vs. other; affects IRS 990 due date] |
| Registered office | 133 Frontage Rd 2116, Rowe, NM 87562 (already public) |

> EIN, Pay.gov receipts, and bank details are **not** recorded here — see
> `governance/financial-controls-policy.md` Section 13.

---

## Annual Obligations

| Obligation | Agency / Authority | Frequency | Due window | Owner | Conditional on | Evidence location |
|---|---|---|---|---|---|---|
| Annual report / corporate report | NM Secretary of State | Annual | [TBD — confirm NM nonprofit report cycle] | Guillermo Martin | — | Private records + note in `governance/milestones.md` |
| IRS Form 990-N (e-Postcard) or 990/990-EZ | IRS | Annual | 15th day of 5th month after fiscal year-end | Adam Kimble | 501(c)(3) determination | Private records |
| NM-COROS charitable registration | NM Attorney General (COROS) | Initial + annual renewal | [TBD — after determination] | Carlos Garcia | Soliciting contributions in NM; 501(c)(3) | Private records |
| Financial controls policy annual review | Board (internal) | Annual | First Board meeting of calendar year | Adam Kimble | Policy adoption | `governance/board-adoption-records/` |
| Data governance annual review | Board (internal) | Annual | [TBD — align with Q1 Board meeting] | Carlos Garcia | DMP adoption | `research/data-management-plan.md` |
| Access & least-privilege review | Carlos Garcia (internal) | Annual (or on role change) | [TBD] | Carlos Garcia | — | `operations/github-access-and-branch-protection-policy.md` |
| Disaster recovery restore-test | Carlos Garcia (internal) | Every 6 months | [TBD] | Carlos Garcia | Field data exists | `operations/disaster-recovery-rto-rpo.md` |
| Conflict-of-interest disclosure refresh | Board (internal) | Annual | First Board meeting of calendar year | Guillermo Martin | — | Private records |
| Public-claims / overclaiming audit | Carlos Garcia (internal) | Quarterly + before each grant | Before each grant submission | Carlos Garcia | — | `risk/attack-surface-analysis.md` |
| Registered agent / office confirmation | NM SOS | Annual (with report) | With NM annual report | Guillermo Martin | — | Private records |

---

## 2026 — Remaining-Year Key Dates

| Target | Item | Status |
|---|---|---|
| Ongoing | Monitor and log IRS correspondence on 1023-EZ | Open — see `operations/next-actions.md` |
| Q3 2026 | Hold Q3 Board meeting; adopt financial controls policy | Pending |
| Upon determination | File NM-COROS if soliciting contributions in NM | Conditional |
| Year-end | Confirm fiscal year and first IRS 990 due date | Pending |

---

## How to Use This Calendar

- Review at the **first Board meeting of each calendar year** and confirm the year's dates.
- When any `[TBD]` is resolved, replace it with the confirmed date and note the source agency.
- When an obligation is completed, record completion in the relevant private records and, if public-safe, in
  `governance/milestones.md`.
- Treat a date as authoritative only after it has been confirmed against the issuing agency — statutory
  cycles change and several items here are conditional on the pending IRS determination.

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| Dates confirmed against agencies | ⬜ Pending |
| Board review | ⬜ Pending |

*Conditional and `[TBD]` items must be confirmed before this calendar is relied upon for filing.*
