# Troubleshooting

Common issues and solutions for OpenClaw setup.

---

## Gateway Issues

### Gateway Won't Start

```bash
# Check what's using port 18789
sudo lsof -i :18789

# Kill existing process
pkill -f openclaw

# Restart gateway
openclaw gateway start

# Check status
openclaw gateway status
```

### Configuration Error

```bash
# Validate config
openclaw doctor

# View logs
openclaw logs

# Reset config
openclaw configure --reset
```

---

## Docker Issues

### Docker Not Running

```bash
# Check status
sudo systemctl status docker

# Start Docker
sudo systemctl start docker

# Enable on boot
sudo systemctl enable docker
```

### Permission Denied

```bash
# Add user to docker group
sudo usermod -aG docker $USER

# Apply immediately
newgrp docker
```

---

## SSH Tunnel Issues

### Connection Refused

```bash
# Test SSH connection
ssh username@vps-ip

# Check VPS SSH service
sudo systemctl status ssh

# Restart SSH
sudo systemctl restart ssh
```

### Tunnel Drops

```bash
# Keep alive in ~/.ssh/config
Host your-vps-ip
    ServerAliveInterval 60
    ServerAliveCountMax 3
```

---

## Channel Pairing Issues

### Telegram Bot Not Responding

```bash
# Test bot token
curl -s https://api.telegram.org/bot<YOUR_TOKEN>/getMe

# Check webhook
curl -s https://api.telegram.org/bot<YOUR_TOKEN>/getWebhookInfo
```

### WhatsApp QR Code Not Showing

```bash
# Ensure terminal size
echo $LINES $COLUMNS

# Should show at least: 24 80
```

### Discord Bot Offline

1. Check [Discord Developer Portal](https://discord.com/developers/applications)
2. Ensure bot is added to server
3. Check bot permissions

---

## AI Model Issues

### API Key Invalid

```bash
# Test MiniMax
curl -s -H "Authorization: Bearer YOUR_KEY" https://api.minimax.io/anthropic/v1/models

# Test Anthropic
curl -s -H "x-api-key: YOUR_KEY" https://api.anthropic.com/v1/models

# Test OpenAI
curl -s -H "Authorization: Bearer YOUR_KEY" https://api.openai.com/v1/models
```

### No Response from Model

1. Check API credits/billing
2. Verify model ID is correct
3. Check rate limits

---

## Get Help

### View Logs

```bash
# All logs
openclaw logs

# Last 100 lines
openclaw logs | tail -100

# Filter for errors
openclaw logs | grep -i error
```

### Health Check

```bash
openclaw health
openclaw doctor
```

---

**Still stuck?** Open an issue on [GitHub](https://github.com/vkolyvas/openclaw-azure-setup/issues)
