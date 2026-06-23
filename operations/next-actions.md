# Luminis Foundation — Prioritized Next Actions

> Last updated: 2026-06-23
> Owner: Carlos Garcia (review with Board quarterly)
> Format: P0 = do now (blocking) | P1 = do this week/month | P2 = plan for next quarter | P3 = future

---

## Legal / Compliance

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Initiate banking (pending / needs board-authorized completion) | Adam Kimble | Medium | Blocks receiving grants, paying expenses, and financial accountability | Bank account open; signatories established; Adam and Carlos have access |
| P0 | Await and log IRS correspondence | Carlos Garcia | Small | 1023-EZ filed Jun 9 — monitor for IRS questions or determination letter | IRS determination letter received and filed privately; status updated in foundation-map.md |
| P1 | Confirm NM-COROS registration requirement | Carlos Garcia | Small | Required if Foundation solicits charitable contributions in NM | Decision documented; registration filed if required |
| P1 | Create compliance calendar | Carlos Garcia, Adam Kimble | Small | Annual NM SOS report, IRS 990/990-N, NM-COROS renewals — all have deadlines | Calendar created with all annual deadlines for 2026–2028 |
| P1 | Draft and adopt financial controls policy | Adam Kimble | Medium | IRS compliance; grant accountability; good governance practice | Policy adopted by Board; stored privately |
| P2 | Review bylaws for quorum and vacancy procedures | Carlos Garcia, Guillermo Martin | Small | Board continuity risk; need to understand quorum with 4-member board | Quorum and vacancy procedures reviewed; documented in private board notes |
| P2 | Draft redacted bylaws summary for public repo | Carlos Garcia | Small | Governance transparency for grant reviewers | Redacted summary committed to `governance/bylaws-summary.md` |
| P2 | File NM-COROS registration (if required) | Carlos Garcia | Small | Post-IRS determination | Registration filed or requirement confirmed not applicable |

---

## Governance

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Confirm signed organizational meeting minutes are retained as a private record; create a public-safe index or template if desired | Guillermo Martin | Small | Confirms bylaws adoption, officer elections — foundational governance record | Signed copy confirmed retained privately; public-safe index or template created if desired |
| ✅ Done | Fix VP surname in Foundation website source: luminis-foundation.github.io/index.html | Carlos Garcia | Small | Corrected via luminis-foundation/luminis-foundation.github.io#4 | ✅ PR merged; website displays "VanKaujk" |
| P1 | Verify Zenodo preprint VP author name spelling; request Zenodo correction if listed as "VanKuijk" | Carlos Garcia | Small | Author record must align with confirmed legal name | Zenodo record checked; correction request submitted if needed |
| P1 | Schedule Q3 2026 board meeting | Carlos Garcia | Small | Governance cadence; review foundation status, research plan, budget | Board meeting held; minutes recorded |
| P1 | Ensure all officers have access to key accounts | Carlos Garcia | Small | Founder dependency risk — single point of failure | Adam has banking access once established; Guillermo has NM SOS access; at least 2 people can access GitHub org |
| P2 | Evaluate board expansion | Board | Medium | 4-person board is small; independent director(s) would strengthen governance | Board discusses expansion; target 5–7 members within 12 months |
| P2 | Create private "operations and credentials" document | Carlos Garcia | Medium | Founder dependency; all key accounts, contacts, and credentials should be accessible to board in emergency | Document created; stored securely offline or in private repo accessible to Board |
| P3 | Draft board member agreement/expectations | Carlos Garcia | Small | Volunteer expectations; time commitment; fiduciary duty | Board member agreement drafted and signed |

---

## Research

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Write calibration protocol | Carlos Garcia | Medium | Required before Step 3; data without calibration records is unusable | `research/protocols/calibration-protocol.md` committed and reviewed |
| P0 | Write field data quality SOP | Carlos Garcia | Medium | Required before Step 3; defines what "valid data" means | `research/protocols/field-data-quality-sop.md` committed and reviewed |
| P1 | Define metadata schema | Carlos Garcia | Small | Required before any dataset is collected | JSON schema committed to `research/protocols/metadata-schema.json` |
| P1 | Add publication record to `research/publications/` | Carlos Garcia | Small | Repository is empty; preprint DOI should be documented | `research/publications/2026-zenodo-20143391.md` committed |
| P1 | Draft data management plan | Carlos Garcia | Medium | Required by most funders; defines storage, retention, sharing, privacy | Data management plan committed to `research/` or available for grant submissions |
| P2 | Design TinyML classifier architecture | Carlos Garcia | Large | Mid-term research milestone per `governance/roadmap.md` | Classifier architecture documented; training approach defined |
| P2 | Write follow-on technical preprint: field deployment protocol | Carlos Garcia | Large | Documents the methodology before empirical data is available | Preprint drafted; submitted to Zenodo |
| P2 | Define seasonal monitoring plan for Rowe, NM site | Carlos Garcia | Small | High-desert conditions; monsoon season timing; seasonal biology affects signals | Seasonal plan documented in `research/protocols/` |

