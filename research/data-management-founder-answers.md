# Data Management — Founder Draft Answers

> **Status:** Founder draft — pending Board review and formal adoption
> **Date:** 2026-06-23
> **Author:** Carlos Garcia, President / Founder / Research Director
> **For:** Board of Directors review
> **File:** `research/data-management-founder-answers.md`
> **Companion:** `research/data-management-security-brainstorm.md`

This document captures Carlos Garcia's draft answers to the 10 open data governance questions from the Data Management and Data Security Brainstorm. These are founder-level decisions, not yet Board-adopted policy. The Board should review, discuss, and formally adopt or modify these positions before final policy documents are drafted.

---

## Guiding Principle

> **Private by default. Public by proof.**

- **Private by default:** Raw data, calibration records, exact node locations, credentials, and operational records stay private.
- **Public by proof:** Only validated, sanitized, reviewed, approved, and documented datasets become public.

---

## Question 1 — Initial Private Raw Data Storage

**Decision:** Private raw sensor data should initially be stored on encrypted local external hard drives, offline by default.

**Recommended structure:**

- Primary encrypted external drive held by Research Director / Data Custodian
- Backup encrypted external drive held by a second authorized officer
- Optional cold archive stored offline in a secure physical location

**Exclusions:** Raw sensor data should not be stored in public GitHub, Slack, normal email, or public cloud storage.

---

## Question 2 — Access to Private Research Data

**Decision:** Private research data may be accessed by:

- Carlos Garcia, President / Founder / Research Director
- Authorized officers as needed for governance, continuity, and oversight
- Vetted contributors interested in contributing research data
- Potential Board-approved collaborators

Access should be least-privilege and project-specific.

External collaborators should only receive data needed for approved work and should not receive exact node locations or unrestricted raw archives unless explicitly approved.

---

## Question 3 — Official Data Custodian

**Decision:** The Research Director should serve as the official Data Custodian.

> Carlos Garcia, President / Founder / Research Director, serves as initial Data Custodian for Luminis Foundation research data.

---

## Question 4 — Exact Node Locations

**Decision:** Exact node locations should never be published publicly.

**Reasons:**

- Hardware protection
- Anti-theft protection
- Site privacy
- Research integrity
- Ecological/site security

**Public materials may use generalized language such as:**

- Rowe, New Mexico
- Pecos watershed region
- Controlled on-site prototype deployment site

**Excluded from publication:** GPS coordinates, site maps, access routes, and identifiable node-placement details.

---

## Question 5 — Cloud Storage Acceptance

**Decision:** Raw/private research data should remain offline-first and local-first at the current stage.

Cloud infrastructure is not accepted for raw/private sensor data until the Board approves a secure architecture.

**Cloud may be acceptable later for:**

- Public-safe summaries
- Published datasets
- Zenodo releases
- Encrypted backups if approved
- Public documentation
- Open-source code

**Future cloud approval must address:**

- Encryption
- Access control
- MFA
- Backup/export ability
- Audit logs
- Vendor lock-in
- Data sovereignty
- Whether the storage aligns with the Foundation's offline-first mission

---

## Question 6 — Backup Interval / Cycle-Based Checks

**Decision:** Use cycle-based backup and integrity checks.

**Draft cycle model:**

**After every field/session collection:**
- Copy raw data to primary archive
- Create SHA-256 hash manifest
- Record session metadata

**Weekly during active data collection:**
- Verify working backup exists
- Confirm no obvious corruption
- Review folder organization

**Monthly:**
- Full archive verification
- Compare primary and backup drive manifests
- Review access log / data log

**Every 6 months:**
- Restore test from backup
- Storage-health audit
- Decide whether to migrate aging drives

**Annually:**
- Archive review
- Retention decision
- Public-release candidate review
- Board-level data governance review

---

## Question 7 — Dataset License

**Decision:** Default proposed public dataset license: **CC-BY-4.0**

Keep as a Board decision before final adoption.

If the Board wants maximum reuse, CC-BY-4.0 is a good default because it allows reuse while preserving attribution.

---

## Question 8 — First Public Data Release Type

**Decision:** Summaries first, processed data second, raw data last if ever appropriate.

**Public release should happen in stages:**

1. Academic-quality summaries
2. Public-safe aggregate reports
3. Processed / quality-reviewed datasets
4. Raw or near-raw data only if sanitized, validated, stripped of sensitive details, and Board-approved

Do not publish raw data first.

---

## Question 9 — Dataset Release Approval

**Decision:** No public dataset release may occur without Research Director review and Board approval.

The Board should vote to approve public dataset releases.

Routine minor corrections to already-published datasets may be handled by the Research Director if the Board later adopts that delegation.

---

## Question 10 — Minimum Calibration Evidence

**Status:** Pending final Carlos/Board decision.

Minimum calibration evidence is not finalized. No public dataset release should occur until the calibration method, hardware identity, firmware version, reference method, drift review, and Research Director signoff are documented.

**Proposed minimum evidence checklist:**

- [ ] Device ID
- [ ] Sensor/electrode configuration
- [ ] Firmware version
- [ ] Pi gateway software version
- [ ] Calibration date/time
- [ ] Calibration operator
- [ ] Reference method or reference equipment used
- [ ] Pre/post calibration readings
- [ ] Drift notes
- [ ] Pass/fail result
- [ ] Research Director review
- [ ] Board approval if dataset release is planned

---

## Future Direction — Local Research Server

The Foundation intends to eventually move from encrypted external drives to a local, low-power, eco-conscious research server once funding and infrastructure allow.

> Future infrastructure may include a local eco-conscious research server for encrypted storage, local model training, dataset preparation, and offline AI research workflows. This server should remain LAN-only unless the Board approves a secure remote-access architecture.

---

## Future Direction — Offline Model Training

Sensor data may eventually be used to train Foundation-controlled offline models after validation, sanitization, and Board-approved research procedures are in place.

**Safeguards:**

- No model training on unreviewed raw data for public claims
- No public model release using sensitive site data
- Model training must preserve site privacy and data integrity

---

## Remaining Open Decisions

| Item | Status |
|---|---|
| Questions 1–9 | Founder draft answers provided; pending Board review |
| Question 10 (calibration evidence) | Pending final Carlos/Board decision |
| Final Data Management Plan | Pending Board review of these answers |
| Final Data Security Policy | Pending Board review of these answers |
| Cloud storage vendor selection | Deferred until Board approves architecture |
| Local research server timeline | Deferred until funding available |
| Offline model training procedures | Future; pending validated data and Board-approved research plan |
