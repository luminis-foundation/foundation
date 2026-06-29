# ADR 0001 — Public / Private Repository Boundary

> Status: Accepted (records an existing decision)
> Date: 2026-06-29
> Deciders: Carlos Garcia (President / Research Director), Board of Directors
> File: docs/adr/0001-public-private-repository-boundary.md

---

## Context

All repositories under the `luminis-foundation` GitHub organization are **public**. The Foundation handles a
mix of public-safe institutional records and strictly private material (legal PDFs, EIN, banking details,
credentials, unredacted personal data, signed minutes). A single accidental commit of private material to a
public repo is immediately visible, cached by GitHub and crawlers, and not removable without a full Git
history rewrite (`risk/attack-surface-analysis.md` #15).

The Foundation needs an explicit, durable decision about **what may live in public repositories and what must
not** — one that AI agents, contributors, and officers can all apply consistently. The boundary is already
stated across `README.md`, `repo-structure.md`, and `governance/financial-controls-policy.md` Section 13; this
ADR records it as a single referenceable decision.

---

## Decision

Foundation repositories are public and contain **only public-safe content**. The following are **never**
committed to any public repository:

- Private legal PDFs (Certificate of Incorporation originals, signed bylaws, IRS correspondence)
- EIN / Federal Employer Identification Number
- Banking, payment, or financial account details; Pay.gov / IRS payment receipts; bank statements
- API keys, credentials, tokens, or secrets of any kind (including `.env` files and `VITE_*` tokens in builds)
- Unredacted personal data of board members, contractors, or collaborators
- Signed board minutes containing personal signatures or home addresses beyond the registered office
- Exact sensor GPS coordinates, site maps, or land-access details

Private material is retained in **officer-controlled private storage** (encrypted drives / private records),
with at least two officers holding emergency access. Public-safe **records of** private facts are allowed
(e.g., "the Board adopted a policy on DATE", "banking established") without the underlying sensitive details.

This boundary is enforced by:
- The written "never commit" lists in `README.md` and `governance/financial-controls-policy.md` Section 13.
- GitHub secret scanning + push protection and pre-commit secret scanners
  (`operations/github-access-and-branch-protection-policy.md`).
- The data classification model in `research/data-management-plan.md` (the "Secrets" and "Operational
  records" classes are never public).

---

## Consequences

**Positive**
- Clear, testable rule for humans and AI agents; reduces exposure risk (#15).
- Supports grant-readiness and transparency without leaking sensitive records.
- Enables automated enforcement (secret scanning, pre-commit hooks).

**Negative / trade-offs**
- Some institutional records (e.g., signed minutes) are not publicly auditable; mitigated by public-safe
  indexes/adoption records (`governance/board-adoption-records/`).
- Requires discipline and tooling; a mistake is an incident
  (`operations/incident-response-plan.md` §4.1, §4.4).

**Revisit if**
- The Foundation adopts a private repo for raw governance records (`repo-structure.md` notes this option), or
- A future secure architecture changes where private records live.
