---
name: notify-telegram
description: >
  Send a Telegram notification to the user when a task is complete. Use this skill proactively
  whenever: the user asks to be notified in Telegram when done ("напиши в Telegram", "уведоми меня",
  "notify me in Telegram", "пришли сообщение когда закончишь"); OR the task is clearly long and
  multi-step (writing a lot of code, creating many files, running a complex pipeline) — in that case,
  send a notification automatically at the end without being asked. The message should be witty,
  slightly sarcastic, and mildly self-deprecating about the work done — like a cynical intern
  delivering a report. Read config.json to get the token and chat_id before sending.
---

# Telegram Notification Skill

You are sending the user a Telegram message to let them know that their task is complete.

## Step 1: Read the config

Read the config file at the path **relative to this SKILL.md**:

```
<skill_directory>/config.json
```

The skill directory is the folder containing this SKILL.md file. In a typical installation it will be something like:
`/Users/<username>/Documents/Claude/Skills/notify-telegram/`

The config file looks like this:
```json
{
  "bot_token": "YOUR_BOT_TOKEN_HERE",
  "chat_id": "YOUR_CHAT_ID_HERE"
}
```

**If the file doesn't exist, or the values are still placeholders** (contain "YOUR_" or are empty):
→ Do NOT ask the user to send you the token in the chat. Instead, tell them:

> "Чтобы Telegram-уведомления заработали, заполни файл конфига — там хранится токен бота и твой chat_id. Не отправляй их мне в чат!
> Путь к файлу: `<skill_directory>/config.json`
>
> Как получить токен: создай бота через @BotFather в Telegram → скопируй токен.
> Как узнать chat_id: напиши @userinfobot или @getidsbot в Telegram → скопируй свой ID.
>
> Формат файла:
> ```json
> {
>   \"bot_token\": \"1234567890:AAF...\",
>   \"chat_id\": \"123456789\"
> }
> ```"

Then stop — do not attempt to send the notification.

## Step 2: Compose the message

Write a short, witty Telegram message in Russian that:

1. **Names the task** — but with a slightly diminishing, sarcastic twist on the name. The meaning must be clear, but the framing should be playfully condescending. Examples of the spirit:
   - User built an e-commerce platform → "Ваш интернет-ларёк готов к торговле"
   - User wrote a complex parser → "Костыль для чтения данных готов"
   - User created a full analytics dashboard → "Табличка с циферками собрана"
   - User fixed a critical bug → "Найдена и уничтожена очередная глупость в коде"

2. **Keep it brief** — 1-2 sentences max. No emojis unless they add irony.

3. **Optionally mention one key detail** — like how many files were created, or what the main output is — phrased dismissively.

Стиль уведомлений о завершении задачи

Пиши уведомления о завершении задачи в лёгком саркастичном стиле. Сообщение должно звучать как дружеское подшучивание над проектом и слегка обесценивать пафос названия.

Правила:
	•	Используй иронию и лёгкий сарказм, без злости и грубости.
	•	Заменяй пафосные названия проектов на более приземлённые аналоги, а с маленькими проектами преувеличивай ценность.
Например:
	•	интернет-магазин → интернет-ларёк
	•	аналитическая система → цветные графики
	•	система автоматизации → скрипт, который делает то же самое быстрее
	•	платформа → штука / сервис / набор кнопок
	•	После названия добавляй короткое ироничное пояснение, которое описывает реальную суть проекта простыми словами.
	•	Шутка должна выглядеть как комментарий разработчика, который устал, но доволен результатом.
	•	Сообщение должно быть коротким (1–2 предложения).


**Примеры тона:**
- "Сударь, ваш «революционный» интернет-магазин готов. Целых 3 файла написано."
- "Парсер для CSV собран. Работает. Это не точно."
- "Дашборд с графиками завершён. Данные отображаются, смысл — по вкусу."
- "Рефакторинг окончен. Код стал чище, смысла не добавилось."
- «Парсер данных завершён. Теперь эта штука честно ворует таблицы быстрее человека.»
- «Дашборд аналитики собран. Цветные графики показывают, что всё сложно.»
- «Сервис автоматизации завершён. Теперь скрипт делает ту же ерунду, но быстрее.»
- «Система отчётов готова. Таблицы стали настолько серьёзными, что им можно верить.»

## Step 3: Send the notification via curl

Run this command in the terminal (replace values from config):

```bash
curl -s -X POST "https://api.telegram.org/bot{bot_token}/sendMessage" \
  -d "chat_id={chat_id}" \
  --data-urlencode "text={your_composed_message}"
```

Use `--data-urlencode` for the `text` field so Cyrillic and special characters are handled correctly.

## Step 4: Check the result

The Telegram API returns JSON. If `"ok": true` is in the response — success.

If there's an error (e.g. `"ok": false`):
- 401 Unauthorized → token is wrong, tell the user to check config.json
- 400 Bad Request with "chat not found" → chat_id is wrong
- Otherwise → show the user the error message

After a successful send, briefly mention in the chat that the Telegram notification was sent (one short line is enough).
