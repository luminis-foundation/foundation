# ADR 0002 — Local-First Field Data Architecture

> Status: Accepted (records an existing decision)
> Date: 2026-06-29
> Deciders: Carlos Garcia (President / Research Director), Board of Directors
> File: docs/adr/0002-local-first-field-data-architecture.md

---

## Context

MycoSense collects ecological sensor data from ESP32 field nodes via a Raspberry Pi gateway. The Foundation
must decide how and where this data is captured, stored, and eventually released. Options range from a
cloud-connected IoT architecture (devices stream directly to a hosted backend) to a fully local-first design
(data stays on local infrastructure until deliberately released).

Constraints and values shaping the decision:
- The Foundation's mission is offline-first and eco-conscious (`research/data-management-founder-answers.md`).
- Field sites (e.g., Rowe, NM) have limited/unreliable connectivity.
- Site locations and raw data are sensitive and must stay private by default
  (`research/data-management-plan.md`).
- A public-internet-exposed gateway is a critical risk (`risk/attack-surface-analysis.md` #6).
- Funders increasingly require a credible data-management approach.

---

## Decision

Adopt a **local-first, offline-first** field data architecture:

1. **ESP32 nodes → Pi gateway over a LAN hotspot.** Nodes never connect directly to the internet. MQTT
   (Mosquitto) carries readings on the local network with username/password auth; NTP sync gates trusted
   timestamps.
2. **Pi gateway stores data locally** (FastAPI + SQLite, `pi-server/main.py`), bound to the LAN interface IP
   — **never internet-routable**. All endpoints require a bearer token; CORS is restricted.
3. **Raw data stays on encrypted local storage**, backed up to a second encrypted drive and (optionally) an
   offline cold archive. No cloud for raw/private data until the Board approves a secure architecture.
4. **The public dashboard runs in mock mode by default** (`mycosense.vercel.app`); live data is shown only on
   trusted local builds and only after validation.
5. **Public release happens deliberately via Zenodo/GitHub** — validated, sanitized, reviewed, approved, with
   DOI + SHA-256 manifest (`research/data-management-plan.md` §9).

See the full data path in `docs/architecture/mycosense-system-architecture.md`.

---

## Consequences

**Positive**
- Minimizes attack surface (no internet-exposed gateway; #6) and protects site privacy.
- Works with poor field connectivity; aligns with the offline-first, eco-conscious mission.
- Keeps the Foundation in control of release timing ("Public by proof").
- Backups and recovery are well-defined (`operations/disaster-recovery-rto-rpo.md`).

**Negative / trade-offs**
- No remote/real-time monitoring of field nodes; data is collected on visits or via local sync.
- Manual backup/export discipline is required (mitigated by the backup cadence and DR plan).
- Known hardening gaps (Pi TLS, MQTT signing/replay, log rotation) must be closed before field deployment
  (`research/data-security-policy.md` §6).
- OTA firmware updates and remote management are deferred (`mycosense/FIELD_STATUS.md`).

**Revisit if**
- The Board approves a secure remote-access or cloud architecture, or
- Scale (multiple field sites/partners) makes purely-local sync impractical — at which point multi-tenancy
  and data-isolation requirements should be added to the DMP and security policy.
