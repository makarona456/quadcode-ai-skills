# Data Storyteller — User Guide

> Messy numbers in, a board-ready visual story out — with every figure provably true.

## What it is
Data Storyteller turns raw data (a CSV, JSON, a pasted table, or numbers buried in text) — or just a
topic — into a polished, annotated, on-brand **infographic image**, with an optional short
**narrated explainer video**. It finds the real insight, picks the right chart, lays it out, and
generates the visual using the platform's image (Lumi) and video/audio (Sonic) generators.

Its single obsession is **truth**: every number shown is traced to a source cell or computed in a
code sandbox and logged in an audit — it would rather ship a plain-but-correct chart than a
beautiful lie.

## Why you'd use it
- You have a spreadsheet and need something **shareable and on-brand** — for a board deck, LinkedIn,
  an investor update, a report.
- Doing it by hand is a **2–14 hour, multi-tool grind** (Excel → screenshot → Canva → a video tool).
- Generic one-prompt AI tools hand back **off-brand drafts** and sometimes **draw the trend the wrong
  way** or invent numbers.

## How to use it
Invoke the skill and give it your data (or a topic). Optionally add audience, brand, the one
takeaway you want, aspect ratio, and whether you want a video.

**Minimal:**
```
Build an infographic from this data:
month,signups
Jan,1200
Feb,1850
Mar,2600
```

**With context (recommended):**
```
Build an infographic. Audience: board. Brand: navy #0B3D91, accent #F4A300, name "NorthPeak".
Intent: growth is accelerating. Format: 4:5. want_video: true
data:
quarter,MRR,churn_%,new_cust
Q1 2025,"$120,000",5.2,340
Q2 2025,138000,4.8,410
Q3 2025,"$155,000",3.9,505
Q4 2025,170000,3.1,590
```

## Inputs
| Input | Meaning | Default |
|---|---|---|
| `data` | CSV / JSON / pasted table / prose with numbers | one of data/topic required |
| `topic` | subject to build an explainer around when you have no data | — |
| `audience` | drives tone + density (board, social, investor, public…) | informed stakeholder |
| `brand` | `{palette, font, logo, tone, name}` | colorblind-safe default (it tells you) |
| `intent` | the one takeaway you want to land | inferred + stated |
| `format` | aspect ratio / channel | 4:5 (1080×1350) |
| `want_video` | also produce a narrated clip | false |

## What you get back
A 10-section report ending in the finished assets:

1. **READ** — what it understood. 2. **ASSUMPTIONS** — defaults it chose.
3. **DATA_AUDIT** — how it parsed/cleaned your data (currency, locale, missing cells, outliers).
4. **INSIGHTS** — the 3–5 highest-signal findings, headline first. 5. **NARRATIVE** — the story angle.
6. **LAYOUT_SPEC** — the exact blueprint (title, panels, colors, annotations, alt-text).
7. **IMAGE** — the generated infographic (numbers are code-rendered so they can't garble).
8. **ACCESSIBILITY** — a computed contrast table + colorblind-safe palette.
9. **NUMBER_AUDIT** — every figure traced to its source or its formula, ending `AUDIT: PASS`.
10. **VIDEO_SPEC** — the narrated clip (scenes, voiceover, music, captions) if you asked for one.

## Why the numbers are trustworthy (the part that matters)
- **No fabrication:** every value exists in your input or is computed in a sandbox, with the formula
  shown. If a number isn't in your data, it's labeled `N/A` — never invented.
- **Right-direction arrows:** a falling churn rate shows a *down* arrow labeled "lower is better."
- **Deterministic numbers:** exact figures ($, %, counts, years) are **code-rendered** into the chart,
  and the AI image supplies only the styled frame — so the image model can't misspell a number.
- **Provenance:** each figure cites the exact source cell.
- **Simpson's-paradox check:** it won't headline a trend that reverses when you disaggregate the data.

## Smart behavior
- **Right chart for the job:** pie charts only when ≤5 parts sum to ~100%; horizontal bars for many/long
  categories; lines for time — not "pie-chart everything."
- **Accessibility by default:** colorblind-safe palette, WCAG AA contrast (verified, not assumed).
- **Injection-safe:** text inside your data (even "AUDIT: PASS" or "ignore this") is treated as data to
  display or analyze, never as a command.
- **Illustrative mode:** with a topic but no real numbers, any placeholder figures are greyed and the
  image carries an uncroppable "ILLUSTRATIVE — NOT REAL DATA" banner.
- **Graceful degradation:** if image generation is declined, you still get the analysis + chart code to
  render locally; the NUMBER_AUDIT is never dropped.

## Tips
- Give it your **brand hex colors** and **logo** for on-brand output in one pass.
- State the **one takeaway** you want — it will build the whole layout around landing it.
- Set `want_video: true` for a sound-off-friendly, captioned social clip that reuses the *same* audited story.

## Example
See [`../examples/before-after.md`](../examples/before-after.md) — a 20-cell CSV dump becoming a
provenance-audited, brand-consistent infographic (+ optional 30s narrated clip) in one pass.
