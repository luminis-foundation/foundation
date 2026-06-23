# Luminis Foundation — Institutional Attack Surface Analysis

> Last updated: 2026-06-23
> Maintained by: Carlos Garcia (President) / reviewed by Board
> This document covers institutional, operational, legal, and technical risks — not only cybersecurity.
> Review before major grant submissions, public announcements, and board meetings.

---

## Top 10 Risks to Address First

| Rank | Risk | Likelihood | Impact | Category |
|---|---|---|---|---|
| 1 | **Founder single point of failure** | High | Critical | Governance / Operations |
| 2 | **501(c)(3) application denial or delay** | Medium | High | Legal / Compliance |
| 3 | **Financial controls policy pending Board adoption** | Medium | High | Finance / Operations |
| 4 | **Scientific overclaiming** | Low | High | Public Communications / Legal |
| 5 | **No field calibration or data quality protocol** | High | High | Research / Data |
| 6 | **Pi server exposed to internet accidentally** | Low | Critical | Security |
| 7 | **VITE_PI_TOKEN embedded in public Vercel bundle** | Medium | High | Security |
| 8 | **Governance documentation gaps** | High | Medium | Governance |
| 9 | **No financial controls policy adopted** | Medium | Medium | Finance / Compliance |
| 10 | **AI agent commits sensitive data or overclaims status** | Medium | High | AI Workflow / Compliance |

---

## 1. Legal / Compliance Risk

**Description:**
The Foundation is a new legal entity (formed March 16, 2026) with several compliance obligations not yet completed: NM-COROS charitable registration, financial controls policy adoption (draft at `governance/financial-controls-policy.md`; pending Board review), annual reporting to NM SOS, and future IRS 990 filings. The 501(c)(3) application (Form 1023-EZ) is pending. Banking has been established.

| Attribute | Value |
|---|---|
| Likelihood | High (multiple open items) |
| Impact | High (compliance failure, funder rejection, IRS jeopardy) |
| Current controls | Form 1023-EZ filed; NM SOS Initial Report filed; NM Entity in good standing; banking established |
| Missing controls | Financial controls policy (draft at `governance/financial-controls-policy.md`, pending Board adoption); NM-COROS registration; board minutes |
| Mitigation | Adopt financial controls policy; file NM-COROS after IRS determination; document all compliance deadlines |
| Owner | Carlos Garcia, Adam Kimble |
| Next action | ✅ Banking established; adopt financial controls policy (see `governance/financial-controls-policy.md`); create compliance calendar with all annual deadlines |

---

## 2. 501(c)(3) Status Risk

**Description:**
The Foundation filed Form 1023-EZ (the simplified exemption application) on June 9, 2026. The IRS may request additional information, require Form 1023 (full), or deny the application. Until the IRS determination letter arrives, the Foundation cannot represent itself as a tax-exempt 501(c)(3) organization, which limits grant eligibility with most institutional funders. Form 1023-EZ has a meaningful denial/request-for-information rate because it requires fewer supporting documents and relies on attestations.

| Attribute | Value |
|---|---|
| Likelihood | Medium (most 1023-EZ applications are approved, but some are delayed or questioned) |
| Impact | High (blocks institutional grants, donor tax deductibility, and NM-COROS registration) |
| Current controls | Application filed; $275 fee paid; activities clearly aligned with scientific/educational purpose |
| Missing controls | No backup plan if IRS requests Form 1023 (full) or additional information |
| Mitigation | Monitor IRS correspondence; ensure activities match stated charitable purpose; do not take on unrelated business income; consult nonprofit attorney if IRS responds with questions |
| Owner | Carlos Garcia |
| Next action | Track IRS correspondence; prepare for possible IRS questions about private benefit and research methodology |

---

## 3. Governance Risk

**Description:**
The Foundation has a 4-person board with no documented meeting cadence, no board minutes in the repository, no independent directors, and no written succession or vacancy procedures visible in public records. Small boards with no quorum safeguards and no minutes trail are a governance red flag for funders and the IRS.

| Attribute | Value |
|---|---|
| Likelihood | High (no minutes documented, no cadence visible) |
| Impact | Medium (grant denial, IRS compliance issue, internal conflict without process) |
| Current controls | Bylaws adopted (Mar 19, 2026); COI policy adopted |
| Missing controls | Meeting minutes; annual meeting cadence; financial oversight procedures; independent director(s) |
| Mitigation | Hold quarterly board meetings; document minutes privately; store offline or in private repo; add at least one independent director when possible |
| Owner | Guillermo Martin (Secretary) |
| Next action | Confirm signed organizational meeting minutes are retained as a private record; create a public-safe index or template if desired; schedule Q3 2026 board meeting; draft financial oversight procedures |

