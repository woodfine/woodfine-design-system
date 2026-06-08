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
| `--wf-chart-magenta` | `woodfine-magenta` (new) | Entirely new. No prior YAML or CSS entry. |
| `--wf-chart-teal` | — | Pending teal/red addition draft (token-woodfine-theme-teal-red-additions). |
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
| Magenta | `#9F1853` | `woodfine-magenta` | Pre-reorganization Bencal Corp |
| Magenta surface | `#FFD6E8` | `woodfine-magenta-tint` | Bencal legacy node background |

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

1. Should `--wf-chart-green` and `--wf-chart-blue` alias to `--wf-safe` and `--wf-accent` respectively (since they share the same hex values), or remain independent? Aliasing documents the hex relationship but conflates the semantic layers. Current recommendation: keep independent, document the relationship in this file only.
