# ⚡ Quick Installation Commands

Copy and run these exact commands in order on your VPS.

---

## Step 1-2: Update System & Install Dependencies

```bash
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release
```

---

## Step 3-4: Install Docker

```bash
# Add Docker's official GPG key and repository
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add user to docker group
sudo usermod -aG docker $USER
```

---

## Step 5-6: Security Updates & OpenClaw

```bash
# Configure automatic security updates
sudo apt update && sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades

# Install OpenClaw
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --install-method npm
```

---

## Step 7-8: PATH & SSH Tunnel

```bash
# Add OpenClaw to PATH
echo 'export PATH="$PATH:$HOME/openclaw/bin"' >> ~/.bashrc
source ~/.bashrc

# SSH tunnel (run from YOUR LOCAL MACHINE, not VPS)
ssh -N -L 18789:127.0.0.1:18789 username@your-vps-ip
```

---

## Step 9-10: Pairing & Homebrew

```bash
# Pair Telegram
openclaw pairing approve telegram

# Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

## Step 11-12: GitHub & Dashboard

```bash
# Configure GitHub access
mkdir -p ~/.openclaw/agents/main/agent
cat > ~/.openclaw/agents/main/agent/auth-profiles.json << 'EOF'
{
  "profiles": {
    "github:default": {
      "type": "api_key",
      "provider": "github",
      "key": "ghp_your_github_token"
    }
  }
}
EOF
```

**Access Dashboard:** Open browser to `http://127.0.0.1:18789` (after SSH tunnel is active)

---

## 🎁 MiniMax Referral Bonus

> Get 10% off MiniMax coding plan: https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

---

**Next:** See [01-PREREQUISITES.md](01-PREREQUISITES.md) for full details
