# CLAUDE.md — woodfine-media-assets

Brand media kit for Woodfine Management Corp. Contains brand primitives
(global color tokens, theme mappings, linguistic protocols) and media
assets (logos, photos of principals, fonts).

This file is repo-specific and inherits the workspace rules in
`~/Foundry/CLAUDE.md`. Read that first for corporate topology, identity
map, commit flow, and rules of engagement.

## Tier

**Admin-only repo.** No staging-tier (j/p mirror) forks, no cluster
clone — commits go straight to canonical. **Author identity is
`jwoodfine`/`pwoodfine` (alternating), never `mcorp-administrator`**
(corrected 2026-08-18 — the repo previously committed as
`mcorp-administrator` directly, which violates the workspace's
commit-identity hard rule; full history rewritten, see NOTAM/NEXT.md
for detail). The `mcorp-administrator` identity is **push-key-only** —
it never appears as a commit author.

## Remotes

| Name | URL | Role |
|---|---|---|
| `origin` | `git@github.com-woodfine-administrator:woodfine/woodfine-media-assets.git` | Canonical — push directly after commit, admin SSH alias |

## Commit procedure

Use `~/Foundry/bin/commit-as-next.sh --admin woodfine "<message>"` —
this is the canonical tool for exactly this pattern (author
`jwoodfine`/`pwoodfine`, alternating; push via the admin SSH alias
above). Do not hand-author commits with `GIT_AUTHOR_NAME=mcorp-administrator`.

## Downstream consumer

**Corrected 2026-07-30** — the prior claim here ("`github.com/woodfine/woodfine-design-bim`
consumes brand primitives from this repo") was checked directly and found wrong on every
count: no repo of that name exists (the real BIM repo is `woodfine-bim-library`); that
repo's own `tokens/bim/*.dtcg.json` files are architectural/domain data (materials, floor
plates, climate zones, tenant mix) with zero reference anywhere to this repo's brand
colors; and this file's own **Repo scope** section already documented the disproof —
`bim.woodfinegroup.com`'s live `tokens.css` has zero `--wf-*` properties, running an
entirely separate `--bim-*` system. BIM is a real, legitimate, separate design-token
system — just never a consumer of this repo, contrary to what this section claimed.

**Real downstream consumers**, per the Carbon-model consumption correction (see
`pointsav-design-system/.agent/rules/design-tokens.md`): whichever Woodfine-branded
applications layer this repo's values via CSS custom-property override —
`theme-woodfine.css` / `theme-woodfine-wcp.css` (both received into this repo 2026-07-30)
being the concrete instances today. There is no single fixed downstream repo; any
Woodfine-branded surface is a legitimate consumer, each in its own codebase, none of them
forking this repo's values inside their own.

**This repo is upstream-only** (2026-07-10 restructure, per a cross-repo
token audit + Fable review — same treatment applied to the sibling
`pointsav-media-assets` repo): it holds raw brand primitives — logo/
photo/font files, design specs, legal/linguistic protocol content, and
raw brand-values YAML — plus, as of 2026-07-30, the real theme CSS that
consumes them. It is not a distribution channel a creative-team member
should ever need to visit directly.

## Repo scope

- `token-global-color.yaml` — canonical palette (Woodfine brand + AEC semantic);
  the single raw source of truth in this repo
- `token-global-telemetry.yaml` — product telemetry tokens
- `theme-woodfine-light.yaml` — semantic theme mappings (light mode)
- `theme-woodfine.css`, `theme-woodfine-wcp.css` — Woodfine's own customer-override theme CSS
  (added 2026-07-30, moved here from `pointsav-design-system`'s legacy root `tokens/` tree per
  the Carbon-model consumption correction — an adopting tenant's brand customization belongs in
  the tenant's own repo, layered on top of the shared design system, not forked inside it)
- `docs/orgchart-brand-spec.md` — org-chart `--wf-chart-*` namespace history/rationale (2026-06-06)
- `fonts/` — Barlow Condensed, Nunito Sans, Sahitya, Zilla Slab
- `logos/` — SVG/PNG brand marks
- `assets/` — logo SVGs + principal photos (S&P-style brand media kit)
- `governance/` — corporate language protocols, trademark/legal disclaimer text (renamed
  2026-07-27 from `tokens/linguistic/` — prose governance content, not a DTCG token)
- `tokens/design/` — logo and signet specifications (kept under `tokens/` deliberately —
  arguably redundant with `logos/`'s actual SVG files, flagged for a future look, not
  renamed/moved this pass)
- `docs/typography/` — typography usage guides for Woodfine communications

**Removed 2026-07-10:**
- `css/theme-woodfine.css`, `css/theme-woodfine-light.css` — hand-maintained
  CSS duplicates of `token-global-color.yaml`'s values. One real drift found
  before removal: `theme-woodfine.css`'s `--wf-accent-hover` was `#f0f2f4`,
  matching no token (should have been `#E9ECEF` / `woodfine-grey-light` per
  the theme injection). Verified no real consumer: bim.woodfinegroup.com's
  actual live `tokens.css` has zero `--wf-*` properties — the deployed
  product uses its own separate `--bim-*` token system. Deleted outright,
  same reasoning as `pointsav-media-assets/css/theme-pointsav.css`.
- `assets/logo/wf-signet_V1.svg` + `wf-signet_V1.png` — contradicted their
  own spec (`tokens/design/wf-signet-spec_V1.yaml` calls for Impact/DIN
  typography and `#111827` background; this file used a hand-drawn glyph
  path and pure `#000000`), were referenced in no README, and were never
  the documented brand mark. `ASSET-SIGNET-MASTER.svg`/`.png` (Impact/DIN
  glyph, `#111827`, documented in `README.md`/`README.es.md`) are canonical.
