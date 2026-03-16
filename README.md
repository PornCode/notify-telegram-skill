# notify-telegram — Claude Skill

> A Claude skill that sends you a sarcastic Telegram notification when your AI finishes a task.
> Скилл для Claude, который отправляет саркастическое уведомление в Telegram, когда задача завершена.

---

## 🇬🇧 English

### What it does

**notify-telegram** is a skill for [Claude](https://claude.ai) (Cowork / Claude Code) that automatically sends you a Telegram message when a long task is done — so you can walk away from your computer and come back only when the work is finished.

The notifications are written in a witty, slightly sarcastic tone, like a cynical intern delivering a report. Claude will subtly downgrade the name of your project:

- *"Your 'revolutionary' online store is ready. A whole 3 files written."*
- *"CSV parser assembled. Works. Probably."*
- *"Analytics dashboard complete. The colorful charts show that everything is complicated."*

### When Claude sends the notification

- You explicitly ask: *"notify me in Telegram when done"*, *"write me in Telegram"*, *"ping me when finished"*
- The task is long and multi-step (writing code, creating many files, running a pipeline) — Claude sends it automatically without being asked

### Installation

#### Option 1 — Claude Desktop (Cowork)

1. Download [`notify-telegram.skill`](./notify-telegram.skill) from this repository
2. Open Claude desktop app → **Settings** → **Skills** → click **+**
3. Upload the `.skill` file
4. Find the installed skill folder and open `config.json`:
   ```
   ~/Library/Application Support/Claude/  (macOS)
   ```
5. Fill in your credentials (see Setup below)

#### Option 2 — Claude Code (terminal)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/notify-telegram ~/.claude/skills/notify-telegram
```

Then fill in `~/.claude/skills/notify-telegram/config.json`.

### Setup: get your Telegram credentials

You need two things: a **bot token** and your **chat ID**.

**Bot token:**
1. Open Telegram → search for **@BotFather**
2. Send `/newbot` → follow the steps → copy the token

**Chat ID:**
1. Open Telegram → search for **@userinfobot** or **@getidsbot**
2. Start it → it shows your numeric ID

**Fill in `config.json`:**
```json
{
  "bot_token": "1234567890:AAFxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "chat_id": "123456789"
}
```

> ⚠️ Never paste your token into the Claude chat window. Always edit the file directly.

### Requirements

- Claude desktop app (Cowork mode) or Claude Code
- A Telegram account
- `curl` installed (comes with macOS and most Linux distros by default)

---

## 🇷🇺 Русский

### Что делает этот скилл

**notify-telegram** — скилл для [Claude](https://claude.ai) (Cowork / Claude Code), который автоматически отправляет тебе сообщение в Telegram, когда долгая задача завершена. Можно отойти от компьютера и вернуться только тогда, когда работа сделана.

Уведомления написаны в саркастичном стиле — как отчёт уставшего, но довольного разработчика. Claude слегка принижает пафос названия проекта:

- *«Сударь, ваш «революционный» интернет-магазин готов. Целых 3 файла написано.»*
- *«Парсер для CSV собран. Работает. Это не точно.»*
- *«Дашборд аналитики собран. Цветные графики показывают, что всё сложно.»*

### Когда Claude отправляет уведомление

- Ты явно просишь: *«уведоми меня в Telegram»*, *«напиши мне когда закончишь»*, *«пинганй меня»*
- Задача длинная и многоэтапная (написание кода, создание файлов, запуск пайплайна) — Claude отправляет автоматически

### Установка

#### Вариант 1 — Claude Desktop (Cowork)

1. Скачай [`notify-telegram.skill`](./notify-telegram.skill) из этого репозитория
2. Открой приложение Claude → **Settings** → **Skills** → нажми **+**
3. Загрузи файл `.skill`
4. Найди папку установленного скилла и открой `config.json`:
   ```
   ~/Library/Application Support/Claude/  (macOS)
   ```
5. Заполни данные (см. ниже)

#### Вариант 2 — Claude Code (терминал)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/notify-telegram ~/.claude/skills/notify-telegram
```

Затем заполни `~/.claude/skills/notify-telegram/config.json`.

### Настройка: получение токена и chat_id

**Токен бота:**
1. Открой Telegram → найди **@BotFather**
2. Отправь `/newbot` → следуй инструкциям → скопируй токен

**Chat ID:**
1. Открой Telegram → найди **@userinfobot** или **@getidsbot**
2. Запусти бота → он покажет твой числовой ID

**Заполни `config.json`:**
```json
{
  "bot_token": "1234567890:AAFxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "chat_id": "123456789"
}
```

> ⚠️ Никогда не вставляй токен в окно чата с Claude. Всегда редактируй файл напрямую.

### Требования

- Приложение Claude Desktop (режим Cowork) или Claude Code
- Аккаунт в Telegram
- `curl` (входит в macOS и большинство Linux-дистрибутивов по умолчанию)

---

## File structure

```
notify-telegram/
├── SKILL.md          # Skill instructions for Claude
├── config.json       # Your credentials (fill this in, never commit!)
└── README.md         # This file
```

## Contributing

PRs welcome. If you want to add support for other notification channels (Slack, Discord, email) — open an issue first to discuss.

## License

MIT

---

*Built with [Claude](https://claude.ai) · Skill format by [Anthropic](https://anthropic.com)*