---

## 4. Board Continuity Risk

**Description:**
If any board member becomes unavailable, the Foundation's governance continuity is at risk. Currently there is no documented vacancy procedure, no succession plan, and no documented reserve officer list. A 4-member board losing one member could create a quorum problem depending on the bylaws.

| Attribute | Value |
|---|---|
| Likelihood | Medium (life events, relocation, workload changes) |
| Impact | High (governance paralysis; IRS compliance questions; grant disruption) |
| Current controls | Bylaws exist (content not public); 4-member board |
| Missing controls | Succession plan; vacancy procedures visible to board; officer backup contacts |
| Mitigation | Review bylaws vacancy procedures; add board member(s) as buffer; document succession line for President role |
| Owner | Carlos Garcia, Guillermo Martin |
| Next action | Review bylaws for quorum and vacancy language; determine if board should expand to 5–7 members |

---

## 5. Founder Dependency Risk

**Description:**
Carlos Garcia is simultaneously President, Founder, Research Director, primary technical contact, and primary public representative. The MycoSense platform, research program, grant relationships, and IRS filing are all anchored to one person. If Carlos becomes unavailable for any reason, most Foundation activities would stall.

| Attribute | Value |
|---|---|
| Likelihood | Low–Medium (personal risk is inherent) |
| Impact | Critical (research, operations, and legal compliance all affected) |
| Current controls | 3 other board members with assigned roles |
| Missing controls | Technical documentation sufficient for handoff; research protocol documentation; key contacts list; credential escrow |
| Mitigation | Document all passwords and credentials in a secure escrow (not a public repo); create a Foundation operations manual; ensure at least one other board member has access to all accounts |
| Owner | Carlos Garcia + Board |
| Next action | Create a private "Foundation Operations & Credentials" document accessible to Board; ensure Adam Kimble has access to banking |

---

## 6. Scientific Overclaiming Risk

**Description:**
Identified public document risks; two primary overclaims addressed via follow-up PRs:
- ✅ `luminis-foundation-open` README field deployment and 501(c)(3) language: corrected via luminis-foundation/luminis-foundation-open#6
- ✅ Website (index.html) VP surname "VanKuijk" → "VanKaujk": corrected via luminis-foundation/luminis-foundation.github.io#4

Remaining risks:
- The Vercel demo could be mistaken for real sensor data if disclaimers are missed.
- The preprint on Zenodo is a synthesis/theoretical paper, not an empirical field study — this distinction matters to scientific funders.
- Zenodo preprint author name: concern reviewed 2026-06-23; current known author is Carlos Garcia; monitor if discrepancy is found.

| Attribute | Value |
|---|---|
| Likelihood | Low (primary overclaims corrected; Zenodo concern reviewed) |
| Impact | High (IRS scrutiny, funder loss of trust, reputational damage, potential misrepresentation) |
| Current controls | Website uses accurate 501(c)(3) language; MycoSense README correctly labels demo as simulated; FIELD_STATUS.md is accurate; luminis-foundation-open README corrected via PR #6 |
| Missing controls | Consistent language across all public repos; no single source of truth for approved status claims |
| Mitigation | Primary overclaims corrected via follow-up PRs; use knowledge-graph/foundation-map.md as the approved status reference for all future claims; audit remaining repos for status claims before next grant submission |
| Owner | Carlos Garcia |
| Next action | (✅ Done) Website VP surname corrected; (✅ Done) luminis-foundation-open README corrected; (P2) confirm Zenodo author record; audit remaining repos before next grant submission |

---

## 7. Hardware Deployment Risk

**Description:**
The Step 3 on-site prototype deployment at Rowe, NM has multiple unvalidated requirements: solar/battery power runtime, weatherproofing, GPS position logging, MQTT TLS, OTA firmware updates, and continuous unattended outdoor operation. Moving to Step 3 without addressing these creates data quality and device reliability risks.

