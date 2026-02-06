# OpenClaw VPS Setup Guide
<img width="1400" height="815" alt="Image" src="https://github.com/user-attachments/assets/e5a982fe-a85a-48d6-94fb-dfca9756a062" />

> **Special Offer:** Get 10% off MiniMax coding plan using this referral link: https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

A comprehensive guide to deploying **OpenClaw** - your AI-powered coding assistant - on an Azure VPS with full Telegram, WhatsApp, Discord integration and GitHub access.

---

## Table of Contents

### Quick Start
- [STEPS.md](guide-steps/STEPS.md) - Copy and run all commands

### Step-by-Step Guide

All step-by-step instructions are in the [`guide-steps/`](guide-steps/) folder:

| File | Description |
|------|-------------|
| [guide-steps/01-PREREQUISITES.md](guide-steps/01-PREREQUISITES.md) | What you need before starting |
| [guide-steps/02-VPS-REQUIREMENTS.md](guide-steps/02-VPS-REQUIREMENTS.md) | Azure VM specifications |
| [guide-steps/03-SYSTEM-UPDATE.md](guide-steps/03-SYSTEM-UPDATE.md) | Update Ubuntu packages |
| [guide-steps/04-DOCKER.md](guide-steps/04-DOCKER.md) | Install Docker Engine |
| [guide-steps/05-SECURITY-UPDATES.md](guide-steps/05-SECURITY-UPDATES.md) | Configure automatic updates |
| [guide-steps/06-OPENCLAW-INSTALL.md](guide-steps/06-OPENCLAW-INSTALL.md) | Install OpenClaw |
| [guide-steps/07-PATH.md](guide-steps/07-PATH.md) | Add OpenClaw to PATH |
| [guide-steps/08-SSH-TUNNEL.md](guide-steps/08-SSH-TUNNEL.md) | Remote access setup |
| [guide-steps/09-PAIRING.md](guide-steps/09-PAIRING.md) | Telegram, WhatsApp, Discord |
| [guide-steps/10-MODELS.md](guide-steps/10-MODELS.md) | Configure MiniMax, Azure AI Foundry |
| [guide-steps/11-ONBOARDING.md](guide-steps/11-ONBOARDING.md) | Configure your AI agent |
| [guide-steps/12-TESTING.md](guide-steps/12-TESTING.md) | Verify everything works |
| [guide-steps/13-GITHUB.md](guide-steps/13-GITHUB.md) | Connect GitHub |
| [guide-steps/14-HOMEBREW.md](guide-steps/14-HOMEBREW.md) | Optional: Install Homebrew |
| [guide-steps/15-AZURE-AI-FOUNDRY.md](guide-steps/15-AZURE-AI-FOUNDRY.md) | Azure AI Foundry API setup |

### Additional Resources
- [PROJECT-IDEAS.md](PROJECT-IDEAS.md) - 10 POC project ideas for TDD
- [TROUBLESHOOTING.md](TROUBLESHOOTING.md) - Common issues and solutions

---

## Overview

OpenClaw is an open-source AI gateway that connects multiple AI coding agents to your messaging platforms (Telegram, WhatsApp, Discord). This guide walks you through deploying it on an Azure VPS with full configuration.

**Key Features:**
- Multi-agent AI support
- Telegram, WhatsApp, Discord integration
- GitHub CLI integration
- Docker container management
- Secure authentication
- Remote access via SSH tunnel

---

## Why This Guide?

This guide is designed for **power users** who want to:
- **Spin up multiple local projects** simultaneously for POC development
- **Run numerous Docker containers** at the same time
- **Keep all development environments active** for rapid iteration
- **Run multiple AI agents** in parallel

---

## Tech Stack

| Component | Technology |
|----------|------------|
| **AI Coding** | MiniMax M2.1 (primary), Azure AI Foundry (Opus 4.6, Kimi K2.5) |
| **Messaging** | Telegram, WhatsApp, Discord |
| **Infrastructure** | Azure VPS (Standard_E6as_v6) |
| **Containerization** | Docker + Docker Compose |
| **Version Control** | GitHub |

---

## What's Included

1. **Complete installation commands** - Copy and paste ready
2. **MiniMax M2.1 integration** - Perfect for multi-coding
3. **Azure AI Foundry setup** - Opus 4.6 and Kimi K2.5 models
4. **Channel pairing guides** - Telegram, WhatsApp, Discord
5. **AI model configuration** - Optimal settings for coding + reasoning
6. **10 project ideas** - For TDD development workflow

---

## Quick Start

Copy and run all commands from [guide-steps/STEPS.md](guide-steps/STEPS.md) - Includes steps 1-15 with one-click copy blocks.

---

## Support

- [OpenClaw Documentation](https://docs.openclaw.ai/)
