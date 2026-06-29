# Luminis Foundation — Data Security Policy

> Status: Draft — pending Board review and adoption
> Last updated: 2026-06-29
> Author: Carlos Garcia, President / Founder / Research Director
> File: research/data-security-policy.md
> Companions: `research/data-management-plan.md`, `research/data-management-security-brainstorm.md`,
> `operations/github-access-and-branch-protection-policy.md`, `operations/incident-response-plan.md`
>
> **This is a draft policy.** It is the formal Data Security Policy called for in the brainstorm (Section 16),
> consolidating the brainstorm's Section 10 security rules. Not operative until adopted by the Board.

---

## Guiding Principle

> **Private by default. Public by proof.** Security controls exist to keep restricted data restricted until it
> is validated, sanitized, reviewed, and approved for release.

---

## 1. Purpose and Scope

This policy defines the security requirements protecting all Foundation data — encryption, access control,
credential management, and network security — across the research archive, the MycoSense system, and the
Foundation's repositories and accounts. It complements the Data Management Plan (which governs lifecycle and
release) and the GitHub Access & Branch Protection Policy (which governs repository access).

---

## 2. Core Security Rules

From the brainstorm Section 10 (consolidated and made normative):

- **No secrets in GitHub** — API keys, tokens, credentials, private keys.
- **No `.env` files** in public repos.
- **No `VITE_*` tokens** (e.g., `VITE_PI_TOKEN`) in public/Vercel builds — they are inlined into the public
  JS bundle (`mycosense/.env.example`, `mycosense/SECURITY.md`).
- **No** routing/account/card numbers in any repo.
- **No** unredacted legal/payment PDFs in public repos.
- **Pi gateway stays LAN-only** unless a future secure architecture is approved by the Research Director.
- **MQTT credentials are private** and never appear in public code or docs.
- **Credentials rotate immediately if exposed** (`operations/incident-response-plan.md`).
- **MFA** on GitHub, email, banking, and cloud storage.
- **≥ 2 authorized officers** have emergency access to private records (continuity — risk #5).
- **GitHub secret scanning** enabled on all repos; **pre-commit secret scanner** on dev machines
  (`operations/github-access-and-branch-protection-policy.md`).
- **Vercel env vars audited** to confirm no secrets are embedded in public builds.

---

## 3. Encryption

| Where | Requirement |
|---|---|
| Raw/private data at rest | Encrypted external drives (LUKS / BitLocker / FileVault) |
| Private cloud (if/when Board-approved) | Encryption + MFA + audit logs (founder answers Q5) |
| Data in transit (Pi ↔ dashboard) | Bearer-token auth today; **TLS is a known gap** for field deployment (Section 6) |
| Data in transit (ESP32 ↔ Pi MQTT) | Username/password auth today; **TLS + signing are known gaps** (Section 6) |
| Backups | Encrypted; integrity-verified with SHA-256 manifests |

---

## 4. Access Control

- **Least privilege**, role-based (see access matrix in `research/data-management-plan.md` Section 4 and
  `operations/github-access-and-branch-protection-policy.md`).
- Access reviewed at least annually or on role change (`governance/compliance-calendar.md`).
- External collaborators receive only project-scoped data under a data access agreement; never exact node
  locations or unrestricted raw archives unless explicitly approved.
- AI agents/automation: read-only on public content; no access to raw private data.

---

## 5. Credential and Secret Management

- Tokens are scoped and expiring; rotation cadence per
  `operations/github-access-and-branch-protection-policy.md` Section 4.
- Pi `MYCOSENSE_API_TOKEN` and MQTT credentials are stored in environment files / ESP32 NVS — never in source
  (`mycosense/SECURITY.md`, `mycosense/docs/FIELD_DEPLOYMENT_SECURITY.md`).
- Generated with strong randomness (e.g., `python3 -c "import secrets; print(secrets.token_hex(32))"`).
- Exposure triggers immediate rotation and an incident record.

---

## 6. Network Security (MycoSense)

Current controls (from `mycosense/SECURITY.md` and `pi-server/main.py`):

- Pi server binds to its **LAN interface IP**, not `0.0.0.0`; **never internet-routable**.
- All Pi endpoints require a **bearer token**; CORS restricted to an explicit origin list.
- Batch size capped (200 readings/POST); query rows capped (5,000).
- ESP32 nodes use a LAN hotspot only; MQTT requires username/password; NTP sync required before timestamps
  are trusted.
- CSP and security headers set in `mycosense/vercel.json`.

**Known gaps to close before field deployment** (tracked in `mycosense/FIELD_STATUS.md`,
`risk/attack-surface-analysis.md` #9, and `operations/next-actions.md`):

| Gap | Risk | Planned control |
|---|---|---|
| Pi server has no TLS | Cleartext tokens if accidentally exposed | Add TLS for field deployment |
| MQTT messages not signed | LAN device can inject fake readings | MQTT signing |
| No MQTT replay protection | Replayed readings | Replay protection / nonces |
| No Pi log rotation | Disk-full during long deployment | Configure log rotation |
| No documented network segmentation | Pi could be misrouted | Network segmentation policy (Pi never internet-routable) |

These are **Phase 2 field-hardening** items; the bench/pre-field posture relies on the trusted-LAN perimeter.

---

## 7. Monitoring and Audit

- PR history + commit records + SHA-256 dataset manifests form the audit trail
  (`research/data-management-security-brainstorm.md` Section 9).
- Restricted data maintains an access log where practical.
- Incidents handled per `operations/incident-response-plan.md`.

---

## 8. Review

Reviewed by the Board at least annually (`governance/compliance-calendar.md`) and whenever the system's
architecture or network exposure changes (e.g., before Step 3 field deployment).

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| Board review | ⬜ Pending |
| Board adoption date | ⬜ Not yet adopted |
| Effective date | ⬜ Upon Board adoption |

*Not operative until adopted. Network-security gaps in Section 6 must be closed before field deployment.*
