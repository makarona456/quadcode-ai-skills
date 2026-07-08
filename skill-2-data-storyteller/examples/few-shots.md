# Data Storyteller — Worked Examples (few-shot)

### Few-shot 1 — Messy CSV → infographic (data mode, Track B)

**INPUT**
```
want_video: false | audience: board | brand: {name:"NorthPeak", palette:["#0B3D91","#F4A300"], tone:"confident"}
data (pasted):
quarter, MRR, churn_%, new_cust, region
Q1 2025, "$120,000", 5.2, 340, NA
Q2 2025, 138000, 4.8, 410, NA
Q3 2025, "$155,000", 3.9, 505, NA
Q4 2025, 170000, 3.1, 590, NA
```

**OUTPUT (abridged to the load-bearing parts)**
```
## 1. READ  Quarterly SaaS KPIs, 4 quarters, board audience. Intent (inferred): "Growth is accelerating while churn falls." Render track: B (financials, exact %, board).
## 2. ASSUMPTIONS  churn_% read as monthly percent; "$" and commas stripped, values in USD; region constant (NA) → dropped from visuals.
## 3. DATA_AUDIT  4 rows→4, 5 cols→4 shown. MRR: currency USD (cleaned "$120,000"→120000). churn_%: percent. new_cust: count. No missing, no outliers. region dropped (single value).
## 4. INSIGHTS
- HEADLINE — MRR grew +42% Q1→Q4 ($120k→$170k). [MRR Q1,Q4] · trend
- Churn fell 40% relative, 5.2%→3.1% (−2.1 pts). [churn Q1,Q4] · trend/outcome
- New customers +74% (340→590), accelerating each quarter. [new_cust all] · trend
- Growth is compounding: QoQ MRR adds rose $18k→$15k→$15k while churn drag shrank. [MRR deltas] · composition
## 5. NARRATIVE  One angle: "durable, compounding growth." Order: headline MRR stat → MRR line (context) → churn line inverse (the why) → new-cust bars (the engine).
## 6. LAYOUT_SPEC  Canvas 1080×1350, 4:5. Title: "MRR Up 42% as Churn Hits a Low 3.1%". Subtitle: "NorthPeak SaaS KPIs · Q1–Q4 2025". 
  Panel1 stat-tile: "$170K MRR" +delta "▲42% YoY". Panel2 line MRR [120,138,155,170]k, highlight Q4. Panel3 line churn% [5.2,4.8,3.9,3.1], accent, "▼ lower is better". Panel4 bars new_cust [340,410,505,590], highlight Q4. 
  color_roles: primary #0B3D91, accent #F4A300 (highlight), positive #009E73, text #111827, bg #F7F9FC. Source line: "Source: NorthPeak internal, 2025." alt_text: "Line and bar charts showing MRR rising $120K→$170K (+42%), churn falling 5.2%→3.1%, new customers 340→590 across 2025."
## 7. IMAGE  TRACK B (board-grade, exact $/%). Chart render: matplotlib/SVG from Panel data (ground truth). Lumi frame prompt: "Clean modern flat infographic frame, top header band in #0B3D91 with white bold sans title area, 4:5 portrait, subtle #F7F9FC background, thin card dividers, NorthPeak logo top-left, NO chart data, NO body text, high contrast, crisp." negative: "garbled text, random glyphs, watermark, 3D, clipart, neon, clutter." Composite: place 4 code-rendered panels into frame slots; typeset title/callouts in code.
## 9. NUMBER_AUDIT
  $170K ← MRR Q4 170000 ✓ | +42% ← (170000−120000)/120000=0.4166→42% ✓ | 3.1% ← churn Q4 ✓ | −2.1 pts ← 5.2−3.1 ✓ | +74% ← (590−340)/340=0.735→74% ✓ | arrows: MRR▲(rising)✓ churn▼(falling)✓ | AUDIT: PASS (6)
## 10. VIDEO_SPEC: skipped (want_video=false)
```

### Few-shot 2 — Topic + prose numbers → single-chart infographic + video (topic mode, Track A)

**INPUT**
```
want_video: true | audience: LinkedIn | format: 1080x1350 | brand: none
topic + prose: "Our support team cut average first-response time from 9 hours to under 2 hours after we added AI triage last quarter, and CSAT went from 82% to 91%."
```

**OUTPUT (abridged)**
```
## 1. READ  Topic post w/ two supplied metrics, LinkedIn audience. Intent: "AI triage sharply improved support speed + satisfaction." Track: A (only 2 exact numbers, 1–2 simple panels).
## 2. ASSUMPTIONS  No brand → DEFAULT SAFE BRAND (Okabe-Ito) used. "under 2 hours" shown as "<2h" (not fabricated to a point value). Single before/after period.
## 4. INSIGHTS
- HEADLINE — First-response time fell ~78%, 9h→<2h after AI triage. [prose] · comparison(before/after)
- CSAT rose +9 pts, 82%→91%. [prose] · comparison
## 6. LAYOUT_SPEC  Title "AI Triage Cut Response Time From 9h to Under 2h". Subtitle "Support KPIs · last quarter". Panel1 before/after bars response-time [9h, <2h], accent on "after", "▼ ~78%". Panel2 stat "CSAT 82% → 91% (+9 pts)". color_roles: primary #0072B2, accent #E69F00, positive #009E73. alt_text: "Before/after: first response 9h to under 2h (~78% faster); CSAT 82% to 91%."
## 7. IMAGE  TRACK A. Lumi prompt: "Flat modern infographic, 4:5 portrait, white background, bold geometric sans, header text \"AI Triage Cut Response Time From 9h to Under 2h\" in dark #111827, two panels: left a before/after bar pair labeled \"9h\" and \"<2h\" (bars in #0072B2 and #E69F00), right a stat block \"CSAT 82% → 91%\" in #009E73, small \"+9 pts\" tag, high contrast, crisp legible text, generous whitespace." negative: "garbled/misspelled text, random glyphs, watermark, 3D bevel, clipart, neon, cluttered." (Fallback ready: same 2 charts renderable via SVG if text garbles.)
## 9. NUMBER_AUDIT  9h ← prose ✓ | <2h ← prose "under 2 hours", shown as bound not point ✓ | ~78% ← (9−2)/9=0.777, hedged "~" ✓ | 82%→91%,+9pts ← prose ✓ | AUDIT: PASS (4)
## 10. VIDEO_SPEC (≤30s, 5 scenes)
  S1 0–5s: title card, VO "What if your support team could answer 4x faster?" music soft.
  S2 5–12s: before/after bars build, caption "9h → under 2h", VO "Last quarter we added AI triage. First-response time dropped from nine hours to under two." music lifts.
  S3 12–20s: CSAT stat, caption "CSAT 82% → 91%", VO "Customer satisfaction climbed from eighty-two to ninety-one percent." 
  S4 20–27s: combined, VO "Faster answers, happier customers — same team." 
  S5 27–30s: end card logo + "AI triage: 4x faster support." 
  Voice: neutral, warm, ~2.4 wps. Music: light corporate, uplift on S2, duck −18 dB. Captions burned-in, ≤7 words/line, #111827 on white. VO uses only audited numbers.
```
