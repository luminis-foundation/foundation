# Luminis Foundation — Institutional Repository

Institutional records for Luminis Foundation, a New Mexico domestic nonprofit corporation organized for scientific research, education, and public-benefit technological development.

## What This Repository Is For

This is the Foundation's internal institutional record — governance documents, research records, and operational documentation. It is a public repository; private records (legal PDFs, financial records, EIN, banking details) are not stored here.

## Directory Structure

```
foundation/
├── governance/          # Mission, milestones, roadmap, grants, board records, compliance calendar, policies
├── research/            # Publications, dataset records, field protocols, data management & security policies
├── knowledge-graph/     # Institutional map — entities, relationships, status
├── risk/                # Institutional attack surface analysis
├── operations/          # Agent operating model, next actions, access/DR/incident-response policies
├── docs/                # ADRs, architecture diagrams, accessibility checklist
├── README.md            # This file
└── repo-structure.md    # GitHub organization structure decision record
```

## What Is Intentionally Not Stored Here

- Private legal PDFs (Certificate of Incorporation originals, IRS correspondence, signed bylaws)
- EIN / Federal Employer Identification Number
- Banking, payment, or financial account details
- Board minutes containing personal signatures or home addresses beyond the registered office
- API keys, credentials, tokens, or secrets of any kind
- Unredacted personal data of board members, contractors, or collaborators

## Related Repositories

| Repository | Purpose |
|---|---|
| `luminis-foundation/mycosense` | MycoSense ecological sensing platform (dashboard + firmware + Pi gateway) |
| `luminis-foundation/luminis-foundation-open` | Public open research and community repository |
| `luminis-foundation/luminis-foundation.github.io` | Foundation public website source |
| `luminis-foundation/security-hardening` | Security documentation and hardening records |

## Key Documents

| Document | Description |
|---|---|
| `knowledge-graph/foundation-map.md` | Complete institutional entity map with status and next actions |
| `risk/attack-surface-analysis.md` | Institutional risk analysis across 16 categories with Top 10 |
| `research/research-roadmap-audit.md` | Path from current state to first validated dataset |
| `operations/agent-operating-model.md` | AI/human workflow and role definitions |
| `operations/next-actions.md` | Prioritized action backlog with Claude-ready tasks |
| `governance/milestones.md` | Confirmed institutional milestones with dates and evidence |
| `governance/grants.md` | Grant applications and awards |
| `governance/mission.md` | Legal mission statement and entity details |
| `governance/roadmap.md` | Forward-looking strategic priorities (Board draft) |
| `governance/financial-controls-policy.md` | Financial controls policy draft (pending Board adoption) |
| `governance/board-adoption-records/financial-controls-adoption-template.md` | Board adoption-record template (makes draft policies operative) |
| `governance/compliance-calendar.md` | Recurring legal/financial/governance obligations (draft) |
| `governance/privacy-retention-deletion-policy.md` | Privacy/PII retention & deletion policy + GDPR/HIPAA memo (draft) |
| `operations/github-access-and-branch-protection-policy.md` | Access matrix, branch protection, secret-scanning runbooks (draft) |
| `operations/disaster-recovery-rto-rpo.md` | RTO/RPO targets and disaster recovery runbooks (draft) |
| `operations/incident-response-plan.md` | Incident severity tiers, notification chain, playbooks (draft) |
| `research/data-management-plan.md` | Formal Data Management Plan (draft, pending Board adoption) |
| `research/data-security-policy.md` | Formal Data Security Policy (draft, pending Board adoption) |
| `research/protocols/calibration-protocol-framework.md` | Calibration planning framework (funding-dependent) |
| `research/protocols/field-data-quality-sop-framework.md` | Field data quality planning framework (funding-dependent) |
| `research/data-management-security-brainstorm.md` | Data management and security design brainstorm |
| `docs/adr/` | Architecture Decision Records (public/private boundary, local-first data) |
| `docs/architecture/mycosense-system-architecture.md` | MycoSense system architecture, data path, and trust boundaries |
| `docs/accessibility-checklist.md` | WCAG 2.1 AA checklist for website and dashboard (draft) |

## Foundation Status at a Glance

| Item | Status |
|---|---|
| NM Incorporation | Complete — Entity ID 0008089293, formed March 16, 2026 |
| 501(c)(3) Application | Filed — awaiting IRS determination (Form 1023-EZ, filed June 9, 2026) |
| Foundational Paper | Published — DOI: [10.5281/zenodo.20143391](https://doi.org/10.5281/zenodo.20143391) |
| MycoSense Dashboard | Live at mycosense.vercel.app (simulated/mock data) |
| MycoSense Hardware | Bench-tested — ESP32 + Pi end-to-end validated on bench |
| On-Site Prototype Deployment | Planned — Foundation office site, Rowe, NM |
| Grants | 1 pending — Awesome Foundation Conservation & Climate, $1,000 |
| Banking | Banking established — board-authorized institutional bank account opened. Account details are retained privately by authorized officers. |
| Financial Controls Policy | Draft created — pending Board review and formal adoption |
| Field Dataset | None — planned after Step 3 on-site prototype validation |

## Public Websites

- Foundation: [luminisfoundationresearch.org](https://luminisfoundationresearch.org)
- MycoSense demo: [mycosense.vercel.app](https://mycosense.vercel.app) (simulated data)
