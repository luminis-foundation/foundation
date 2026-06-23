# Luminis Foundation — GitHub Organization Structure

A decision record for how repositories and folders are organized under the
`luminis-foundation` GitHub organization. Goal: separate organizational history,
research outputs, and software early — without creating empty repos that add friction.

## Principle

One repo per *thing that has its own lifecycle*. Folders inside a repo for things that
share a lifecycle. Split a folder out into its own repo only when it **earns it** (its own
contributors, its own release cadence, its own deploy target). Splitting later is easy;
un-splitting is annoying.

## Current layout (June 2026)

```
luminis-foundation/                 (GitHub organization)
├── foundation                      records: org history + research (one repo)
│   ├── governance/
│   │   ├── mission.md
│   │   ├── milestones.md
│   │   ├── roadmap.md
│   │   ├── grants.md
│   │   ├── board-minutes/          (consider PRIVATE — see Notes)
│   │   └── annual-reports/
│   └── research/
│       ├── publications/           papers + Zenodo DOIs (metadata/records, not large files)
│       ├── datasets/               dataset records; host the data itself on Zenodo
│       └── protocols/              experimental + field protocols
│
├── mycosense                       software (EXISTING) — full system, kept as a monorepo
│   ├── src/                        React 18 dashboard (deployed: mycosense.vercel.app)
│   ├── esp32-firmware/             ESP32 / C++ device firmware
│   └── pi-server/                  Raspberry Pi gateway (Python)
│
└── .github                         (optional) org profile README — public face of the org
```

## Deferred until earned

- `mycosense-firmware` — split out when the bio-impedance blueprint becomes a maintained codebase
- `mycosense-server` — split out if the Pi gateway grows its own release cycle
- a dedicated datasets repo — only if Zenodo hosting proves insufficient

## Notes

- **Datasets:** git handles large/binary data poorly. Keep dataset *records* (description,
  schema, DOI link) in `research/datasets/` and host the actual files on Zenodo.
- **Board minutes:** signed minutes contain personal data (names, addresses, signatures).
  Consider a private repo or redacted copies for anything beyond what already appears in
  public state filings.
- **Public vs private:** mission, milestones, roadmap, and published papers → public.
  Raw governance records → your call.
- **mycosense README:** update it to describe the whole system (dashboard + firmware +
  server), not just "a React dashboard," so the repo's scope is clear to outsiders.
