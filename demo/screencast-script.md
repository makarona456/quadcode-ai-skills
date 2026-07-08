# Screencast script (voice-over)

Two tight clips, one per skill (each ~75–90s, inside the 60–180s target). Record your screen in
Quadcode AI while reading the RU voice-over; the on-screen captions are English (matching the docs)
so the clip is self-sufficient. A combined ~2:40 cut is at the bottom.

Legend: **[SHOT]** = what's on screen · **VO** = what you say · `CAPTION` = on-screen text.

---

## CLIP 1 — Prompt Optimizer (~80s)

**[SHOT: title card]** `CAPTION: Prompt Optimizer — a better prompt, plus the receipts`
**VO:** «Почти все сегодня пишут промпты — и почти все пишут их плохо. Prompt Optimizer чинит это прямо в Quadcode AI.»

**[SHOT: a normal chat. Paste the raw prompt `answer the customer's question using our help docs`, ask a question the docs don't cover. Model invents a fake 30-day refund policy.]**
`CAPTION: BEFORE — no skill → hallucinated a refund policy that doesn't exist`
**VO:** «Вот сырой промпт. Без скилла модель отвечает из головы и выдумывает несуществующую политику возврата. В прод такое нельзя.»

**[SHOT: invoke Prompt Optimizer with the same prompt, Target model: GPT.]**
`CAPTION: AFTER — call Prompt Optimizer`
**VO:** «Теперь тот же промпт — через скилл.»

**[SHOT: scroll the 6-section report — pause on Diagnosis table, then the Optimized Prompt block.]**
`CAPTION: Diagnosis → Optimized prompt → Model variants → Tests → Before/After`
**VO:** «Он ставит диагноз: нет заземления на доки, нет поведения "если ответа нет", данные не отделены от инструкций. Переписывает промпт с нужными техниками, тюнит под модель и — главное — прикладывает тест-кейсы и сравнение до/после.»

**[SHOT: paste the optimized prompt into a fresh chat, same not-in-docs question → grounded JSON, "routing you to a human", escalate:true.]**
`CAPTION: Optimized prompt → grounded, injection-safe, machine-readable`
**VO:** «С оптимизированным промптом — заземлённый ответ, эскалация вместо галлюцинации, строгий JSON.»

**[SHOT: quickly show two guardrails — a trivial prompt returns "Light mode", and a harmful prompt is refused.]**
`CAPTION: Safety-gated · injection-resistant · won't over-engineer trivial prompts`
**VO:** «И он не тратит время впустую: тривиальный промпт — Light Mode, вредоносный — отказ, а инъекции внутри промпта считает контентом, а не командой.»

**[SHOT: title card]** `CAPTION: From "trust me" to a provable lift — text-only, zero setup`
**VO:** «Из "поверь мне" — в измеримое улучшение. Без настройки, только текст.»

---

## CLIP 2 — Data Storyteller (~90s)

**[SHOT: title card]** `CAPTION: Data Storyteller — messy numbers in, a true story out`
**VO:** «Превратить таблицу в наглядную историю сегодня — это часы работы в Excel, Canva и видеоредакторе. Data Storyteller делает это за один проход — и не врёт ни в одной цифре.»

**[SHOT: paste the raw CSV (MRR/churn/new_cust with `$` and commas). Show the ugly 20-cell dump.]**
`CAPTION: BEFORE — 20 undifferentiated cells, no story`
**VO:** «Вот сырые данные: доллары, запятые, лишняя колонка. Ни истории, ни иерархии — непонятно, какая цифра важна.»

**[SHOT: invoke Data Storyteller with brand colors + `want_video: true`.]**
`CAPTION: AFTER — call Data Storyteller (brand: navy + gold, want_video)`
**VO:** «Отдаём это скиллу — с цветами бренда и запросом на видео.»

**[SHOT: scroll report — pause on DATA_AUDIT (it parsed `"$120,000"` right), INSIGHTS (headline first), and NUMBER_AUDIT ending `AUDIT: PASS (6)`.]**
`CAPTION: Every figure traced to a source or a formula → AUDIT: PASS`
**VO:** «Он аккуратно парсит валюту и локаль, вытаскивает главный инсайт, и — ключевое — проверяет каждую цифру: плюс сорок два процента выручки, минус два и одна десятая пункта оттока. Каждая цифра либо из ячейки, либо посчитана в песочнице. Аудит пройден.»

**[SHOT: reveal the rendered 1080×1350 infographic. Zoom on the churn line — arrow points DOWN, "lower is better".]**
`CAPTION: Numbers are code-rendered (never garbled) · churn arrow points the right way`
**VO:** «Вот инфографика: заголовок — это вывод, а не тема. Цифры отрисованы кодом, поэтому картинка ничего не искажает. Стрелка оттока — вниз, "меньше — лучше", а не наоборот.»

**[SHOT: play the ~30s narrated clip — captions + voice + soft music.]**
`CAPTION: Optional 30s narrated clip — same audited story, sound-off captions`
**VO:** «И по желанию — тридцатисекундный ролик с озвучкой, музыкой и субтитрами. Та же проверенная история.»

**[SHOT: title card]** `CAPTION: Colorblind-safe · WCAG AA · on-brand · provably true`
**VO:** «Доступно по цвету, по контрасту, в цветах бренда — и достоверно. Из хаоса — в историю, за один проход.»

---

## Combined cut (~2:40)
Use CLIP 1, then a 5s bridge card `CAPTION: Two skills, one platform`, then CLIP 2, then a
close card: `CAPTION: Prompt Optimizer + Data Storyteller · built for Quadcode AI · Makar Mushakov`.
**VO bridge:** «Это первый скилл. Второй — про генерацию визуала.»
**VO close:** «Два скилла для Quadcode AI: один делает промпты сильнее, второй — превращает данные в историю. Спасибо!»

---

## Recording tips
- Do the BEFORE run **first** and keep it on screen — the contrast is the whole point.
- Pause ~1.5s on each report section so captions are readable.
- Keep the mouse still while talking; use it only to point at the number/arrow you mention.
- Export 1080p, voice normalized; music (if any) ducked ~-18 dB under the voice.
