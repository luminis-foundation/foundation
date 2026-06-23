# Luminis Foundation — Institutional Map

> Last updated: 2026-06-23
> Maintained by: Carlos Garcia (President) / Board of Directors
> Status legend: ✅ Complete | 🔄 In progress | 📋 Planned | ⬜ Future | ❓ Unknown | ⚠️ Gap
>
> Evidence confidence key: ✅ Pub = Confirmed from public repo | 📋 Legal = Confirmed from legal/state records (private) | 🗣️ Founder = Founder-confirmed | ⚠️ Conflict = Conflicted / contradicted by another source | ❓ = Missing or unknown
>
> **Important:** "Not publicly present in this repo" does not mean "does not exist." Signed bylaws, COI policies, IRS correspondence, and board minutes are expected to exist as private records held by officers. This map documents only what is knowable from public sources or confirmed by the founder.

---

## 1. Legal Entity

| Field | Value | Source | Notes |
|---|---|---|---|
| Legal name | Luminis Foundation | NM SOS filings | |
| Entity type | Domestic Nonprofit Corporation | NM SOS | |
| State | New Mexico | NM SOS | |
| Entity ID | 0008089293 | `governance/mission.md`, NM SOS | Already public |
| Formation date | March 16, 2026 | `governance/milestones.md` | |
| Registered office | 133 Frontage Rd 2116, Rowe, NM 87562 | `governance/mission.md` | Public registered address |
| Mailing address | P.O. Box 86, Rowe, NM 87562 | `governance/mission.md` | Public mailing address |
| Governing law | Chapter 53, Article 8 NMSA 1978 (NM Nonprofit Corporation Act) | `governance/mission.md` | |
| EIN | Not included in public records | — | Keep private; do not commit |
| Banking | Pending / needs board-authorized completion | `governance/roadmap.md` (open item) | ⚠️ Gap — 🗣️ Status confirmed as not yet established |

---

## 2. Governance

> **Note:** Documents marked "not publicly present" may exist as private records held by officers. Absence from this public repository does not confirm non-existence. Signed bylaws, COI policies, and meeting minutes are standard private governance records.

| Document | Status | Source | Owner | Next Action |
|---|---|---|---|---|
| Certificate of Incorporation | ✅ Issued Mar 16, 2026 | `governance/milestones.md` | Carlos Garcia | Not publicly present in repo — keep in private records |
| Bylaws | ✅ Adopted Mar 19, 2026 | `governance/milestones.md` | Board | Not publicly present in repo — consider redacted public summary |
| Conflict-of-interest policy | ✅ Adopted Mar 19, 2026 | `governance/milestones.md` | Board | Not publicly present in repo — consider committing redacted version |
| NM Initial Report | ✅ Filed May 7, 2026 | `governance/milestones.md` | Guillermo Martin | Annual report due each year |
| Form 1023-EZ | ✅ Filed Jun 9, 2026 | `governance/milestones.md` | Carlos Garcia | Await IRS determination letter |
| NM-COROS charitable registration | ⬜ Not yet filed | `governance/roadmap.md` (open) | Carlos Garcia | File after 501(c)(3) determination |
| Board minutes | ⚠️ Not publicly present in repo | `governance/board-minutes/` empty in this repo | Board Secretary | Private records may exist; document organizational meeting; store privately |
| Annual reports | ⚠️ Not yet needed | `governance/annual-reports/` empty in repo | Guillermo Martin | Not yet due; required each year to NM SOS |
| Banking infrastructure | ⚠️ Pending / needs board-authorized completion | Open roadmap item | Adam Kimble | Initiate board-authorized banking process |
| 501(c)(3) determination letter | 📋 Pending IRS | Filed Jun 9, 2026 | IRS / Carlos | Await; do not claim exemption until received |

---

## 3. Board and Officers

| Name | Role | Contact | Status | Notes |
|---|---|---|---|---|
| Carlos Garcia | President, Founder, Research Director | carlos@luminisfoundationresearch.org | ✅ Active | Primary technical and research lead; single point of failure risk |
| Guillermo Martin | Secretary | — | ✅ Active | Board minutes and filing responsibilities |
| Adam Kimble | Treasurer | adam@luminisfoundationresearch.org | ✅ Active | Financial oversight; banking pending / needs board-authorized completion |
| Sterling VanKaujk | Vice President | sterling@luminisfoundationresearch.org | ✅ Active | 🗣️ Legal name confirmed by founder as "VanKaujk". ✅ Website surname corrected via luminis-foundation/luminis-foundation.github.io#4 |

