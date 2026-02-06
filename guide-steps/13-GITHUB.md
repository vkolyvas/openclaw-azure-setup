# 1️⃣3️⃣ GitHub Integration

Connect GitHub for repository management, issues, and PRs.

---

## 📦 Create Auth Profile

```bash
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

---

## 🔑 Generate GitHub Token

1. Go to **GitHub Settings** → **Developer Settings** → **Personal Access Tokens** → **Tokens (classic)**
2. Generate new token with scopes:
   - `repo` — Full control of private repositories
   - `read:user` — Read user profile data
   - `delete_repo` — Delete repositories (optional)
3. Copy and use in the config above

---

## ✅ Verify Connection

```bash
# Using GitHub CLI
gh auth status

# Or test API directly
curl -s -H "Authorization: token YOUR_TOKEN" https://api.github.com/user
```

---

## 🎯 Example Commands

### Create Repository

```bash
gh repo create my-new-repo --public --description "My new project"
```

### List Repositories

```bash
gh repo list --limit 10
```

### Create Issue

```bash
gh issue create --title "Bug found" --body "Description of the bug"
```

---

## ✅ Success Criteria

- [ ] Auth profile created
- [ ] `gh auth status` shows authenticated
- [ ] Can create/list repositories
- [ ] Can manage issues and PRs

---

## ⚠️ Common Issues

### Token Invalid

```bash
# Test token
curl -s -H "Authorization: token YOUR_TOKEN" https://api.github.com/user
```

### Permission Denied

Ensure token has required scopes (`repo` for private repos)

---

## 🎯 Next Step

**[14-HOMEBREW.md](14-HOMEBREW.md)** — Install Homebrew (optional)
