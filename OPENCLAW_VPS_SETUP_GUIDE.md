# 🚀 OpenClaw VPS Setup Guide

> **🎁 Special Offer:** Get 10% off MiniMax coding plan using this referral link: https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

A comprehensive guide to deploying **OpenClaw** — your AI-powered coding assistant — on an Azure VPS with full Telegram, WhatsApp, Discord integration and GitHub access.

---

## ⚡ Quick Installation Commands

Copy and run these exact commands in order:

```bash
# Step 1: Update system and install dependencies
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release

# Step 2: Add Docker's official GPG key and repository
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Step 3: Install Docker Engine
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Step 4: Add user to docker group
sudo usermod -aG docker $USER

# Step 5: Configure automatic security updates
sudo apt update && sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades

# Step 6: Install OpenClaw
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --install-method npm

# Step 7: Add OpenClaw to PATH
echo 'export PATH="$PATH:$HOME/openclaw/bin"' >> ~/.bashrc
source ~/.bashrc

# Step 8: SSH tunnel for remote access (run from your local machine)
ssh -N -L 18789:127.0.0.1:18789 username@your-vps-ip

# Step 9: Pair Telegram
openclaw pairing approve telegram

# Step 10: Install Homebrew
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

# Step 11: Configure GitHub access
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

# Step 12: Access OpenClaw Dashboard
# Open browser to: http://127.0.0.1:18789 (after SSH tunnel)
```

> 💡 **Note:** Steps 8 and 12 require SSH tunnel setup. See detailed instructions below.

---

A comprehensive guide to deploying **OpenClaw** — your AI-powered coding assistant — on an Azure VPS with full Telegram, WhatsApp, Discord integration and GitHub access.

---

