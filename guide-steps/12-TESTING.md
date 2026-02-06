# 1⃣2⃣ Testing Your Setup

Verify that all components are working correctly.

---

##  Verification Checklist

### 1. Gateway Status

```bash
openclaw gateway status
```

**Expected:** Gateway is running on port 18789

### 2. Channel Connection

Send a test message through paired channel:

**Telegram:** Message your bot `/start`

**WhatsApp:** Send a message to your linked number

**Discord:** Mention your bot in chat

### 3. AI Model Response

```bash
# Test coding capability
"Write a Python function to calculate Fibonacci numbers with memoization"

# Test reasoning capability
"Design a microservices architecture for an e-commerce platform"
```

### 4. GitHub Integration

```bash
# Test GitHub access
gh auth status

# Or test API directly
curl -s -H "Authorization: token YOUR_GITHUB_TOKEN" https://api.github.com/user
```

---

##  Test Prompts

### Coding Test

```
Write a Python class for a simple bank account with deposit, withdraw, and balance methods. Include unit tests.
```

**Expected:** Working Python code with tests

### Reasoning Test

```
What are the trade-offs between REST and GraphQL APIs? Give examples of when to use each.
```

**Expected:** Detailed analysis with examples

### Docker Test

```
Create a Dockerfile for a Python Flask application
```

**Expected:** Complete Dockerfile with proper structure

---

##  Success Criteria

- [ ] Gateway is running
- [ ] At least one channel is paired
- [ ] Coding model responds to code requests
- [ ] Reasoning model handles complex questions
- [ ] GitHub integration works (if configured)

---

##  Common Failures

### No Response from AI

1. Check API keys are correct
2. Verify model is available
3. Check billing/credits

### Channel Not Responding

1. Check channel is enabled in config
2. Verify pairing was completed
3. Check logs: `openclaw logs`

---

##  Next Step

**[13-GITHUB.md](13-GITHUB.md)** - Complete GitHub integration setup
