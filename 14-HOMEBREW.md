# 1️⃣4️⃣ Homebrew Installation (Optional)

Install Homebrew for additional development tools on Linux.

---

## 📦 Installation Command

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

---

## 🔍 What This Does

| Feature | Purpose |
|---------|---------|
| **Homebrew** | Package manager for Linux |
| **brew** | Command to install software |
| **Linuxbrew** | Linux-specific packages |

---

## ✅ Verify Installation

```bash
brew --version
brew doctor
```

---

## 📦 Useful Brew Packages

```bash
# Install useful tools
brew install git
brew install node
brew install python
brew install docker-compose
brew install gh
brew install lazygit
brew install fzf
brew install ripgrep
brew install fd
```

---

## ⚠️ Common Issues

### Installation Fails

```bash
# Install dependencies first
sudo apt-get install build-essential curl file git

# Then retry
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### PATH Not Set

```bash
# For bash
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.bashrc
eval "$(/opt/homebrew/bin/brew shellenv)"

# For zsh
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc
eval "$(/opt/homebrew/bin/brew shellenv)"
```

---

## 🎯 What's Next?

✅ **Setup Complete!** You're ready to use OpenClaw.

**Next:** [12-TESTING.md](12-TESTING.md) to verify everything works

**Or:** [PROJECT-IDEAS.md](PROJECT-IDEAS.md) for 10 project ideas to build
