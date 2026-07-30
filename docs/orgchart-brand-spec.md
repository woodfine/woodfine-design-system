# Org Chart Brand Specification — Woodfine

*Source: project-orgcharts 9-chart production set. Authored 2026-06-06.*

## Purpose

This document explains how the `--wf-chart-*` CSS custom properties and the `woodfine-*` YAML tokens relate to the broader Woodfine brand token system, and why the separate `--wf-chart-*` namespace exists.

## Token relationship map

| Chart CSS variable | YAML token | Relationship to existing `--wf-*` |
|---|---|---|
| `--wf-chart-green` | `woodfine-green` | Same hex as `--wf-safe` (`#54924E`). Different semantic meaning: chart green = corporate holding company; `--wf-safe` = IDS validation pass / compliance safe-state. |
| `--wf-chart-blue` | `woodfine-blue` | Same hex as `--wf-accent` (`#164679`). Different semantic meaning: chart blue = investment vehicle; `--wf-accent` = primary interactive brand blue. |
| `--wf-chart-purple` | `woodfine-purple` (YAML) | No existing CSS var. Purple is in YAML only; `--wf-chart-purple` is the first CSS variable for this color. |
| `--wf-chart-orange` | `woodfine-orange` (YAML) | No existing CSS var. Orange is in YAML only. |
| `--wf-chart-yellow` | `woodfine-yellow` (new) | Entirely new. Was `#F57F17` (amber), updated 2026-06-06 to `#EAB308`. |
| `--wf-chart-grey` | `woodfine-grey-mid` (`#6B7280`) | Different value — chart grey `#9CA3AF` is lighter than `woodfine-grey-mid`. |

## Why `--wf-chart-*` prefix

The `--wf-*` namespace already contains AEC semantic colors: `--wf-safe` (green, IDS pass), `--wf-warning` (amber, regulation alert), `--wf-error` (red, clash/failure), `--wf-mep` (cyan, systems indicator).

The AEC colors and the org chart entity-role colors share base hues:
- `--wf-safe` and `--wf-chart-green` are both `#54924E` — but "safe/compliant" and "corporate holding company" are different meanings.
- A future AEC chart consumer referencing `--wf-safe` for structural compliance indicators must not receive an org-chart corporate entity meaning.

The `--wf-chart-*` prefix scopes all org chart variables to a single namespace, preventing semantic bleed between the two domains. Chart authors reference `--wf-chart-*` only; AEC authors reference `--wf-*` only.

## Colors that are new to the Woodfine token system

These did not exist in any prior `woodfine-media-assets` file:

| Color | Hex | YAML token | Use |
|---|---|---|---|
| Yellow | `#EAB308` | `woodfine-yellow` | Fund vehicle LP nodes — dashed pill |
| Yellow surface | `#FFFDE7` | `woodfine-yellow-tint` | LP node background |

## Colors in YAML but missing from CSS (now covered by `--wf-chart-*`)

| YAML token | Hex | New CSS var |
|---|---|---|
| `woodfine-purple` | `#7C468C` | `--wf-chart-purple` |
| `woodfine-purple-tint` | `#EEE6F1` | `--wf-chart-purple-tint` |
| `woodfine-orange` | `#F15F22` | `--wf-chart-orange` |
| `woodfine-orange-tint` | `#FDE8DD` | `--wf-chart-orange-tint` |
| `woodfine-gold` | `#C89211` | — (gold not used in charts; not added) |
| `woodfine-gold-tint` | `#FAEFCC` | — (gold not used in charts; not added) |

## Open questions

1. **RESOLVED 2026-07-30 — not via the `--wf-chart-*` prefix scheme this file originally
   proposed.** That scheme was never actually implemented (`--wf-chart-*` never appears in any
   real CSS this workspace ships); `theme-woodfine.css` kept using its existing bare `--wf-*`
   names for chart-entity colors the whole time, so the semantic-bleed risk this file warned
   about was real but unaddressed for over a month. Resolved instead by disambiguating the
   *other* side directly: the AEC-role green in `token-global-color.yaml` was renamed
   `woodfine-green` → `woodfine-status-verified` (still `#54924E`), leaving `theme-woodfine.css`'s
   `--wf-green` (`#198038` as of 2026-06-03 — already diverged from this doc's stated `#54924E`
   by the time this doc was written) as the sole "green" name. Confirmed as two genuinely
   different, deliberately-approved roles, not drift — same value collision this doc already
   identified, opposite fix (rename instead of alias).
2. **Also found and corrected while resolving #1:** `theme-woodfine.css`'s `--wf-amber`
   (`#F57F17`) was never updated for the amber → yellow rename this file documents in the table
   above (2026-06-06) — it was still the pre-rename value, over three weeks stale. Corrected to
   `--wf-yellow: #EAB308` / `--wf-yellow-tint: #FFFDE7`, matching this file's own already-documented
   intent. `woodfine-amber`/`woodfine-amber-tint` in `token-global-color.yaml`'s AEC block were
   never the same color as the chart role in the first place (different hex even before this
   fix) — `woodfine-amber` itself needs no rename, only the now-orphaned `woodfine-amber-tint`
   (the chart role's leftover tint) was removed.
3. **RESOLVED 2026-07-30 — `--wf-grey` had no real chart provenance; corrected.**
   `theme-woodfine.css`'s `--wf-grey` (`#6B7280`) was simply borrowed from `woodfine-grey-mid`
   (a general-brand ink grey, still `--wf-ink-3`) — never sourced from real chart usage. Direct
   grep across project-orgcharts' full real chart corpus found `.token-grey`/`.token-gray*`
   consistently using fill `#E6E7E8` / border `#9CA3AF` (57/57 occurrences), matching
   MEMO-Woodfine-Color-Matrix.md's own ratified chart-grey and `org-chart-print`'s
   (pointsav-design-system) already-shipped `role-grey-border` default. Corrected
   `--wf-grey: #E6E7E8` and added a new `--wf-grey-border: #9CA3AF`; new
   `woodfine-grey-chart`/`woodfine-grey-chart-border` entries added to `token-global-color.yaml`
   as the source. `--wf-grey`'s corrected value coincidentally matches `--wf-rule` (`#E6E7E8`,
   a separate hairline-separator role) — same shared-hue-different-role pattern already
   confirmed for green in #1, not a conflict.
   The table above's claim that "chart grey `#9CA3AF` is lighter than `woodfine-grey-mid`"
   was directionally correct about `#9CA3AF` being a real chart value, but named it as the
   *fill* rather than the *border* of the pair — corrected by this finding. `woodfine-gold`
   (`#C89211`) was checked against the same real corpus during this pass and confirmed absent
   — the "gold not used in charts; not added" line in the table above still holds; no change.
