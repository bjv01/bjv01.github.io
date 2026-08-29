# Homepage redesign — 2026 ("The Sociomatrix")

The site homepage was replaced with a single-page design (August 2026). This note documents
what changed, how it is built, and how to maintain or roll it back.

## What changed

- **New homepage:** a self-contained one-page site with an animated hero (an organic network of
  people and AI agents where the "secondhand AI" effect transmits along the connections), followed
  by content sections: `_me`, Research, Publications, Talks & posters, The path, Teaching,
  Fellowships & awards, Contact, Affiliations.
- **Identity:** "The Sociomatrix" — white ground, lacquer ink, one sociometric red; Josefin Sans
  (caps) + Spectral (reading). See `DESIGN.md` and `PRODUCT.md` on branch `redesign/sociomatrix`.
- The previous Hugo Blox academic-CV homepage is **preserved** (see Rollback).

## How it is built (important)

Hugo Blox renders the home from `content/_index.md` (`type: landing`). A `static/index.html`
does **not** override that on a clean CI build. So the homepage is served by a **custom Hugo
template**:

- `layouts/index.html` — the entire self-contained page (HTML + inline CSS + inline JS/canvas).
  It has no `{{ define }}` block, so Hugo renders it standalone and Blox's `baseof` is bypassed.
- `content/_index.md` — neutralized to `title: ""` (the `type: landing` block was removed) so
  Hugo uses `layouts/index.html` instead of the Blox landing renderer.

Deployment is automatic: pushing to `main` triggers `.github/workflows/deploy.yml`
(`hugo --minify` → GitHub Pages) and publishes to https://bjv01.github.io.

The site links to `/uploads/resume.pdf` (present in `static/uploads/`) and loads fonts from
Google Fonts. Old inner Blox pages (e.g. `/me/`, `/research/`) still build but are unlinked; the
new homepage navigates via in-page anchors (`#research`, `#publications`, …).

## How to edit / redeploy

1. Edit `layouts/index.html` (it is a normal, self-contained HTML file).
   - Design source of truth for iteration lives on branch `redesign/sociomatrix` and as a
     published artifact; regenerate `layouts/index.html` from it if you prefer.
2. Optional local check: `hugo --minify -d /tmp/out` then open `/tmp/out/index.html`
   (note: untracked local files under `layouts/` can make a local build differ from CI).
3. `git add layouts/index.html && git commit && git push origin main` — Actions redeploys.

## To-do

- **Affiliations logos:** the strip currently shows text tiles. Add real crest/mark files for
  TRACE Lab, University of Cambridge, Wolfson College, and eLab/SPARK (put them in
  `static/logos/` and reference `/logos/…` from `layouts/index.html`).

## Rollback

The previous Hugo Blox site is on branch **`previous-site`** (commit `6501a84`).
To restore it:

```
git checkout main
git revert --no-edit be28148 152aaaa 05c0540 49605e8   # undo the redesign commits
# — or — hard reset main to the previous site:
# git reset --hard previous-site && git push --force-with-lease origin main
git push origin main
```
