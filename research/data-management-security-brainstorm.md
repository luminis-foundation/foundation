# Data Management and Data Security Brainstorm

> **Status:** Planning draft — not a final Board-adopted policy
> **Last updated:** 2026-06-23
> **Author:** Carlos Garcia, President / Research Director
> **For:** Carlos Garcia review and Board of Directors approval
> **File:** `research/data-management-security-brainstorm.md`

**This document is a planning draft.** It is not yet a final Board-adopted policy. It is intended to support grant readiness, research integrity, privacy, security, and future public dataset release. Luminis Foundation should default to local-first, privacy-preserving, evidence-based data handling. Public release should happen only after validation, review, sanitization, and approval.

---

## Section 1 — Purpose

The purpose of this document is to design the Foundation's data trust layer — the policies, classifications, workflows, and safeguards that govern how data is created, stored, protected, shared, and released across the Foundation's research and operational activities.

This brainstorm covers:

- MycoSense sensor data
- Calibration records
- Field notes
- Metadata
- Site/location details
- Device logs
- Public datasets
- Private operational records
- Future Zenodo releases

The goal is to produce a design that the Board can review, refine, and adopt as the Foundation's formal Data Management Plan and Data Security Policy.

---

## Section 2 — Data Classification Model

All Foundation data should be classified according to the following model. Classification determines default visibility, storage rules, and release requirements.

| Class | Examples | Default Visibility | Storage Rule |
|---|---|---|---|
| Public | Website content, public README files, published datasets, public reports | Public | GitHub / Zenodo / website |
| Public-safe summary | Deployment summaries, non-sensitive calibration summaries, aggregate findings | Public after review | GitHub / reports |
| Restricted research | Raw sensor readings, calibration logs, field notes, device logs, preliminary analysis | Private by default | Private research storage |
| Sensitive site data | Exact sensor locations, site maps, GPS coordinates, land access details | Private | Restricted access only |
| Operational records | Signed minutes, legal PDFs, bank records, Pay.gov receipts, internal receipts | Private | Officer-controlled records |
| Secrets | API keys, tokens, WiFi credentials, MQTT credentials, private keys, card/bank details | Never public | Secret manager / private officer storage |

Every piece of data created or received by the Foundation should be classifiable under this model before it is stored or shared.

---

## Section 3 — MycoSense Data Lifecycle

Data flows through a defined lifecycle from sensor node to potential public release:

1. **Sensor node reading** — ESP32 node captures raw ADC readings from electrode arrays
2. **Raspberry Pi gateway ingestion** — Pi gateway receives readings via MQTT and stores in local SQLite
3. **Local raw data storage** — Raw readings are stored immutably on the Pi with session and timestamp metadata
4. **Calibration / drift review** — Raw data is reviewed against calibration records; drift is flagged
5. **Quality control review** — Data is checked for artifacts, gaps, sensor failures, and anomalies per the field data quality SOP
6. **Processed dataset creation** — Quality-reviewed data is transformed into processed datasets with derived metrics
7. **Public-safe summary** — Aggregate statistics, summaries, and visualizations are prepared with sensitive details removed
8. **Carlos / Board / research approval** — Research Director and/or Board reviews the dataset package for release readiness
9. **Zenodo or GitHub release** — Approved dataset is published with DOI, metadata, license, and hash manifest
10. **Post-release version tracking** — Released datasets are versioned; corrections produce new DOI versions, not overwrites

> **Important:** The public MycoSense dashboard remains simulated/mock unless live data has been validated and approved for release.

---

## Section 4 — Raw Data Rules

- Raw data is private by default.
- Raw data should not be committed to public GitHub.
- Raw data should include:
  - Timestamp (UTC)
  - Node ID
  - Sensor channel
  - Unit
  - Firmware version
  - Pi gateway software version
  - Calibration status
  - Site/session ID
