# Luminis Foundation — Data Management Plan (DMP)

> Status: Draft — pending Board review and adoption
> Last updated: 2026-06-29
> Author: Carlos Garcia, President / Founder / Research Director (Data Custodian)
> File: research/data-management-plan.md
> Companions: `research/data-management-security-brainstorm.md`, `research/data-management-founder-answers.md`,
> `research/data-security-policy.md`
>
> **This is a draft Data Management Plan.** It synthesizes the founder's draft answers into the formal DMP
> structure called for in the brainstorm (Section 16). It is grant-oriented but **not** yet Board-adopted, and
> several thresholds remain funding-dependent. Not operative until adopted by the Board.

---

## Guiding Principle

> **Private by default. Public by proof.**

- **Private by default:** raw data, calibration records, exact node locations, credentials, and operational
  records stay private.
- **Public by proof:** only validated, sanitized, reviewed, approved, and documented datasets become public.

---

## 1. Purpose and Scope

This DMP governs how the Foundation creates, classifies, stores, protects, retains, and releases research
data across the MycoSense program and related activities. It covers sensor readings, calibration records,
field notes, metadata, site/location details, device logs, processed datasets, and public releases. Security
requirements are specified in the companion `research/data-security-policy.md`; personal data is governed by
`governance/privacy-retention-deletion-policy.md`.

This plan is written to satisfy common environmental/technology funder DMP requirements while reflecting the
Foundation's offline-first, local-first posture.

---

## 2. Data Classification

