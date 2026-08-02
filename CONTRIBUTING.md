# Contributing

## What belongs here

This repo's scope is **narrower than it sounds** — read this before adding anything.

- **Woodfine's own brand-specific token values** — `token-global-color.yaml`,
  `theme-woodfine-light.yaml`, `theme-woodfine.css`, `theme-woodfine-wcp.css`. This is
  the one real exception to the "no design tokens in a media-assets repo" rule (see
  `pointsav-media-assets/CONTRIBUTING.md` for the more restrictive sibling case): Woodfine
  is an *adopting tenant* of `pointsav-design-system`, not its vendor, so Woodfine's own
  brand values are layered on top via CSS custom-property override, in Woodfine's own
  repo — not forked inside the shared design system. See
  `pointsav-design-system/.agent/rules/design-tokens.md` for the full Carbon-model
  rationale (the same pattern Carbon, Material, Polaris, and Lightning all use for their
  own adopting customers).
- **Binary brand assets** — logos, principal photos, fonts, in `logos/`, `assets/`,
  `fonts/`.
- **Non-token brand governance content** — corporate language protocols, trademark and
  legal disclaimer text, in `governance/` (renamed 2026-07-27 from `tokens/linguistic/`
  — prose, not a design token, despite the old folder name).
- **Telemetry endpoint config** — `token-global-telemetry.yaml`, an operational endpoint
  URL, not a design token.

## What doesn't belong here — and where it actually goes

**Generic, tenant-neutral tokens — anything reusable across any adopting brand — never
land here.** Color primitives, spacing, typography, radius, motion, or a document-family
substrate that doesn't encode Woodfine's own brand identity all belong in
`pointsav-design-system` directly. The test: does the value encode *Woodfine's own* brand
identity specifically? If yes, it's this repo's. If it's a generic building block any
future adopting tenant could reuse unchanged, it's `pointsav-design-system`'s, not
Woodfine's brand fork.

**A second tenant's brand values never land here either** — this repo is Woodfine-only.

**`tokens/architecture/`** (the WCP entity-registry CSV/manifest) and **`tokens/design/`**
(logo/signet spec YAML, arguably redundant with the actual SVGs in `logos/`) are both
known pre-existing exceptions, not models to copy — real business-admin content and a
minor duplication respectively, each needing its own operator-directed disposition, not
new content added alongside them.

## Why the token exception here is real, not drift

This repo previously held CSS generated from stale color YAML, deleted 2026-07-10 after
being found drifted from its own source; the YAML half of that same pattern was
corrected 2026-07-17. The failure mode both times was the same shape found across this
whole workspace's design-token history: **two consumption surfaces for the same values,
with conflicting "operator/Master co-signed" provenance on each side.** The fix here is
not "zero tokens" (that's `pointsav-media-assets`'s fix, because PointSav is the vendor)
— it's **exactly one surface** for Woodfine's brand values, and this repo is it. If you
ever find a second copy of a Woodfine brand color anywhere else in the workspace
(`pointsav-design-system` included), that's the bug this file exists to prevent — fix it
by deleting the second copy, not by reconciling values between two "sources of truth."

## How to propose a change

Open an issue on [GitHub](https://github.com/woodfine/woodfine-media-assets) or route a
`DESIGN-TOKEN-CHANGE`/`DESIGN-ASSET` draft through the normal cross-cluster design-draft
pipeline (see `pointsav-design-system`'s own `dtcg-vault/designing/contributing.md` for
how that pipeline works end to end — shared mechanics, different content scope per the
rules above). Token changes require a `master_cosign` before they land, same as in
`pointsav-design-system`.
