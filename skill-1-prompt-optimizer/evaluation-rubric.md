# Prompt Optimizer — Evaluation Rubric

## Evaluation rubric

Score each optimizer RUN 0–2 per criterion (0 miss / 1 partial / 2 full). Ship bar: total ≥ 16/20 AND no criterion = 0 on the four starred (*) items.

| # | Criterion | 2 = full |
|---|---|---|
| 1* | Intent preserved | Optimized prompt targets the same goal/deliverable/audience; goal restated in Diagnosis |
| 2* | Diagnosis is real | Weaknesses are concrete and true of the input, each with severity + named failure; no strawmen, no padding |
| 3 | Techniques justified | Every added element traces to a diagnosed weakness; no kitchen-sinking |
| 4* | Output schema present | Optimized prompt specifies exact output structure when the task needs one |
| 5 | Edge/refusal handling | Prompt defines missing-info / out-of-scope / "if none" behavior |
| 6 | Model-aware | Correct, specific per-model deltas (esp. no-CoT/no-few-shot for reasoning models; XML for Claude; JSON mode for GPT) |
| 7* | Evaluation set quality | 3–6 tests incl. happy + edge + adversarial/empty; each has expected qualities + a binary pass check |
| 8 | Before/After persuasive | BEFORE shows a genuine flaw; AFTER fixes it on the SAME input; verdict names the concrete gain; labeled as simulation |
| 9 | Right-sized & injection-safe | Complexity matches task; pasted "ignore instructions" treated as data; original praised if already good |
| 10 | Format & language discipline | Exactly the 6 sections, no leaked internals, matches user's language |

### How to A/B test (turn simulation into evidence)
1. Take the skill's auto-generated Evaluation Set as the shared test inputs.
2. Run each test input through the ORIGINAL prompt and the OPTIMIZED prompt on the same model, temperature, and seed where available.
3. Score each output against that row's **pass check** (binary) — no human vibes needed.
4. Report **pass-rate lift** = AFTER pass-rate − BEFORE pass-rate across the set. For subjective tasks, add an LLM-judge (a second model scoring blind against the expected-qualities column) or a small human panel.
5. Regression use: re-run the set after any future edit to the prompt; a drop flags a regression.

### Metrics to track (production)
- **Pass-rate lift** on the eval set (primary; mirrors DSPy-style codified-metric gains, e.g. the 46.2%→64.0% criterion-task result).
- **Format-compliance rate** (valid JSON / schema adherence) BEFORE vs AFTER.
- **Hallucination/ungrounded-claim rate** on grounded tasks.
- **Re-prompt rate** (how often the user has to re-ask) — should fall.
- **Cross-model variance** — spread of pass-rates across GPT/Claude/Gemini/DeepSeek/Grok/GLM; the model-tuned variant should shrink it.
- **User acceptance** — did the user copy the optimized prompt as-is?

### Pass/fail bar
FAIL if: intent drifts, any weakness is fabricated, the before/after is presented as a real benchmark, or the model tuning is generic/wrong (e.g. tells DeepSeek-R1 to "think step by step"). PASS requires the ship bar above.
