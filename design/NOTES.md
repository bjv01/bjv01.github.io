# Redesign — "The Sociomatrix" (work in progress)

Saved 2026-08-29 to branch `redesign/sociomatrix`. Picking this up another day.

## Where we landed
A personal brand + site redesign for Bernardo Villegas Moreno, to be **rebuilt in Framer**
(framer.com) — these files are the design/spec, not the deployed site.

**Chosen direction: "The Sociomatrix"** — a Vienna Secession / Wiener Werkstätte square lattice,
read as J.L. Moreno's *sociomatrix*: an open square = someone not yet reached; a filled square =
a social effect (externality) that has landed. Ties Vienna's social-science lineage (Neurath's
Isotype, the Vienna Circle) to the research on ripple effects of human–AI interaction.

## Locked decisions
- **White only** — no dark-background version (see DESIGN.md, "The White-Only Rule").
- **Colours:** Lacquer Ink `#16171A` on Gallery Paper `#F1F2F3` (NOT cream); one Sociometric
  Red `#C81E1E` used sparingly (~once per view).
- **Type:** Josefin Sans (letterspaced geometric caps) + Spectral (reading serif).
- **Form:** strict square lattice, zero border-radius, no shadows.
- **Hero motif:** a refined Isotype-style figure that WALKS toward the cursor (hover = it moves);
  sparse people (not a full grid); when it meets someone their SQUARE fills solid ink
  (fills squares, not connecting lines). No 8-bit, no numbers.

## Files here (open in a browser)
- `identity.html` — the identity system (mark, colour, type, motif, applications).
- `landing.html` — the full single-page site in the new colours (the current build).
- `hero.html` — the homepage hero in isolation (walking figure fills squares).
- `motion-study.html` — the walking human + AI concept study.
- `spread-studies.html` — 8 alternative ways to show the "spread" (ripple, Isotype tally,
  delayed fill, present-vs-absent, contagion, ink-bleed, ledger, distortion).
- `visual-directions.html` — 4 alternative visual languages beyond the Sociomatrix
  (Isotype Data, The Field, The Offprint, The Archive).

Repo root also has `PRODUCT.md` (product truth) and `DESIGN.md` (the visual system).

## Published artifacts (private, on claude.ai)
- Identity system: https://claude.ai/code/artifact/7725b475-8414-4335-a453-ddf844fd85ff
- Landing page:    https://claude.ai/code/artifact/c5d396be-5c7c-45bb-8f40-85293cbf5b0a
- Hero:            https://claude.ai/code/artifact/b357ef42-102d-48e9-b32a-2d567b73cc3c
- Motion study:    https://claude.ai/code/artifact/f3f8ad99-9fea-41ce-95cb-f22bb5dbafe7
- Spread studies:  https://claude.ai/code/artifact/6353a6dc-2652-4380-bef4-23fa6bda5951
- Visual directions:https://claude.ai/code/artifact/cf6926b0-feaf-4df6-ab10-91e0b69fa4a9

## Superseded (earlier "techy" concept — abandoned)
"Propagation Field" (dark, neon, force-directed canvas) + its Framer Build Kit. The user
pivoted away from techy toward the social-science Sociomatrix. Not saved here on purpose.

## Open threads / next steps
- The user said "I'll tell you more things to update" on the landing page — expect edits.
- Parked ideas: personal photo as an 8-bit lattice portrait; a bigger cinematic opening;
  ElevenLabs (voice) — all deferred.
- Not yet done: extend landing to inner pages if desired; a Framer build kit in this new world
  (tokens + a paste-ready Framer code component for the walking-figure canvas).
- Possible refinements: walk feel/speed, number of people, giving "you" a distinct silhouette.