---

## MycoSense

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Set Step 3 deployment target date | Carlos Garcia | Small | Everything else depends on this date | Date set; FIELD_STATUS.md updated with target |
| P0 | Confirm land access for Rowe, NM deployment site | Carlos Garcia | Small | Cannot deploy without clear site access | Land access confirmed in writing; documented |
| P1 | Specify enclosure IP rating and procure | Carlos Garcia | Medium | Required for outdoor operation in Rowe, NM (heat, dust, monsoon) | Enclosure model selected; procurement ordered |
| P1 | Identify and procure solar + battery system | Carlos Garcia | Medium | Required for continuous unattended outdoor operation | Solar/battery system specified; procured or ordered |
| P1 | Complete Phase 2 security hardening (`docs/FIELD_DEPLOYMENT_SECURITY.md`) | Carlos Garcia | Medium | Required before field deployment | All pre-deployment checklist items checked |
| P1 | Implement log rotation on Pi server | Carlos Garcia | Small | Disk full risk during long outdoor deployments | Log rotation configured; tested |
| P1 | Specify electrode array model and ADC board | Carlos Garcia | Small | Needed for hardware documentation and reproducibility | Electrode and ADC model documented in hardware spec file |
| P2 | Implement MQTT signing / replay protection | Carlos Garcia | Medium | Security hardening for Phase 2 field deployment | MQTT signing implemented; tested |
| P2 | Implement production MQTT TLS | Carlos Garcia | Medium | End-to-end security for field deployment | TLS configured between ESP32 and Pi; tested |
| P2 | Implement OTA firmware updates | Carlos Garcia | Large | Enables remote firmware management for field nodes | OTA update tested; rollback procedure documented |
| P3 | Implement on-chain provenance anchoring (Polygon / Gnosis Safe) | Carlos Garcia | Large | Optional; planned for Phase 3 per FIELD_STATUS.md | On-chain posting tested for a session hash |

---

## Grants

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Monitor Awesome Foundation application | Carlos Garcia | Small | $1,000 pending; first grant | Application result recorded in `governance/grants.md` |
| P1 | Identify 5 grant opportunities for next cycle | Carlos Garcia, Lumen | Medium | No funding pipeline exists; 501(c)(3) pending will unlock more options | 5 opportunities identified with deadlines, amounts, requirements, and eligibility |
| P1 | Draft data management plan (dual use: grants + research) | Carlos Garcia | Medium | Most environmental and technology funders require it | Plan drafted; reviewed by Lumen |
| P2 | Draft 12-month operating budget | Adam Kimble | Medium | Required for most grant applications; defines realistic ask | Budget drafted; reviewed by Board |
| P2 | Apply to environmental and tech foundations (post-IRS determination) | Carlos Garcia | Large | 501(c)(3) determination unlocks most institutional grants | Applications submitted to ≥ 3 funders |
| P3 | Investigate NSF SBIR/STTR or NSF BIO program eligibility | Carlos Garcia | Medium | Federal funding for ecological sensor research | Eligibility determination; letter of intent drafted if eligible |

---

## Public Website

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| ✅ Done | Fix VP surname in Foundation website source (index.html: VanKuijk → VanKaujk) | Carlos Garcia | Small | Corrected via luminis-foundation/luminis-foundation.github.io#4 | ✅ PR merged; website displays "Sterling VanKaujk" |
| ✅ Done | Fix overclaiming language in `luminis-foundation-open` README | Carlos Garcia | Small | Corrected via luminis-foundation/luminis-foundation-open#6 | ✅ PR merged; deployment table updated: simulated dashboard / bench-tested hardware / Rowe on-site prototype planned / Pecos future |
| ✅ Done | Fix 501(c)(3) language in `luminis-foundation-open` README | Carlos Garcia | Small | Corrected via luminis-foundation/luminis-foundation-open#6 | ✅ PR merged; language updated to "applied for recognition under IRC §501(c)(3); determination pending" |
| P2 | Add privacy policy to Foundation website | Carlos Garcia | Small | Best practice; required if any data is collected through the site | Privacy policy page added |
| P2 | Add "Open Research" section linking luminis-foundation-open | Carlos Garcia | Small | Website does not prominently link the open research repo | Section added to index.html |
| P3 | Add Foundation blog or research updates section | Carlos Garcia | Medium | Communicates research progress to funders and community | At least one update published post-Step 3 |

---

