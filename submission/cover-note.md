# Cover note — Skills Engineer test task

**Кандидат:** Мушаков Макар Максимович · mmm110908@gmail.com · [@Makarich456](https://t.me/Makarich456)

## Что сдаётся
Два готовых скилла для платформы Quadcode AI:

1. **Prompt Optimizer** — свободный выбор идеи (Скилл 1). Переписывает промпт и доказывает улучшение.
2. **Data Storyteller** — генерация графики/визуализации (Скилл 2). Данные → достоверная брендовая инфографика (+ опц. видео).

## Соответствие требованиям задания
| Требование задания | Где выполнено |
|---|---|
| Скилл 1 — актуальная задача из открытых источников | `skill-1-prompt-optimizer/market-research.md` (с цитатами) |
| Скилл 2 — использует генеративные возможности (изображения/видео/звук) | Lumi (image) + Sonic (video/TTS/music) — `skill-2-data-storyteller/` |
| «Результат без скилла / со скиллом» | `examples/before-after.md` в каждом скилле + демо-лендинг |
| Оптимизированные промпты, edge-cases, современные AI-подходы | `system-prompt.md` + `red-team-report.md` в каждом скилле |
| Демонстрация (лендинг/статья/презентация/скринкаст) | Демо-лендинг (ссылка ниже) + `demo/screencast-script.md` |
| Код скиллов с промптами | `SKILL.md` + `system-prompt.md` + `pipeline.md` |
| Примеры результатов | `skill-1/examples/live-run.md` (реальный прогон скилла) + `before-after.md` + живая инфографика на лендинге |
| Документация для пользователя (EN) | `README.md` + `docs/USER-GUIDE.md` (оба английские) |

## Ссылки
- **Демо-лендинг:** https://claude.ai/code/artifact/835692eb-3b92-4df2-ba35-6afec0506bce
- **Google Drive (исходники):** _подставить перед отправкой_

## Как это делалось
Каждый скилл прошёл конвейер: **research спроса → инженерия промпта → adversarial red-team → hardening**.
Это ровно та дисциплина, которую описывает вакансия Skills Engineer: оптимизированные, A/B-тестируемые,
устойчивые к edge-cases, задокументированные скиллы.

## Что осталось сделать кандидату (перед отправкой)
Скриншоты не обязательны — пакет самодостаточен (лендинг + `examples/live-run.md` + `before-after.md`).
1. Залить `QC-Skills-Submission/` на Google Drive, открыть доступ по ссылке.
2. Отправить в @qcaitestbot текст из `submission/telegram-message.md` (подставив ссылку на Drive).
3. *(Опц.)* прогнать скиллы в Quadcode AI и вложить живые рендеры/видео в `examples/` (гайд — `RUN-CHECKLIST.md`).
4. *(Опц.)* записать скринкаст по `demo/screencast-script.md`.
