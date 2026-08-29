---
name: The Sociomatrix — Bernardo Villegas Moreno
description: A Vienna Secession square-lattice identity read as a social matrix, for a researcher of AI's downstream social effects.
colors:
  ink: "#16171A"
  paper: "#F1F2F3"
  card: "#FFFFFF"
  silver: "#9A9C9E"
  silver-faint: "#C9CBCC"
  sociometric-red: "#C81E1E"
typography:
  wordmark:
    fontFamily: "Josefin Sans, Futura, 'Century Gothic', sans-serif"
    fontSize: "clamp(2rem, 6vw, 4.5rem)"
    fontWeight: 600
    lineHeight: 1
    letterSpacing: "0.14em"
  display:
    fontFamily: "Josefin Sans, Futura, 'Century Gothic', sans-serif"
    fontSize: "clamp(1.4rem, 3vw, 2.2rem)"
    fontWeight: 500
    lineHeight: 1.1
    letterSpacing: "0.1em"
  label:
    fontFamily: "Josefin Sans, Futura, 'Century Gothic', sans-serif"
    fontSize: "0.72rem"
    fontWeight: 500
    lineHeight: 1.4
    letterSpacing: "0.22em"
  body:
    fontFamily: "Spectral, Georgia, 'Times New Roman', serif"
    fontSize: "clamp(1rem, 1.4vw, 1.18rem)"
    fontWeight: 400
    lineHeight: 1.65
    letterSpacing: "normal"
  apparatus:
    fontFamily: "Spectral, Georgia, serif"
    fontSize: "0.86rem"
    fontWeight: 400
    lineHeight: 1.55
    letterSpacing: "normal"
rounded:
  none: "0px"
spacing:
  unit: "8px"
  cell: "88px"
components:
  button-primary:
    backgroundColor: "{colors.paper}"
    textColor: "{colors.ink}"
    rounded: "{rounded.none}"
    padding: "14px 22px"
  button-primary-hover:
    backgroundColor: "{colors.ink}"
    textColor: "{colors.paper}"
    rounded: "{rounded.none}"
    padding: "14px 22px"
---

# Design System: The Sociomatrix

## Overview

**Creative North Star: "The Sociomatrix"**

The identity fuses two things that turn out to be the same shape. The Wiener Werkstätte (Vienna, 1903 — Josef Hoffmann, "Quadratl-Hoffmann") built luxury out of the square: hammered silver baskets pierced with rows of perfect square holes, walls ruled as if drawn with a lacquer-dipped ruler. Independently, Jacob **Moreno** (sociometry, 1934) recorded human relations as a *sociomatrix* — a grid whose filled cells mark who is tied to whom. This system reads the Secession lattice AS a sociomatrix: an open square is a person not yet reached; a solid square is a social effect that has landed on them. It is the subject's own thesis — the downstream externalities of human–AI interaction — rendered as the interface's fundamental unit. The lineage is not decorative: Vienna is also where empirical social science was born (Neurath's Isotype, Lazarsfeld's Marienthal study, the Vienna Circle), so the aesthetic and the argument come from one city.

The personality is exacting, austere, and confident — gallery precision, not warmth-by-cream. It rejects the two academic defaults outright: the cream-paper-and-serif "scholarly" look, and the dark-neon "techy" look the earlier concept explored. Density is deliberate and rhythmic: strict lattice, generous margins, one voice of color held in reserve.

**Key Characteristics:**
- The square is the only module; every element aligns to a lattice of cells.
- Strict black-and-white; a single sociometric red appears on ≤2% of any surface, once.
- State is shown by *filling* — open (pierced) vs. solid (inked) — not by color or shadow.
- Letterspaced geometric capitals over a refined reading serif.
- Zero border radius, anywhere, forever.

## Colors

A monochrome system of printer's ink on cool gallery paper, with silver as the only mid-tone and one reserved red.

