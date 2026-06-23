# Luminis Foundation — Research Roadmap Audit

> Last updated: 2026-06-23
> Purpose: Audit the path from current state to the first validated, publishable dataset.
> This document is the authoritative reference for research status claims.

---

## Current State Inventory

### Research Assets

| Asset | Status | Location |
|---|---|---|
| Foundational preprint (theoretical/synthesis) | ✅ Published | [DOI 10.5281/zenodo.20143391](https://doi.org/10.5281/zenodo.20143391) |
| Research mission and program definition | ✅ Documented | `governance/mission.md`, `luminis-foundation-open/governance/mission.md` |
| Deployment ladder (Steps 1–5) | ✅ Documented | `mycosense/FIELD_STATUS.md` |
| Field deployment framework (Section 10.5) | ✅ In preprint | Zenodo preprint |
| Research protocols | ⚠️ Not yet written | `research/protocols/` is empty |
| Field notes | ⚠️ Not yet collected | `luminis-foundation-open/research/field-notes/` is empty |
| Dataset records | ⚠️ None | `research/datasets/` is empty |
| Calibration protocol | ⚠️ Not written | — |
| Data quality SOP | ⚠️ Not written | — |
| Metadata schema | ⚠️ Not defined | — |

### Software Assets

| Asset | Status | Location |
|---|---|---|
| React 18 dashboard (data visualization) | ✅ Deployed | mycosense.vercel.app |
| Mock data generator | ✅ Complete | `src/data/mockSensorData.js` |
| Signal processing hooks (rolling avg, spike detection) | ✅ Built | `src/hooks/useSignalProcessor.js` |
| Ecosystem health score logic | ✅ Built | `src/hooks/useEcosystemScore.js` |
| Calibration panel | ✅ Built (not field-used) | `src/components/CalibrationPanel.jsx` |
| Data export + SHA-256 provenance hashing | ✅ Built | `src/utils/provenanceHash.js`, `src/utils/dataExport.js` |
| Field map / zone layout | ✅ Built (mock zones) | `src/data/fieldLayout.js` |
| WebSocket sensor client | ✅ Built | `src/api/sensorClient.js` |
| ESP32 firmware scaffold | ✅ Bench-tested | `esp32-firmware/` |
| Raspberry Pi FastAPI + SQLite gateway | ✅ Bench-tested | `pi-server/` |
| Security model documentation | ✅ Written | `docs/SECURITY_MODEL.md` |
| Red/blue team plan | ✅ Written | `docs/RED_BLUE_TEAM_PLAN.md` |
| Pre-deployment security checklist | ✅ Written | `docs/FIELD_DEPLOYMENT_SECURITY.md` |

### Hardware Assets

| Asset | Status | Notes |
|---|---|---|
| ESP32-C6/S3 sensor nodes | ✅ Bench-tested | WiFi + MQTT; NVS credentials |
| Raspberry Pi gateway | ✅ Bench-tested | FastAPI + SQLite |
| Electrode arrays | ❓ Status unknown | Specific model not in public docs |
| ADS1115/ADS1299 ADC | 📋 Specified in roadmap | Acquisition boards for signal sampling |
| Solar + battery system | ⬜ Not yet assembled | Required for continuous outdoor operation |
| Weatherproof enclosures | ⬜ Not yet specified | IP65+ required for Rowe, NM conditions |

### Current Data Status

| Data Type | Status | Notes |
|---|---|---|
| Simulated dashboard data | ✅ Live | Procedurally generated; not real sensor data |
| Bench-test sensor readings | ❓ May exist locally | Not in public repository |
| On-site field data | ⬜ None | Requires Step 3 deployment |
| Calibrated sensor data | ⬜ None | Requires calibration protocol + Step 3 |
| Validated dataset | ⬜ None | Requires Steps 3 and 4 |

---

## What "Validated Dataset" Means for Luminis Foundation

A validated dataset from MycoSense is a collection of sensor readings that meets all of the following criteria:

### 1. Provenance
- Each reading has a UUID, timestamp (NTP-synchronized), and node ID
- SHA-256 provenance hash anchors the session
- GPS coordinates of each electrode node are recorded
- Site conditions at deployment (soil type, substrate, species present) are documented

### 2. Calibration
- Each electrode node has been calibrated against a known reference signal before deployment
- Calibration records are preserved alongside the dataset
- Calibration drift is documented at collection end

### 3. Data Quality
- Minimum session duration: defined (e.g., 72 continuous hours minimum for a baseline)
- Acceptable noise floor: defined and measured
- Spike detection threshold: calibrated to site conditions, not defaults
- Missing data rate: documented with gaps labeled, not silently dropped
- NTP sync confirmed for all timestamps (no `ts == -1` readings in final dataset)

### 4. Metadata
- Site name, GPS coordinates, elevation, aspect
- Deployment date, duration, personnel
- Weather conditions during collection
- Substrate description: soil type, moisture, fungal species (if identified)
- Hardware version, firmware version, software version
- Any anomalies or interventions during collection

### 5. Review
- Internal review by Foundation researcher(s)
- Signal traces inspected for obvious artifacts
- Comparison to mock data baselines to confirm real signal variation
- Written QC report

### 6. Privacy / Ethics
- No personal data in dataset
- No GPS data for private land without landowner consent
- Ecological sensitivity of site assessed (protected species, sensitive habitat)

---

## Minimum Viable Field Protocol

The minimum viable field protocol for Step 3 (on-site prototype deployment) is:

1. **Site preparation:** GPS survey of each electrode placement; site conditions documented
2. **Hardware setup:** Enclosure assembly, solar/battery connection, WiFi/MQTT configuration
3. **Pre-deployment calibration:** Each node calibrated before installation; records saved
4. **Deployment:** Electrode arrays installed in soil/substrate; nodes secured
5. **Connectivity check:** ESP32 → Pi MQTT confirmed; Pi → Dashboard live data confirmed
6. **Data collection start:** Begin logging; record start time and conditions
7. **Monitoring:** Check Pi storage daily; check solar/battery status
8. **Collection end:** Record end time, conditions, any anomalies
9. **Post-collection calibration:** Calibrate again to measure drift
10. **Data export:** Export from Pi SQLite; generate SHA-256 provenance hash
11. **QC review:** Inspect signal traces; document quality assessment
12. **Archive:** Save raw + QC'd dataset with full metadata

---

## Calibration Requirements

- Defined reference signal (known voltage) for pre/post calibration
- Calibration log: node ID, signal applied, reading recorded, deviation
- Acceptable deviation threshold defined before deployment
- Calibration invalidation criteria (e.g., >10% drift = node removed from dataset)
- Temperature compensation notes (high-desert temperature swings affect electrode impedance)

---

## Metadata Requirements

Minimum required metadata for each deployment session:

```json
{
  "session_id": "uuid",
  "site_name": "string",
  "site_gps": { "lat": "float", "lon": "float", "elevation_m": "float" },
  "deployment_start": "ISO8601",
  "deployment_end": "ISO8601",
  "personnel": ["string"],
  "substrate": "string (soil type, fungal species if known)",
  "weather_conditions": "string",
  "hardware_version": "string",
  "firmware_version": "string",
  "dashboard_version": "string",
  "calibration_pre": { "node_id": "deviation" },
  "calibration_post": { "node_id": "deviation" },
  "anomalies": ["string"],
  "provenance_hash": "sha256"
}
```

---

## Data Quality Requirements

| Requirement | Minimum Standard | Notes |
|---|---|---|
| Session duration | ≥ 72 continuous hours | Longer for seasonal baselines |
| Timestamp sync | 100% NTP-verified | No `ts == -1` in final dataset |
| Missing data rate | < 5% of readings | Document all gaps |
| Noise floor | Measured and documented | Site-specific |
| Calibration drift | < 10% per node | Nodes exceeding threshold excluded |
| GPS accuracy | ± 3 meters | Record with HDOP value |
| Metadata completeness | 100% of required fields | See schema above |

---

## Publication Requirements

Before publishing a dataset or empirical paper:

1. Dataset meets all validation criteria above
2. Metadata schema is complete
3. QC report written and reviewed
4. Data hosted on Zenodo with DOI
5. Dataset README explains measurement methodology, units, and limitations
6. Software version used for collection is tagged in git
7. Paper or preprint describes: site, methods, hardware version, limitations
8. No overclaiming in abstract or conclusions about biological significance before peer review
9. Data limitations clearly stated (prototype hardware, single site, limited duration)

---

## Ethics and Privacy

- No personal data collected by MycoSense sensors (soil electrode measurements only)
- Ecological sensitivity: document if site contains protected species or sensitive habitat
- Land access: written permission from landowner before any deployment outside Foundation property
- If future deployments involve Indigenous land or traditional ecological knowledge, formal community consultation and consent is required before collection or publication
- On-chain provenance anchoring (Polygon / Gnosis Safe, planned) does not create privacy risk for current sensor data

---

## Dataset Release Stages

| Stage | Description | Requirements Before Release |
|---|---|---|
| Stage 0 | Simulated demo data | Already live at mycosense.vercel.app — clearly labeled mock |
| Stage 1 | Bench-test data (internal only) | QC + internal review; not for public release |
| Stage 2 | On-site prototype data (Step 3) | Full validation protocol + QC + metadata + internal review |
| Stage 3 | Validated local dataset (Step 4) | Stage 2 + extended duration + peer review-ready |
| Stage 4 | Public dataset on Zenodo (Step 5) | Stage 3 + Zenodo upload + DOI + dataset paper or preprint |

---

## Practical Research Roadmap

### 0–30 Days (July 2026)

- [ ] Write `research/protocols/calibration-protocol.md`
- [ ] Write `research/protocols/field-data-quality-sop.md`
- [ ] Define metadata schema (JSON) and commit to `research/protocols/`
- [ ] Confirm Step 3 deployment site and land access at Rowe, NM
- [ ] Complete Phase 2 security hardening checklist (`docs/FIELD_DEPLOYMENT_SECURITY.md`)
- [ ] Specify electrode array model and ADC board (ADS1115 vs ADS1299)
- [ ] Specify enclosure IP rating and procurement
- [ ] Identify solar/battery system for Step 3
- [ ] Set Step 3 target deployment date

### 3 Months (September 2026)

- [ ] Step 3: Controlled on-site prototype deployment at Foundation office, Rowe, NM
- [ ] First real sensor data collection (≥ 72 hours)
- [ ] Pre- and post-deployment calibration records
- [ ] Initial QC review of bench-to-field signal comparison
- [ ] Hardware iteration: identify enclosure, power, and connectivity improvements
- [ ] Draft field notes for `luminis-foundation-open/research/field-notes/`
- [ ] Update FIELD_STATUS.md to reflect Step 3 completion (when confirmed)

### 6 Months (December 2026)

- [ ] Step 3 protocol refined after initial deployment experience
- [ ] Multiple Step 3 sessions (different conditions: dry vs monsoon-adjacent season)
- [ ] Internal dataset review — can any Step 3 data be advanced to Stage 3?
- [ ] Begin TinyML classifier design for mycorrhizal health state
- [ ] Draft follow-on preprint or technical note: field deployment protocol
- [ ] Apply for research-focused grants (NSF, environmental foundations) with Step 3 data in hand
- [ ] Establish baseline EI/EC profiles for Rowe, NM site

### 12 Months (June 2027)

- [ ] Step 4: Validated local field dataset — extended duration, full QC, publication-ready
- [ ] Dataset archived on Zenodo with DOI
- [ ] Dataset paper or data descriptor preprint submitted
- [ ] TinyML model: first quantized classifier trained on validated data
- [ ] Board annual review of research program progress
- [ ] First IRS 990/990-N filing (for tax year 2026)
- [ ] NM-COROS registration (if not yet filed)
- [ ] Second grant cycle — larger funders now accessible with 501(c)(3) + data in hand

### 24 Months (June 2028)

- [ ] Step 5 planning: Broader Pecos watershed deployment design
- [ ] Inter-watershed federation protocol specification
- [ ] Community engagement for watershed-scale deployment sites
- [ ] Formal land access agreements with landowners
- [ ] Indigenous community consultation (if relevant to deployment sites)
- [ ] Multi-site dataset: multiple nodes across watershed
- [ ] Publication: longitudinal ecological monitoring paper
- [ ] Public dataset release on Zenodo (Stage 4)
- [ ] Federated learning protocol tested across nodes

---

## MycoSense Deployment Ladder — Current Status

| Step | Milestone | Status | What's Needed |
|---|---|---|---|
| 1 | Simulated public dashboard | ✅ Complete | Nothing — live at mycosense.vercel.app |
| 2 | Bench-tested hardware prototype | ✅ Complete | Nothing — E2E validated on bench |
| 3 | Controlled on-site prototype (Rowe, NM) | 📋 Planned | Protocols + hardware prep + site access + deployment date |
| 4 | Validated local field dataset | ⬜ Future | Step 3 complete + calibration + QC + extended run |
| 5 | Pecos watershed deployment + public dataset | ⬜ Future | Step 4 complete + land access + community engagement |

---

## Evidence Confidence

### Key

| Symbol | Meaning |
|---|---|
| ✅ Pub | Confirmed from public repository files |
| 📋 Legal | Confirmed from legal/state records (private) |
| 🗣️ Founder | Stated or confirmed by the founder |
| ⚠️ Conflict | Conflicted — multiple sources disagree |
| ❓ Unknown | Missing or not verifiable from available public sources |

### Assessment

| Claim | Confidence | Source |
|---|---|---|
| MycoSense Vercel dashboard is live with simulated data | ✅ Pub | `mycosense/FIELD_STATUS.md`; mycosense.vercel.app |
| ESP32 + Pi bench-validated end-to-end | ✅ Pub | `mycosense/FIELD_STATUS.md` |
| Step 3 on-site deployment planned, not started | ✅ Pub | `mycosense/FIELD_STATUS.md` |
| No validated public field dataset exists | ✅ Pub | `research/datasets/` empty; FIELD_STATUS.md confirms |
| No calibration protocol written | ✅ Pub | `research/protocols/` directory is empty |
| No data quality SOP written | ✅ Pub | `research/protocols/` directory is empty |
| No real bench-test data in public repo | ✅ Pub | Not found in any public repo; may exist locally |
| Bench-test data may exist locally but not published | ❓ Unknown | No confirmation either way |
| Preprint is theoretical/synthesis — not empirical field data | ✅ Pub | DOI 10.5281/zenodo.20143391; preprint content |
| Land access for Rowe, NM site confirmed | ❓ Unknown | Not documented in any public repo |
