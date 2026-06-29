# Luminis Foundation — Accessibility Checklist

> Status: Draft checklist — pending first accessibility pass
> Last updated: 2026-06-29
> Owner: Carlos Garcia (President / Research Director)
> Scope: `luminis-foundation.github.io` (public website) and the MycoSense dashboard (`mycosense/src/`)
> File: docs/accessibility-checklist.md

---

## Purpose

The Foundation's public-facing surfaces — the website and the MycoSense dashboard — should be usable by people
with disabilities. This checklist targets **WCAG 2.1 Level AA** as a practical baseline and gives each item an
owner and status so an accessibility pass can be tracked. It is a working checklist, not a conformance claim.

> No formal accessibility audit has been performed yet. Do not state WCAG conformance publicly until the
> checklist is completed and, ideally, verified with assistive technology.

---

## How to Use

- Run an automated check first (e.g., browser Lighthouse accessibility audit, axe DevTools) for quick wins.
- Then verify the manual items below with keyboard-only navigation and a screen reader (VoiceOver / NVDA).
- Mark each item ✅ / ⬜ / N/A and note findings.

---

## 1. Perceivable

| Item (WCAG ref) | Website | Dashboard | Notes |
|---|---|---|---|
| Text alternatives for images / icons (1.1.1) | ⬜ | ⬜ | `alt` on banner/logo; `aria-label`/`<title>` on SVG icons |
| Color contrast ≥ 4.5:1 for text (1.4.3) | ⬜ | ⬜ | Check dark-theme dashboard cards and chart labels |
| Information not conveyed by color alone (1.4.1) | ⬜ | ⬜ | Sensor status / alerts must have text or shape cues, not just color |
| Charts have non-visual equivalents (1.1.1 / 1.4.1) | N/A | ⬜ | Recharts: provide accessible summary/table or `aria` description |
| Content reflows / responsive (1.4.10) | ⬜ | ⬜ | Usable at 320px width / 200% zoom |
| Text resizes without loss (1.4.4) | ⬜ | ⬜ | No clipped content at 200% |

---

## 2. Operable

| Item (WCAG ref) | Website | Dashboard | Notes |
|---|---|---|---|
| All functionality keyboard-accessible (2.1.1) | ⬜ | ⬜ | Tabs, panels, export, calibration controls reachable by keyboard |
| No keyboard traps (2.1.2) | ⬜ | ⬜ | Drawers/modals (e.g., NotificationDrawer) release focus |
| Visible focus indicator (2.4.7) | ⬜ | ⬜ | Don't remove focus outlines without a replacement |
| Logical focus order (2.4.3) | ⬜ | ⬜ | DOM order matches visual order |
| Skip-to-content link (2.4.1) | ⬜ | ⬜ | Add a skip link for long nav |
| Descriptive link/button text (2.4.4) | ⬜ | ⬜ | Avoid "click here"; label icon-only buttons |
| Target size adequate (2.5.5 AAA-leaning) | ⬜ | ⬜ | Touch targets comfortably tappable |

---

## 3. Understandable

| Item (WCAG ref) | Website | Dashboard | Notes |
|---|---|---|---|
| Page language set (3.1.1) | ⬜ | ⬜ | `<html lang="en">` |
| Consistent navigation (3.2.3) | ⬜ | ⬜ | Nav order consistent across views |
| Clear labels & instructions (3.3.2) | ⬜ | ⬜ | Form fields (e.g., contact form) have visible labels |
| Error identification & suggestions (3.3.1 / 3.3.3) | ⬜ | ⬜ | Validation messages are clear and programmatically associated |

---

## 4. Robust

| Item (WCAG ref) | Website | Dashboard | Notes |
|---|---|---|---|
| Valid, semantic HTML (4.1.1) | ⬜ | ⬜ | Use landmarks: `<header> <nav> <main> <footer>` |
| Name/role/value for custom widgets (4.1.2) | ⬜ | ⬜ | Tabs/toggles expose ARIA roles & state |
| Status messages announced (4.1.3) | ⬜ | ⬜ | Live regions for notifications / async updates |

---

## 5. Documents & Media

| Item | Status | Notes |
|---|---|---|
| PDFs/reports released publicly are tagged/accessible | ⬜ | Applies to any public report or dataset README |
| No information-only images without alt text | ⬜ | Diagrams include text equivalents |

---

## Action Log

| Date | Surface | Tool / method | Findings | Owner |
|---|---|---|---|---|
| ⬜ | Website | Lighthouse / axe | | Carlos Garcia |
| ⬜ | Dashboard | Lighthouse / axe + keyboard + SR | | Carlos Garcia |

---

## Status

| | |
|---|---|
| Checklist prepared | 2026-06-29 |
| First automated pass | ⬜ Pending |
| First manual (keyboard + screen reader) pass | ⬜ Pending |

*This is a working checklist. Do not make public WCAG conformance claims until it is completed and verified.*
