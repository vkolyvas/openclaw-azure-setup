# 8️⃣ SSH Tunnel (Remote Access)

Set up secure tunnel to access OpenClaw from your local machine.

---

## 📦 Command (Run Locally)

```bash
ssh -N -L 18789:127.0.0.1:18789 username@your-vps-ip
```

---

## 🔍 Command Breakdown

| Flag/Part | Purpose |
|-----------|---------|
| `-N` | Don't execute remote commands (tunnel only) |
| `-L 18789:127.0.0.1:18789` | Forward local port 18789 to VPS localhost:18789 |
| `username@your-vps-ip` | Your VPS SSH credentials |

---

## ✅ Verify Connection

1. **Keep terminal running** with the SSH tunnel
2. **Open browser** to: `http://127.0.0.1:18789`
3. You should see OpenClaw dashboard

---

## ⚠️ Common Issues

### Connection Refused

```bash
# Check VPS IP
ssh username@your-vps-ip

# Check SSH is running on VPS
sudo systemctl status ssh
```

### Port Already in Use

```bash
# Find what's using port 18789 locally
lsof -i :18789

# Kill the process or use different port
ssh -N -L 18789:127.0.0.1:18789 username@your-vps-ip -p 22
```

### SSH Key Not Working

```bash
# Generate SSH key if needed
ssh-keygen -t ed25519

# Copy key to VPS
ssh-copy-id username@your-vps-ip
```

---

## 🔐 Security Note

- The SSH tunnel is **encrypted** and secure
- No need to open port 18789 on VPS firewall
- Only accessible from your local machine

---

## 🎯 Next Step

**[09-PAIRING.md](09-PAIRING.md)** — Pair messaging channels (Telegram, WhatsApp, Discord)
