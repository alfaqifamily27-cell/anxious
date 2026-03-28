# is_poem Bot — فهرس القصائد

A Telegram bot for **@is_poem** that automatically builds and maintains a live index message in the channel whenever a poem is posted.

---

## How it works

1. You post a poem in the channel using the format below
2. The bot detects the metadata, adds the poem to the index, and updates the pinned index message — automatically

---

## Posting format

When you post a poem, include these hashtags **anywhere** in the message:

```
#عنوان:اسم_القصيدة
#شاعر:اسم_الشاعر
#وسم:وسم1،وسم2
```

**Example:**

```
قصيدة جميلة...

نص القصيدة هنا

#عنوان:المتنبي_وسيف_الدولة #شاعر:المتنبي #وسم:فخر،مديح
```

- Use `_` for spaces in names (the bot converts them back to spaces)
- Multiple tags: separate with `,` or `،`
- `#وسم` is optional — title and poet are required

---

## Setup

### 1. Create a bot via BotFather

- Open [@BotFather](https://t.me/BotFather) on Telegram
- Send `/newbot` and follow the steps
- Copy your **BOT_TOKEN**

### 2. Add the bot to your channel as an Admin

- Go to your channel → Edit → Administrators → Add Admin
- Add your bot
- Give it permission to **Post Messages** and **Pin Messages**

### 3. Get your Channel ID

- Forward any message from your channel to [@userinfobot](https://t.me/userinfobot)
- It will show the channel ID (looks like `-1001234567890`)

### 4. Deploy to Railway

1. Push this folder to a GitHub repo
2. Go to [railway.app](https://railway.app) → New Project → Deploy from GitHub
3. Add these two environment variables:
   - `BOT_TOKEN` → your token from BotFather
   - `CHANNEL_ID` → your channel ID (e.g. `-1001234567890`)
4. Railway auto-detects the `Procfile` and starts the bot

> ⚠️ Railway's free tier gives you 500 hours/month — enough for a bot that runs ~16h/day. For 24/7, use the Hobby plan ($5/mo) or Render's free tier.

---

## Index message format

The bot maintains one pinned message that looks like this:

```
📚 فهرس القصائد

1. المتنبي وسيف الدولة — المتنبي
    #فخر · #مديح

2. لا تُلقِ عصاك — نزار قباني
    #حب · #حنين

آخر تحديث: 2025-01-15
```

Each title is a link that jumps directly to the poem post.

---

## Local testing (optional)

```bash
pip install -r requirements.txt
export BOT_TOKEN="your_token"
export CHANNEL_ID="-1001234567890"
python bot.py
```
