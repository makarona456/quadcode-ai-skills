# Data Storyteller — Internal Pipeline

## Internal execution pipeline (stages, I/O, generative calls)

**Stage 0 — Route & scope**
- In: user request. Out: mode = `data` | `topic`; audience, intent, format, brand, want_video resolved (defaults applied + logged). If blocked (no data, no topic, or brand-critical ambiguity) → emit ≤3 questions and stop. Else proceed.

**Stage 1 — Ingest & parse** (`file_read` / inline)
- In: raw CSV/JSON/pasted table/prose. Out: normalized typed table + preserved original strings. Handles delimiters, thousands separators, currency/%, merged headers, ISO dates, and number-extraction-from-prose. No generative call.

**Stage 2 — Clean & validate** (`code_sandbox`)
- In: normalized table. Out: DATA_AUDIT (rows/cols in→out, per-column type/unit, missing counts, outliers, aggregation to top-N/binning for large data). Edge-case branch: empty/1-row → stat-tile-only; all-flat → no fake slope; huge → aggregate. Transformations logged; nothing imputed into a shown figure unflagged.

**Stage 3 — Insight extraction** (reasoning)
- In: clean table + audience + intent. Out: 3–5 scored insights (magnitude×surprise×relevance) across archetypes, headline chosen, each with exact figures + source cells. Kills low-signal noise.

**Stage 4 — Narrative & chart selection** (reasoning + CHART DECISION TABLE)
- In: insights. Out: one angle, ordered panel plan, chart type per insight, highlight targets.

**Stage 5 — Layout spec** (reasoning)
- In: narrative + brand + format. Out: LAYOUT_SPEC (canvas/grid, title, subtitle, panels[] with exact data/labels/units/callouts, color_roles, logo, source, alt-text). This is the machine-readable contract feeding both render tracks.

**Stage 6 — Render decision + image** 
- Fidelity-risk check → choose Track A (AI-native) or Track B (deterministic).
- Track A: `lumi_image(prompt, negative_prompt, size)` with text-in-image protocol.
- Track B: `code_sandbox` renders real charts (matplotlib/plotly/SVG) from LAYOUT_SPEC = numeric ground truth → `lumi_image` produces styled frame/background only → composite (code) charts+typeset text over frame. 
- Out: final infographic image (or chart assets + composite plan). Track B is always reachable from the spec.

**Stage 7 — Accessibility pass** (`code_sandbox` contrast check)
- In: color_roles + text. Out: colorblind-safe confirmation, WCAG AA contrast pass/fix, non-color cues, alt-text.

**Stage 8 — Number audit (gate)** (reasoning)
- In: every figure in image+video. Out: audit table (shown→source/derivation→PASS/FAIL), sign/sum/max checks, `AUDIT: PASS (n)`. FAIL → loop back to Stage 5, do not emit.

**Stage 9 — Optional video** (only if want_video)
- In: audited story. Calls: `sonic_tts(script, voice)` → VO; `sonic_music(mood, duration)` → bed (ducked −18 dB); `sonic_video(scene_list, captions)` → assembled ≤60s clip with burned-in captions + end card. Out: VIDEO_SPEC + assets. No new numbers.

**Stage 10 — Assemble output** — emit the 10 fixed sections + deliverables.

Loops: Stage 8 failure → Stage 5. Missing brand → Stage 5 default-brand branch. Large/odd data → Stage 2 edge branch. Everything upstream of Stage 6 is model-agnostic reasoning; only 6/9 hit generative services.
