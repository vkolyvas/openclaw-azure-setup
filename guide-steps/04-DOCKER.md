# 4⃣ Install Docker

Install Docker Engine, CLI, containerd, and Docker Compose plugins.

---

##  Commands

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

##  What This Does

| Step | Purpose |
|------|---------|
| GPG Key | Adds Docker's official cryptographic key |
| Repository | Adds Docker's Ubuntu package repository |
| Docker Engine | Core container runtime |
| Docker CLI | Command-line interface |
| Containerd | Container runtime daemon |
| Docker BuildX | Advanced build features |
| Docker Compose | Multi-container orchestration |
| User Group | Run Docker without sudo |

---

##  Verify Installation

```bash
docker --version
docker compose version
docker run hello-world
```

**Expected output:**
```
Docker version 26.x.x
Docker Compose version v2.x.x
Hello from Docker!
```

---

##  Common Issues

### Group Membership Not Active

```bash
# Log out and back in, or run:
newgrp docker
```

### Service Not Running

```bash
sudo systemctl status docker
sudo systemctl start docker
```

---

##  Next Step

**[05-SECURITY-UPDATES.md](05-SECURITY-UPDATES.md)** - Configure automatic security updates