- Raw data should be immutable where practical.
- Corrections should create derived/processed data, not overwrite raw data.
- Public release requires validation and review per the release criteria in Section 11.
- Raw data files should never be shared via email, Slack, or any unencrypted channel without explicit authorization.

---

## Section 5 — Calibration Data Rules

- Calibration records are private operational research records.
- Raw calibration records should not be committed to public GitHub.
- Public-safe summaries (e.g., "sensors calibrated within ±X% on date Y") may be published after review.
- Calibration records should include:
  - Date/time
  - Device ID
  - Firmware version
  - Calibration method
  - Reference equipment used
  - Operator
  - Pre/post readings
  - Drift notes
  - Pass/fail result
  - Reviewer
- Final calibration thresholds are funding-dependent and cannot be finalized until hardware, reference equipment, and pilot data are available.
- See also: `research/protocols/calibration-protocol-framework.md`

---

## Section 6 — Site / Location Privacy

- Exact node locations should be restricted.
- Public materials may use generalized location language such as "Rowe, New Mexico" or "Pecos watershed region."
- GPS coordinates should not be public by default.
- Site photos should be reviewed before publication for identifying features, access routes, or sensitive ecological details.
- Land access agreements, property details, and sensitive ecological locations should remain private unless explicitly approved for release.
- If a dataset includes spatial data, coordinates should be generalized, offset, or removed before public release.

---

## Section 7 — Access Roles

Draft access roles for Foundation data:

| Role | Access |
|---|---|
| President / Research Director | Mission approval, research approval, data release approval |
| Treasurer | Financial records, receipts, grant financial records |
| Secretary | Corporate records, minutes, governance records |
| Board | Oversight, approval of major data/publication policies |
| Research collaborator | Limited project-specific research data access |
| Public | Only published/sanitized/approved materials |

Additional access principles:

- Access should follow least privilege — each role accesses only what is needed for their function.
- Access should be reviewed periodically (at minimum annually or when roles change).
- External collaborators should receive only the data needed for approved work, governed by a data access agreement.
- AI agents and automated tools should have read-only access to public repository content only; no access to raw private data or private records.

---

## Section 8 — Storage and Backup Model

A practical staged model that grows with the Foundation's resources and needs.

### Current / Low-Cost Stage

- Local encrypted drive or computer folder for raw data and private records
- Officer-controlled private cloud folder if available (e.g., encrypted cloud storage)
- Physical receipt/legal record storage (paper copies retained by officers)
- Scanned PDFs for private records
- GitHub only for public-safe documents and code
- Manual backup after each field session with SHA-256 verification

### Better Future Stage

- Encrypted backup drive (LUKS, BitLocker, or FileVault)
- Private cloud storage with MFA (e.g., Backblaze B2, encrypted Dropbox Business, or similar)
- Folder-level access control
- Periodic backup checks (monthly verification)
- Checksum/hash manifest for important datasets

### Ideal Future Stage

- Dedicated research data repository (institutional or commercial)
- Automated hash manifests on ingest
- Versioned dataset releases with DOI linkage
- Access logs for all restricted data
- Encrypted off-site backup at a geographically separate location
- Formal data custodian role with defined responsibilities

---

## Section 9 — Data Integrity

All released datasets and important research artifacts should be verifiable:

- SHA-256 hashes for dataset releases
- Manifest files for public datasets listing file names, sizes, and hashes
- Firmware version recorded with every data collection session
- Gateway software version recorded with every data collection session
- Calibration state recorded with every data collection session
- Immutable raw-data copies where practical
- Audit trail for transformations (what was changed, by whom, when, and why)

### Proposed Public Release File Structure

```text
dataset/
  README.md
  metadata.json
  manifest.sha256
  raw-summary.csv
  processed-data.csv
  calibration-summary.md
  data-dictionary.md
  license.md
```

Each file serves a defined purpose:

