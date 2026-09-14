# Deprecated: the Hugo Blox theme layer

**Status: deprecated 2026-09-14. Frozen in place — deliberately NOT removed.**

The site is now `layouts/index.html`, a single self-contained page. The Hugo Blox theme
underneath it is no longer the site; it is kept only because parts of it still serve live,
indexed URLs. Nothing here should be deleted casually — read "Why not just delete it" below.

## Deprecated — do not invest further

| Thing | State |
|---|---|
| `content/courses/`, `content/events/`, `content/projects/` | Untouched Hugo Blox **demo content**. Excluded from the build by `ignoreFiles` in `config/_default/hugo.yaml`. Files still on disk; URLs return 404. |
| `content/habitus.md` | Empty stub. Same exclusion. |
| Blox module (`go.mod`, `config/_default/module.yaml`) | Still required to build the inner pages. Do not upgrade for features. |
| `config/_default/params.yaml` SEO + navbar blocks | Inert for the homepage — it bypasses Blox's `baseof` and every SEO partial. Homepage metadata lives in `layouts/index.html`. |
| `content/blog/` | Empty section, no posts. Builds as an empty list page. |

## NOT deprecated — live and maintained

| Thing | Why it stays |
|---|---|
| `layouts/index.html` | This is the site. All homepage and SEO work happens here. |
| `content/publications/*` (5 entries) | Live, indexed, and the only pages carrying research topics — economic elites, populism, legal analytics, AI. They do real SEO work for "Bernardo Villegas Moreno". |
| `/me/`, `/research/`, `/cv/`, `/teaching/`, `/experience/` | Unlinked from the homepage but live and indexed. Kept deliberately. |
| `static/` (CV PDF, favicons, GSC verification) | Referenced by the live homepage. |

## Why not just delete it

The Blox inner pages account for most of the sitemap. Deleting them 404s real indexed content —
a direct reversal of the 2026-09-14 SEO work (see `REDESIGN.md`). Deprecation keeps the URLs
alive while signalling that no further work goes into the theme.

## Rules going forward

1. New homepage or SEO work → `layouts/index.html`. Never `params.yaml`; it does not reach the homepage.
2. New writing → `content/publications/` (real bibliographic entries), not the demo sections.
3. Before deleting anything under `content/`, diff the sitemap before and after:
   `hugo --minify -d /tmp/out && grep -o '<loc>[^<]*</loc>' /tmp/out/sitemap.xml | sort`
4. Never commit `layouts/_default/`. Empty overrides there suppress every inner page while the
   sitemap still lists the URLs — see the hazard note in `REDESIGN.md`.

## Preservation

- `deprecated/hugo-blox` — branch pinned to the full state at deprecation (2026-09-14).
- `previous-site` — the pre-redesign Blox site (commit `6501a84`).

## If the theme is ever fully removed

Retire it in this order, checking the sitemap at each step:
demo content (already dark, safe) → `content/blog/` → inner pages, only once their content has a
home on the one-page site → the Blox module and `config/_default/`. Drop the matching
`ignoreFiles` entries as each set of files actually goes.