| Attribute | Value |
|---|---|
| Likelihood | High (all listed items are confirmed gaps in FIELD_STATUS.md) |
| Impact | Medium (failed prototype; lost data; hardware damage; delayed research) |
| Current controls | FIELD_STATUS.md clearly tracks what is and isn't validated; security docs in `docs/` |
| Missing controls | Pre-deployment checklist completion; weatherproofing validation; solar runtime test |
| Mitigation | Complete pre-deployment checklist in `docs/FIELD_DEPLOYMENT_SECURITY.md` before Step 3; add solar runtime test; document enclosure specifications |
| Owner | Carlos Garcia |
| Next action | Set Step 3 deployment date; complete pre-deployment checklist; document enclosure specs and solar configuration |

---

## 8. Data Quality Risk

**Description:**
No real field data exists yet. When it does, data quality risks include: uncalibrated sensors producing invalid readings, missing timestamps (NTP sync failure), metadata gaps (no GPS coordinates, no site conditions), and no defined acceptance criteria for a "valid" reading. Without a data quality protocol, the first field dataset will not be publishable.

| Attribute | Value |
|---|---|
| Likelihood | High (no final protocol yet defined) |
| Impact | High (unpublishable data; wasted field effort; grant deliverable failure) |
| Current controls | CalibrationPanel.jsx exists in dashboard; provenanceHash.js implemented for provenance anchoring; calibration framework and data quality SOP framework committed |
| Missing controls | Final calibration thresholds (funding-dependent); final field data quality thresholds (funding-dependent); metadata schema; QC review process |
| Mitigation | Review calibration framework and SOP framework before Step 3; define minimum metadata requirements; final thresholds derived from pilot data after funding |
| Owner | Carlos Garcia |
| Next action | Carlos reviews `research/protocols/calibration-protocol-framework.md` and `research/protocols/field-data-quality-sop-framework.md`; confirm equipment list and metadata requirements |

---

## 9. Security / Privacy Risk

**Description:**
Known technical security limitations documented in SECURITY.md and FIELD_DEPLOYMENT_SECURITY.md:
- Pi server has no TLS — suitable for trusted LAN only; bearer token authentication is present but tokens transmit in cleartext if the server is accidentally port-forwarded
- MQTT messages are not signed — LAN devices can inject fake readings
- No replay protection on MQTT
- `VITE_PI_TOKEN` embedded in browser bundle at Vercel build time if ever set — token visible in public JS
- No log rotation on Pi — disk full risk during long deployment

| Attribute | Value |
|---|---|
| Likelihood | Low (current bench-only deployment; no internet exposure) / Medium (increases with field deployment) |
| Impact | High (data integrity; unauthorized control of field devices; token exposure) |
| Current controls | Pi server binds to LAN IP only; bearer token authentication; CORS restricted; CSP in Vercel; no secrets in repos |
| Missing controls | MQTT signing; replay protection; TLS for Pi server; log rotation; network segmentation policy |
| Mitigation | Address Phase 2 security hardening before Step 3 field deployment; never set VITE_PI_TOKEN in Vercel environment; implement log rotation on Pi |
| Owner | Carlos Garcia |
| Next action | Review `docs/FIELD_DEPLOYMENT_SECURITY.md` and complete Phase 2 hardening checklist before Step 3 |

---

## 10. Funding Risk

**Description:**
The Foundation has one pending grant ($1,000 microgrant) and no other funding pipeline, no earned revenue, and no documented operating budget. Banking has been established. Without 501(c)(3) determination, most institutional grants are inaccessible.

