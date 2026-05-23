# 🇪🇹⚽ EthioFootball CRBT Bot

A Telegram bot that helps Ethiopian Ethio Telecom users discover, preview, and activate football CRBT (Caller Ring Back Tone) songs via SMS to **822**.

---

## 🎯 Features

- Browse songs by **league → team → song**
- 🔥 Trending songs section
- 🔍 Search by team or song name
- ▶️ **Audio preview** (15–30 sec MP3 sent inside Telegram)
- 🚀 One-tap SMS activation link (`sms:822?body=SUB CODE`)
- 📋 Copy SMS command
- ℹ️ First-time CRBT service activation guide
- 🔐 Admin panel: add / remove / list songs
- ⏳ Per-user rate limiting

---


## 🤖 Bot Commands

| Command         | Who      | Description                    |
|-----------------|----------|--------------------------------|
| `/start`        | All      | Main menu                      |
| `/help`         | All      | Help & instructions            |
| `/search query` | All      | Search songs/teams             |
| `/addsong`      | Admin    | Add a new song (step-by-step)  |
| `/removesong`   | Admin    | Remove a song by ID            |
| `/listsongs`    | Admin    | List all songs                 |
| `/cancel`       | Admin    | Cancel ongoing admin action    |

---

## 📱 CRBT Activation Flow

```
User opens bot
    ↓
Selects league → team → song
    ↓
Plays 15–30 sec preview (MP3 in Telegram)
    ↓
Taps "🚀 Activate CRBT"
    ↓
Bot shows SMS instructions + deep link
    ↓
User taps link → SMS app opens with:
  To: 822
  Message: SUB MU124
    ↓
User taps SEND
    ↓
Ethio Telecom activates CRBT ✅
```

**First-time users** must first send `A` to `822` to enable the CRBT service.

---

## 🔐 Security

- Bot token stored in `.env` (never committed to git)
- Admin commands protected by Telegram user ID whitelist
- Input validation on all user inputs
- Per-user rate limiting (configurable, default 3 seconds)

---


## 🛠 Extending the Bot

- **Add songs:** Use `/addsong` as admin or edit `data/songs.json` and re-run
- **Add leagues:** Just add songs with a new `league` value — menus update automatically
- **Add preview files:** Drop MP3s in `previews/` and reference them in the database
- **Webhook mode:** For production, switch `run_polling()` to `run_webhook()` in `main.py`

---

