# notify-telegram — AI Skill

> An AI skill that sends you a sarcastic Telegram notification when your assistant finishes a task.

> Скилл для AI-ассистентов, который отправляет саркастическое уведомление в Telegram, когда задача завершена.

---

## 🇬🇧 English

### What it does

**notify-telegram** is a skill for AI coding assistants (Claude, OpenAI Codex, and others that support the `SKILL.md` format) that automatically sends you a Telegram message when a long task is done — so you can walk away from your computer and come back only when the work is finished.

The notifications are written in a witty, slightly sarcastic tone, like a cynical intern delivering a report. The AI will subtly downgrade the name of your project:

- *"Your 'revolutionary' online store is ready. A whole 3 files written."*
- *"CSV parser assembled. Works. Probably."*
- *"Analytics dashboard complete. The colorful charts show that everything is complicated."*

### When the AI sends the notification

- You explicitly ask: *"notify me in Telegram when done"*, *"write me in Telegram"*, *"ping me when finished"*
- The task is long and multi-step (writing code, creating many files, running a pipeline) — the AI sends it automatically without being asked

### Installation

#### Claude Desktop (Cowork) — macOS

1. Download [`notify-telegram.skill`](./notify-telegram.skill) from this repository
2. Open the Claude desktop app
3. Go to **Settings** → **Capabilities** → **Skills** → click **"Go to Customize"**
4. Click **+** and upload the `.skill` file
5. After installation, find the `config.json` inside the skill folder and fill in your credentials (see Setup below)

> Note: Claude Desktop stores skills in the cloud tied to your account — there is no local folder to copy files into. The only way to add a skill is through the Settings interface described above.

#### Claude Code (terminal)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/notify-telegram ~/.claude/skills/notify-telegram
```

Then fill in `~/.claude/skills/notify-telegram/config.json`.

#### OpenAI Codex (VS Code extension)

Copy the skill folder into your Codex skills directory:

```bash
cp -r notify-telegram-skill ~/.codex/skills/
```

Then fill in `~/.codex/skills/notify-telegram-skill/config.json`.

#### Other AI assistants

If your AI assistant supports skill files (`SKILL.md` format), copy the `notify-telegram-skill/` folder into the skills directory of that tool and fill in `config.json`.

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

> ⚠️ Never paste your token into the AI chat window. Always edit the file directly.

### Requirements

- An AI assistant that supports `SKILL.md` skills (Claude, Codex, etc.)
- A Telegram account
- `curl` installed (comes with macOS and most Linux distros by default)

---

## 🇷🇺 Русский

### Что делает этот скилл

**notify-telegram** — скилл для AI-ассистентов (Claude, OpenAI Codex и других, поддерживающих формат `SKILL.md`), который автоматически отправляет тебе сообщение в Telegram, когда долгая задача завершена. Можно отойти от компьютера и вернуться только тогда, когда работа сделана.

Уведомления написаны в саркастичном стиле — как отчёт уставшего, но довольного разработчика. ИИ слегка принижает пафос названия проекта:

- *«Сударь, ваш «революционный» интернет-магазин готов. Целых 3 файла написано.»*
- *«Парсер для CSV собран. Работает. Это не точно.»*
- *«Дашборд аналитики собран. Цветные графики показывают, что всё сложно.»*

### Когда ИИ отправляет уведомление

- Ты явно просишь: *«уведоми меня в Telegram»*, *«напиши мне когда закончишь»*, *«пингани меня»*
- Задача длинная и многоэтапная (написание кода, создание файлов, запуск пайплайна) — ИИ отправляет автоматически

### Установка

#### Claude Desktop (Cowork) — macOS

1. Скачай [`notify-telegram.skill`](./notify-telegram.skill) из этого репозитория
2. Открой приложение Claude на десктопе
3. Перейди в **Settings** → **Capabilities** → **Skills** → нажми **"Go to Customize"**
4. Нажми **+** и загрузи файл `.skill`
5. После установки найди `config.json` внутри папки скилла и заполни данные (см. ниже)

> Важно: Claude Desktop хранит скиллы в облаке, привязанном к аккаунту — никакой локальной папки для копирования нет. Единственный способ добавить скилл — через интерфейс настроек, описанный выше.

#### Claude Code (терминал)

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/YOUR_USERNAME/notify-telegram ~/.claude/skills/notify-telegram
```

Затем заполни `~/.claude/skills/notify-telegram/config.json`.

#### OpenAI Codex (расширение VS Code)

Скопируй папку скилла в директорию скиллов Codex:

```bash
cp -r notify-telegram-skill ~/.codex/skills/
```

Затем заполни `~/.codex/skills/notify-telegram-skill/config.json`.

#### Другие AI-ассистенты

Если твой ИИ-ассистент поддерживает формат скиллов (`SKILL.md`), скопируй папку `notify-telegram-skill/` в директорию скиллов этого инструмента и заполни `config.json`.

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

> ⚠️ Никогда не вставляй токен в окно чата с ИИ. Всегда редактируй файл напрямую.

### Требования

- AI-ассистент с поддержкой скиллов формата `SKILL.md` (Claude, Codex и др.)
- Аккаунт в Telegram
- `curl` (входит в macOS и большинство Linux-дистрибутивов по умолчанию)

---

## File structure

```
notify-telegram/
├── SKILL.md              # Skill instructions for the AI
├── config.json           # Your credentials (fill this in, never commit!)
├── config.example.json   # Template — copy to config.json and fill in
└── README.md             # This file
```

## Contributing

PRs welcome. If you want to add support for other notification channels (Slack, Discord, email) — open an issue first to discuss.

## License

MIT

---

*Skill format by [Anthropic](https://anthropic.com)*
