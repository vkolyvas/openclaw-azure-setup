# 2⃣ VPS Requirements

Azure VM specifications optimized for running multiple AI projects and Docker containers simultaneously.

---

## ⚙ Recommended Configuration

| Resource | Specification |
|----------|---------------|
| **VM Size** | **Standard_E6as_v6** |
| **vCPUs** | 6 |
| **RAM** | 36 GB |
| **Temp Storage** | 140 GB |
| **Est. Cost** | ~€140/month |

---

##  Why This Configuration?

### Heavy Workload Requirements

This VPS is designed for **power users** who need to:

-  **Spin up multiple local projects** simultaneously for POC development
-  **Run numerous Docker containers** at the same time
-  **Keep all development environments active** for rapid iteration
-  **Run multiple AI agents** in parallel

---

##  Resource Allocation

With **36 GB RAM**, you can comfortably run:

| Use Case | RAM Required | Containers |
|----------|-------------|-------------|
| Main OpenClaw Gateway | 2-4 GB | 1-2 |
| Docker Daemon | 1-2 GB | System |
| Development Projects | 4-6 GB each | 4-6 concurrent |
| CI/CD Pipelines | 2-4 GB | 2-3 |
| **Total Available** | ~24 GB | **10-12** |

---

## 💰 Cost Breakdown

| Component | Monthly Cost |
|----------|-------------|
| VM (Standard_E6as_v6) | ~€140 |
| Data transfer | ~€10-20 |
| **Total** | **~€150-160/month** |

---

##  Create Azure VM

1. Go to [Azure Portal](https://portal.azure.com)
2. Click **Create** → **Virtual Machine**
3. Configure:
   - **Size:** Standard_E6as_v6
   - **Image:** Ubuntu 22.04 LTS
   - **SSH:** Allow port 22
4. Review and create

---

##  Scaling Options

| Workload Type | Recommended RAM |
|---------------|----------------|
| 5 Light Projects | 16 GB |
| 10 Medium Projects | 32 GB |
| 10 Heavy Projects (ML/AI) | 64 GB+ |

>  **Pro Tip:** Start with Standard_E6as_v6 (36 GB) and scale up based on your needs.

---

**Next:** [03-SYSTEM-UPDATE.md](03-SYSTEM-UPDATE.md)