| Attribute | Value |
|---|---|
| Likelihood | High (single grant, no pipeline) |
| Impact | High (operations stall; research halted; personnel can't be compensated) |
| Current controls | Operations currently run on founder's time; low overhead; banking established |
| Missing controls | Operating budget; financial controls policy adoption; grant strategy; donor cultivation; 501(c)(3) determination |
| Mitigation | Banking established; adopt financial controls policy; await 501(c)(3) determination; develop a 12-month grant pipeline targeting environmental/tech foundations; document operating expenses |
| Owner | Adam Kimble, Carlos Garcia |
| Next action | Adopt financial controls policy; draft 12-month operating budget; identify 5 grant opportunities for next cycle |

---

## 11. Public Communications Risk

**Description:**
Inconsistent or inaccurate public statements about the Foundation's status — 501(c)(3) approval, field deployment completeness, data validity, or research maturity — carry reputational and legal risk. Public statements appear across a website, 4 GitHub repos, a published preprint, and AI-generated content. Two confirmed errors have been corrected via follow-up PRs: website VP surname (luminis-foundation/luminis-foundation.github.io#4) and luminis-foundation-open README overclaims (luminis-foundation/luminis-foundation-open#6). Remaining risk: Zenodo preprint author record reviewed; no correction currently needed.

| Attribute | Value |
|---|---|
| Likelihood | Low–Medium (primary inconsistencies corrected; ongoing risk from future edits) |
| Impact | High (IRS scrutiny; funder distrust; reputational damage) |
| Current controls | Website and MycoSense README use accurate language; FIELD_STATUS.md is authoritative; luminis-foundation-open README corrected via PR #6 |
| Missing controls | Consistent language policy across all repos; single approved status statement |
| Mitigation | VP surname and README overclaims corrected via follow-up PRs; adopt a "Public Status Language Standard"; audit all repos before each grant submission |
| Owner | Carlos Garcia |
| Next action | Confirm Zenodo author record (P2); create a status language reference doc; enable quarterly repo audits before grant submissions |

---

## 12. Partnership Risk

**Description:**
The Foundation currently has no formal partnership agreements, MOUs, or collaboration agreements documented in public or private records. Future field deployment may require land access agreements, university research partnerships, or Indigenous community agreements that carry their own obligations.

| Attribute | Value |
|---|---|
| Likelihood | Low now / Medium at Step 3+ |
| Impact | Medium (blocked field access; unmet expectations; relationship damage) |
| Current controls | No active partnerships requiring formal agreements yet |
| Missing controls | MOU templates; partnership review process; land access agreements |
| Mitigation | Draft MOU template; identify land ownership for Rowe, NM site; establish partnership review process before Step 3 |
| Owner | Carlos Garcia |
| Next action | Confirm land access for Step 3 deployment site; draft a simple land access agreement |

---

## 13. Volunteer / Contractor Execution Risk

**Description:**
The Foundation currently operates with a small volunteer team. Volunteers may have competing obligations, variable availability, and unclear scope. Without written agreements, deliverable definitions, or IP assignment, contributions may be disputed or may not meet research quality standards.

| Attribute | Value |
|---|---|
| Likelihood | Medium |
| Impact | Medium (missed deliverables; IP disputes; governance friction) |
| Current controls | CODE_OF_CONDUCT.md in luminis-foundation-open; CONTRIBUTING.md |
| Missing controls | Volunteer agreements; IP assignment policy; clear deliverable definitions |
| Mitigation | Draft a simple volunteer/contributor agreement; clarify IP assignment for all contributions; document contribution scope for each participant |
| Owner | Carlos Garcia |
| Next action | Draft volunteer contribution agreement; add IP assignment clause |

---

## 14. AI Agent Workflow Risk

**Description:**
AI agents (Claude, ChatGPT/Lumen) are actively used for repository execution, documentation, and institutional analysis. Risks include: agents committing sensitive data to public repos; agents generating inaccurate institutional claims; agents pushing directly to main; agents hallucinating grant amounts, legal status, or deployment facts.

| Attribute | Value |
|---|---|
| Likelihood | Medium (active and growing use of AI agents) |
| Impact | High (false records committed; sensitive data exposed; institutional credibility damaged) |
| Current controls | Branch protection (PRs to main); task instructions include safety rules; audit pass before commit |
| Missing controls | Formal AI agent operating policy; human review before every merge; sensitive data checklist |
| Mitigation | Enforce PR-only workflow (no direct main commits); require human review for all AI-generated institutional documents; use operations/agent-operating-model.md as the policy reference |
| Owner | Carlos Garcia, Viktor |
| Next action | Enforce branch protection on main in all repos; ensure all AI-authored changes go through PR review |

---

## 15. Repository / Public Record Exposure Risk

**Description:**
All repos under `luminis-foundation` are public. A single accidental commit of a private legal PDF, EIN, banking credential, API key, or personal data would be immediately visible and cached by GitHub, web crawlers, and third-party services. Git history makes deletion insufficient without a full history rewrite.

| Attribute | Value |
|---|---|
| Likelihood | Low–Medium (risk increases as team grows and AI agents are used for commits) |
| Impact | High (IRS record exposure; identity theft risk; credential compromise) |
| Current controls | .gitignore in mycosense covers .env; SECURITY.md warns against committing secrets; AI task instructions include safety rules |
| Missing controls | Pre-commit secret scanning hook; org-level secret scanning; contributor onboarding checklist |
| Mitigation | Enable GitHub secret scanning on all repos; add a pre-commit hook; create a contributor onboarding guide with explicit "never commit" list |
| Owner | Carlos Garcia |
| Next action | Enable GitHub secret scanning; add `git-secrets` or similar to mycosense pre-commit; document the "never commit" list in CONTRIBUTING.md |

---

## 16. Environmental / Field Site Risk

**Description:**
The planned Step 3 deployment is at the Foundation's office site in Rowe, NM — a high-desert environment with temperature extremes, monsoon season flooding risk, wildlife interference, and seasonal access limitations. Outdoor electronics without proper enclosures and power management will fail.

| Attribute | Value |
|---|---|
| Likelihood | High (climate and wildlife factors are predictable; hardware is not yet hardened) |
| Impact | Medium (hardware loss; data loss; delayed research; safety if improper electrical installation) |
| Current controls | FIELD_STATUS.md tracks unvalidated items; pre-deployment checklist in docs/ |
| Missing controls | Enclosure IP rating specification; lightning protection plan; wildlife interference assessment; monsoon season plan |
| Mitigation | Specify enclosure IP rating (IP65 minimum); plan for monsoon season timing; assess rodent/bird interference; install lightning protection |
| Owner | Carlos Garcia |
| Next action | Draft site risk assessment for Rowe, NM; specify enclosure requirements; plan seasonal deployment windows |

---

## Risk Matrix Summary

| # | Risk Category | Likelihood | Impact | Priority |
|---|---|---|---|---|
| 1 | Legal / Compliance | High | High | P0 |
| 2 | 501(c)(3) Status | Medium | High | P0 |
| 3 | Governance | High | Medium | P1 |
| 4 | Board Continuity | Medium | High | P1 |
| 5 | Founder Dependency | Medium | Critical | P0 |
| 6 | Scientific Overclaiming | Low | High | P1 |
| 7 | Hardware Deployment | High | Medium | P1 |
| 8 | Data Quality | High | High | P1 |
| 9 | Security / Privacy | Low–Med | High | P1 |
| 10 | Funding | High | High | P0 |
| 11 | Public Communications | Low–Med | High | P1 |
| 12 | Partnership | Low–Med | Medium | P2 |
| 13 | Volunteer / Contractor | Medium | Medium | P2 |
| 14 | AI Agent Workflow | Medium | High | P1 |
| 15 | Repository Exposure | Low–Med | High | P1 |
| 16 | Environmental / Field Site | High | Medium | P1 |

---

## Evidence Confidence

### Key

| Symbol | Meaning |
|---|---|
| ✅ Pub | Confirmed from public repository files |
| 📋 Legal | Confirmed from legal/state records (private) |
| 🗣️ Founder | Stated or confirmed by the founder |
| ⚠️ Conflict | Conflicted — multiple sources give different information |
| ❓ Unknown | Missing or not verifiable from available public sources |

### Assessment

| Risk Claim | Confidence | Source |
|---|---|---|
| NM incorporation complete; entity in good standing | ✅ Pub | `governance/mission.md`, `governance/milestones.md` |
| 501(c)(3) applied for; determination pending | ✅ Pub | `governance/milestones.md`; website |
| Banking established | 🗣️ Founder | Confirmed by founder 2026-06-23; account details private |
| VP legal name is "VanKaujk" | ✅ Pub + 🗣️ Founder | Confirmed by founder; website corrected via luminis-foundation/luminis-foundation.github.io#4 |
| Website VP surname corrected to "VanKaujk" | ✅ Pub | luminis-foundation/luminis-foundation.github.io#4 merged |
| luminis-foundation-open README overclaims corrected | ✅ Pub | luminis-foundation/luminis-foundation-open#6 merged |
| Zenodo author concern reviewed | 🗣️ Founder | Current known author: Carlos Garcia; no correction needed unless Zenodo metadata shows discrepancy |
| VITE_PI_TOKEN risk (not currently set in Vercel) | ❓ Unknown | Risk is documented in SECURITY.md; current Vercel env var state unconfirmed |
| No validated public field dataset | ✅ Pub | `research/datasets/` empty; `mycosense/FIELD_STATUS.md` |
| No board minutes in public repo | ✅ Pub | `governance/board-minutes/` empty in this repo |
| No financial controls policy adopted | ✅ Pub | Draft at `governance/financial-controls-policy.md`; not yet Board-adopted |