### Primary
- **Lacquer Ink** (#16171A): All text, all 1px rules, and the *filled* (active/affected) cell. The system's black.

### Secondary
- **Sociometric Red** (#C81E1E): The one voice of color. Reserved for a single meaning per view — the externality made visible, "the one who wasn't present." Borrowed from Moreno's convention (red = a positive tie) and Secession two-color offset. Never a fill wash, never on more than one element in view.

### Neutral
- **Gallery Paper** (#F1F2F3): The ground. A cool near-white — deliberately not cream (#F4F1EA), to refuse the AI-academic default.
- **Card White** (#FFFFFF): Raised cells and framed cartouches, one step brighter than the ground.
- **Hammered Silver** (#9A9C9E): Secondary text, captions, and apparatus labels; the metal sheen.
- **Faint Silver** (#C9CBCC): The lightest lattice rules and idle dividers.

### Named Rules
**The White-Only Rule.** The identity is committed to a single light world — gallery paper ground, always. There is no dark-background version; the confident white field is part of the brand's restraint.
**The One Red Rule.** Sociometric Red appears exactly once per view, on the single element that carries the "hidden cost made visible" meaning (the mark's one cell, or the active externality node). A second red anywhere is a bug.
**The Fill-Not-Hue Rule.** State is communicated by filling a cell solid ink (or inverting it), never by tinting. Color is meaning, not decoration.

## Typography

**Display / Wordmark / Label Font:** Josefin Sans (fallback: Futura, Century Gothic, sans-serif)
**Body / Apparatus Font:** Spectral (fallback: Georgia, Times New Roman, serif)

**Character:** Geometric Secession capitals — thin, wide, letterspaced — carry every title, label, and the wordmark, echoing Ver Sacrum roman caps. A refined text serif carries all sustained reading (the abstract, prose, footnotes), so the page stays a scholar's page under the geometry.

### Hierarchy
- **Wordmark** (Josefin 600, clamp 2–4.5rem, 0.14em tracking, UPPERCASE): "VILLEGAS MORENO" / full name lockup.
- **Display** (Josefin 500, clamp 1.4–2.2rem, 0.1em, UPPERCASE): Section titles inside ruled cartouches.
- **Label** (Josefin 500, 0.72rem, 0.22em, UPPERCASE): Nav (`_ME`, `_RESEARCH`), running heads, matrix axis labels, kickers.
- **Body** (Spectral 400, clamp 1–1.18rem, 1.65 line, ~64ch max): The abstract and prose.
- **Apparatus** (Spectral 400, 0.86rem, 1.55 line): Footnotes, margin notes, captions — the annotation layer where downstream effects are named.

### Named Rules
**The Caps-and-Reading Rule.** Josefin only ever appears as letterspaced capitals; Spectral carries anything longer than a line. Never set body copy in the geometric face, never set a title in the serif.

## Layout

A square-cell lattice governs everything. Base module: an 8px spacing unit; a nominal **88px cell** on desktop that scales down responsively (the lattice re-counts cells per viewport — it never stretches one cell). Content sits inside square-punched frames and ruled cartouches; sections are nested "caskets" that open along strict orthogonal seams. Container max ~1200px, with generous outer margins (Vienna luxury = precision plus space). Symmetry is held to the lattice; asymmetry, when used, is a deliberate single break against an otherwise strict grid. 1px Lacquer Ink rules divide cells; Faint Silver for the quietest dividers.

## Elevation & Depth

Flat by doctrine. No drop shadows. Depth is tonal and structural only: Card White lifts a cell one step off Gallery Paper; a 1px ink rule does the work a shadow would. The only "sheen" is Hammered Silver used as a hairline or secondary tone. Motion, not shadow, signals interactivity.

### Named Rules
**The No-Shadow Rule.** If a surface needs to read as raised, brighten it to Card White and rule its edge — never float it on a shadow.

## Shapes

Border-radius is **0px** everywhere — the square is the identity. Forms are built from the pierced square (open cell, 1px ink outline) and its solid counterpart (filled ink cell). Recurring silhouette: the lattice, the ruled cartouche, the checkerboard. Lines are hairline-precise (1px), drawn as if with a ruler.

## Components

### Buttons
- **Shape:** Square corners (0px), 1px Lacquer Ink border.
- **Primary (idle):** Gallery Paper ground, ink text, letterspaced caps (Josefin), padding ~14×22px — a pierced cell.
- **Hover / Focus:** Inverts to solid — Lacquer Ink ground, Paper text (the cell fills). Focus adds a 2px offset ink outline.
- **Motion:** Crisp fill, ~120ms, no easing bounce.

### Navigation
- Letterspaced caps labels (`_ME`, `_RESEARCH`, `_WORK`, `_CONTACT`) laid as cells on the top rule. Default: ink on paper. Hover/active: the cell fills solid ink, label reverses to paper. Mobile: the nav collapses to a single stacked column of full-width cells.

### Cards / Containers (Cartouches)
- **Corner Style:** 0px. **Background:** Card White on Gallery Paper. **Border:** 1px Lacquer Ink (or Faint Silver for quiet frames). **Shadow:** none. **Padding:** one cell-unit inset. Title sits in a ruled cap-cartouche at the top edge.

### Inputs / Fields
- 1px ink underline or full ink box, square, Card White fill. Focus: box fills to a 2px ink frame. No glow.

### The Sociomatrix (signature component)
An N×N grid of square cells. **Idle:** open cells, 1px silver outline. **Affected/tie:** solid Lacquer Ink fill. **The one externality:** a single Sociometric Red cell. **Reading interaction:** a wavefront fills cells outward from a source node — the ripple, rendered as a Secession lattice — with a caption naming how many downstream nodes were reached. **Reduced motion:** renders a static, pre-filled matrix. This component doubles as the monogram's construction grid and the site hero.

### The Mark / Monogram
A square containing a lattice glyph built from filled cells — an interlocking B·V·M / a "one node reaching many" sociogram figure — with exactly one Sociometric Red cell. Always sits in or implies its square bounding box. Minimum size preserves cell legibility; never rounded, never recolored beyond the ink/paper/one-red set.

## Do's and Don'ts

### Do:
- **Do** align every element to the square lattice; let the grid, not margins, set spacing.
- **Do** show state by filling or inverting a cell (open → solid), per The Fill-Not-Hue Rule.
- **Do** keep Sociometric Red to one element per view (The One Red Rule).
- **Do** set all titles/labels as letterspaced Josefin capitals and all reading in Spectral.
- **Do** keep corners at 0px and surfaces flat (no shadows).

### Don't:
- **Don't** use a cream/parchment ground (#F4F1EA family) or a high-contrast serif display — the academic default this world exists to refuse.
- **Don't** ship a dark-background version — the identity is white-only (The White-Only Rule).
- **Don't** reintroduce the dark-neon "techy" register (glowing edges, force-directed canvas as chrome).
- **Don't** add a second accent color, a gradient, or a rounded corner.
- **Don't** set body copy in Josefin or a title in Spectral.
- **Don't** float cells on shadows to fake depth.