All data is classified before storage or sharing (from the brainstorm's classification model):

| Class | Examples | Default visibility | Storage rule |
|---|---|---|---|
| Public | Website content, public READMEs, published datasets, public reports | Public | GitHub / Zenodo / website |
| Public-safe summary | Deployment summaries, aggregate findings, non-sensitive calibration summaries | Public after review | GitHub / reports |
| Restricted research | Raw sensor readings, calibration logs, field notes, device logs, preliminary analysis | Private by default | Private encrypted research storage |
| Sensitive site data | Exact sensor locations, site maps, GPS coordinates, land access details | Private | Restricted access only |
| Operational records | Signed minutes, legal PDFs, bank records, receipts | Private | Officer-controlled records |
| Secrets | API keys, tokens, WiFi/MQTT credentials, private keys, card/bank details | Never public | Secret manager / private officer storage |

---

## 3. Data Lifecycle

Sensor data flows through a defined lifecycle (brainstorm Section 3):

1. Sensor node reading (ESP32 captures raw ADC from electrode arrays)
2. Pi gateway ingestion (MQTT → local SQLite)
3. Local raw data storage (immutable, with session + timestamp metadata)
4. Calibration / drift review
5. Quality-control review (per field data quality SOP)
6. Processed dataset creation (derived metrics)
7. Public-safe summary (sensitive details removed)
8. Research Director / Board approval
9. Zenodo or GitHub release (DOI, metadata, license, hash manifest)
10. Post-release version tracking (corrections create new DOI versions, never overwrites)

> The public MycoSense dashboard remains **simulated/mock** until live data is validated and approved
> (`mycosense/FIELD_STATUS.md`).

---

## 4. Roles and Access

| Role | Access |
|---|---|
| President / Research Director (Data Custodian) | Mission, research, and data-release approval; full archive |
| Treasurer | Financial records, receipts, grant financial records |
| Secretary | Corporate records, minutes, governance records |
| Board | Oversight; approval of major data/publication policies and releases |
| Research collaborator | Project-specific, least-privilege research data under a data access agreement |
| Public | Published/sanitized/approved materials only |

- **Data Custodian:** Carlos Garcia, President / Founder / Research Director (per
  `research/data-management-founder-answers.md` Q3).
- Access follows **least privilege**, reviewed at least annually or on role change
  (`governance/compliance-calendar.md`).
- AI agents/automation: read-only on public content; no access to raw private data
  (`operations/github-access-and-branch-protection-policy.md`).

---

## 5. Storage and Backup

Per the founder answers (offline-first, local-first):

- **Raw/private data** is stored on **encrypted local external drives, offline by default** — a primary drive
  (Data Custodian), a backup drive (second officer), and an optional offline cold archive.
- **No** raw sensor data in public GitHub, Slack, normal email, or public cloud storage.
- **Cloud** is not used for raw/private data until the Board approves a secure architecture; it may later hold
  public-safe summaries, published datasets, Zenodo releases, and (if approved) encrypted backups.
- **Backup cadence** (cycle-based, from founder answers Q6): after every session, weekly during active
  collection, monthly verification, 6-month restore test, annual review. Recovery objectives are specified in
  `operations/disaster-recovery-rto-rpo.md`.

---

## 6. Metadata

Every collection session records: timestamp (UTC), node ID, sensor channel, unit, firmware version, Pi
gateway software version, calibration status, and site/session ID. A formal machine-readable schema is to be
committed at `research/protocols/metadata-schema.json` (tracked in `operations/next-actions.md`). MycoSense
already defines a sensor-reading JSON schema (`mycosense/src/schema/v1/sensor-reading.schema.json`) that the
metadata schema should align with.

---

## 7. Data Integrity

- SHA-256 hashes for dataset releases; manifest files listing names, sizes, and hashes.
- Firmware, gateway version, and calibration state recorded with every session.
- Immutable raw-data copies where practical; corrections create derived data, never overwrite raw.
- Audit trail for transformations (what changed, by whom, when, why).

---

## 8. Retention

| Data class | Retention | Notes |
|---|---|---|
| Raw research data | Indefinite (research value) unless superseded | Immutable; archived on encrypted drives |
| Processed datasets | Indefinite; versioned | New versions, not overwrites |
| Published datasets (Zenodo) | Permanent (DOI) | Corrections via new DOI versions |
| Device/gateway logs | [TBD — proposed: retain per session, rotate live logs] | Pi log rotation needed (`FIELD_STATUS.md`) |
| Personal data within records | Per `governance/privacy-retention-deletion-policy.md` | Redact before release |

---

## 9. Public Release Criteria

A dataset becomes public only when **all** are satisfied (brainstorm Section 11):

- [ ] Data source known and documented
- [ ] Calibration status documented
- [ ] Metadata complete per schema
- [ ] Sensitive site details removed/generalized
- [ ] Data quality review complete per field data quality SOP
- [ ] No secrets or private records included
- [ ] Research Director approves
- [ ] Board approval obtained where required
- [ ] License selected and included (proposed default **CC-BY-4.0**)
- [ ] Release notes written
- [ ] SHA-256 hash manifest generated and included

A dataset-release operational checklist should be maintained at `research/dataset-release-checklist.md`
(brainstorm Section 16).

---

## 10. Site / Location Privacy

Exact node locations are **never** published (founder answers Q4). Public materials use generalized language
("Rowe, New Mexico"; "Pecos watershed region"). GPS coordinates, site maps, and access routes are excluded;
spatial data is generalized, offset, or removed before release.

---

## 11. Release Approval

No public dataset release occurs without Research Director review **and** Board approval (founder answers Q9).
Routine minor corrections to already-published datasets may be delegated to the Research Director if the Board
later adopts that delegation.

---

## 12. Funding-Dependent Items

The following cannot be finalized until hardware, reference equipment, and pilot data exist:

- Final calibration thresholds (`research/protocols/calibration-protocol-framework.md`)
- Final field data quality thresholds (`research/protocols/field-data-quality-sop-framework.md`)
- Minimum calibration evidence for release (founder answers Q10 — pending final decision)

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| Founder answers reviewed by Board | ⬜ Pending |
| Board adoption date | ⬜ Not yet adopted |
| Effective date | ⬜ Upon Board adoption |

*Not operative until adopted. Funding-dependent thresholds remain open per the founder answers.*
