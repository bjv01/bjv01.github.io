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

## SEO & the custom domain (September 2026)

### Why this needed doing

Because `layouts/index.html` is standalone (no `{{ define }}`, so Blox's `baseof` is bypassed),
it also bypasses every Blox **SEO partial**. The correct title and `Person` metadata in
`config/_default/` therefore never reached the homepage — it shipped with `<title>Villegas
Moreno</title>` and no structured data at all. Anything SEO-related on the homepage must be
edited directly in `layouts/index.html`; changing `hugo.yaml` or `params.yaml` will not affect it.

Done on 2026-09-14 (commit `33ea9fd`): name-forward `<title>` and description, canonical, Open
Graph, Twitter card, and a JSON-LD `Person` block whose `sameAs` points at ORCID, Google Scholar,
LinkedIn, GitHub and X. Canonical and `og:url` use `{{ .Permalink }}`, so they follow `baseURL`
automatically and need no edit when the domain changes.

Also added `ignoreFiles` entries in `hugo.yaml` excluding the untouched Hugo Blox demo content
(`content/courses/`, `content/events/`, `content/projects/`) and the empty `content/habitus.md`.
These files still exist on disk but no longer build. Sitemap went 61 → 33 URLs. If the files are
ever deleted for real, drop the matching `ignoreFiles` entries.

### Decision: register `bernardovillegasmoreno.com` — NOT YET DONE

**Decided 2026-09-14. Deferred; no domain purchased as of that date.**

`bjv01.github.io` carries no name signal, so it earns nothing for "Bernardo Villegas Moreno".
The competing Bernardo Villegas (Filipino economist) holds `bernardovillegas.org` with 15+ years
of indexed content and a Wikipedia article. Bare "Bernardo Villegas" is not a winnable query and
is not the goal; the targets are "Bernardo Villegas Moreno", "Bernardo Villegas Cambridge" and
"Bernardo Villegas AI". `bernardovillegasmoreno.com` was confirmed unregistered on 2026-09-14
(`villegasmoreno.com` is taken — do not pursue it).

**The domain must be canonical, not a redirect to `bjv01.github.io`.** A domain that merely
redirects accumulates no ranking equity of its own. Correct order:

1. Register the domain.
2. Add `static/CNAME` containing the bare domain (in `static/` so it survives the Hugo build).
3. Repo Settings → Pages → Custom domain; enable Enforce HTTPS once the cert issues.
4. Set `baseURL` in `config/_default/hugo.yaml`. (CI passes `--baseURL` from
   `actions/configure-pages`, which picks up the custom domain once step 3 is done.)
5. GitHub then 301s `bjv01.github.io` → the custom domain, inheriting the existing index.

### Still outstanding (owner: BV, not code)

- Google Search Console: submit the sitemap and request indexing on the homepage. Without this
  the 2026-09-14 metadata waits on a natural crawl. The GSC verification file is in `static/`.
- Google Scholar profile (`j6a2kQkAAAAJ`): confirm the name reads "Bernardo Villegas Moreno" in
  full, so it matches the `sameAs` entry.

### Hazard: empty `layouts/_default/` overrides

Untracked zero-byte `baseof.html`, `list.html` and `single.html` may be present in
`layouts/_default/`. They do not blank inner pages — they suppress them entirely (no
`/me/index.html` is emitted at all) while the sitemap still advertises those URLs. Untracked, so
CI never sees them and the live site is unaffected; **if they are ever committed, every inner URL
in the sitemap 404s.** Delete them rather than work around them.
