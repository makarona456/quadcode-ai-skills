# Installing a skill in Quadcode AI

These skills are authored in the **portable Agent-Skills format** — a `SKILL.md` with a small
YAML frontmatter block (`name`, `description`, `version`, `tags`, `model`, `tools`) followed by a
Markdown instruction body. That format maps cleanly onto Quadcode AI's YAML-based agent/skill
configuration. Field labels in the builder may differ slightly from the names below — map by
meaning, not by exact spelling.

## Field mapping

| Agent-Skills field (in `SKILL.md`) | Quadcode AI skill/agent field | Notes |
|---|---|---|
| `name` | Skill name / id | keep it short + kebab-case |
| `description` | Skill description / summary | ≤ 500 chars; this is what the router uses to decide when to invoke the skill |
| Markdown body of `SKILL.md` **or** `system-prompt.md` | System prompt / Instructions | **Use `system-prompt.md`** — it is the full, hardened instruction body. The `SKILL.md` body is the user-facing summary. |
| `model` | Model selection | `any` = leave the user's chosen model; Data Storyteller benefits from a strong reasoning model (Claude Opus/Sonnet or GPT) for the number-audit stage |
| `tools` | Enabled tools / agents | see below |

## Tools each skill needs enabled

- **Prompt Optimizer:** none. Text-only. Works on any model, no integrations.
- **Data Storyteller:** enable **Lumi** (image generation), a **code sandbox** (Python/SVG — used for deterministic chart rendering and all arithmetic), and, only if you want the video, **Sonic** (TTS voiceover / music / video).

## Step-by-step

1. In Quadcode AI, create a new skill/agent.
2. Paste the contents of `system-prompt.md` into the **System prompt / Instructions** field.
3. Copy `name` and `description` from the top of `SKILL.md` into the corresponding fields.
4. Set the model (`any` for Prompt Optimizer; a strong reasoning model for Data Storyteller).
5. Enable the tools listed above (Data Storyteller only).
6. Save. Test with the inputs in `RUN-CHECKLIST.md`.

## Reference YAML (if the builder accepts a raw config)

If Quadcode AI lets you paste a raw YAML skill config, this is the shape to fill in — replace
`SYSTEM_PROMPT_HERE` with the full contents of `system-prompt.md`:

```yaml
name: prompt-optimizer
description: >-
  Turns a rough LLM prompt into a production-grade one and proves the gain:
  diagnosis, rewrite, model-specific variants, auto-generated test cases,
  and a BEFORE/AFTER output contrast. Safety-gated and injection-resistant.
model: any
tools: []
system_prompt: |
  SYSTEM_PROMPT_HERE
```

```yaml
name: data-storyteller
description: >-
  Turns raw data (CSV/JSON/table) into a polished, provenance-audited,
  on-brand infographic image, with an optional narrated explainer video.
  Never fabricates a number; renders figures deterministically.
model: claude-opus   # or any strong reasoning model
tools: [lumi_image, code_sandbox, sonic_video]
system_prompt: |
  SYSTEM_PROMPT_HERE
```

> **Note on encoding (from the platform FAQ):** Quadcode AI's Python runtime expects strict
> **UTF-8 without BOM** and dislikes Cyrillic characters in project paths. Save these files as
> UTF-8 and keep the project folder path Latin-only to avoid the YAML-loading errors described
> in the platform's FAQ.
