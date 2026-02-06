# 1️⃣5️⃣ Azure AI Foundry Setup

Create an Azure AI Foundry project and deploy Opus 4.6 or Kimi K2.5 models for advanced reasoning.

---

## 🎯 Why Azure AI Foundry?

| Model | Strengths | Best For |
|-------|-----------|----------|
| **Opus 4.6** | Advanced reasoning, planning | Architecture decisions, complex problem solving |
| **Kimi K2.5** | Extended context window | Document analysis, long conversations |

---

## 📦 Step 1: Create Azure Account

1. Visit [Azure Portal](https://portal.azure.com)
2. Sign in or create free account
3. Navigate to **Azure AI Foundry**

---

## 📦 Step 2: Create AI Foundry Project

1. Go to [Azure AI Foundry](https://ai.azure.com)
2. Click **New project**
3. Configure:
   - **Project name:** `openclaw-models`
   - **Subscription:** Your Azure subscription
   - **Resource group:** Create new or select existing
4. Click **Create**

---

## 📦 Step 3: Deploy Model

### Deploy Opus 4.6

1. In your project, click **Deployments** → **+ New deployment**
2. Select model: **Opus 4.6**
3. Configure:
   - **Deployment name:** `opus-4-6`
   - **Tokens per minute:** Adjust based on needs
4. Click **Deploy**

### Deploy Kimi K2.5

1. In your project, click **Deployments** → **+ New deployment**
2. Select model: **Kimi K2.5**
3. Configure:
   - **Deployment name:** `kimi-k2-5`
   - **Tokens per minute:** Adjust based on needs
4. Click **Deploy**

---

## 📦 Step 4: Get API Key

1. In Azure portal, go to your **AI Foundry resource**
2. Click **Keys and Endpoint**
3. Copy **Key 1** or **Key 2**
4. Copy the **Endpoint** URL

---

## 📦 Step 5: Configure OpenClaw

Edit `~/.openclaw/openclaw.json`:

```json
{
  "models": {
    "providers": {
      "azure-ai-foundry": {
        "apiKey": "YOUR_AZURE_API_KEY",
        "baseUrl": "https://YOUR_RESOURCE_NAME.openai.azure.com/",
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
            "bestFor": "Advanced reasoning, architecture"
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
            "bestFor": "Extended context, documents"
          }
        ]
      }
    }
  }
}
```

---

## ✅ Verify Deployment

```bash
# Test API connection
curl -s -H "Authorization: Bearer YOUR_AZURE_KEY" \
  "https://YOUR_RESOURCE.openai.azure.com/openai/models?api-version=2024-02-15-preview"

# Restart OpenClaw
openclaw gateway restart
```

---

## 💰 Cost Management

| Resource | Estimated Cost |
|----------|----------------|
| AI Foundry Resource | ~€10/month (minimum) |
| Opus 4.6 | ~$15 input / $75 output per 1M tokens |
| Kimi K2.5 | ~$10 input / $40 output per 1M tokens |

---

## ⚠️ Common Issues

### Authentication Failed

1. Verify API key is correct
2. Check endpoint URL format
3. Ensure resource is in same region

### Model Not Available

1. Check Azure regional availability
2. Verify model name exactly (opus-4-6, kimik2-5)

---

## ✅ Success Criteria

- [ ] Azure AI Foundry project created
- [ ] Opus 4.6 deployed
- [ ] API key copied
- [ ] OpenClaw configured
- [ ] Gateway restart successful

---

## 🎯 Next Step

**[12-TESTING.md](12-TESTING.md)** — Verify your setup works correctly
