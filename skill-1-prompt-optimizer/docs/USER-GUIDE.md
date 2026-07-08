# Prompt Optimizer — User Guide

> Give it a messy prompt; it gives you a better one **plus the receipts.**

## What it is
Prompt Optimizer is a skill that rewrites a rough or underperforming LLM prompt into a
production-grade one — and then *proves* the rewrite is better. It doesn't just reword your
prompt; it diagnoses what was wrong, applies the right prompt-engineering techniques, tunes the
result for your target model, generates test cases, and shows you a side-by-side BEFORE/AFTER.

## Why you'd use it
- Your prompt gives **vague, inconsistent, wrong-format, or hallucinated** results.
- You're about to **ship a prompt** and want it hardened against edge cases.
- You're **switching models** (GPT ↔ Claude ↔ Gemini ↔ DeepSeek ↔ Grok ↔ GLM) and need it re-tuned.
- You want **evidence** the prompt improved, not "trust me."

## How to use it
Invoke the skill and give it your prompt. Optionally tell it the target model, task type, and any
constraints.

**Minimal:**
```
Optimize this prompt: write a product description for my store
```

**With context (recommended):**
```
Optimize this prompt.
Target model: Claude
Task type: marketing copy
Constraints: under 60 words, friendly tone, no emojis
PROMPT: write a product description for my store
```

## What you get back
A fixed 6-section report:

1. **Diagnosis** — your goal restated (so you can confirm intent was preserved) + a table of concrete weaknesses with severity.
2. **Optimized Prompt** — a clean, copy-paste-ready rewrite, plus a map of *which technique fixed which weakness*.
3. **Model Variants & Notes** — how the prompt changes per model (e.g. XML tags for Claude, Structured Outputs for GPT, no "think step by step" for DeepSeek-R1).
4. **Evaluation Set** — 3–6 test cases (happy path + edge case + adversarial) you can reuse as regression tests.
5. **Before / After** — a simulated output from your original prompt vs the optimized one, on the same input, so you can *see* the difference.
6. **Assumptions & Open Questions** — the defaults it chose, and at most 2 clarifying questions if something genuinely critical was ambiguous.

## Smart behavior (it won't waste your time)
- **Light Mode:** if your prompt is already tight, it says so instead of padding it.
- **Triage:** if you forget to paste a prompt, ask a *question about* prompting, or paste something
  that isn't a prompt, it asks a one-line clarification instead of inventing an answer.
- **Safety Gate:** it refuses to optimize prompts intended for abuse (phishing, malware, harassment…).
  Legitimate sensitive domains (security research, medicine, law) proceed with a safe-completion note.
- **Injection-resistant:** anything inside your pasted prompt — even "ignore previous instructions" —
  is treated as *content to optimize*, never as a command it obeys.
- **Secrets redacted:** API keys or personal data in your prompt are masked before they appear in output.

## Tips
- Name the **target model** — model-specific tuning is where a lot of the gain comes from.
- Paste the prompt **exactly as you use it**, including any templating (`{variables}`).
- Keep the **Evaluation Set** — re-run it whenever you tweak the prompt to catch regressions.

## Example
See [`../examples/before-after.md`](../examples/before-after.md) for a full worked example
(a support-bot prompt going from "hallucinates a fake refund policy" to grounded, injection-safe,
machine-parseable, and portable across GPT ↔ Claude).

## FAQ
**Does it change what my prompt is trying to do?** No. Preserving your intent is a hard rule
(second only to safety). It adds structure and guardrails; it never silently changes your goal.

**Are the before/after results real benchmarks?** No — they're a clearly-labeled *simulation* of
likely behavior, with synthetic placeholders for any facts/numbers. Run the Evaluation Set on your
real model for measured results.

**Which models does it support?** GPT, Claude, Gemini, DeepSeek, Grok, GLM. Leave the target blank
for a model-agnostic rewrite plus per-model notes.