## Data

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Write calibration protocol (see Research above) | Carlos Garcia | Medium | No calibration protocol = no valid data | Protocol committed |
| P1 | Write metadata schema | Carlos Garcia | Small | Defined before first data collection | Schema committed |
| P1 | Write data quality SOP | Carlos Garcia | Medium | Defines what counts as a valid reading | SOP committed |
| P2 | Set up local backup for Pi SQLite database | Carlos Garcia | Small | Disk failure risk during deployment | Backup procedure documented and tested |
| P3 | Research Zenodo dataset upload workflow | Carlos Garcia | Small | Needed for Step 4 public dataset release | Zenodo upload procedure documented |

---

## Security

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P1 | Enable GitHub secret scanning on all repos | Carlos Garcia | Small | Prevent accidental credential commits | Secret scanning enabled on foundation, mycosense, luminis-foundation-open |
| P1 | Add log rotation to Pi server | Carlos Garcia | Small | Disk full risk | Log rotation configured |
| P1 | Confirm VITE_PI_TOKEN is not set in Vercel environment | Carlos Garcia | Small | Would embed token in public JS bundle | Vercel environment vars audited; VITE_PI_TOKEN confirmed not set |
| P2 | Add pre-commit secret scanning hook to mycosense | Carlos Garcia | Small | Defense in depth against credential commits | `git-secrets` or similar installed; tested |
| P2 | Implement MQTT signing | Carlos Garcia | Medium | Protects field data integrity | MQTT messages signed; tested in bench environment |
| P2 | Document network segmentation policy for field deployment | Carlos Garcia | Small | Pi must never be internet-routable | Policy documented; tested |

---

## Partnerships

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P2 | Draft MOU template for research collaborations | Carlos Garcia | Small | Partnership agreements needed before Step 5 | Template drafted; reviewed by attorney |
| P2 | Identify university research partners | Carlos Garcia, Lumen | Medium | Peer review and research credibility | ≥ 1 research partner identified; initial contact made |
| P3 | Indigenous community consultation plan | Carlos Garcia | Large | Required before deploying on or near Indigenous land or using TEK | Consultation framework drafted; community contacts identified |

---

## Internal Operations

| Priority | Action | Owner | Effort | Reason | Acceptance Criteria |
|---|---|---|---|---|---|
| P0 | Create private ops + credentials document | Carlos Garcia | Medium | Founder dependency; board needs emergency access | Document created; 2+ board members have access |
| P1 | Create compliance calendar | Carlos Garcia, Adam Kimble | Small | Annual filing deadlines across IRS, NM SOS, NM-COROS | Calendar created with all 2026–2028 deadlines |
| P1 | Update `knowledge-graph/foundation-map.md` after each major event | Carlos Garcia / Viktor | Small (ongoing) | Keeps the institutional map current | Map updated within 1 week of each confirmed milestone |
| P2 | Volunteer contribution agreement template | Carlos Garcia | Small | IP clarity and expectations | Template drafted |
| P2 | Draft annual report template | Guillermo Martin | Small | Needed by 2027 for NM SOS; useful for grant transparency | Template committed to `governance/annual-reports/` |

---

## Best Next Claude Tasks

Ranked by institutional value. Each is scoped, executable, and produces a committed document.

| Rank | Task | Description | Output | Branch |
|---|---|---|---|---|
| 1 | **Write calibration protocol** | Draft `research/protocols/calibration-protocol.md` based on ADS1115/ADS1299 electrode systems; include reference signal, deviation threshold, temperature compensation notes | Protocol document ready for Carlos review | `docs/calibration-protocol` |
| 2 | **Write field data quality SOP** | Draft `research/protocols/field-data-quality-sop.md` based on metadata schema and quality requirements in the research roadmap audit | SOP ready for Step 3 | `docs/field-data-quality-sop` |
| 3 | **Add publication record** | Create `research/publications/2026-zenodo-20143391.md` with full citation, abstract summary, CC-BY license note, and relationship to MycoSense | Publication record committed | `docs/publication-records` |
| 4 | **Draft data management plan** | Create `research/data-management-plan.md` covering: data types, storage, retention, sharing, privacy, Zenodo upload procedure, versioning | DMP ready for grant submissions | `docs/data-management-plan` |
| 5 | ✅ **Fix P0 website + open-repo public-claims errors** | (a) luminis-foundation/luminis-foundation.github.io#4: VP surname VanKuijk → VanKaujk — merged. (b) luminis-foundation/luminis-foundation-open#6: README field deployment and 501(c)(3) language corrected — merged | ✅ Both PRs merged | `fix/vp-surname-vankaujk`, `fix/readme-public-claims` |
| 6 | **Draft board meeting agenda template** | Create a reusable board meeting agenda template in `governance/board-minutes/` covering standard NM nonprofit agenda items | Template committed | `docs/board-meeting-template` |
| 7 | **Write volunteer contribution agreement** | Draft a simple 1-page volunteer contributor agreement covering IP assignment, scope, and Foundation IP | Agreement template committed | `docs/volunteer-agreement` |
| 8 | **Draft hardware specification document** | Create `research/protocols/hardware-spec.md` documenting ESP32-C6/S3 model, ADC board, electrode type, Pi model, power system — all with part numbers | Hardware spec committed | `docs/hardware-spec` |
| 9 | **Write site risk assessment template** | Create `research/protocols/site-risk-assessment.md` for Rowe, NM: temperature ranges, monsoon season, wildlife, enclosure requirements, lightning risk | Template committed; ready for Carlos to fill in | `docs/site-risk-assessment` |
| 10 | **Audit security-hardening repo** | Inspect `luminis-foundation/security-hardening` contents; identify gaps vs. current system; produce a gap analysis document | Gap analysis committed to this repo | `audit/security-hardening-gap` |
| 11 | **Draft annual report template** | Create `governance/annual-reports/annual-report-template.md` based on NM SOS requirements and common funder expectations | Template committed | `docs/annual-report-template` |
| 12 | **Write grant pipeline document** | Research and draft `governance/grants-pipeline.md` with 5–10 grant opportunities: funder, program, amount, deadline, eligibility, alignment | Grant pipeline committed | `docs/grant-pipeline` |

