# 3️⃣ Update System Packages

Update Ubuntu packages and install required dependencies.

---

## 📦 Commands

```bash
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release
```

---

## 🔍 What This Does

| Command | Purpose |
|---------|---------|
| `apt-get update` | Refreshes package lists from repositories |
| `apt-get upgrade` | Installs latest security patches and updates |
| `apt-get install` | Installs required dependencies for Docker and OpenClaw |

---

## ✅ Expected Output

```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
...
```

---

## ⚠️ Common Issues

### Slow Updates

If updates are slow, change to a faster mirror:

```bash
sudo sed -i 's|us.archive.ubuntu.com| mirrors.edge.akamai.net|g' /etc/apt/sources.list
sudo apt-get update
```

### Permission Denied

If you get permission errors, ensure you're using `sudo`:

```bash
sudo apt-get update
```

---

## 🎯 Next Step

Once complete, proceed to:

**[04-DOCKER.md](04-DOCKER.md)** — Install Docker Engine
