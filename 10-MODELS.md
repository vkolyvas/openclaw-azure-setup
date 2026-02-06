# 🔟 Configure AI Models

Configure your coding and reasoning AI models for optimal performance.

---

## 🎁 MiniMax Referral Bonus

> Get 10% off MiniMax coding plan: https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

---

## 📦 Configuration File

Edit `~/.openclaw/openclaw.json`:

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

---

## 🎯 Model Selection Strategy

| Task Type | Recommended Model | Reason |
|-----------|-------------------|--------|
| **Code Generation** | MiniMax M2.1 | Perfect multi-coding, fast & cost-effective |
| **Code Review** | MiniMax M2.1 Lightning | Quick feedback |
| **Complex Refactoring** | MiniMax M2.1 | Deep context, strong reasoning |
| **Architecture Decisions** | Claude Opus 4 | Advanced reasoning |
| **Debugging** | MiniMax M2.1 | Multi-language support |
| **Planning** | o1-pro | Extended reasoning |

---

## 🔑 Getting API Keys

### MiniMax (Recommended for Coding)

1. Visit [MiniMax Platform](https://platform.minimax.io/)
2. Sign up and navigate to API section
3. Generate API key
4. Copy to `apiKey` field

### Anthropic (For Reasoning)

1. Visit [Anthropic Console](https://console.anthropic.com/)
2. Create account and generate API key
3. Copy to `apiKey` field

### OpenAI (For Advanced Reasoning)

1. Visit [OpenAI Platform](https://platform.openai.com/)
2. Create account and generate API key
3. Copy to `apiKey` field

---

## ✅ Verify Configuration

```bash
openclaw gateway restart
openclaw gateway status
```

---

## ⚠️ Common Issues

### API Key Invalid

```bash
# Test MiniMax key
curl -s -H "Authorization: Bearer YOUR_MINIMAX_KEY" https://api.minimax.io/anthropic/v1/models

# Test Anthropic key
curl -s -H "x-api-key: YOUR_ANTHROPIC_KEY" https://api.anthropic.com/v1/models

# Test OpenAI key
curl -s -H "Authorization: Bearer YOUR_OPENAI_KEY" https://api.openai.com/v1/models
```

### Model Not Found

Ensure model ID matches exactly what's available from the provider.

---

## 🎯 Next Step

**[11-ONBOARDING.md](11-ONBOARDING.md)** — Configure your AI agent's personality and workflow
