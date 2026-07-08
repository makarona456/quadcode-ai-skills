# Quadcode AI — Skills Engineer Test Task

**Author:** Makar Mushakov · mmm110908@gmail.com · Telegram [@Makarich456](https://t.me/Makarich456)
**Deliverable:** two production-grade, reusable skills for the Quadcode AI platform.

### ▶ Live demo (self-contained — open in any browser)
- **Hosted page:** https://makarona456.github.io/quadcode-ai-skills/
- **Or open locally:** double-click [`index.html`](index.html) — no server, no dependencies.

It shows what each skill does, how it works, the before/after, guardrails, a live infographic, and
the demand evidence — no extra reading required.

---

## What's inside

Two skills, each solving a real, in-demand problem, each shipped with optimized prompts,
an evaluation rubric, an adversarial red-team report, and a concrete **before-skill vs
with-skill** comparison.

| # | Skill | What it does | Uses |
|---|-------|--------------|------|
| 1 | **Prompt Optimizer** | Turns a rough LLM prompt into a production-grade one **and proves the gain** — diagnosis, rewrite, model-specific variants, auto-generated test cases, and a BEFORE/AFTER output contrast. | Text (any model: GPT / Claude / Gemini / DeepSeek / Grok / GLM) |
| 2 | **Data Storyteller** | Turns raw data (CSV / JSON / a pasted table) into a polished, annotated, on-brand **infographic image** — with an optional short **narrated explainer video**. Every number is provenance-audited. | Lumi (image), Sonic (video / TTS / music), code sandbox (deterministic charts) |

Both skills satisfy the task requirement explicitly: **if a skill improves something, it shows the result without the skill and with the skill.**

---

## Folder map

```
QC-Skills-Submission/
├── README.md                      ← you are here (English user docs)
├── INSTALL-and-field-mapping.md   ← how to load a skill into the Quadcode AI builder
├── RUN-CHECKLIST.md               ← how to run each skill and capture real results
│
├── skill-1-prompt-optimizer/
│   ├── SKILL.md                   ← the skill definition (portable Agent-Skills format)
│   ├── system-prompt.md           ← the hardened system prompt (the core IP)
│   ├── pipeline.md                ← the internal step-by-step method
│   ├── evaluation-rubric.md       ← how quality is measured / A-B tested
│   ├── extras.md                  ← technique library + per-model tuning notes
│   ├── market-research.md         ← why this is in demand (cited)
│   ├── red-team-report.md         ← adversarial findings + hardening changelog
│   ├── docs/USER-GUIDE.md         ← end-user guide (English)
│   └── examples/
│       ├── live-run.md            ← a real, unedited run of the skill (its actual output)
│       ├── few-shots.md           ← worked examples
│       └── before-after.md        ← BEFORE (no skill) vs AFTER (with skill)
│
└── skill-2-data-storyteller/      ← same structure
```

---

## The 30-second pitch for each

### 1. Prompt Optimizer — *"a better prompt, plus the receipts"*
Hundreds of millions of people now write prompts, and most write bad ones. Existing rewriters
change wording but never prove they helped, and a prompt tuned for one model silently
underperforms on another. Prompt Optimizer **diagnoses** the weaknesses, **rewrites** the prompt
with the right techniques, **tunes it per model**, generates **test cases**, and renders a
**BEFORE/AFTER** so the user can *see* the lift — all inside the IDE, zero setup, text-only.
It is safety-gated, injection-resistant, and right-sized (it refuses to over-engineer a trivial prompt).

### 2. Data Storyteller — *"messy numbers in, board-ready story out"*
Turning a spreadsheet into a shareable, on-brand visual today is a 2–14 hour, multi-tool grind
(Excel → screenshot → Canva → a video tool). Data Storyteller does it in one governed pass:
it finds the real insight, picks the right chart, lays out an annotated infographic, and
generates the image — with an optional narrated video. Its obsession is **truth**: every figure
is traced to a source cell or computed in a sandbox and logged in a NUMBER_AUDIT, numbers are
**code-rendered** so the image model can't garble them, and the palette is colorblind-safe with
verified WCAG contrast.

---

## How these were built (engineering approach)

Each skill went through a four-stage pipeline before shipping:

1. **Demand research** — web-grounded evidence that the problem is real and current (see each `market-research.md`).
2. **Prompt engineering** — a full production system prompt (role → method → constraints → guardrails → strict output format), optimized for token efficiency and cross-model robustness.
3. **Adversarial red-team** — a QA pass that tried to break each prompt with hostile, malformed, and edge-case inputs (see each `red-team-report.md`).
4. **Hardening** — every valid finding folded back into the prompt (see the changelog in each red-team report).

This mirrors exactly what the Skills Engineer role asks for: optimized, A/B-testable, edge-case-hardened, well-documented skills.

---

## Start here
- To **use** a skill: read `skill-*/docs/USER-GUIDE.md`.
- To **install** a skill in Quadcode AI: read `INSTALL-and-field-mapping.md`.
- To **reproduce the results** shown in the demo: follow `RUN-CHECKLIST.md`.
