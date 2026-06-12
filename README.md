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