**Board gap notes:**
- No succession plan documented for any officer
- No quorum or meeting cadence policy visible in public records
- Board size (4) is at lower end for sustained governance
- No independent director(s) on record

---

## 4. Public Websites

| Site | URL | Status | Owner | Notes |
|---|---|---|---|---|
| Foundation website | luminisfoundationresearch.org | ✅ Live | Carlos Garcia | Single-page HTML; good CSP headers |
| MycoSense demo | mycosense.vercel.app | ✅ Live | Carlos Garcia | Simulated/mock data; correctly labeled in UI and README |
| GitHub org | github.com/luminis-foundation | ✅ Live | Carlos Garcia | Public-facing org; 5 repos |

**Website audit notes:**
- 501(c)(3) language on website: "Filed — awaiting IRS determination" ✅ Correct
- MycoSense status on website: "Prototype planned" ✅ Correct
- Simulated data disclaimer: Present ✅
- No CSP issues noted; strict `default-src 'none'` base ✅
- ✅ **P0 Resolved:** VP surname corrected in website source (index.html) via luminis-foundation/luminis-foundation.github.io#4

---

## 5. Repositories

| Repository | Purpose | Status | Key Files | Gaps |
|---|---|---|---|---|
| `luminis-foundation/foundation` | Institutional records (this repo) | ✅ Active | governance/, research/, knowledge-graph/, risk/, operations/ | Board minutes, annual reports, bylaws text not publicly present in repo |
| `luminis-foundation/mycosense` | MycoSense platform (dashboard + firmware + Pi) | ✅ Active | README.md, FIELD_STATUS.md, SECURITY.md, docs/ | Field protocols, calibration docs absent |
| `luminis-foundation/luminis-foundation-open` | Public research + community | ✅ Active | governance/, research/, field-deployment/ | field-deployment/protocols/, field-deployment/site-specs/ empty; publications/ empty |
| `luminis-foundation/luminis-foundation.github.io` | Foundation website source | ✅ Active | index.html, luminis-banner.jpg, luminis-logo.jpg | ✅ VP surname corrected to "VanKaujk" via luminis-foundation/luminis-foundation.github.io#4; no privacy policy; no contact form |
| `luminis-foundation/security-hardening` | Security documentation | ❓ Unknown | — | Not yet inspected in this audit |

**Repo audit notes:**
- ✅ `luminis-foundation-open` README field deployment and 501(c)(3) language: corrected via luminis-foundation/luminis-foundation-open#6
- ✅ `luminis-foundation.github.io` VP surname: corrected to "VanKaujk" via luminis-foundation/luminis-foundation.github.io#4

---

## 6. Research Programs

| Program | Description | Status | Publication | Next Milestone |
|---|---|---|---|---|
| Fungal electrophysiology & mycelial biosensing | Electrode sensing of mycelial electrical signals; spike detection; EI/EC profiling | 🔄 Software built; no field data | DOI 10.5281/zenodo.20143391 | Step 3: on-site prototype deployment |
| Mycelium-inspired decentralized AI | Network topology research inspired by mycorrhizal architecture | 🔄 Theoretical framework published | DOI 10.5281/zenodo.20143391 | TinyML classifier design |
| TinyML and edge-deployed sensor networks | Quantized ML models for ESP32 deployment | 📋 Planned | — | Firmware v2 with TinyML |
| Privacy-preserving federated learning | Federated model-update protocol with biological threshold-gating | 📋 Planned | DOI 10.5281/zenodo.20143391 (Section 10.5 framework) | Protocol specification |
| Bio-hybrid plant–fungal–AI systems | Integration of living systems with AI decision-making | 📋 Theoretical | DOI 10.5281/zenodo.20143391 | First field trial |

---

## 7. MycoSense — Detailed Status

