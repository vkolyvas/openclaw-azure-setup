# Long-Term Memory

## 🔐 Security Rules (Non-Negotiable)

### Never Push Secrets
**ALWAYS use placeholder values in config files:**
- API keys → `your_api_key`, `ghp_your_token`
- Tokens → `YOUR_TOKEN_HERE`
- Secrets → Never commit real credentials

**Why:** Protects user security, GitHub blocks secret pushes, prevents credential leaks.

### API Keys to Protect
- GitHub Personal Access Tokens
- MiniMax API keys
- OpenAI API keys
- Anthropic API keys
- Any OAuth tokens
- Database credentials
- SSH private keys

### Best Practices
- Use `.env` files for local secrets
- Add `.env` to `.gitignore`
- Use secret scanning tools
- Rotate compromised keys immediately

---

## 🚫 Never Upload Local Workspace Files to GitHub

These OpenClaw workspace files are **personal and local** — never commit them to public repositories:

| File | Why Not |
|------|---------|
| **AGENTS.md** | Personal agent configurations |
| **SOUL.md** | AI persona and behavior rules |
| **TOOLS.md** | Local infrastructure (cameras, SSH hosts, devices) |
| **USER.md** | Personal user preferences and notes |
| **MEMORY.md** | Long-term memory with security rules |
| **IDENTITY.md** | Personal AI identity |
| **HEARTBEAT.md** | Periodic task reminders |
| **BOOTSTRAP.md** | Initial setup script |
| **.env** | Contains real API keys and secrets |

**Rule:** Keep these files local. Only push guide-specific files like `README.md`, `STEPS.md`, `01-*.md`, etc.

---

## 🔗 MiniMax Referral
- **Code:** `5eJqeeb1XH`
- **URL:** https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link
- **Offer:** 10% off coding plan
