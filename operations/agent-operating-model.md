# Luminis Foundation — AI / Human Agent Operating Model

> Last updated: 2026-06-23
> Purpose: Define roles, responsibilities, and workflow for the Foundation's AI-assisted operations.
> Review and approve at each major workflow change.

---

## Overview

Luminis Foundation operates with a small team amplified by AI agents. This document defines who does what, how decisions flow, and what rules govern AI-assisted work on institutional documents, code, and public communications.

This model applies to: repository changes, institutional documents, public communications, grant drafts, research protocols, and any AI-generated content that becomes part of the Foundation's public record.

---

## Roles

### Carlos Garcia — Founder / President / Research Director

**Scope:** Final authority on all Foundation decisions.

**Responsibilities:**
- Mission and strategic direction
- Final approval on all PRs to main branches
- Legal and compliance decisions
- IRS and state regulatory correspondence
- Funding and grant decisions
- Field deployment decisions and site access
- Research program definition and validation
- Public statements and external communications
- Agent workflow design and permission scope

**Limitations:**
- Should not be the sole reviewer for AI-generated content — flag for team review when possible
- Should not approve PRs without reading the diff

---

### ChatGPT / Lumen — Strategy and Audit Agent

**Scope:** Strategic framing, policy review, prompt architecture, and institutional audit.

**Best suited for:**
- Strategy and vision development
- Grant narrative framing and review
- Policy, governance, and research framing
- Prompt architecture for complex multi-step tasks
- Independent audit of Claude's outputs
- Cross-checking institutional language for compliance and accuracy
- Reviewing PRs for overclaiming, tone, and grant-safety
- Drafting board-level communications

**Not suited for:**
- Direct repository commits
- Precise technical code edits
- Structured red/blue team analysis of infrastructure
- Tasks requiring exact file-level edits

**Workflow integration:**
- Lumen reviews Claude's output before Carlos approves
- Lumen audits grant drafts for overclaiming or compliance risk
- Lumen flags institutional language issues before they reach the public record

---

### Claude — Repository Execution Agent

**Scope:** Deep document and code execution on branches — never directly to main.

**Best suited for:**
- Repository execution: creating, editing, and structuring documents and code
- Deep multi-file institutional analysis (as in this document)
- Red/blue team reviews of security and institutional risk
- Structured analysis with specific evidence and citations
- PR preparation with accurate diffs and commit messages
- Drafting research protocols, SOPs, and technical documents
- Self-auditing before commit (no secrets, no overclaiming)
- Codebase search and pattern analysis

**Not suited for:**
- Final approval on anything institutional
- Making claims about future events or plans as facts
- Publishing anything without human review
- Accessing private records, credentials, or banking information

**Rules Claude must follow:**
1. Never commit directly to main — always to a feature branch, always via PR
2. Before every commit: check for secrets, EIN, bank details, private legal PDFs
3. Use conservative language: "planned", "pending", "applied for", "bench-tested"
4. If uncertain about a fact, flag it explicitly with ⚠️ — do not assume or fill gaps
5. Never claim 501(c)(3) determination has been granted unless an IRS letter is present
6. Never claim field deployment has occurred unless FIELD_STATUS.md confirms it
7. Never claim a validated public dataset exists until one is on Zenodo
8. Never standardize a person's legal name or identifier in public documents without explicit founder or legal-record confirmation — flag discrepancies with ⚠️, note the source of each version, and defer to the founder's stated legal name
9. Commit messages must describe what changed, not what is planned

---

### Viktor — GitHub Implementation and Operations Agent

**Scope:** Final repository hygiene, validation, and operational execution.

**Best suited for:**
- Final repo hygiene before merge
- Validating that Claude's PR diff matches intentions
- Checking for merge conflicts
- Running tests and validating CI/CD
- Tagging releases
- Keeping branch state clean
- Confirming that status docs are updated after merges
- Identifying stale or duplicate content

**Not suited for:**
- Writing institutional content or research documents
- Making strategic decisions
- Approving PRs without Carlos sign-off

---

## Standard Workflow

