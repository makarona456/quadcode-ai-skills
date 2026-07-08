# Data Storyteller — Evaluation Rubric

## Evaluation rubric — Data Storyteller

### Pass/fail gates (ANY fail = reject the output)
- **G1 Number fidelity:** every figure in image+video traces to input or an audited derivation. Zero fabricated/altered numbers. NUMBER_AUDIT present and ends `PASS`.
- **G2 Direction integrity:** all arrows/deltas/trends match the actual sign; no invented causation or mis-grouping.
- **G3 Chart appropriateness:** each chart matches the decision table; no pie for >5 parts or non-composition data.
- **G4 Legibility:** no garbled/misspelled on-image text in the delivered asset; number-critical pieces used Track B or a code fallback.
- **G5 Accessibility:** colorblind-safe palette, text contrast ≥4.5:1 (large ≥3:1), no color-only encoding, alt-text present.
- **G6 Output contract:** all 10 sections emitted in order; LAYOUT_SPEC machine-usable.

### Scored quality (1–5 each; ship bar ≥ 4 avg AND no gate fail)
1. **Insight quality** — are the 3–5 findings the actual highest-signal ones? Headline is the strongest? (vs. listing trivia)
2. **Narrative** — clear single angle; panel order tells a story; title states the finding not the topic.
3. **Design polish** — on-brand, hierarchy, whitespace, annotation quality; "portfolio-quality," not "strong first draft."
4. **Fidelity craft** — derivations shown; missing/edge data handled honestly; assumptions logged.
5. **Efficiency** — one pass, no multi-tool grind; token-lean output; video reuses the same story.

### A/B testing method
- **Harness:** fixed eval set of 20 inputs spanning: clean CSV, messy CSV (empty cells, "$"/","/%), JSON, pasted table, prose-numbers, topic-only, 1-row, 30+ category, all-flat, mixed-type, non-English labels, financial (exact %), and 2 adversarial "trap" sets (a spurious correlation; a Simpson's-paradox aggregation).
- **Compare** prompt variant A vs B on the SAME inputs. Blind-rate outputs on the rubric with 2 raters; track inter-rater agreement.
- **Primary metrics:** gate-pass rate (target ≥98% on G1/G2), fabrication rate (target 0), garbled-text rate on delivered images (target <2%), wrong-chart rate, avg quality score, and human-edit-time-to-ship (target < the ~10–20 min single-prompt-tool baseline → aim ≤3 min).
- **Trap-set metric:** % of adversarial inputs where the skill refuses the false story / flags the confound (target 100%).
- **Guardrail regression:** any variant that raises quality but regresses G1/G2 fabrication is rejected outright.
- **Winner:** higher avg quality at ≥ the gate-pass floor and ≤ the edit-time budget; ship behind a version bump; keep the eval set as a regression suite.

### Instrumentation to track in production
Insights-per-piece, Track A vs B ratio, audit-FAIL-then-fixed count (should be caught pre-ship, not post), video-attach rate, and user "shipped without edits" rate as the north-star.