| Component | Description | Status | Location |
|---|---|---|---|
| React 18 dashboard | Browser-based biosensor visualization | ✅ Deployed (mock data) | mycosense.vercel.app |
| Mock data generator | Procedural simulated sensor data | ✅ Complete | `src/data/mockSensorData.js` |
| ESP32-C6/S3 firmware | Sensor node firmware (Arduino/C++) | ✅ Bench-tested | `esp32-firmware/` |
| Raspberry Pi gateway | FastAPI + SQLite data coordinator | ✅ Bench-tested | `pi-server/` |
| Full E2E stack (ESP32 → Pi → Dashboard) | Complete data pipeline | ✅ Bench-validated | — |
| Calibration system | CalibrationPanel.jsx; calibration hooks | ✅ Built (not field-calibrated) | `src/components/CalibrationPanel.jsx` |
| Data export + provenance hashing | SHA-256 provenance; CSV export | ✅ Built | `src/utils/provenanceHash.js` |
| Field map / zone layout | Spatial zone layout definitions | ✅ Built (mock zones) | `src/data/fieldLayout.js` |
| GPS coordinates | Node position recording | ⚠️ Not yet set — null values | `FIELD_STATUS.md` |
| Solar power + outdoor runtime | Continuous unattended operation | ⬜ Not validated | — |
| Weatherproofing | Outdoor enclosure validation | ⬜ Not validated | — |
| MQTT TLS (production) | Encrypted field MQTT | ⬜ Planned for Phase 2 | `docs/FIELD_DEPLOYMENT_SECURITY.md` |
| OTA firmware updates | Automated firmware delivery | ⬜ Planned | — |
| Data retention policy | Long-term log management | ⬜ Not defined | — |
| On-site prototype deployment (Step 3) | Rowe, NM Foundation office site | 📋 Planned | `FIELD_STATUS.md` |
| Validated local field dataset (Step 4) | First real sensor dataset | ⬜ Future | — |
| Pecos watershed deployment (Step 5) | Broader deployment + public data | ⬜ Future | — |

---

## 8. Legal / Compliance Records

