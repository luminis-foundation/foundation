# Luminis Foundation — Incident Response Plan

> Status: Draft — pending Board/Research Director review and adoption
> Last updated: 2026-06-29
> Owner: Carlos Garcia (President / Research Director)
> File: operations/incident-response-plan.md
>
> **This is a draft plan.** It formalizes and consolidates the incident scenarios first drafted in
> `research/data-management-security-brainstorm.md` Section 13 into a standalone operational runbook with
> severity tiers, a notification chain, and a post-incident log. Not operative until adopted by the Board.

---

## Purpose

The Foundation's data brainstorm already enumerates eight concrete incident types. This plan turns that into
an operational document a responder can follow under pressure: how to classify an incident, who to notify, the
containment runbook per type, and how to record what happened. It pairs with the security runbooks in
`operations/github-access-and-branch-protection-policy.md` and the recovery runbooks in
`operations/disaster-recovery-rto-rpo.md`.

---

## 1. Severity Tiers

| Tier | Definition | Examples | Response start |
|---|---|---|---|
| **SEV-1 Critical** | Active exposure of secrets, private data, or financial records; or loss of irreplaceable data | Live credential leaked publicly; bank/legal record committed; field DB lost with no backup | Immediately |
| **SEV-2 High** | Contained or low-likelihood exposure; integrity risk | Token in a build (not known accessed); GPS/site location published; Pi briefly internet-exposed | Same day |
| **SEV-3 Moderate** | Accuracy/reputational issue; no data exposure | False public dataset claim; corrupted dataset released | Within 48 h |

---

## 2. Roles and Notification Chain

| Role | Person | Responsibility |
|---|---|---|
| Incident Lead | Carlos Garcia (Research Director) | Coordinates response; makes containment decisions |
| Financial incidents | Adam Kimble (Treasurer) | Notified for any bank/financial exposure; contacts institution |
| Governance / records | Guillermo Martin (Secretary) | Records the incident in private governance records |
| Board | All directors | Notified for SEV-1 and any material SEV-2 |
| Affected service owner | As applicable | E.g., Vercel/hosting owner for build/token incidents |

**Notification rule:** SEV-1 → notify Incident Lead immediately and Board promptly. SEV-2 → notify Incident
Lead same day; Board if material. SEV-3 → notify Incident Lead.

---

## 3. General Response Workflow

1. **Detect & classify** — assign a severity tier.
2. **Contain** — stop ongoing exposure (remove file, disconnect device, revoke token).
3. **Eradicate** — rotate credentials, rewrite Git history, remove exposed data from all copies/caches.
4. **Notify** — per the chain in Section 2.
5. **Recover** — restore service/data per `operations/disaster-recovery-rto-rpo.md`.
6. **Document** — complete the post-incident log (Section 5).
7. **Review** — identify the root cause and the control that would have prevented it; update policy.

---

## 4. Incident Playbooks

Consolidated from `research/data-management-security-brainstorm.md` Section 13.

### 4.1 Secret committed to GitHub — SEV-1
- **Contain:** remove from Git history (`git filter-repo` / BFG); force-push.
- **Eradicate:** rotate the exposed credential/token/key immediately (assume compromised — public repos are
  cached).
- **Notify:** Incident Lead; affected service owner.
- **Document:** date, credential type, exposure duration, remediation.

### 4.2 Raw private data accidentally published — SEV-1
- **Contain:** remove file from public repo; scrub from Git history.
- **Eradicate:** assess caches/forks; request takedown where possible.
- **Notify:** Incident Lead; Board if significant; affected subjects/sites if applicable.
- **Document:** data type, volume, exposure duration, affected subjects/sites. (Data cannot be "rotated.")

### 4.3 GPS / site location accidentally published — SEV-2
- **Contain:** remove from public repo and Git history.
- **Notify:** Incident Lead; landowner if applicable.
- **Document:** location precision exposed, duration, context. Assess ecological/anti-theft/site risk.

### 4.4 Bank / legal / payment record committed — SEV-1
- **Contain:** remove from Git history immediately; force-push.
- **Eradicate:** rotate account credentials if banking details were exposed.
- **Notify:** Incident Lead; Adam Kimble (Treasurer); affected financial institution.
- **Document:** record type, exposure duration, whether account details were included; monitor for fraud.

### 4.5 Pi gateway exposed to internet — SEV-2 (SEV-1 if data exfiltrated)
- **Contain:** disconnect Pi from internet; verify LAN-only configuration (`--host` bound to LAN interface).
- **Eradicate:** rotate all Pi credentials, MQTT credentials, bearer tokens; re-provision nodes.
- **Notify:** Incident Lead.
- **Document:** exposure duration, services reachable, access logs if available.

### 4.6 Token leaked in public build (e.g., `VITE_PI_TOKEN`) — SEV-2
- **Contain:** redeploy without the token; confirm `VITE_PI_TOKEN` removed from Vercel env.
- **Eradicate:** rotate the leaked token and related credentials.
- **Notify:** Incident Lead; platform owner (Vercel).
- **Document:** token type, build platform, exposure duration.

### 4.7 False public dataset / status claim — SEV-3
- **Contain:** retract or correct the claim in all public locations (website, repos, releases).
- **Notify:** Incident Lead; Board.
- **Document:** the incorrect claim, where it appeared, correction issued. Cross-ref overclaiming risk in
  `risk/attack-surface-analysis.md`.

### 4.8 Corrupted dataset released — SEV-3
- **Contain:** mark the release withdrawn/deprecated on Zenodo (do not delete — publish a corrected version
  with a new DOI).
- **Notify:** Incident Lead; anyone who cited/downloaded the dataset.
- **Document:** nature of corruption, affected files, root cause; link corrected version to original.

---

## 5. Post-Incident Log Template

Complete one per incident; retain in private records, commit a public-safe summary only if it contains no
sensitive data.

| Field | Value |
|---|---|
| Incident ID / date | |
| Severity tier | |
| Type (4.1–4.8 or other) | |
| Summary | |
| Detected by / how | |
| Exposure window | |
| Containment actions | |
| Credentials rotated | |
| Data/service recovered | |
| Parties notified | |
| Root cause | |
| Preventive control added | |
| Closed date / by | |

---

## 6. Tamper-Evidence & Audit Trail

- Treat the PR history, commit signatures, and dataset SHA-256 manifests as the Foundation's audit trail
  (`research/data-management-security-brainstorm.md` Section 9).
- For restricted data, maintain an access log (who accessed what, when) per the storage model.
- Incident logs themselves are append-only: corrections add entries, they do not overwrite.

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| Board review | ⬜ Pending |
| Adoption date | ⬜ Not yet adopted |

*Not operative until adopted. Supersedes the inline incident notes in the data brainstorm once adopted.*
