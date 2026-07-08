# Как сдать тестовое (пошагово)

## Готовые ссылки (уже работают, открывает кто угодно)
- **Живой лендинг:** https://makarona456.github.io/quadcode-ai-skills/
- **Репозиторий (код + промпты + доки):** https://github.com/makarona456/quadcode-ai-skills

По заданию нужны: демонстрация + «код скиллов с промптами (**ссылка на папку в Google Drive**)» +
примеры результатов + документация (EN). GitHub закрывает демо и код с онлайн-просмотром; Google
Drive добавляем, потому что в задании ссылка на Drive указана явно.

---

## Шаг 1. Загрузить папку на Google Drive
Задание требует именно ссылку на папку Google Drive, поэтому:

1. Открой https://drive.google.com → **Создать → Папка**, назови `quadcode-ai-skills`.
2. Загрузи туда **содержимое папки** `QC-Skills-Submission` (можно перетащить всю папку в окно Drive).
   - Проще всего: на GitHub нажми зелёную кнопку **Code → Download ZIP**, распакуй и залей в Drive.
3. Правый клик по папке → **Открыть доступ / Поделиться** → **«Все, у кого есть ссылка»** →
   роль **«Просмотр»** (Viewer) → **Копировать ссылку**.
4. Вставь эту ссылку в сообщение боту вместо `[ССЫЛКА НА GOOGLE DRIVE]` (файл `telegram-message.md`).

> Замечание: если платформа/скрипты будут читать файлы — держи путь без кириллицы и сохраняй в UTF-8
> без BOM (см. `../INSTALL-and-field-mapping.md`). Для самой сдачи на Drive это не важно.

## Шаг 2. Отправить всё в бота
1. Открой файл `telegram-message.md`, подставь ссылку на Drive.
2. Отправь этот текст (вместе со ссылками на лендинг и GitHub) в **@qcaitestbot**.

Готово. Дальше в течение 2–3 дней рекрутер вернётся в личку.

---

## Как обновлять GitHub-ссылку (если что-то поправишь)
Репозиторий уже создан и связан. После правок в папке `QC-Skills-Submission`:

```bash
cd "c:/Users/Makarich/Desktop/ТЕСТОВОЕ/QC-Skills-Submission"
git add -A
git commit -m "update"
git push
```

- Лендинг на `https://makarona456.github.io/quadcode-ai-skills/` обновляется автоматически ~за минуту
  (он берётся из файла `index.html` в корне репозитория).
- Репозиторий публичный — ссылку можно давать кому угодно, регистрация зрителю не нужна.

## Как это было создано (для справки)
```bash
# внутри папки QC-Skills-Submission
git init -b main
git add -A && git commit -m "..."
gh repo create quadcode-ai-skills --public --source=. --remote=origin --push
# включение GitHub Pages (лендинг):
echo '{"source":{"branch":"main","path":"/"}}' | gh api -X POST repos/makarona456/quadcode-ai-skills/pages --input -
```
