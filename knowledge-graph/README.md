# Luminis Foundation — Knowledge Graph

A structured, human-readable map of everything Luminis Foundation is, has built, owns, operates, and intends to build.

## Purpose

The knowledge graph answers:

- **What are we?** Legal entity, mission, board, and legal standing
- **What have we already built?** Repositories, software, hardware, publications
- **What assets exist?** Repos, websites, hardware, data, legal records, grants
- **What is missing?** Gaps in governance, data, protocols, funding, records
- **What can fail?** See `risk/attack-surface-analysis.md`
- **What should we do next?** See `operations/next-actions.md`
- **What research pathway gets us to the first validated dataset?** See `research/research-roadmap-audit.md`
- **What should Claude, Viktor, and ChatGPT each be used for?** See `operations/agent-operating-model.md`

This is not a live database. It is a deliberately maintained institutional map updated after confirmed events only, so that any team member, funder, or AI agent has enough context to act responsibly on behalf of the Foundation.

## Entity Types

| Entity Type | Description | Examples |
|---|---|---|
| **Legal Entity** | Foundation incorporation, registration, and tax status | NM Domestic Nonprofit Corp 0008089293 |
| **Governance** | Board, bylaws, policies, elections, officer roles | Board of Directors, COI Policy |
| **People / Roles** | Named individuals and their organizational roles | Carlos Garcia — President |
| **Projects** | Active and planned technical or research projects | MycoSense |
| **Repositories** | GitHub repos and their purpose and deployment status | luminis-foundation/mycosense |
| **Research Programs** | Scientific research tracks and objectives | Fungal electrophysiology, TinyML edge AI |
| **Publications** | Preprints, papers, DOIs, and citation records | Zenodo 10.5281/zenodo.20143391 |
| **Datasets** | Data collections — actual or planned — with provenance | None released; on-site collection planned |
| **Hardware Assets** | Physical devices, sensors, and field infrastructure | ESP32-C6, Raspberry Pi, electrode arrays |
| **Legal Records** | Incorporation docs, bylaws, IRS filings, state filings | Form 1023-EZ (filed Jun 9, 2026) |
| **Grants** | Applications, awards, funders, amounts, and status | Awesome Foundation $1,000 pending |
| **Public Websites** | External-facing online presences and their status | luminisfoundationresearch.org |
| **Risks** | Institutional, operational, and technical risks | See `risk/attack-surface-analysis.md` |
| **Milestones** | Confirmed past events with dates and evidence | Incorporation Mar 16, 2026 |
| **Next Actions** | Prioritized pending tasks with owners | See `operations/next-actions.md` |

## Relationship Map

```
Luminis Foundation (NM Nonprofit, Entity ID 0008089293)
  │
  ├── governed by ──────────────────────────────────────────────────────────
  │   └── Board of Directors
  │       ├── Carlos Garcia — President / Founder / Research Director
  │       ├── Guillermo Martin — Secretary
  │       ├── Adam Kimble — Treasurer
  │       └── Sterling VanKaujk — Vice President
  │
  ├── holds legal records ────────────────────────────────────────────────
  │   ├── NM Certificate of Incorporation (Mar 16, 2026)
  │   ├── Bylaws (adopted Mar 19, 2026)
  │   ├── Conflict-of-interest policy (adopted Mar 19, 2026)
  │   ├── NM Initial Report (filed May 7, 2026)
  │   └── Form 1023-EZ — 501(c)(3) application (filed Jun 9, 2026, pending)
  │
  ├── owns repositories ────────────────────────────────────────────────
  │   ├── foundation (this repo) — institutional records
  │   ├── mycosense — ecological sensing platform (software + firmware)
  │   ├── luminis-foundation.github.io — public website
  │   ├── luminis-foundation-open — public research & community repo
  │   └── security-hardening — security documentation
  │
  ├── operates projects ─────────────────────────────────────────────────
  │   └── MycoSense — ecological sensing platform
  │       ├── React 18 dashboard — deployed (Vercel, SIMULATED data)
  │       ├── ESP32 firmware — bench-tested, not field-deployed
  │       ├── Raspberry Pi gateway — bench-tested, not field-deployed
  │       ├── Step 3: on-site prototype deployment — PLANNED (Rowe, NM)
  │       ├── Step 4: validated local field dataset — FUTURE
  │       └── Step 5: Pecos watershed deployment + public dataset — FUTURE
  │
  ├── conducts research programs ─────────────────────────────────────
  │   ├── Fungal electrophysiology and mycelial biosensing
  │   ├── Mycelium-inspired decentralized AI architectures
  │   ├── TinyML and edge-deployed sensor networks
  │   ├── Privacy-preserving federated learning
  │   └── Bio-hybrid plant–fungal–AI systems
  │
  ├── holds publications ────────────────────────────────────────────────
  │   └── Zenodo preprint (2026) — DOI: 10.5281/zenodo.20143391
  │       Authors: Garcia C., Kimble A., Martin G., VanKaujk S.
  │       License: CC-BY-4.0
  │
  ├── applied for grants ──────────────────────────────────────────────
  │   └── Awesome Foundation — Conservation & Climate
  │       Amount: $1,000 | Status: Pending | Submitted: Jun 10, 2026
  │
  └── operates public websites ────────────────────────────────────────
      ├── luminisfoundationresearch.org — Foundation website (live)
      └── mycosense.vercel.app — MycoSense demo (live, SIMULATED data)
```

> **⚠️ P0 Data Quality Issue — VP Surname:**
> The Foundation website source (`luminis-foundation.github.io/index.html`) lists the Vice President as "Sterling VanKuijk." The correct legal name, confirmed by the founder, is **"Sterling VanKaujk."** This is an error in the live public website requiring a separate PR to the `luminis-foundation.github.io` repository. All documents in this repo use the confirmed spelling "VanKaujk." The Zenodo preprint author list should also be verified; if it was submitted as "VanKuijk," a Zenodo metadata correction request is needed.

## Files in This Directory

| File | Purpose |
|---|---|
| `README.md` | This file — entity types, relationships, and map overview |
| `foundation-map.md` | Full entity-by-entity map with status, evidence, owner, and next action |

## Update Protocol

1. Update after confirmed events only — not after plans or intentions
2. Do not include private legal PDFs, EIN, bank details, or payment records
3. Review before every grant submission and IRS correspondence
4. Assign an owner to every open next action
5. Date every status change
6. Do not standardize a person's legal name or identifier without explicit founder or legal-record confirmation — flag discrepancies with ⚠️ and note the source of each version