- `README.md` — Dataset description, collection context, and usage notes
- `metadata.json` — Machine-readable metadata (authors, dates, methods, equipment)
- `manifest.sha256` — SHA-256 hashes for every file in the release
- `raw-summary.csv` — Aggregated/summarized raw data (not full raw dump)
- `processed-data.csv` — Quality-reviewed processed dataset
- `calibration-summary.md` — Public-safe calibration summary
- `data-dictionary.md` — Column definitions, units, and codes
- `license.md` — Dataset license (e.g., CC-BY-4.0)

---

## Section 10 — Security Rules

- No secrets in GitHub (API keys, tokens, credentials, private keys).
- No `.env` files in public repos.
- No API tokens in Vercel public builds.
- No routing numbers, account numbers, or card/bank details in any repo.
- No unredacted legal/payment PDFs in public repos.
- Pi gateway stays LAN-only unless a future secure architecture is approved by the Research Director.
- MQTT credentials are private and should never appear in public code or documentation.
- Credentials rotate immediately if exposed.
- MFA recommended for GitHub, email, banking, and cloud storage accounts.
- Private records should have at least two authorized officers with emergency access.
- GitHub secret scanning should be enabled on all Foundation repositories.
- Pre-commit hooks (e.g., `git-secrets`) should be installed on development machines.
- Vercel environment variables should be audited to confirm no secrets are embedded in public builds.

---

## Section 11 — Public Release Criteria

A dataset may become public only when all of the following conditions are met:

