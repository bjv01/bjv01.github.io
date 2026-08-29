# Homepage redesign — 2026 ("The Sociomatrix")

The site homepage was replaced with a custom single-page design (August 2026). This documents
what changed, how it is built, how to edit/redeploy, and how to roll back.

## What it is

A self-contained one-page site, **live at https://bjv01.github.io**. Hero: an animated network of
people and AI agents where the AI effect transmits along the connections (the "secondhand AI" /
ripple-effects idea), seeded at middle-right. Subhero is the CV thesis line. Sections, in order:

1. `_me`  2. Research  3. Publications  4. Talks & posters  5. The path
6. Teaching  7. Fellowships & awards  8. Contact  9. Affiliations (logos)

Identity: white ground, lacquer ink, one sociometric red; Josefin Sans (caps) + Spectral (serif);
strict square lattice, zero radius, no shadows. It has a mobile hamburger menu and respects
`prefers-reduced-motion`.

## How it is built (important)

Hugo Blox renders the home from `content/_index.md` (`type: landing`). A `static/index.html` does
**not** override that on a clean CI build. So the homepage is served by a **custom Hugo template**:

- **`layouts/index.html`** — the entire self-contained page (HTML + inline CSS + inline JS/canvas,
  and the affiliation logos inlined as data-URIs). No `{{ define }}` block, so Hugo renders it
  standalone and Blox's `baseof` is bypassed.
- **`content/_index.md`** — neutralized to `title: ""` (the `type: landing` block was removed) so
  Hugo uses `layouts/index.html` instead of the Blox landing renderer.

Deployment is automatic: pushing to `main` runs `.github/workflows/deploy.yml`
(`hugo --minify` → GitHub Pages). Assets: `/uploads/resume.pdf` (in `static/uploads/`); fonts from
Google Fonts. Old Blox inner pages (`/me/`, `/research/`, …) still build but are unlinked; the
homepage navigates via in-page anchors.

## How to edit / redeploy

1. Edit `layouts/index.html` (a normal self-contained HTML file).
2. Optional local check that matches CI (untracked files under `layouts/` can skew a local build):
   ```
   mv layouts/_default /tmp/hold 2>/dev/null   # hide untracked overrides
   hugo --minify -d /tmp/out                    # open /tmp/out/index.html
   mv /tmp/hold layouts/_default 2>/dev/null
   ```
3. `git add layouts/index.html && git commit && git push origin main` — Actions redeploys.

## Design system & source

The full visual system and product context live on branch **`redesign/sociomatrix`**:
`DESIGN.md`, `PRODUCT.md`, and a `design/` folder (identity, studies, notes). The editable design
source is also mirrored as a private Claude artifact.

## Affiliation logos

All four are real, inlined as data-URIs, rendered grayscale to fit the identity:
TRACE (from trace-lab.ai), University of Cambridge, Wolfson College, King's Entrepreneurship Lab
(eLab / SPARK, from kingselab.org). To change one, replace its `data:` URI in the `.assoc` block of
`layouts/index.html`. (Note: when downloading a logo, verify the file is a real image — GitHub
Pages can transiently return an HTML 404 page for a missing asset.)

## Rollback

The previous Hugo Blox site is on branch **`previous-site`** (commit `6501a84`):

```
git checkout main
# soft: revert the redesign commits
git revert --no-edit $(git rev-list previous-site..main)
git push origin main
# — or hard: make main equal the previous site
# git reset --hard previous-site && git push --force-with-lease origin main
```
