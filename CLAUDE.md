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

## Repo scope

- `token-global-color.yaml` — canonical palette (Woodfine brand + AEC semantic)
- `token-global-telemetry.yaml` — product telemetry tokens
- `theme-woodfine-light.yaml` — semantic theme mappings (light mode)
- `css/theme-woodfine-light.css` — CSS custom properties (--wf-* prefix, light mode)
- `css/theme-woodfine.css` — CSS custom properties (--wf-* prefix, alternate variant)
- `fonts/` — Barlow Condensed, Nunito Sans, Sahitya, Zilla Slab
- `logos/` — SVG/PNG brand marks
- `assets/` — logo SVGs + principal photos (S&P-style brand media kit)
- `tokens/linguistic/` — corporate language protocols
- `tokens/design/` — logo and signet specifications
- `docs/typography/` — typography usage guides for Woodfine communications