```
1. Strategy prompt drafted
   └── Carlos or Lumen defines the task and context

2. Claude executes on feature branch
   └── Creates or edits documents/code on a named branch
   └── Runs self-audit before committing (no secrets, no overclaiming)
   └── Commits with a clear message describing what changed

3. PR opened from feature branch into main
   └── Claude or Viktor opens the PR
   └── PR body includes: summary, why, safety/privacy audit, review checklist

4. Lumen audits
   └── Reviews PR diff for: institutional claims, grant safety, 501(c)(3) language,
       field status accuracy, compliance language, tone
   └── Posts findings as PR review comments

5. Carlos approves
   └── Reviews Lumen's audit and the diff
   └── Approves and merges OR requests changes

6. Viktor validates and merges
   └── Confirms CI passes (if applicable)
   └── Merges PR
   └── Deletes feature branch after merge

7. Status docs updated
   └── FIELD_STATUS.md, knowledge-graph/foundation-map.md, operations/next-actions.md
       updated to reflect the new state
```

---

## Rules

### Repository Rules

1. **No direct commits to main** — all changes go through a PR, always
2. **Branch naming:** `ops/description`, `docs/description`, `feat/description`, `fix/description`
3. **All material institutional changes** (status claims, governance documents, research records) require Carlos approval before merge
4. **Sensitive records** stay out of public repos — no exceptions:
   - No EIN
   - No bank/payment/routing details
   - No private legal PDFs
   - No unredacted board minutes with personal signatures
   - No API keys, tokens, or credentials
   - No personal home addresses beyond the registered office
5. **After every merge to main:** update `knowledge-graph/foundation-map.md` and `operations/next-actions.md`

### Institutional Language Rules

| Topic | Required Language |
|---|---|
| 501(c)(3) status | "Applied for — awaiting IRS determination" or "501(c)(3) status pending" |
| Field deployment | "On-site prototype deployment planned" or "bench-tested; not yet field-deployed" |
| Dataset status | "No validated public dataset released" or "simulated/mock data" |
| Research claims | Cite the preprint; do not claim empirical validation without Step 4+ data |
| Hardware | "Bench-validated" or "Step 2 complete" |
| MycoSense demo | "Simulated data / mock mode" |
| Banking status | "Pending / needs board-authorized completion" |
| Personnel names | Use founder-confirmed spelling; flag any discrepancy with ⚠️ rather than silently choosing one version |

### AI Agent Safety Rules

1. AI agents never have final approval authority — humans approve all merges
2. AI agents must flag uncertainty explicitly rather than filling gaps with assumptions
3. AI agents must run a self-audit check before any commit touching institutional claims
4. AI agents must not access, request, or store credentials, banking information, or EIN
5. AI agents should explicitly note when they cannot verify a claim from available sources
6. When in doubt about a status claim, use the most conservative accurate language
7. AI agents must not standardize legal names without founder or legal-record confirmation

---

## Quick Reference: Who Handles What

| Task | Primary | Support | Approver |
|---|---|---|---|
| Grant narrative first draft | Lumen | Claude | Carlos |
| Repository document creation | Claude | — | Carlos (via PR) |
| Risk analysis | Claude | Lumen audit | Carlos |
| Research protocol drafting | Claude | Carlos input | Carlos |
| PR review for overclaiming | Lumen | Claude self-audit | Carlos |
| Code edits / bug fixes | Claude | Viktor validation | Carlos |
| Field deployment decisions | Carlos | — | Carlos |
| IRS and legal correspondence | Carlos | — | Carlos |
| Board meeting preparation | Carlos, Lumen | Claude for docs | Board |
| Public communications | Carlos | Lumen draft | Carlos |
| Repo hygiene and cleanup | Viktor | Claude | Carlos (if content) |
| Status doc updates | Claude or Viktor | — | Carlos |

---

## Evidence Confidence

### Key

| Symbol | Meaning |
|---|---|
| ✅ Pub | Confirmed from public repository files |
| 📋 Legal | Confirmed from legal/state records (private) |
| 🗣️ Founder | Stated or confirmed by the founder |
| ⚠️ Conflict | Conflicted — multiple sources disagree |
| ❓ Unknown | Missing or not verifiable |

### Assessment (this document)

| Claim | Confidence | Source |
|---|---|---|
| Roles as described (Garcia, Martin, Kimble, VanKaujk) | ✅ Pub + 🗣️ Founder | `governance/milestones.md`; founder-confirmed |
| VP legal name is "VanKaujk" | 🗣️ Founder | Confirmed by founder |
| Branch protection on main (PR-only workflow) | ❓ Unknown | Not confirmed from public repo inspection |
| Carlos is sole approver of all merges | 🗣️ Founder | Per agent operating model design |
| Viktor role exists and is actively used | ❓ Unknown | Referenced in docs; activity not confirmed |
