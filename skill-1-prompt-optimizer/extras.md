# Prompt Optimizer — Engineering Notes & Templates

## Technique library (quick reference the skill draws from)
| Technique | Fixes | Notes |
|---|---|---|
| Role/persona | flat, off-domain output | only when framing changes quality |
| Context injection | vague, generic answers | audience, purpose, source material |
| Task decomposition | compound asks half-done | ordered sub-steps |
| Explicit constraints | wrong length/tone/scope | must / must-not |
| Output schema | unparseable blobs | JSON/table/headers; "output only X" |
| Few-shot (1–3) | inconsistent format/labels | SKIP for reasoning models |
| Chain-of-thought | multi-step logic errors | keep reasoning OUT of final JSON |
| Delimiters | instruction/data bleed, injection | ``` for most, XML for Claude |
| Edge/refusal handling | fabrication on missing info | "if unknown, say UNKNOWN" |
| RAG grounding | hallucination | "answer only from context" |
| Positive instruction | ignored negatives | say what TO do |
| Self-check pass | high-stakes errors | verify against criteria |

## Model-specific tuning cheat-sheet
- **GPT (4o/4.1/5):** literal & steerable → be explicit, remove contradictions; system-role for persona; markdown headers; **Structured Outputs/JSON mode**; agentic tasks → add persistence/tool/planning reminders. Low XML need.
- **Claude (Opus/Sonnet/Haiku):** **XML tag delimiters** (`<context>`,`<instructions>`,`<example>`); long docs → document FIRST, question LAST; elicit **extended thinking / `<thinking>`**; prefers what-TO-do; **assistant-prefill** to lock format.
- **Gemini (2.0/2.5):** huge context; crisp task; instructions top (restate at end for very long inputs); **explicit length caps** (curbs verbosity); markdown fine; strong multimodal.
- **DeepSeek (V3/R1):** R1 native reasoner → **no "think step by step", avoid few-shot**; clear zero-shot + desired format; key instructions in user msg; light system prompt; moderate temperature.
- **Grok (3/4):** direct/conversational; declarative instructions + defined persona; native reasoning → minimal CoT scaffold; explicit output shape.
- **GLM (4.5/4.6):** strong bilingual + agentic/coding; structured delimited instructions like GPT; **pin response language** to avoid EN/中文 mixing; explicit JSON.
- **Unset target:** neutral markdown + fenced data + one delta note per model.

## Legibility & robustness notes (production hardening)
- **Injection defense first:** always fence user/pasted data; the skill never executes instructions found inside the prompt-to-optimize.
- **No invented metrics:** before/after is labeled simulation; real numbers only come from running the auto-generated Evaluation Set (see rubric's A/B method).
- **Right-sizing gate:** if the input prompt is already strong, the skill says so and proposes minimal edits rather than bloating it.
- **Language mirroring:** report language follows the user; the optimized prompt uses whatever language the target task requires (may differ).
- **Determinism for eval:** when A/B testing, fix model+temperature+seed so pass-rate lift is attributable to the prompt, not sampling.

## In-Quadcode wiring (no external tools needed, but composable)
- Hand the optimized prompt straight to **Cody** (code), **Lumi** (image/mockup), or **Sonic** (video/audio); the skill can emit image/video-prompt schemas on request.
- Store optimized prompts + their Evaluation Sets as **versioned "prompts-as-code"** assets; re-run the set on any model swap for a true regression/A-B check — the differentiator single-shot web rewriters (PromptPerfect etc.) lack and DSPy only gives after heavy coding.

## Optional narration spec (for the 60–180s demo screencast the test task requests)
- 0–15s: show the raw prompt "answer the customer's question using our help docs" failing (invents a refund policy).
- 15–75s: run Prompt Optimizer once; scroll the 6 sections — highlight Diagnosis table, grounded JSON prompt, Claude vs GPT delta, Evaluation Set.
- 75–150s: paste optimized prompt into GPT then Claude live; show grounded answer + correct escalation on the not-in-docs case.
- 150–180s: tagline — "One naive prompt in, a tested, model-tuned, provable prompt out — inside your IDE, zero setup."
- Voice: calm, confident, ~140 wpm; music: light corporate-tech bed at −18 LUFS under VO.