- [ ] Data source is known and documented
- [ ] Calibration status is documented
- [ ] Metadata is complete (per the Foundation's metadata schema)
- [ ] Sensitive site details are removed or generalized
- [ ] Data quality review is complete per the field data quality SOP
- [ ] No secrets or private records are included
- [ ] Carlos Garcia / Research Director approves
- [ ] Board approval is obtained if required by policy
- [ ] License is selected and included
- [ ] Zenodo/GitHub release notes are written
- [ ] SHA-256 hash manifest is generated and included

No dataset should be released publicly without satisfying every item on this checklist.

---

## Section 12 — Zenodo Release Process

Draft process for publishing a dataset to Zenodo:

1. Prepare public-safe dataset package (per the file structure in Section 9)
2. Review for secrets, private information, and sensitive site details
3. Review metadata and authorship for accuracy
4. Select license (proposed default: CC-BY-4.0)
5. Generate SHA-256 hash manifest
6. Upload to Zenodo
7. Save DOI and record in `governance/milestones.md` and `research/publications/`
8. Update Foundation repo and website with public release link
9. Preserve private source records separately (raw data, calibration logs, field notes)

> **Zenodo author note:** Current known Zenodo author record is Carlos Garcia, President / Founder / Research Director. No VanKaujk correction is needed unless Zenodo metadata contains that discrepancy.

---

## Section 13 — Incident Response

### Defined Incidents

The following incidents require immediate response:

#### 13.1 — Secret committed to GitHub

- **Immediate containment:** Remove from Git history (BFG Repo Cleaner or `git filter-repo`); force-push
- **Who is notified:** Carlos Garcia (Research Director); affected service owners
- **What gets rotated:** The exposed credential, token, or key — immediately
- **What gets documented:** Incident date, credential type, exposure duration, remediation steps
- **Public correction:** If the secret was in a public repo, assume it was compromised; rotate and monitor

#### 13.2 — Raw private data accidentally published

- **Immediate containment:** Remove file from public repo; scrub from Git history
- **Who is notified:** Carlos Garcia; Board if significant
- **What gets rotated:** N/A (data cannot be "rotated")
- **What gets documented:** Data type, volume, exposure duration, affected subjects/sites
- **Public correction:** If the data contained site locations or personal information, assess notification obligations

#### 13.3 — GPS / site location accidentally published

- **Immediate containment:** Remove from public repo and Git history
- **Who is notified:** Carlos Garcia; landowner if applicable
- **What gets rotated:** N/A
- **What gets documented:** Location precision exposed, duration, context
- **Public correction:** Assess whether the location exposure creates ecological or security risk

#### 13.4 — Bank / legal / payment record committed

- **Immediate containment:** Remove from Git history immediately; force-push
- **Who is notified:** Carlos Garcia; Adam Kimble (Treasurer); affected financial institution
- **What gets rotated:** Account credentials if banking details were exposed
- **What gets documented:** Record type, exposure duration, whether account details were included
- **Public correction:** Contact bank if routing/account numbers were exposed; monitor for fraud

#### 13.5 — Pi gateway exposed to internet

- **Immediate containment:** Disconnect Pi from internet; verify LAN-only configuration
- **Who is notified:** Carlos Garcia
- **What gets rotated:** All Pi credentials, MQTT credentials, bearer tokens
- **What gets documented:** Duration of exposure, services accessible, access logs if available
- **Public correction:** None unless data was exfiltrated

#### 13.6 — Token leaked in public build

- **Immediate containment:** Redeploy without token; rotate token immediately
- **Who is notified:** Carlos Garcia; platform owner (e.g., Vercel)
- **What gets rotated:** The leaked token and any related credentials
- **What gets documented:** Token type, build platform, exposure duration
- **Public correction:** None unless the token granted access to private data

#### 13.7 — False public dataset claim

- **Immediate containment:** Retract or correct the claim in all public locations
- **Who is notified:** Carlos Garcia; Board
- **What gets rotated:** N/A
- **What gets documented:** The incorrect claim, where it appeared, correction issued
- **Public correction:** Issue a correction notice; update Zenodo/GitHub release notes if applicable

#### 13.8 — Corrupted dataset released

- **Immediate containment:** Mark the release as withdrawn or deprecated on Zenodo (do not delete — add a new version with correction note)
- **Who is notified:** Carlos Garcia; anyone who cited or downloaded the dataset
- **What gets rotated:** N/A
- **What gets documented:** Nature of corruption, affected files, root cause
- **Public correction:** Publish a corrected version with a new DOI version; link to the original with explanation

---

## Section 14 — Open Questions for Carlos / Board

The following questions must be answered before a final Data Management Plan can be drafted:

1. **Where will private raw sensor data be stored initially?** (Local encrypted drive? Officer's computer? Private cloud folder?)
2. **Who besides Carlos can access private research data?** (Any officer? Only Research Director? Named individuals?)
3. **Who is the official data custodian?** (Is this the Research Director by default, or should a separate role be created?)
4. **Should exact node locations ever be published?** (If so, under what conditions and what precision?)
5. **What cloud storage, if any, is acceptable?** (Backblaze B2? Encrypted Dropbox? AWS S3? None until funded?)
6. **What backup interval is realistic?** (After every session? Weekly? Monthly?)
7. **What license should public datasets use?** (CC-BY-4.0? CC0? ODbL?)
8. **What data should be published first: summaries, processed data, or raw data?**
9. **Should the Board approve every public dataset release?** (Or can the Research Director approve routine releases with Board oversight?)
10. **What minimum calibration evidence is required before public release?** (Pass/fail? Reference equipment traceable to NIST? Peer review of calibration method?)

These answers will directly shape the final `research/data-management-plan.md` and `research/data-security-policy.md`.

---

## Section 15 — Recommended Final Policy Structure

When this brainstorm is reviewed and the open questions are answered, the following final documents should be drafted and adopted:

- `research/data-management-plan.md` — The Foundation's formal Data Management Plan, covering data lifecycle, classification, storage, backup, retention, and release
- `research/data-security-policy.md` — Security requirements for all Foundation data: encryption, access control, credential management, network security
- `research/dataset-release-checklist.md` — Operational checklist for every public dataset release (based on Section 11)
- `research/metadata-schema.md` — Formal metadata schema definition for all collected data
- `research/incident-response.md` — Formal incident response plan (based on Section 13)
- `research/publication-policy.md` — Policy governing authorship, review, and publication of research outputs

Each document should be reviewed by the Board, formally adopted by resolution, and version-controlled in this repository.
