# 5️⃣ Configure Automatic Security Updates

Set up unattended upgrades for automatic security patching.

---

## 📦 Commands

```bash
sudo apt update && sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades
```

---

## 🔍 What This Does

| Command | Purpose |
|---------|---------|
| `apt update` | Refresh package lists |
| `apt install unattended-upgrades` | Installs automatic update package |
| `dpkg-reconfigure -plow unattended-upgrades` | Configures unattended upgrades |

---

## ✅ Verify Configuration

```bash
sudo cat /etc/apt/apt.conf.d/50unattended-upgrades
```

**Ensure these are enabled:**
```
Unattended-Upgrade::Allowed-Origins {
    "${distro_id}:${distro_codename}";
    "${distro_id}:${distro_codename}-security";
    "${distro_id}ESMApps:${distro_codename}-apps-security";
    "${distro_id}ESM:${distro_codename}-infra-security";
};
```

---

## ⚠️ Common Issues

### Configuration Not Applied

```bash
# Re-run configuration
sudo dpkg-reconfigure -plow unattended-upgrades
```

### Check Status

```bash
sudo unattended-upgrades --dry-run --debug
```

---

## 🎯 Next Step

**[06-OPENCLAW-INSTALL.md](06-OPENCLAW-INSTALL.md)** — Install OpenClaw