---

## Before Next Grant Application — Pre-Submission Checklist

Complete all items before submitting any grant application. Review with Carlos Garcia and audit with Claude or Lumen before submission.

### P0 — Must be resolved before any application

| Item | Owner | Status |
|---|---|---|
| Fix VP surname in Foundation website (index.html): VanKuijk → VanKaujk | Carlos Garcia | ✅ Done (luminis-foundation/luminis-foundation.github.io#4 merged) |
| Fix field deployment language in luminis-foundation-open README: remove "✅ Building" overclaim | Carlos Garcia | ✅ Done (luminis-foundation/luminis-foundation-open#6 merged) |
| Fix 501(c)(3) language in luminis-foundation-open README: "organized under IRC §501(c)(3)" → "applied for recognition" | Carlos Garcia | ✅ Done (luminis-foundation/luminis-foundation-open#6 merged) |
| Initiate banking (pending / needs board-authorized completion) | Adam Kimble | ⬜ Pending |
| Confirm no EIN committed to any public repo | Carlos Garcia | ⬜ Verify |
| Confirm no Pay.gov receipt, bank/routing/account details in any public repo | Carlos Garcia | ⬜ Verify |
| Confirm 501(c)(3) language is "applied for / pending IRS determination" everywhere public | Carlos Garcia | ⬜ Verify |
| Confirm MycoSense demo is labeled "simulated/mock data" in all public materials | Carlos Garcia | ✅ Done (website + README accurate) |

### P1 — Should be resolved before a significant grant application

| Item | Owner | Status |
|---|---|---|
| Write calibration protocol (`research/protocols/calibration-protocol.md`) | Carlos Garcia | ⬜ Pending |
| Write data management plan | Carlos Garcia | ⬜ Pending |
| Write field data quality SOP | Carlos Garcia | ⬜ Pending |
| Draft redacted bylaws summary for public repo | Carlos Garcia | ⬜ Pending |
| Confirm board minutes are being recorded and stored privately | Guillermo Martin | ⬜ Pending |
| Draft and adopt financial controls policy | Adam Kimble | ⬜ Pending |
| Add publication record to `research/publications/` directory | Carlos Garcia | ⬜ Pending |
| Verify Zenodo preprint author name (VanKaujk vs VanKuijk); request Zenodo correction if needed | Carlos Garcia | ⬜ Pending |

### Private-Records Warning

Do not include or attach the following in any materials committed to a public repo, even as part of a grant application package:

- EIN / Federal Employer Identification Number
- Pay.gov receipt or IRS fee payment confirmation
- Bank account, routing, or payment details
- Private legal PDFs (Certificate of Incorporation, signed bylaws, IRS correspondence)
- Personal home addresses beyond the already-public registered office (133 Frontage Rd 2116, Rowe, NM 87562)
- API keys, tokens, credentials, or secrets of any kind
- Unredacted board minutes containing personal signatures
- Any document not intended for public disclosure

### Grant Readiness Status

| Criterion | Status |
|---|---|
| NM Incorporation | ✅ Complete |
| 501(c)(3) applied | ✅ Filed Jun 9, 2026 |
| 501(c)(3) determination received | ❌ Pending IRS |
| Banking established | ⬜ Pending / needs board-authorized completion |
| Website public-claims accurate | ✅ Done — VP surname corrected via luminis-foundation.github.io#4; README overclaims corrected via luminis-foundation-open#6 |
| Research protocols documented | ❌ Not yet written |
| Data management plan | ❌ Not yet written |
| Field data exists | ❌ Simulated only — Step 3 not yet started |
| Funder-required empirical data | ❌ Step 3 not yet started |