| Record | Status | Date | Notes |
|---|---|---|---|
| NM Certificate of Incorporation | ✅ Issued | Mar 16, 2026 | Not publicly present in repo — do not commit PDF |
| Bylaws | ✅ Adopted by Board | Mar 19, 2026 | Not publicly present in repo — consider redacted summary |
| Conflict-of-interest policy | ✅ Adopted by Board | Mar 19, 2026 | Not publicly present in repo — consider redacted version |
| NM Initial Report | ✅ Filed | May 7, 2026 | Adds Sterling VanKaujk as VP (✅ website surname corrected via luminis-foundation/luminis-foundation.github.io#4) |
| Form 1023-EZ | ✅ Filed | Jun 9, 2026 | $275 user fee paid Jun 10; IRS determination pending |
| NM-COROS registration | ⬜ Not filed | — | Required if soliciting in NM; file after IRS determination |
| Federal EIN | ❓ Not in public records | — | Do not commit — keep private |
| Annual report (NM SOS) | ⬜ Not yet due | — | Required annually; first due 2027 |
| IRS 990 / 990-N | ⬜ Not yet filed | — | Required annually after tax year end |

---

## 9. Funding and Grant Status

| Funder | Program | Amount | Status | Submitted | Notes |
|---|---|---|---|---|---|
| Awesome Foundation | Conservation & Climate | $1,000 | Pending | Jun 10, 2026 | Microgrant; does not require 501(c)(3) |

**Funding gaps:**
- No operational budget documented
- No financial reserves
- Banking pending / needs board-authorized completion
- No major grant strategy documented
- No earned revenue model
- No donor acknowledgment process documented

---

## 10. Publications

| Title | Authors | Year | DOI | License | Status |
|---|---|---|---|---|---|
| Bridging Mycelium-Inspired Decentralized Computing and Symbiotic Plant–Fungal–AI Bio-Hybrid Systems in Northern New Mexico's High-Desert Ecosystems | Garcia, Kimble, Martin, VanKaujk | 2026 | [10.5281/zenodo.20143391](https://doi.org/10.5281/zenodo.20143391) | CC-BY-4.0 | Preprint (Zenodo) |

> **⚠️ Author name note:** Correct legal name is "VanKaujk" (founder-confirmed). If the Zenodo submission listed "VanKuijk," a Zenodo metadata correction request should be submitted. Do not assume the preprint is correct until the Zenodo record is verified.

**Publication gaps:**
- No follow-on empirical publications
- No peer-reviewed journal placement recorded
- No conference presentations recorded
- `research/publications/` directory is empty (records not yet added)
- `luminis-foundation-open/research/publications/` directory also empty

---

## 11. Prototype Hardware

| Asset | Description | Status | Location | Notes |
|---|---|---|---|---|
| ESP32-C6/S3 nodes | Sensor node microcontrollers | ✅ Bench-tested | Foundation office / Rowe, NM | WiFi + MQTT; NVS credential storage |
| Raspberry Pi (gateway) | Local data coordinator | ✅ Bench-tested | Foundation office / Rowe, NM | FastAPI + SQLite; LAN-only |
| Electrode arrays | Soil/mycelial contact electrodes | ❓ Status unknown | — | Specific model/spec not in public docs |
| ADS1115/ADS1299 ADC | Signal acquisition boards | 📋 Specified in roadmap | — | Referenced in governance/roadmap.md |
| Solar power system | Off-grid outdoor power | ⬜ Not yet validated | — | Required for Step 3 |
| Outdoor enclosures | Weatherproofing for nodes | ⬜ Not yet validated | — | Required for Step 3 |

---

## 12. Data / Dataset Status

| Dataset | Status | Notes |
|---|---|---|
| Simulated dashboard data | ✅ Procedurally generated | `src/data/mockSensorData.js` — not real sensor data |
| Bench-test readings | ❓ Unknown | May exist locally; not in public repo |
| On-site prototype data | ⬜ Future | Requires Step 3 deployment |
| Validated local field dataset | ⬜ Future | Requires Step 3 + calibration + QC |
| Public Zenodo dataset | ⬜ Future | Requires Step 4 before release |

---

## 13. Open Questions

| Question | Category | Owner | Priority |
|---|---|---|---|
| Has an EIN been assigned by the IRS? | Legal/compliance | Carlos Garcia | P0 |
| What specifically is blocking banking establishment, and who has board authorization to initiate it? | Finance | Adam Kimble | P0 |
| Does the Zenodo preprint list "VanKuijk" or "VanKaujk" as the author? | Records | Carlos Garcia | P1 |
| When is the NM-COROS charitable registration required? | Legal/compliance | Carlos Garcia | P1 |
| Are there bench-test data logs from ESP32/Pi that should be preserved? | Research/data | Carlos Garcia | P1 |
| What is the specific electrode array model and part number? | Hardware | Carlos Garcia | P1 |
| Is there a fiscal sponsorship or umbrella arrangement in place? | Finance | Adam Kimble | P1 |
| What is the on-site deployment timeline for Step 3? | MycoSense | Carlos Garcia | P1 |
| Are board meeting minutes being recorded? Where are they stored? | Governance | Guillermo Martin | P1 |
| Is the Rowe, NM site owned/leased by the Foundation or a private party? | Legal/compliance | Carlos Garcia | P2 |

---

## 14. Missing Records

| Missing Record | Why It Matters | Recommended Action |
|---|---|---|
| Bylaws (even redacted text) | Governance transparency; grant reviewers expect it | Commit a public summary or redacted version |
| Conflict-of-interest policy | IRS and grant compliance | Commit a public version |
| Board meeting minutes | Governance continuity | Store privately; keep a log |
| Organizational meeting minutes | Confirms bylaws adoption, officer elections | Store privately |
| Financial controls policy | Required for grant accountability | Draft and adopt |
| Field protocol documents | Research credibility; needed before deployment | Draft in `research/protocols/` |
| Calibration protocol | Data quality for any future dataset | Draft before Step 3 |
| Data management plan | Required by many funders | Draft before first grant |
| Site agreements/permits | Required before field deployment | Confirm land access |
| Research ethics review | May be required for ecological sensing | Determine if IRB/IEC needed |

---

## 15. Dependencies

| Dependency | Type | Risk if Lost | Mitigation Status |
|---|---|---|---|
| Carlos Garcia | Human — founder, researcher, primary technical contact | Critical — research stalls | No succession plan ⚠️ |
| Vercel hosting (MycoSense) | Infrastructure | Demo goes offline | Free tier; switch to GitHub Pages if needed |
| Zenodo (publication host) | Research infrastructure | Preprint inaccessible | DOI persists; Zenodo has high uptime |
| GitHub (repositories) | Infrastructure | Codebase inaccessible | Mirror/backup not documented |
| ESP32 supply chain | Hardware | Prototype can't be scaled | Common chip; multiple suppliers |
| Rowe, NM site access | Physical | Step 3 deployment blocked | Site ownership/access unclear |
| IRS 501(c)(3) determination | Legal/financial | Grant eligibility restricted | Form 1023-EZ filed; no controls on IRS timing |

---

## 16. Near-Term Decisions

| Decision | Deadline | Owner | Stakes |
|---|---|---|---|
| Initiate banking (pending / needs board-authorized completion) | ASAP — blocks financial operations | Adam Kimble | Cannot receive grants, manage expenses, or pay fees |
| ✅ Fix VP surname in website source: luminis-foundation.github.io/index.html | Resolved | Carlos Garcia | Corrected via luminis-foundation/luminis-foundation.github.io#4 |
| Verify Zenodo preprint VP author name; request Zenodo correction if listed as "VanKuijk" | P1 | Carlos Garcia | Author record accuracy; must align with confirmed legal name |
| Determine NM-COROS registration requirement | After 501(c)(3) determination | Carlos Garcia | Legal compliance for NM charitable solicitation |
| ✅ Revise luminis-foundation-open README: field deployment and 501(c)(3) language | Resolved | Carlos Garcia | Corrected via luminis-foundation/luminis-foundation-open#6 |
| Set Step 3 deployment date | P1 | Carlos Garcia | Unlocks research program, grant eligibility |
| Draft and adopt financial controls policy | P1 | Adam Kimble | Required for IRS compliance and grant accountability |
| Draft field and calibration protocols | Before Step 3 | Carlos Garcia | Research credibility; data quality |
| Decide board expansion strategy | P2 | Board | Governance resilience; diverse expertise |

---

## Evidence Confidence

### Key

| Symbol | Meaning |
|---|---|
| ✅ Pub | Confirmed from public repository files |
| 📋 Legal | Confirmed from legal/state records (private — not in this public repo) |
| 🗣️ Founder | Stated or confirmed by the founder |
| ⚠️ Conflict | Conflicted — multiple sources give different information |
| ❓ Unknown | Missing or not verifiable from available public sources |

### Assessment

| Claim | Confidence | Source |
|---|---|---|
| NM Entity ID 0008089293, formed March 16, 2026 | ✅ Pub | `governance/mission.md`, `governance/milestones.md` |
| Bylaws adopted March 19, 2026 | ✅ Pub | `governance/milestones.md` |
| COI policy adopted March 19, 2026 | ✅ Pub | `governance/milestones.md` |
| NM Initial Report filed May 7, 2026 | ✅ Pub | `governance/milestones.md` |
| Form 1023-EZ filed June 9, 2026; $275 fee June 10 | ✅ Pub | `governance/milestones.md` |
| 501(c)(3) applied for — determination not yet received | ✅ Pub | `governance/milestones.md`; website |
| VP legal name is "VanKaujk" | ✅ Pub + 🗣️ Founder | Confirmed by founder; website corrected via luminis-foundation/luminis-foundation.github.io#4 |
| Website VP surname corrected to "VanKaujk" | ✅ Pub | luminis-foundation/luminis-foundation.github.io#4 merged |
| luminis-foundation-open README overclaims corrected | ✅ Pub | luminis-foundation/luminis-foundation-open#6 merged |
| Banking not yet established | 🗣️ Founder | Open item in `governance/roadmap.md`; confirmed as pending |
| EIN assigned or not | ❓ Unknown | Not in public records; keep private |
| ESP32 + Pi bench-validated end-to-end | ✅ Pub | `mycosense/FIELD_STATUS.md` |
| Step 3 on-site deployment is planned, not started | ✅ Pub | `mycosense/FIELD_STATUS.md` |
| No validated public field dataset | ✅ Pub | `research/datasets/` empty; FIELD_STATUS.md confirms |
| Preprint published — DOI 10.5281/zenodo.20143391 | ✅ Pub | `governance/milestones.md` |
| Awesome Foundation grant pending ($1,000) | ✅ Pub | `governance/grants.md` |
| Bylaws / COI text / board minutes exist | ❓ Unknown (public) / 📋 Legal (private) | Not publicly present in repo; existence inferred from milestones |
| Zenodo preprint author spelling | ⚠️ Unverified | Needs manual check; correction request may be needed |