## 📋 Table of Contents

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [AI Model API Keys](#-ai-model-api-keys)
4. [VPS Requirements](#vps-requirements)
5. [Step 1: Update System Packages](#step-1-update-system-packages)
6. [Step 2: Install Docker](#step-2-install-docker)
7. [Step 3: Configure Automatic Updates](#step-3-configure-automatic-security-updates)
8. [Step 4: Install OpenClaw](#step-4-install-openclaw)
9. [Step 5: Add OpenClaw to PATH](#step-5-add-openclaw-to-path)
10. [Step 6: SSH Tunnel (Remote Access)](#step-6-set-up-ssh-tunnel-remote-access)
11. [Step 7: Pairing Your Channels](#step-7-pairing-your-channels)
12. [Step 8: Configure AI Models](#step-8-configure-ai-models)
13. [Step 9: Onboarding Your Agent](#step-9-onboarding-your-agent)
14. [Step 10: Testing Your Setup](#step-10-testing-your-setup)
15. [GitHub Integration](#github-integration)
16. [Homebrew Installation](#homebrew-installation)
17. [Post-Installation Setup](#post-installation-setup)
18. [Troubleshooting](#troubleshooting)

---

## 🎯 Overview

OpenClaw is an open-source AI gateway that connects multiple AI coding agents to your messaging platforms (Telegram, WhatsApp, Discord). This guide walks you through deploying it on an Azure VPS with full configuration.

**Key Features:**
- 🤖 Multi-agent AI support
- 💬 Telegram, WhatsApp, Discord integration
- 🔧 GitHub CLI integration
- 🐳 Docker container management
- 🔐 Secure authentication
- 🌐 Remote access via SSH tunnel

---

## 💻 Prerequisites

Before starting, ensure you have:

- **Azure Account** with billing enabled
- **SSH Client** (Terminal, PuTTY, or Windows Terminal)
- **GitHub Account** (for API access)
- **Telegram Account** (to create a bot)
- **WhatsApp Number** (dedicated for the bot)
- **Discord Application** (optional, for Discord integration)

---

## 🖥️ VPS Requirements

### Recommended Configuration

| Resource | Specification |
|----------|---------------|
| **VM Size** | **Standard_E6as_v6** |
| **vCPUs** | 6 |
| **RAM** | 36 GB |
| **Temp Storage** | 140 GB |
| **Est. Cost** | ~€140/month |

### Why This Configuration?

#### 🎯 Heavy Workload Requirements

This VPS configuration is designed for **power users** who need to:

- 🚀 **Spin up multiple local projects** simultaneously for Proof of Concept (POC) development
- 🐳 **Run numerous Docker containers** at the same time without performance degradation
- 💾 **Keep all development environments active** for rapid iteration and testing
- 🤖 **Run multiple AI agents** in parallel for complex coding tasks

#### 📊 Resource Allocation Strategy

With **36 GB RAM**, you can comfortably run:

| Use Case | RAM Required | Containers |
|----------|-------------|-------------|
| Main OpenClaw Gateway | 2-4 GB | 1-2 |
| Docker Daemon | 1-2 GB | System |
| Development Projects | 4-6 GB each | 4-6 concurrent |
| CI/CD Pipelines | 2-4 GB | 2-3 |
| **Total Available** | ~24 GB | **10-12** |

---

## 💡 10 Project Ideas for Local Development

This setup is perfect for **Test-Driven Development (TDD)** workflows where you need to rapidly prototype, test, and iterate across multiple projects.

### 1. 📊 **Portfolio Tracker** — TDD with Python/Django
- **Purpose:** Track stock and crypto portfolios
- **Tests:** Unit tests for calculations, API integration tests
- **Tech:** Python, Django, PostgreSQL, Docker

### 2. 🤖 **AI Code Reviewer** — TDD with Node.js/TypeScript
- **Purpose:** Automated code review using AI agents
- **Tests:** Mock API responses, integration tests for GitHub webhooks
- **Tech:** TypeScript, Express, Docker, GitHub API

### 3. 📝 **Note-Taking App** — TDD with React/Vue
- **Purpose:** Personal knowledge management system
- **Tests:** Component tests, API endpoint tests
- **Tech:** Vue.js, Node.js API, SQLite, Docker

### 4. 💬 **Chat Application** — TDD with Elixir/Phoenix
- **Purpose:** Real-time messaging platform
- **Tests:** Channel tests, presence tests, database tests
- **Tech:** Elixir, Phoenix Framework, PostgreSQL, Docker

### 5. 🔐 **Password Manager** — TDD with Rust
- **Purpose:** Secure password storage and generation
- **Tests:** Cryptographic tests, encryption verification tests
- **Tech:** Rust, Actix-web, SQLite, Docker

### 6. 📈 **ML Pipeline** — TDD with Python/FastAPI
- **Purpose:** Machine learning model training and inference
- **Tests:** Data validation tests, model accuracy tests, API tests
- **Tech:** Python, FastAPI, ML libraries, Docker

### 7. 🌐 **API Gateway** — TDD with Go
- **Purpose:** Centralized API management and routing
- **Tests:** Routing tests, middleware tests, load tests
- **Tech:** Go, Gin framework, Docker

### 8. 📱 **Task Manager** — TDD with Kotlin/Spring Boot
- **Purpose:** Team productivity and task tracking
- **Tests:** Repository tests, service layer tests, controller tests
- **Tech:** Kotlin, Spring Boot, PostgreSQL, Docker

### 9. 🎵 **Music Streaming API** — TDD with Ruby on Rails
- **Purpose:** Music library management and streaming
- **Tests:** Background job tests, streaming tests, API contracts
- **Tech:** Ruby, Rails, PostgreSQL, Docker

### 10. 🔗 **URL Shortener** — TDD with Java/Quarkus
- **Purpose:** URL shortening with analytics
- **Tests:** Redirect tests, analytics tests, database tests
- **Tech:** Java, Quarkus, PostgreSQL, Redis, Docker

---

## 🏗️ TDD Workflow Benefits

With this VPS setup, you can implement a robust **Test-Driven Development** workflow:

```
┌─────────────────────────────────────────────────────────────┐
│                    TDD CYCLE                                │
│                                                             │
│   1. 🔴 RED     → Write failing test                       │
│   2. 🟢 GREEN   → Write minimal code to pass test          │
│   3. 🔵 REFACTOR → Improve code while keeping tests passing │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### Benefits for Multiple Projects:

- ⚡ **Fast Iteration** — All projects running locally = instant feedback
- 🐳 **Isolated Environments** — Docker ensures no dependency conflicts
- 🔄 **Parallel Testing** — Run multiple test suites simultaneously
- 📦 **Resource Efficiency** — Centralized development = lower costs
- 🎯 **Focus on Code** — No waiting for CI/CD pipelines

---

## 📈 Scaling Considerations

| Workload Type | Recommended RAM |
|---------------|----------------|
| 5 Light Projects | 16 GB |
| 10 Medium Projects | 32 GB |
| 10 Heavy Projects (ML/AI) | 64 GB+ |

Start with **Standard_E6as_v6** (36 GB) and scale up based on your needs.

> 💡 **Pro Tip:** Use Docker Compose to manage multi-container projects efficiently and `docker stats` to monitor resource usage.

---

## 🧠 AI Model API Keys

OpenClaw requires **at least one AI model** to function. For optimal performance, configure **two separate models**:

### 🤖 Coding Model (Primary)

**Purpose:** Code generation, refactoring, debugging, file operations

**Recommended Model:**
- **MiniMax M2.1** — Perfect for multi-coding capabilities with exceptional performance across languages

**🎁 MiniMax Coding Plan Special Offer:**
> New Year Mega Offer! Invite friends and earn rewards for both! Exclusive 10% OFF for friends. Ready-to-use API vouchers for you!
> 👉 **Get your referral link:** https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

**Getting the API Key:**
1. Visit [MiniMax Platform](https://platform.minimax.io/)
2. Sign up and navigate to API section
3. Generate API key
4. Copy and store securely

**Why MiniMax M2.1 for Coding?**
- Excellent multi-language support
- Fast inference speeds
- Cost-effective pricing
- Strong code generation capabilities

### 🧠 Reasoning Model (Secondary)

**Purpose:** Complex problem-solving, planning, architectural decisions

**Recommended Models:**
- **Claude Opus 4** (Anthropic) — Best reasoning capabilities
- **GPT-4o** (OpenAI) — Excellent reasoning
- **o1-pro** (OpenAI) — Advanced reasoning

**Getting the API Key:**
1. Visit [OpenAI Platform](https://platform.openai.com/)
2. Create account and generate API key
3. Copy and store securely

> ⚠️ **Important:** Store API keys securely. Never commit them to version control.

---

## 📦 Step 1: Update System Packages

```bash
sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get install -y apt-transport-https ca-certificates curl gnupg lsb-release
```

**What this does:**
- `apt-get update` — Refreshes package lists
- `apt-get upgrade` — Installs latest security patches
- `apt-get install` — Installs required dependencies for Docker and OpenClaw

---

## 🐳 Step 2: Install Docker

```bash
# Add Docker's official GPG key and repository
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Install Docker Engine
sudo apt-get update
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Add your user to the docker group
sudo usermod -aG docker $USER
```

**What this does:**
- Adds Docker's official repository
- Installs Docker Engine, CLI, containerd, and plugins
- Allows running Docker without `sudo`

> ⚠️ **Important:** Log out and back in for group membership to take effect.

---

## 🔒 Step 3: Configure Automatic Security Updates

```bash
sudo apt update && sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure -plow unattended-upgrades
```

**What this does:**
- Installs automatic security update package
- Configures daily security patches
- Reduces maintenance overhead

---

## 🚀 Step 4: Install OpenClaw

```bash
curl -fsSL https://openclaw.ai/install.sh | bash -s -- --install-method npm
```

**What this does:**
- Downloads and runs OpenClaw installer
- Installs via npm (Node Package Manager)
- Sets up the gateway and default configurations

---

## 📍 Step 5: Add OpenClaw to PATH

```bash
echo 'export PATH="$PATH:$HOME/openclaw/bin"' >> ~/.bashrc
source ~/.bashrc
```

**What this does:**
- Adds OpenClaw binaries to your PATH
- Makes `openclaw` command available globally

---

## 🌐 Step 6: Set Up SSH Tunnel (Remote Access)

To access your VPS OpenClaw from your local machine:

```bash
ssh -N -L 18789:127.0.0.1:18789 username@your-vps-ip
```

**Breakdown:**
- `-N` — Don't execute remote commands (just tunnel)
- `-L 18789:127.0.0.1:18789` — Forward local port 18789 to VPS localhost:18789
- `username@your-vps-ip` — Your VPS credentials

**What this does:**
- Creates secure tunnel to your VPS
- Access OpenClaw Dashboard at `http://127.0.0.1:18789`
- No need to open ports on VPS firewall

> 💡 **Keep this terminal running** while using OpenClaw remotely.

---

## 🎛️ Step 7: Pairing Your Channels

For OpenClaw to work, you need to **pair at least one messaging channel**.

### 📱 Telegram Setup

1. **Create a Bot:**
   - Message [@BotFather](https://t.me/BotFather) on Telegram
   - Send `/newbot`
   - Follow instructions
   - Copy the bot token

2. **Configure in OpenClaw:**
   ```bash
   openclaw configure --section channels.telegram
   ```

   Or edit `~/.openclaw/openclaw.json`:
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

3. **Pair Your Account:**
   ```bash
   openclaw pairing approve telegram
   ```

4. **Start Talking:**
   - Message your bot on Telegram
   - First message triggers pairing flow
   - Run `openclaw pairing approve telegram` on VPS

### 📞 WhatsApp Setup

1. **Requirements:**
   - Dedicated phone number (can use personal or business)
   - No additional app installation needed

2. **Configure in OpenClaw:**
   ```bash
   openclaw configure --section channels.whatsapp
   ```

   Or edit `~/.claw/openclaw.json`:
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

3. **Pair Your Number:**
   ```bash
   openclaw pairing approve whatsapp
   ```

4. **Scan QR Code:**
   - A QR code will be displayed in terminal
   - Scan with WhatsApp (Settings → Linked Devices → Link Device)
   - Your number is now paired

### 💬 Discord Setup

1. **Create Discord Application:**
   - Go to [Discord Developer Portal](https://discord.com/developers/applications)
   - Click "New Application"
   - Name it and create

2. **Create Bot:**
   - Go to "Bot" section
   - Click "Add Bot"
   - Copy the bot token

3. **Configure in OpenClaw:**
   ```bash
   openclaw configure --section channels.discord
   ```

   Or edit `~/.claw/openclaw.json`:
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

4. **Invite Bot to Server:**
   - Go to OAuth2 → URL Generator
   - Select scopes: `bot`, `applications.commands`
   - Select permissions: `Send Messages`, `Manage Messages`, `Read Message History`
   - Copy URL and open in browser

5. **Pair Your Account:**
   ```bash
   openclaw pairing approve discord
   ```

---

## 🧠 Step 8: Configure AI Models

Edit `~/.openclaw/openclaw.json` to configure your models:

**🎁 MiniMax Referral Bonus:**
> Use this referral link for 10% OFF: https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

```json
{
  "models": {
    "providers": {
      "minimax": {
        "apiKey": "your_minimax_api_key",
        "baseUrl": "https://api.minimax.io/anthropic",
        "api": "anthropic-messages",
        "models": [
          {
            "id": "MiniMax-M2.1-lightning",
            "name": "MiniMax M2.1 Lightning",
            "cost": {
              "input": 15,
              "output": 60
            },
            "contextWindow": 200000,
            "maxTokens": 8192,
            "bestFor": "Fast coding tasks, quick iterations"
          },
          {
            "id": "MiniMax-M2.1",
            "name": "MiniMax M2.1",
            "cost": {
              "input": 15,
              "output": 60
            },
            "contextWindow": 200000,
            "maxTokens": 8192,
            "bestFor": "Complex code generation, refactoring"
          }
        ]
      },
      "anthropic": {
        "apiKey": "your_anthropic_api_key",
        "baseUrl": "https://api.anthropic.com",
        "models": [
          {
            "id": "claude-opus-4-20250514",
            "name": "Claude Opus 4",
            "cost": {
              "input": 15.00,
              "output": 75.00
            },
            "contextWindow": 200000,
            "maxTokens": 8192,
            "bestFor": "Advanced reasoning, architecture"
          }
        ]
      },
      "openai": {
        "apiKey": "your_openai_api_key",
        "baseUrl": "https://api.openai.com/v1",
        "models": [
          {
            "id": "o1-pro",
            "name": "o1-pro",
            "cost": {
              "input": 150.00,
              "output": 600.00
            },
            "contextWindow": 200000,
            "maxTokens": 100000,
            "bestFor": "Extended reasoning, planning"
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "minimax/MiniMax-M2.1",
        "fallbacks": ["minimax/MiniMax-M2.1-lightning", "anthropic/claude-opus-4-20250514"]
      }
    }
  }
}
```

### Model Selection Strategy

| Task Type | Recommended Model | Reason |
|-----------|-------------------|--------|
| **Code Generation** | MiniMax M2.1 | Perfect multi-coding, fast & cost-effective |
| **Code Review** | MiniMax M2.1 Lightning | Quick feedback |
| **Complex Refactoring** | MiniMax M2.1 | Deep context, strong reasoning |
| **Architecture Decisions** | Claude Opus 4 | Advanced reasoning |
| **Debugging** | MiniMax M2.1 | Multi-language support |
| **Planning** | o1-pro | Extended reasoning |

> 💡 **Pro Tip:** MiniMax M2.1 is your go-to for most coding tasks. Use o1-pro only for complex architectural decisions.

---

## 🤖 Step 9: Onboarding Your Agent

### Create Agent Profile

Edit `~/.claw/workspace/AGENTS.md`:

```markdown
# AGENTS.md - Your Development Team

## Agent: OpenClaw (Primary)

**Role:** Senior Software Engineer & AI Assistant

**Capabilities:**
- Full-stack development (frontend, backend, DevOps)
- Code review and refactoring
- Test-driven development (TDD)
- GitHub repository management
- Docker containerization
- API design and integration

**Vibe:**
- Concise and direct
- Provides working code first, explanations second
- Asks clarifying questions when needed
- Respects security and privacy

**Specializations:**
- JavaScript/TypeScript (Node.js, React, Vue)
- Python (Django, FastAPI)
- Rust, Go, Elixir
- SQL and NoSQL databases
- Docker and Kubernetes
- CI/CD pipelines

---

## Workflow Guidelines

### For New Features

1. Write failing tests (TDD)
2. Implement minimal code to pass tests
3. Refactor for readability and performance
4. Ensure all tests pass
5. Create PR with description

### For Bug Fixes

1. Write test that reproduces the bug
2. Fix the code
3. Verify test passes
4. Check for edge cases
```

---

## ✅ Step 10: Testing Your Setup

### Verify All Components

```bash
# 1. Check gateway status
openclaw gateway status

# 2. Test messaging channels
# Send a message via Telegram, WhatsApp, or Discord

# 3. Test coding capabilities
"Write a Python function to calculate Fibonacci numbers with memoization"

# 4. Test reasoning capabilities
"Design a microservices architecture for an e-commerce platform"

# 5. Test GitHub integration
"Create a new repository called test-repo"
```

### Success Criteria ✅

- [ ] Gateway is running
- [ ] At least one channel is paired
- [ ] Coding model responds to code requests
- [ ] Reasoning model handles complex questions
- [ ] GitHub integration works (if configured)
- [ ] All Docker containers are healthy

---

## 🐙 GitHub Integration

### Create Auth Profile

Edit `~/.claw/agents/main/agent/auth-profiles.json`:

```json
{
  "profiles": {
    "github:default": {
      "type": "api_key",
      "provider": "github",
      "key": "ghp_your_personal_access_token"
    }
  }
}
```

### Generate GitHub Token

1. Go to **GitHub Settings** → **Developer Settings** → **Personal Access Tokens** → **Tokens (classic)**
2. Generate new token with `repo` scope
3. Copy and paste into the config above

**What this enables:**
- Create repositories
- Manage issues and PRs
- Push code
- Run GitHub CLI commands

---

## 🍺 Homebrew Installation (Optional)

For macOS development tools on Linux:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

**What this does:**
- Installs Homebrew package manager
- Provides access to Linuxbrew packages
- Useful for development tools

---

## ⚙️ Post-Installation Setup

### Verify Installation

```bash
openclaw status
openclaw gateway status
```

### Restart Gateway

```bash
openclaw gateway restart
```

---

## 🐛 Troubleshooting

### Docker Issues

```bash
# Check Docker status
sudo systemctl status docker

# Restart Docker
sudo systemctl restart docker

# View logs
sudo journalctl -u docker.service
```

### OpenClaw Gateway Issues

```bash
# Check gateway status
openclaw gateway status

# View logs
openclaw logs

# Restart gateway
openclaw gateway restart
```

### SSH Tunnel Not Working

```bash
# Test VPS SSH access
ssh username@vps-ip

# Check if port is forwarded
netstat -tlnp | grep 18789
```

---

## 📚 Additional Resources

- [OpenClaw Documentation](https://docs.openclaw.ai/)
- [GitHub CLI Documentation](https://cli.github.com/)
- [Docker Installation Guide](https://docs.docker.com/engine/install/)
- [TDD Best Practices](https://martinfowler.com/bliki/TestDrivenDevelopment.html)

---

## 💼 Project Ideas for POC Development

This VPS setup is optimized for running multiple local development environments for **Proof of Concept (POC)** projects. Each project can run its own Docker containers for testing and development.

### 🔟 Suggested Projects (Test-Driven Development Approach)

| # | Project | Tech Stack | Purpose |
|---|---------|------------|---------|
| 1 | **Portfolio Tracker** | Python/Django | Stock & crypto tracking with TDD |
| 2 | **AI Code Reviewer** | Node.js/TypeScript | Automated code review with AI agents |
| 3 | **Note-Taking App** | Vue.js/Node.js | Personal knowledge management |
| 4 | **Chat Application** | Elixir/Phoenix | Real-time messaging platform |
| 5 | **Password Manager** | Rust/Actix | Secure credential storage |
| 6 | **ML Pipeline** | Python/FastAPI | ML model training & inference |
| 7 | **API Gateway** | Go/Gin | Centralized API management |
| 8 | **Task Manager** | Kotlin/Spring Boot | Team productivity tracking |
| 9 | **Music Streaming API** | Ruby on Rails | Music library & streaming |
| 10 | **URL Shortener** | Java/Quarkus | URL management with analytics |

### 🏗️ Development Workflow

```
┌─────────────────────────────────────────────────────┐
│              LOCAL DEVELOPMENT CYCLE                 │
│                                                     │
│   1. 🏃 Run all Docker containers locally          │
│   2. 🔄 Rapid iteration on code                    │
│   3. ✅ Run TDD test suites in parallel            │
│   4. 🚀 Push to GitHub when ready                  │
│                                                     │
└─────────────────────────────────────────────────────┘
```

---

## 🤝 Contributing

Found an issue or have a suggestion? Open an issue or PR!

---

## 📄 License

MIT License — feel free to use and share.

---

**Built with ❤️ using OpenClaw**
