# 9️⃣ Pair Messaging Channels

Connect Telegram, WhatsApp, or Discord to start messaging your AI agent.

---

## 📱 Telegram Setup

### 1. Create a Bot

1. Message [@BotFather](https://t.me/BotFather) on Telegram
2. Send `/newbot`
3. Follow instructions
4. Copy the bot token

### 2. Configure OpenClaw

```bash
openclaw configure --section channels.telegram
```

**Or edit** `~/.openclaw/openclaw.json`:

```json
{
  "channels": {
    "telegram": {
      "enabled": true,
      "botToken": "YOUR_TELEGRAM_BOT_TOKEN",
      "dmPolicy": "pairing",
      "groupPolicy": "allowlist"
    }
  }
}
```

### 3. Pair Your Account

```bash
openclaw pairing approve telegram
```

### 4. Start Talking

1. Message your bot on Telegram
2. Run `openclaw pairing approve telegram` on VPS

---

## 📞 WhatsApp Setup

### 1. Configure OpenClaw

```bash
openclaw configure --section channels.whatsapp
```

**Or edit** `~/.openclaw/openclaw.json`:

```json
{
  "channels": {
    "whatsapp": {
      "enabled": true,
      "dmPolicy": "pairing"
    }
  }
}
```

### 2. Pair Your Number

```bash
openclaw pairing approve whatsapp
```

### 3. Scan QR Code

1. A QR code displays in terminal
2. Open WhatsApp → Settings → Linked Devices → Link Device
3. Scan the QR code

---

## 💬 Discord Setup

### 1. Create Discord Application

1. Go to [Discord Developer Portal](https://discord.com/developers/applications)
2. Click **New Application**
3. Name it and create

### 2. Create Bot

1. Go to **Bot** section
2. Click **Add Bot**
3. Copy the bot token

### 3. Configure OpenClaw

```bash
openclaw configure --section channels.discord
```

**Or edit** `~/.openclaw/openclaw.json`:

```json
{
  "channels": {
    "discord": {
      "enabled": true,
      "token": "YOUR_DISCORD_BOT_TOKEN",
      "dmPolicy": "pairing",
      "groupPolicy": "allowlist"
    }
  }
}
```

### 4. Invite Bot to Server

1. Go to **OAuth2** → **URL Generator**
2. Select scopes: `bot`, `applications.commands`
3. Select permissions: `Send Messages`, `Manage Messages`, `Read Message History`
4. Copy URL and open in browser

### 5. Pair Your Account

```bash
openclaw pairing approve discord
```

---

## ✅ Success Criteria

| Channel | Paired When... |
|---------|----------------|
| Telegram | `/start` message sent to bot |
| WhatsApp | QR code scanned and linked |
| Discord | Bot joins server and `/start` sent |

---

## ⚠️ Common Issues

### Telegram: Bot Token Invalid

```bash
# Test bot token
curl -s https://api.telegram.org/bot<YOUR_BOT_TOKEN>/getMe
```

### WhatsApp: QR Code Not Showing

```bash
# Check terminal size (needs minimum 80x24)
echo $LINES $COLUMNS

# Restart pairing
openclaw pairing approve whatsapp
```

### Discord: Bot Not Responding

1. Check bot has correct permissions
2. Ensure bot is online
3. Check Discord server settings

---

## 🎯 Next Step

**[10-MODELS.md](10-MODELS.md)** — Configure AI models (MiniMax, Claude, OpenAI)
