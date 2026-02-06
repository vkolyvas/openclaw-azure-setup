# 🔟 Configure AI Models

Configure your coding and reasoning AI models for optimal performance.

---

##  MiniMax Referral Bonus

> Get 10% off MiniMax coding plan: https://platform.minimax.io/subscribe/coding-plan?code=5eJqeeb1XH&source=link

---

##  Configuration File

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
      "azure-ai-foundry": {
        "apiKey": "your_azure_api_key",
        "baseUrl": "https://your-resource.openai.azure.com/",
        "api": "azure",
        "models": [
          {
            "id": "opus-4-6",
            "name": "Opus 4.6",
            "cost": {
              "input": 15.00,
              "output": 75.00
            },
            "contextWindow": 200000,
            "maxTokens": 16384,
            "bestFor": "Advanced reasoning, architecture, planning"
          },
          {
            "id": "kimik2-5",
            "name": "Kimi K2.5",
            "cost": {
              "input": 10.00,
              "output": 40.00
            },
            "contextWindow": 200000,
            "maxTokens": 16384,
            "bestFor": "Extended context, document analysis"
          }
        ]
      }
    }
  },
  "agents": {
    "defaults": {
      "model": {
        "primary": "minimax/MiniMax-M2.1",
        "fallbacks": ["minimax/MiniMax-M2.1-lightning", "azure-ai-foundry/opus-4-6"]
      }
    }
  }
}
```

---

##  Model Selection Strategy

| Task Type | Recommended Model | Reason |
|-----------|-------------------|--------|
| **Code Generation** | MiniMax M2.1 | Perfect multi-coding, fast & cost-effective |
| **Code Review** | MiniMax M2.1 Lightning | Quick feedback |
| **Complex Refactoring** | MiniMax M2.1 | Deep context, strong reasoning |
| **Architecture Decisions** | Opus 4.6 (Azure) | Advanced reasoning, planning |
| **Debugging** | MiniMax M2.1 | Multi-language support |
| **Long Context Tasks** | Kimi K2.5 (Azure) | Extended context, documents |

---

##  Getting API Keys

### MiniMax (Recommended for Coding)

1. Visit [MiniMax Platform](https://platform.minimax.io/)
2. Sign up and navigate to API section
3. Generate API key
4. Copy to `apiKey` field

### Azure AI Foundry (For Advanced Reasoning)

1. Create Azure AI Foundry project (see [15-AZURE-AI-FOUNDRY.md](15-AZURE-AI-FOUNDRY.md))
2. Deploy Opus 4.6 or Kimi K2.5 models
3. Get API key from Azure portal
4. Copy to `apiKey` field

---

##  Verify Configuration

```bash
openclaw gateway restart
openclaw gateway status
```

---

##  Common Issues

### API Key Invalid

```bash
# Test MiniMax key
curl -s -H "Authorization: Bearer YOUR_MINIMAX_KEY" https://api.minimax.io/anthropic/v1/models

# Test Azure AI Foundry key
curl -s -H "Authorization: Bearer YOUR_AZURE_KEY" https://your-resource.openai.azure.com/openai/models?api-version=2024-02-15-preview
```

### Model Not Found

Ensure model ID matches exactly what's available from the provider.

---

##  Next Step

**[11-ONBOARDING.md](11-ONBOARDING.md)** - Configure your AI agent's personality and workflow
