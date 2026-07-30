# CLAUDE.md — woodfine-media-assets

Brand media kit for Woodfine Management Corp. Contains brand primitives
(global color tokens, theme mappings, linguistic protocols) and media
assets (logos, photos of principals, fonts).

This file is repo-specific and inherits the workspace rules in
`~/Foundry/CLAUDE.md`. Read that first for corporate topology, identity
map, commit flow, and rules of engagement.

## Tier

**Admin-only repo.** Direct commits from `mcorp-administrator` identity.
No staging-tier (jwoodfine/pwoodfine) flow. No cluster clone.

## Remotes

| Name | URL | Role |
|---|---|---|
| `origin` | `git@github.com-woodfine-administrator:woodfine/woodfine-media-assets.git` | Canonical — push directly after commit |

## Commit procedure

Follow `~/Foundry/CLAUDE.md §8` admin-tier procedure for `woodfine/*` repos:

```bash
GIT_AUTHOR_NAME="mcorp-administrator" \
GIT_AUTHOR_EMAIL="mcorp-administrator@users.noreply.github.com" \
GIT_COMMITTER_NAME="mcorp-administrator" \
GIT_COMMITTER_EMAIL="mcorp-administrator@users.noreply.github.com" \
git -c user.signingkey="$HOME/Foundry/identity/woodfine-administrator/id_woodfine-administrator.pub" \
    -c commit.gpgsign=true \
    -c gpg.format=ssh \
    -c gpg.ssh.allowedSignersFile="$HOME/Foundry/identity/allowed_signers" \
    commit -m "<message>"
```

## Downstream consumer

`github.com/woodfine/woodfine-design-bim` consumes brand primitives
from this repo. When token values change here, woodfine-design-bim DTCG
tokens should be updated accordingly via project-bim Task.

**This repo is upstream-only** (2026-07-10 restructure, per a cross-repo
token audit + Fable review — same treatment applied to the sibling
`pointsav-media-assets` repo): it holds raw brand primitives — logo/
photo/font files, design specs, legal/linguistic protocol content, and
raw brand-values YAML — that feed downstream consumers' builds. It is
not a distribution channel a creative-team member should ever need to
visit directly. All derived CSS/theme artifacts are generated
downstream, not hand-maintained here.

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
