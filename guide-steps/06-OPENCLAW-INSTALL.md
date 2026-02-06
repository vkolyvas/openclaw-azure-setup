# 6️⃣ Install OpenClaw

Install the OpenClaw AI gateway using npm.

---

## 📦 Command

```bash
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --install-method npm
```

---

## 🔍 What This Does

| Step | Purpose |
|------|---------|
| Downloads installer | Fetches OpenClaw installation script |
| Runs installer | Installs via npm (Node Package Manager) |
| Sets up gateway | Creates OpenClaw gateway process |
| Configures workspace | Sets up default directories |

---

## ✅ Verify Installation

```bash
openclaw --version
openclaw gateway status
```

**Expected output:**
```
OpenClaw version x.x.x
Gateway is running on port 18789
```

---

## 📁 Installed Files

| Location | Purpose |
|----------|---------|
| `~/.openclaw/` | Main configuration directory |
| `~/.openclaw/bin/` | OpenClaw binaries |
| `~/.openclaw/workspace/` | Agent workspace |
| `~/.openclaw/openclaw.json` | Main configuration file |

---

## ⚠️ Common Issues

### Installation Fails

```bash
# Check npm is installed
npm --version

# Try with verbose output
curl -fsSL https://openclaw.ai/install.sh | bash -x -s -- --install-method npm
```

### Gateway Won't Start

```bash
# Check what's using port 18789
sudo lsof -i :18789

# Kill and restart
pkill -f openclaw
openclaw gateway start
```

---

## 🎯 Next Step

**[07-PATH.md](07-PATH.md)** — Add OpenClaw to PATH
