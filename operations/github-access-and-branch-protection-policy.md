# Luminis Foundation — GitHub Access & Branch Protection Policy

> Status: Draft — pending Board/Research Director confirmation; several items are founder admin actions
> Last updated: 2026-06-29
> Owner: Carlos Garcia (President / Research Director)
> File: operations/github-access-and-branch-protection-policy.md
>
> **This policy defines how access to the Foundation's GitHub organization is granted and how the `main`
> branch is protected.** Items marked **[ADMIN ACTION]** are settings that must be applied in the GitHub
> (or Vercel) dashboard by an org owner — they cannot be set by committing a file. This document records the
> intended configuration and provides the runbooks; it does not itself change any live setting.

---

## Purpose

All repositories under `luminis-foundation` are public (`risk/attack-surface-analysis.md` risk #15). As the
team grows and AI agents make commits (risk #14), the Foundation needs a written access model, a
least-privilege standard, a credential-rotation schedule, and confirmed branch protection so that no single
mistake or compromised account can publish secrets or rewrite institutional history.

---

## 1. Access Matrix (Contributor RBAC)

| Principal | Role | Org/Repo permission | What they can do |
|---|---|---|---|
| Carlos Garcia (President / Research Director) | Org owner | Admin | Full control; manages settings, members, branch protection |
| Adam Kimble (Treasurer) | Org owner (continuity) | Admin (recommended for continuity) | Emergency access; second admin so there is no single point of failure |
| Guillermo Martin (Secretary) | Member | Write on governance docs as needed | Governance record contributions via PR |
| Vetted contributors | Outside collaborator / member | Write on specific repos | Contribute via PR; no admin |
| Research collaborators | Outside collaborator | Read or Write on specific repo only | Project-scoped access per data access agreement |
| AI agents (Claude, etc.) | Automation | Operate via PR only; no admin | Read public content; propose changes via PR; never direct push to `main`; never access private records |
| Public | — | Read (public repos) | View published content only |

Principles:
- **Least privilege** — each principal gets the minimum permission for their function.
- **At least two org owners** — avoids the founder single-point-of-failure (risk #5). Adam Kimble should hold
  admin/owner access for continuity.
- **Access is reviewed at least annually** and whenever a role changes (`governance/compliance-calendar.md`).
- **AI agents are PR-only** and read-only against private data — consistent with
  `operations/agent-operating-model.md` and `research/data-management-security-brainstorm.md` Section 7.

---

## 2. Branch Protection Standard (`main`)

Every Foundation repo's `main` branch should enforce:

- Require a pull request before merging (no direct pushes to `main`).
- Require at least **1 approving review** before merge (human review of AI-authored changes — risk #14).
- Dismiss stale approvals when new commits are pushed.
- Require status checks to pass before merging (where CI exists, e.g. mycosense `ci.yml`).
- Require branches to be up to date before merging.
- Restrict force-pushes and branch deletion on `main`.
- Apply rules to administrators where practical (with a documented break-glass exception for incident
  remediation such as history rewrite after a secret leak).

> The attack-surface analysis notes branch protection as a **current control** for the AI-agent workflow but
> also flags that its enforced state is **not confirmed**. This policy makes confirming it an explicit action.

### [ADMIN ACTION] Confirm/enable branch protection
For each repo (`foundation`, `mycosense`, `luminis-foundation-open`, `luminis-foundation.github.io`):
1. GitHub → repo → **Settings → Branches → Branch protection rules**.
2. Add/confirm a rule for `main` with the settings above.
3. Record the confirmation date and who confirmed it in the table in Section 6.

---

## 3. Secret Scanning & Push Protection

A single committed secret in a public repo is immediately exposed and cached (risk #15). GitHub secret
scanning and push protection are the primary automated defense.

### [ADMIN ACTION] Enable secret scanning + push protection
For each repo:
1. GitHub → repo → **Settings → Code security and analysis**.
2. Enable **Secret scanning** and **Push protection**.
3. (Optional, recommended) Enable **Dependabot alerts** and **Dependabot security updates** for
   dependency-vulnerability coverage (audit P2).
4. Record confirmation in Section 6.

### Pre-commit defense in depth (developer machines)
Install a pre-commit secret scanner on every machine that commits to Foundation repos:
- `gitleaks` (recommended) or `git-secrets`.
- Configure a pre-commit hook that blocks commits containing high-entropy strings, known token formats,
  `.env` contents, EIN patterns, or bank/routing-number patterns.
- Document the setup in `luminis-foundation-open/CONTRIBUTING.md` contributor onboarding.

> Note: the "never commit" list already exists across `README.md`,
> `governance/financial-controls-policy.md` Section 13, and `operations/next-actions.md`. This policy adds the
> *automated* enforcement layer on top of those written rules.

---

## 4. Credential, Token, and Session Management

| Credential | Rotation cadence | On compromise |
|---|---|---|
| GitHub personal access tokens / fine-grained tokens | Expire ≤ 90 days; rotate on expiry | Revoke immediately; see incident plan |
| MycoSense Pi API bearer token (`MYCOSENSE_API_TOKEN`) | Rotate on personnel change or suspected exposure; before each new deployment | Rotate immediately; re-provision nodes |
| MQTT broker credentials | Rotate on personnel change / suspected exposure | Rotate immediately |
| Vercel / hosting tokens | Rotate on personnel change; ≤ 12 months | Revoke and reissue |
| Email / banking / cloud account passwords | MFA required; rotate on suspected exposure | Reset; review account activity |

Rules:
- **MFA required** on GitHub, email, banking, and cloud storage accounts.
- Tokens should be **scoped** (least privilege) and **expiring** — avoid non-expiring tokens.
- Tokens are never committed; `VITE_*` tokens are never set in public builds (see Section 5).
- Credential rotation on exposure is immediate (see `operations/incident-response-plan.md`).

### [ADMIN ACTION] Confirm `VITE_PI_TOKEN` is not set in Vercel
`VITE_*` variables are inlined into the public JS bundle at build time (mycosense `SECURITY.md`;
`.env.example` warning). Setting `VITE_PI_TOKEN` in a public Vercel deployment would expose the Pi bearer
token to anyone who inspects the bundle (risk #7).
1. Vercel → MycoSense project → **Settings → Environment Variables**.
2. Confirm `VITE_PI_TOKEN` is **not** set in any public/preview/production environment.
3. Record confirmation in Section 6.

---

## 5. Repository Hygiene

- `.gitignore` covers `.env` and local secrets in every repo that builds code (confirmed for mycosense).
- No secrets, EIN, bank details, or unredacted personal data in any public repo (cross-ref README "never
  store" list).
- Board minutes with signatures/addresses stay private (`repo-structure.md`).

---

## 6. Confirmation Log (fill in as admin actions are completed)

| Action | Repo / system | Confirmed by | Date | Notes |
|---|---|---|---|---|
| Branch protection on `main` | foundation | ⬜ | | |
| Branch protection on `main` | mycosense | ⬜ | | |
| Branch protection on `main` | luminis-foundation-open | ⬜ | | |
| Branch protection on `main` | luminis-foundation.github.io | ⬜ | | |
| Secret scanning + push protection | all repos | ⬜ | | |
| Pre-commit secret scanner installed | dev machines | ⬜ | | |
| Second org owner (continuity) | org | ⬜ | | Adam Kimble admin access |
| `VITE_PI_TOKEN` confirmed not set | Vercel | ⬜ | | |
| Dependabot alerts enabled | mycosense | ⬜ | | |

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| Admin actions completed | ⬜ See Section 6 |
| Research Director / Board confirmation | ⬜ Pending |

*This document records intended configuration and runbooks. Live settings change only when the
[ADMIN ACTION] steps are performed in the GitHub/Vercel dashboards.*
