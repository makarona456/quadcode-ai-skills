# Data Storyteller — BEFORE (no skill) vs AFTER (with skill)

## BEFORE (no skill) — a raw spreadsheet dump the user pastes
```
quarter,MRR,churn_%,new_cust,region
Q1 2025,"$120,000",5.2,340,NA
Q2 2025,138000,4.8,410,NA
Q3 2025,"$155,000",3.9,505,NA
Q4 2025,170000,3.1,590,NA
```
What the user actually has: 20 undifferentiated cells with `$`, commas, and a stray `region` column. No story, no hierarchy, no idea which number matters. To make it board-ready today they'd open Excel to build charts, screenshot them, rebuild + annotate in Canva/PowerPoint, hand-match brand colors, then re-author the whole thing again as a video in a separate tool — the documented ~2.3–14 hour, multi-tool grind — and a single-prompt AI tool would hand back an off-brand draft still needing 10–20 min of fixes (and might draw the churn arrow pointing the wrong way).

## AFTER (with Data Storyteller) — one governed pass
A **1080×1350 board-ready infographic**:
- **Title (the finding, not the topic):** "MRR Up 42% as Churn Hits a Low 3.1%"
- **Subtitle:** "NorthPeak SaaS KPIs · Q1–Q4 2025 · Source: internal"
- **Panel 1 — hero stat tile:** `$170K MRR` with `▲ 42%` in brand accent.
- **Panel 2 — MRR line** ($120K→$170K), Q4 highlighted — the momentum.
- **Panel 3 — churn line** (5.2%→3.1%) with `▼ lower is better` — the *why*, arrow correctly pointing down.
- **Panel 4 — new-customer bars** (340→590, +74%) — the growth engine.
- On-brand `#0B3D91`/`#F4A300`, Okabe-Ito-safe, AA contrast, logo, alt-text.
- **A NUMBER_AUDIT proving every figure:** `+42% ← (170000−120000)/120000 ✓`, `−2.1 pts ← 5.2−3.1 ✓`, `+74% ← (590−340)/340 ✓`, arrows sign-checked → `AUDIT: PASS (6)`.
- Numbers rendered deterministically (Track B: real SVG charts composited into a Lumi-styled frame), so nothing is garbled or invented.
- **Optional 30s narrated clip** reusing the *same* audited story: 5 scenes, TTS voiceover ("MRR grew forty-two percent while churn fell to a low three-point-one…"), light uplifting music ducked under the voice, burned-in captions, logo end card.

**The delta:** messy 20-cell dump → a portfolio-quality, brand-consistent, provenance-audited visual story (+ shareable video) in one pass — no Excel→screenshot→Canva→Synthesia relay, no wrong-direction arrows, no fabricated numbers, no 10–20 min of manual cleanup.
