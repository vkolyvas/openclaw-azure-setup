# 7⃣ Configure PATH

Add OpenClaw to your PATH for global access.

---

##  Command

```bash
echo 'export PATH="$PATH:$HOME/openclaw/bin"' >> ~/.bashrc
source ~/.bashrc
```

---

##  What This Does

| Command | Purpose |
|---------|---------|
| `echo ... >> ~/.bashrc` | Adds OpenClaw bin directory to PATH in bashrc |
| `source ~/.bashrc` | Loads the updated PATH immediately |

---

##  Verify Configuration

```bash
openclaw gateway status
which openclaw
```

**Expected output:**
```
Gateway is running on port 18789
/home/username/.openclaw/bin/openclaw
```

---

##  Common Issues

### Command Not Found After Reboot

The `source ~/.bashrc` only affects current session. For new sessions, bashrc is loaded automatically on login.

**Alternative for immediate effect:**
```bash
export PATH="$PATH:$HOME/openclaw/bin"
```

**Alternative shells (zsh, fish):**

```bash
# For zsh
echo 'export PATH="$PATH:$HOME/openclaw/bin"' >> ~/.zshrc
source ~/.zshrc

# For fish
set -U fish_user_paths $HOME/openclaw/bin $fish_user_paths
```

---

##  Next Step

**[08-SSH-TUNNEL.md](08-SSH-TUNNEL.md)** - Set up SSH tunnel for remote access
