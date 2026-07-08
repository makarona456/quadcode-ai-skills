# Data Storyteller — Engineering Notes & Templates

## A. Lumi image-generation prompt templates

**Track A — full AI-native infographic (light/1–2 charts):**
```
Flat modern editorial infographic, {aspect} ({W}x{H}), {bg} background, bold geometric sans-serif.
Header text "{TITLE ≤8 words}" in {text_hex}; subtitle "{SUBTITLE ≤14 words}" in {muted_hex}.
{Panel descriptions, each naming chart type + the EXACT short labels in "quotes" + hex fills}.
Accent color {accent_hex} used ONLY to highlight "{the one insight}".
High contrast, crisp legible text, generous whitespace, thin card dividers, {logo placement}.
```
**Universal negative prompt:** `garbled text, misspelled words, random glyphs, lorem ipsum, gibberish numbers, watermark, signature, 3D bevel, drop-shadow clutter, stock clipart, neon, oversaturated, busy background, distorted charts, extra axes`.

**Track B — styled frame only (deterministic, default for exact numbers):**
```
Clean infographic frame/background only, {aspect}, header band in {primary_hex}, empty card slots with subtle borders on {bg}, {logo} top-left, minimal geometric accents. NO charts, NO numbers, NO body text — leave chart areas blank. High contrast, flat, modern.
```
Then code-render each chart from LAYOUT_SPEC (matplotlib/plotly/SVG) and composite; typeset all text in code. This layer is the numeric source of truth.

## B. Style / brand presets (swap in brand tokens when given)
- **Corporate/Board:** navy primary, single warm accent, lots of whitespace, serif-free, one hero stat. Restrained.
- **LinkedIn/Social:** high-contrast, big title, 1–2 charts max, thumb-stoppable hero number, 4:5 or 1:1.
- **Investor:** dense-but-clean, trend + composition, explicit source line + timeframe, conservative palette.
- **Public/Nonprofit:** friendly rounded, iconography, plain-language callouts, extra accessibility.
- **Default safe (no brand):** Okabe-Ito colorblind-safe — `#0072B2 #E69F00 #009E73 #D55E00 #56B4E9 #CC79A7`; text `#111827`, muted `#6B7280`, bg `#FFFFFF/#F7F9FC`.

## C. Text-in-image legibility strategy (why Track B exists)
Diffusion models garble text as string count/length rises. Rules: (1) ≤~12 total text elements; (2) every string ≤5 words (title ≤8); (3) quote exact strings verbatim in the prompt; (4) demand "bold, large, high-contrast, crisp legible text"; (5) never place text over busy areas; (6) **fidelity-risk switch** → if any panel >6 numeric labels, exact $/%, >2 charts, small multiples, or C-suite/investor audience ⇒ Track B (code-rendered numbers, AI does frame only). LAYOUT_SPEC always carries chart-ready data so Track B is one step away even if Track A was attempted.

## D. Model-specific tuning
- **Analysis/audit stage (Claude Opus/Sonnet):** best at the verification discipline — keep the "emit NUMBER_AUDIT before finalizing" gate; Claude reliably refuses to invent. On GPT/Gemini, add an explicit "list any number you cannot source and DROP it" line — they hallucinate-fill more.
- **DeepSeek/GLM/Grok:** shorten the system prompt, front-load the 7 NON-NEGOTIABLES, and require the audit table as literal output (weaker instruction-following → make constraints checkable, not implicit).
- **Lumi (image):** always pass the negative prompt; request one clear style word ("flat editorial infographic"); if text garbles on regen, auto-fall-back to Track B rather than re-rolling.
- **Cross-model robustness:** keep numbers OUT of free-form generation and IN code whenever exactness matters — the most model-portable fidelity guarantee.

## E. Sonic narrated-video / voice / music spec
- **Length:** ≤60s (hits the sub-60s ≈2.5x-engagement demand). 5–8 scenes, 4–8s each.
- **Script:** ~110–150 words (≈2.4–2.5 wps); write for the ear — takeaway first, one number per line, spell tricky figures ("forty-two percent"), no clause pile-ups. **Only numbers present in NUMBER_AUDIT.**
- **Scene object:** `{visual: which panel / animated build, caption ≤7 words, vo_line}`. Build charts progressively (bar grows, line draws) to guide the eye.
- **Voice preset:** gender-neutral default, warm-confident for board, energetic for social; pace matched to audience; consistent single narrator.
- **Music:** light corporate/ambient; energy curve soft intro → **lift on the hero stat scene** → calm outro; ducked −18 dB under VO; no lyrics.
- **Captions:** burned-in for sound-off (majority of social viewing), ≤7 words/line, AA contrast (`#111827` on light plate), synced to VO.
- **End card:** logo + one-line takeaway + optional CTA.
- **SFX (optional):** a single soft "rise" on the key-stat reveal; avoid gimmicky stingers.
- **Fidelity:** the video is a re-timing of the audited infographic — no new analysis, no new numbers, same palette/brand.
