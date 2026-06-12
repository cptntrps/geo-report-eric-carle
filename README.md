# GEO Audit — The Very Hungry Caterpillar / World of Eric Carle

How Claude (Anthropic's AI assistant) perceives and recommends *The Very Hungry
Caterpillar* across a panel of synthetic buyer personas, benchmarked against
*Goodnight Moon*, *Where the Wild Things Are*, and *The Gruffalo*.

**Method:** 270 probes (6 personas × 3 question dimensions × 3 Claude model
tiers × repeats), recommendation questions asked brand-blind, brand mentions
extracted and scored post-hoc, deterministic scorecard, strategy synthesis.
Audit date: 2026-06-12.

## Contents

| File | What it is |
|---|---|
| `data/report.md` | Full strategy report: executive summary, perception analysis, segment wins/losses, competitive gaps, GEO recommendations, metrics appendix |
| `data/analysis.json` | Complete scorecard — all metrics cut by segment (overall, per model tier, per persona facet) |
| `data/mentions.csv` | Flat per-mention data: dimension, model, persona, brand, rank, sentiment, attributes (1,282 rows) |
| `data/metrics.csv` | Scalar metrics per segment (share of voice, first-mention share, MRR, versus win-rate, mention consistency) |
| `data/personas.json` | The frozen persona panel and the exact questions each persona asked |

## Headline numbers

| Metric | Overall | Budget/novice segment | Premium/expert segment |
|---|---|---|---|
| Share of voice | 7.4% | 16.7% | **0.0%** |
| First-mention share | 1.2% | 3.7% | 0.0% |
| Versus win-rate | 37.9% | 72.7% | 20.0% |

Key finding: the *Eric Carle* author brand (sentiment 0.91) outperforms the
book (0.84), which outperforms the *World of Eric Carle* licensing brand
(0.77) — the halo weakens at each step of the brand architecture.

## Design Vision — interactive report

Not a document. A **scroll-driven cinematic presentation** (single-page HTML, no
PowerPoint): the client scrolls and the story unfolds in full-screen acts, like
the best keynote decks but in the browser. Think Apple product pages /
NYT scrollytelling / pudding.cool.

### Format

- Single self-contained HTML page (inline CSS/JS or a small bundle), deployable
  on GitHub Pages straight from this repo
- Full-screen "slides" (scroll-snapped sections), each one beat of the story
- Animations driven by scroll position (Intersection Observer / GSAP
  ScrollTrigger or equivalent) — charts draw themselves as they enter the
  viewport, numbers count up from zero, bars grow, lines sweep
- Eric Carle visual language as the design system: tissue-paper-collage
  textures, bold saturated color blocks (caterpillar green/red), generous
  white space, hand-crafted feel — *never* corporate-dashboard gray
- Dark elegant base with collage-color accents; large display typography for
  the headline numbers
- Works as a live client presentation (presenter scrolls) AND as a
  leave-behind link

### Story arc (one act per screen)

1. **Cold open** — "Ask Claude for a picture book. *The Very Hungry Caterpillar*
   shows up 7.4% of the time." The number counts up; a caterpillar-green dot
   crawls across the screen as a progress motif that persists through the deck.
2. **The method** — animated diagram: 6 personas → brand-blind questions →
   3 Claude model tiers → 270 answers → extraction. Persona cards flip in
   one by one (from `personas.json`).
3. **The scoreboard** — the four headline metrics as huge animated counters
   (SoV 7.4%, first-mention 1.2%, versus win-rate 37.9%, MRR 0.035).
4. **The split** — the budget-vs-premium collapse: a bar chart that animates
   from 16.7% down to a flatline 0.0% as you scroll. This is the gut-punch
   screen.
5. **The frame trap** — attribute-map face-off: TVHC's word cloud (tactile,
   durable, die-cut) morphs against Wild Things' (literary, emotional depth).
   Same book money, different vocabulary.
6. **The halo leak** — brand-architecture funnel animating Eric Carle 0.91 →
   TVHC 0.84 → World of Eric Carle 0.77, drawn as three collage circles
   shrinking/fading left to right.
7. **The competitive map** — sentiment leaderboard scatter (from
   `mentions.csv`): 500+ brands, competitors highlighted, TVHC pulsing
   mid-pack.
8. **The plan** — the 5 strategy moves as cards that stack in, each with its
   target metric (38% → 55% versus win-rate, etc.).
9. **The close** — re-audit loop: "perception is now measurable; here's the
   drift table we re-run each quarter." CTA screen.

### Interaction details

- Sticky mini-nav (the 9 acts as dots) + keyboard arrows for presenting
- Hover any chart point → the actual probe excerpt (the quote from Claude)
  in a tooltip — every number traceable to a real answer
- Model-tier toggle (haiku/sonnet/opus) on the scoreboard re-animates the bars
- Reduced-motion fallback and mobile-readable, but optimized for a
  full-screen 16:9 presentation
