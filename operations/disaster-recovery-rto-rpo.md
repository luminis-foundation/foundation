# Luminis Foundation — Disaster Recovery, RTO & RPO

> Status: Draft — pending Board/Research Director review; targets are proposals until confirmed
> Last updated: 2026-06-29
> Owner: Carlos Garcia (President / Research Director, Data Custodian)
> File: operations/disaster-recovery-rto-rpo.md
>
> **This is a draft recovery plan.** RTO/RPO targets below are proposals to be confirmed by the Research
> Director and Board. The plan reflects the Foundation's current bench/pre-field stage; sections that depend
> on a live field deployment are marked accordingly.

---

## Purpose

The Foundation's existing data docs describe manual export and cycle-based backups
(`research/data-management-founder-answers.md` Q6) but do not define **recovery objectives** or a full
**disaster recovery (DR) plan**. This document fills that gap: it states how quickly each asset must be
recovered (RTO), how much data loss is tolerable (RPO), and the runbooks to get there. It also captures the
Pi SQLite backup gap tracked in `operations/next-actions.md` ("Set up local backup for Pi SQLite database").

---

## Definitions

- **RTO (Recovery Time Objective):** maximum acceptable time to restore an asset to working order after a
  failure.
- **RPO (Recovery Point Objective):** maximum acceptable amount of data loss, measured as time since the last
  good backup.

---

## 1. Asset Inventory and Objectives

| Asset | What it is | Criticality | RTO (proposed) | RPO (proposed) | Backup method |
|---|---|---|---|---|---|
| Pi SQLite field database | Raw sensor readings on the Pi gateway (`pi-server/main.py`) | High (irreplaceable field data) | [TBD — proposed: 48 h] | [TBD — proposed: 1 field session] | Copy DB + SHA-256 manifest after every session; second encrypted drive |
| Private research archive (raw data, calibration logs) | Encrypted external drives held by officers | High | [TBD — proposed: 72 h] | Last session | Primary + backup drive + optional cold archive (`data-management-founder-answers.md` Q1) |
| GitHub repositories (docs/code) | Public foundation/mycosense/etc. repos | Medium | [TBD — proposed: 24 h] | Last push | Distributed git clones; GitHub-hosted; local clones |
| Public website | `luminis-foundation.github.io` (static) | Low–Medium | [TBD — proposed: 48 h] | Last commit | Git repo is source of truth; redeploy from repo |
| Private officer records (legal/financial PDFs) | Bank, legal, IRS records | High (compliance) | [TBD — proposed: 72 h] | Last update | Officer-controlled storage; ≥ 2 officers with emergency access |
| Hosting / Vercel deployment | MycoSense demo (mock data) | Low | [TBD — proposed: 24 h] | N/A (rebuildable from repo) | Redeploy from `mycosense` repo |

Targets are drafting proposals matched to current resources; the Board confirms them at adoption.

---

## 2. Pi Gateway Backup & Restore Runbook

> Applies once field data collection begins (currently bench/pre-field — `mycosense/FIELD_STATUS.md`).

### Backup (after every field/collection session)
1. Stop or pause the Pi server service to ensure a consistent SQLite snapshot.
2. Copy the SQLite database file to the primary encrypted external drive.
3. Generate a SHA-256 manifest of the copied file(s).
4. Record session metadata (date, node IDs, firmware/gateway versions, calibration state) alongside the copy.
5. Replicate to the backup encrypted drive held by a second authorized officer.
6. Verify the copy opens and row counts match before considering the backup complete.

### Restore
1. Provision a replacement Pi (or reimage the SD card) with the pinned gateway software version.
2. Restore the most recent verified SQLite database from the primary (or backup) drive.
3. Verify integrity against the SHA-256 manifest; confirm row counts and latest timestamp.
4. Restart the Pi server bound to the LAN interface only (`--host 192.168.x.x`, never `0.0.0.0`).
5. Confirm nodes reconnect and new readings append correctly.

### SD card resilience
- Treat the Pi SD card as **expendable**: the database of record is the backed-up copy, not the live card.
- Keep a spare flashed SD card with the pinned OS + gateway version for fast swap.

---

## 3. Failure Scenarios and Response

| Scenario | Impact | Immediate response | Recovery |
|---|---|---|---|
| Pi SD card failure / corruption | Live DB lost | Swap to spare SD; treat as data-loss event back to last backup | Restore DB from latest verified backup (Section 2) |
| Power loss at field site | Pi down; possible partial-write | Restore power; verify DB integrity | Recover from backup if corruption found |
| Sensor / node dropout | Gaps in data | Log gap; flag in QC review | No DB recovery needed; document gap per field data quality SOP |
| Backup drive failure | Loss of one backup copy | Re-replicate from surviving copy | Procure replacement drive; restore 2-copy state |
| GitHub outage / repo loss | Docs/code unavailable | Use local clone | Re-push from a local clone; GitHub is not the only copy |
| Website down | Public site unavailable | Low urgency | Redeploy static site from repo |
| Officer unavailable (continuity) | Access blocked | Use second-officer emergency access | Ensure ≥ 2 officers hold drive + account access (risk #5) |

---

## 4. Restore-Test Cadence

A backup is only as good as its last successful restore. Aligned with the cycle model in
`research/data-management-founder-answers.md` Q6:

- **Monthly:** compare primary vs. backup drive SHA-256 manifests.
- **Every 6 months:** perform a **full restore test** from backup to confirm recoverability; audit storage
  health; decide whether to migrate aging drives.
- **Annually:** Board-level data-governance review includes confirming DR objectives are still appropriate.

Record each restore test (date, result, issues) — see Section 6.

---

## 5. Continuity & Roles

- **Data Custodian:** Carlos Garcia (Research Director) owns the DR plan and primary archive.
- **Second officer:** holds the backup drive and has emergency access (avoids single point of failure).
- **At least two people** can access GitHub org, banking, and the encrypted archives in an emergency
  (`operations/next-actions.md` — internal operations; risk #5).

---

## 6. Restore-Test Log (fill in)

| Date | Asset tested | Result | Issues found | Tested by |
|---|---|---|---|---|
| ⬜ | Pi SQLite DB | | | |

---

## Adoption Status

| | |
|---|---|
| Draft prepared | 2026-06-29 |
| RTO/RPO targets confirmed | ⬜ Pending |
| First restore test completed | ⬜ Pending field data |
| Board review | ⬜ Pending |

*Not operative until reviewed; RTO/RPO values are proposals until confirmed by the Research Director and Board.*
