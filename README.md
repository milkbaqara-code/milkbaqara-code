<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=25&pause=800&color=00D4FF&center=true&vCenter=true&width=950&height=60&lines=Mohammad+Shajidur+Rahman;Chief+Digital+Officer+%7C+DevOps+%26+AI+Architect;Sovereign+OS+%E2%80%A2+Healthcare+HIS+%E2%80%A2+POS+%E2%80%A2+School+AGI;Wake-on-Demand+%7C+Zero-Downtime+Deploy+%7C+GitOps;Live+in+Dubai%2C+UK%2C+US+%26+Bangladesh." alt="Typing SVG" />

<br/>

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/mohammad-shajidur-rahman)
[![Company](https://img.shields.io/badge/Vigilant_IT_Solution-FF6B35?style=for-the-badge&logo=globe&logoColor=white)](https://www.vigilantitsolution.com)
[![Miracle OS](https://img.shields.io/badge/Miracle_OS_LIVE-00D4FF?style=for-the-badge&logo=vercel&logoColor=black)](https://miracle.vigilantitsolution.com)
[![Miracle HMS](https://img.shields.io/badge/Miracle_HMS_LIVE-00FF88?style=for-the-badge&logo=medscape&logoColor=black)](https://hms.vigilantitsolution.com)
[![Miracle POS](https://img.shields.io/badge/Miracle_POS_LIVE-D4AF37?style=for-the-badge&logo=square&logoColor=black)](https://pos-app.vigilantitsolution.com/auth)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:shajid@vigilantitsolution.com)
[![WhatsApp](https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white)](https://wa.me/8801711477509)

![Profile Views](https://komarev.com/ghpvc/?username=milkbaqara-code&color=00D4FF&style=flat-square&label=Profile+Views)

</div>

---

## 🧠 Who I Am

**Chief Digital Officer (CDO) & Enterprise Architect** at **Vigilant IT Solution Ltd.** — engineering autonomous, production-grade systems across healthcare, hospitality, retail, and education.

I don't just write code. I **design, deploy, and maintain full-stack sovereign ecosystems** — from the database schema to the Nginx reverse proxy, from the SSL certificate to the GitHub Actions CI pipeline. Every architecture below is **live in production**, battle-tested against real hardware, real attacks, and real traffic.

---

## ⚙️ The DevOps Stack I Built — Named & Mapped to Industry Standards

> This is not a list of tools I "know." These are systems I **designed from scratch and run in production**, with documented incident reports, Iron Laws, and auto-recovery protocols.

### 🔵 Layer 1 — Source Control & Continuous Integration

| What I Built | Industry Name | How I Use It |
|---|---|---|
| Git + GitHub (private repos) | **SCM / VCS** | Full version history, branch protection, commit audit trail |
| `.github/workflows/miracle_ci.yml` | **GitHub Actions CI** | Auto-triggers on every `git push` — validates syntax, checks Two-Root Law, verifies WebP assets. No manual step required. |
| `.github/workflows/deploy.yml` | **CD Pipeline (Manual Gate)** | `workflow_dispatch` — deliberate manual trigger for VPS deploy. Prevents accidental pushes from deploying to production. |
| Merge conflict resolution protocol | **Git Conflict Management** | Documented in SOVEREIGN_ENGINEERING_DIRECTIVE — root cause, fix, and Iron Law written for every resolved conflict. |

```
git push origin main
        ↓
GitHub Actions CI fires automatically
  ├── ✅ Python syntax validation
  ├── ✅ Two-Root Law structure check (web/public ↔ public/)
  ├── ✅ WebP asset verification
  └── ❌ If any check fails → BLOCKED. VPS never touched.
```

---

### 🟢 Layer 2 — Process Management & Zero-Downtime Deployment

| What I Built | Industry Name | How I Use It |
|---|---|---|
| PM2 Cluster Mode (2 workers) | **Process Manager + Load Balancer** | Identical to AWS Elastic Beanstalk's multi-instance worker model |
| `pm2 reload --update-env` | **Rolling Deployment / Blue-Green** | Worker 1 restarts → Worker 2 handles all traffic → then Worker 2 restarts. **Zero 502 errors.** |
| Health Probe + Auto-Rollback | **Deployment Health Gate** | Identical to AWS CodeDeploy health checks — probes `/api/health` for 30s post-deploy. If it fails → `.next/` is restored from snapshot. |
| `sovereign_deploy_all.py` (V3.0) | **Custom CD Orchestrator** | SSH + Paramiko. Modes: `all`, `frontend`, `backend`, `audit`, `check`. Writes `deploy_history.jsonl` on every deploy. |
| `logs/deploy_history.jsonl` | **Deployment Audit Log** | Immutable append-only log. Records: timestamp, git commit, build ID, health status, duration. |

```
Before deploy:     cp -r .next/ .next_rollback/    ← snapshot
After pm2 reload:  curl /api/health (15 retries, 2s gap)
If FAILED:         mv .next_rollback/ .next/        ← auto-rollback
                   pm2 reload miracle-frontend      ← instant recovery
```

**Real incident documented:** Before cluster mode, every deploy caused **4–8 seconds of 502 Bad Gateway**. Zero-downtime rolling reload was engineered as a direct fix, now a permanent Iron Law.

---

### 🟡 Layer 3 — Reverse Proxy, SSL & Traffic Routing

| What I Built | Industry Name | How I Use It |
|---|---|---|
| Nginx multi-vhost config | **Reverse Proxy / API Gateway** | Routes traffic to 6 different apps on one VPS by `server_name`. Identical to AWS ALB (Application Load Balancer) routing rules. |
| Let's Encrypt + Certbot | **Automated TLS Certificate Manager** | Like AWS ACM — auto-renews every 90 days via `systemd timer`. Manual certs are banned (Iron Law). |
| Nginx `proxy_pass` to PM2 ports | **Upstream Proxy** | Identical to Nginx as ingress controller in Kubernetes — sits in front of app servers and forwards requests. |
| WebSocket `Upgrade` headers in Nginx | **WebSocket Proxying** | Required for real-time features (WhatsApp Gateway, HMS doctor rooms). |
| UTF-8 charset enforcement in Nginx | **Encoding-Safe HTTP Headers** | Prevents Mojibake corruption — `charset utf-8;` on all HTML locations. Real incident: Bengali & Arabic text was corrupted before this fix. |

---

### 🔴 Layer 4 — Wake-on-Demand (Serverless-Style Cold Start)

> This is the most architecturally unique part of our infrastructure. **I built AWS Lambda-equivalent behavior from scratch on a single VPS.**

| What I Built | Industry Equivalent | Behavior |
|---|---|---|
| `miracle-wakeup-api.py` (Port 9099) | **AWS Lambda / Vercel Serverless Function** | An always-on microservice that boots other services on demand |
| `miracle-auto-sleep.py` | **AWS Lambda Idle Timeout / Scale-to-Zero** | Monitors Nginx access logs every 5 min — if idle >30 min, sends `pm2 stop` to HMS/POS |
| `/var/www/miracle-loading/loading.html` | **Cold Start Loading UI** | The user sees a cyberpunk animation while HMS boots — not an error page |
| Nginx conditional routing to loading page | **Traffic Failover / Health-Based Routing** | If app port is closed, Nginx serves loading page + wakeup trigger instead of 502 |
| Port-open detection (`socket.create_connection`) | **Readiness Probe** | Like Kubernetes `readinessProbe` — doesn't return "online" until TCP port is actually accepting connections |
| `_waking` set (race-condition guard) | **Idempotency Lock / Mutex** | Prevents double-wake if two users hit the endpoint simultaneously |

```
User clicks "HMS Demo" on vigilantitsolution.com
        │
        ▼
hms.vigilantitsolution.com → Nginx checks port 3002
        │
   ┌────┴────┐
   │         │
 OPEN      CLOSED
   │         │
   ▼         ▼
HMS live  /wakeup-api/ → Port 9099
          │
          ├─ pm2 start miracle-hms-backend
          ├─ pm2 start miracle-hms-frontend
          ├─ pm2 start miracle-hms-sentinel
          │
          └─ Poll: socket.connect(3002)?
               NO  → { status: "starting" }
               YES → { status: "online", redirect: "https://hms..." }
                      → loading.html polls → auto-redirect!

After 30 min idle → auto-sleep fires → pm2 stop → RAM freed
Next visitor → cold start cycle repeats
```

**Why this matters:** Miracle HMS + Miracle POS share a 3.7GB VPS with 6 other production services. This pattern means demo services consume **0MB RAM when not in use** — identical to what AWS charges per-invocation for Lambda.

---

### 🟣 Layer 5 — Security Engineering

| What I Built | Industry Name | What It Does |
|---|---|---|
| `scripts/audit_vps_security.py` | **CSPM / Security Audit Tool** | 8-check automated security scan: crypto-miner detection, crontab whitelist, `/etc/ld.so.preload` immutability, known attack IPs in iptables, malware hidden dirs, hidden `/tmp` files, PM2 user audit, SSL expiry |
| `logs/security_audit.jsonl` | **Security Event Log (SIEM-style)** | Append-only JSON Lines audit trail |
| iptables block rules | **Network Firewall / WAF** | Known attack IPs (`193.32.162.73`, `195.178.110.29`) permanently blocked |
| `.env` chmod 600 | **Secret File Hardening** | Environment files readable only by root — compensates for PM2 running as root |
| Anti-Hallucination Sentinel (ops-sentinel) | **Watchdog / Self-Healing Agent** | Always-on Python process that monitors DB state consistency |

**Real security incidents survived and documented:**
- Cryptominer injection attempt via `/etc/ld.so.preload`
- Brute-force IP blocked and permabanned via iptables
- Expired SSL certificate causing `NET::ERR_CERT_DATE_INVALID` — migrated from manual certs to Certbot

---

### ⚪ Layer 6 — Containerization (Built, Ready to Deploy)

| What I Built | Industry Name | Status |
|---|---|---|
| `web/Dockerfile` — 3-stage Next.js | **Multi-Stage Container Build** | ✅ Built — ~150MB image vs ~800MB naive |
| `backend_api/Dockerfile` — 2-stage FastAPI | **Containerized Python Microservice** | ✅ Built — ~120MB image, non-root `miracle-svc` user |
| `docker-compose.yml` — 4-service local stack | **Local Orchestration** | nginx + frontend + backend + redis, with health checks |
| `docker-compose.aws.yml` — AWS override | **Cloud-Ready Compose Profile** | ECR images, RDS, ElastiCache, CloudWatch logging |
| Non-root container user (`miracle-svc`) | **Container Security Hardening** | CIS Docker Benchmark compliance |
| Built-in `HEALTHCHECK` in Dockerfiles | **Container Readiness Probe** | Docker-native equivalent of Kubernetes liveness probe |

> **Status:** Docker fleet is fully designed and built. Currently running on PM2 (stable). Docker migration is the next planned upgrade — drop-in replacement.

---

## 🏗️ Live Production Systems

### 🌐 Miracle OS — The Sovereign Enterprise OS
**`miracle.vigilantitsolution.com`** | Next.js 16 + FastAPI + PostgreSQL

The flagship product. A fully autonomous Enterprise Resource Planning system that unifies 35 operational zones under one sovereign database kernel.

**Architectural highlights:**
- **3-Layer Banking Ledger:** Department Till → Gateway Auth (Z-1B) → Master Ledger (APPEND-ONLY, zero UPDATE/DELETE ever)
- **35 Operational Zones** including: Front Desk PMS, F&B BOM, Real Estate, Fleet, Biometric HR, WhatsApp Gateway, AI Sales Funnel, Task Orchestration Command Matrix
- **Double-Entry Accounting Atomicity:** Every `till_transaction` and `dept_ledger_entry` in the same DB transaction — Iron Law 69
- **Zero-Downtime PM2 Cluster:** 2-worker rolling reload, health probe, auto-rollback
- **WebSocket real-time telemetry** on operational dashboards
- **Multi-language:** English, Bengali, German, Arabic — with UTF-8 encoding Iron Laws enforced at Python, Nginx, and HTML layers

---

### 🏥 Miracle HMS — Clinical Healthcare Intelligence System
**`hms.vigilantitsolution.com`** | FastAPI + Next.js | **Wake-on-Demand (Cold Start)**

A full Hospital Information System (HIS). **Not hospitality. Clinical healthcare.**

- **Doctor WebRTC Tele-Consultation** — real-time peer-to-peer video in browser, no third-party service
- **EMR (Electronic Medical Records)** — patient history, prescription, diagnosis
- **4-Layer Zero-Token AI Cost Pyramid** — routes medical queries through free → cached → local → paid AI tiers
- **Emergency, Lab Reception, Pharmacy** module zones
- **Sovereign Brain V67.0** — the AI clinical assistant backbone
- **Sleep Mode:** Runs on-demand only. `miracle-auto-sleep` parks it after 30 min idle. Zero RAM cost at rest.

---

### 🛒 Miracle POS — Enterprise Point-of-Sale Engine
**`pos-app.vigilantitsolution.com/auth`** | Next.js 15.3 + TypeScript | **100% Offline-Capable**

A standalone POS with **zero cloud dependency**. Operates entirely on flat-file JSON persistence. No internet = still works.

- **6 BOM Department Engines:** F&B, Spa, Boutique, Mini-Shop, Fleet, Pool/Gym
- **Bill of Materials Explosion:** Sell a coffee → system deducts exact grams of raw beans from warehouse in real-time
- **Offline-first architecture:** `db_orders.json`, `db_products.json`, `db_raw_materials.json` — syncs when connection restored
- **Hardware integrations:** Barcode scanner, thermal printer, biometric reader
- **42-hour TTL pruning:** Automatic order cleanup to prevent JSON file bloat
- **Guest PWA:** Customers scan QR → place orders from their phone → auto-appear on POS terminal

---

### 🎓 Miracle School — AI-Powered LMS & MMA AGI Cluster
**Port 9000** | Multi-modal AI Learning Management System

- AGI Cluster for combat sports training analytics
- 3-Path safety protocol for student AI interactions
- Live session tracking and performance telemetry

---

## 🔬 Engineering Depth — What Makes This Different

### The Iron Law System
Every production incident becomes a permanent **Iron Law** — a numbered, documented rule written into `SOVEREIGN_ENGINEERING_DIRECTIVE.md` and enforced in code. As of today: **75+ Iron Laws** across deployment, accounting, security, multi-language, SSL, Docker, and API design.

**Example Laws from real incidents:**

| Law | Incident | Rule |
|---|---|---|
| Law 15 | 4–8s 502 on every deploy | NEVER `pm2 stop/start`. Only `pm2 reload` on cluster mode. |
| Law 66 | Accounting integrity | `master_ledger` is APPEND-ONLY. Zero UPDATE or DELETE, ever. |
| Law 23 | Docker build failure | `DOCKER_BUILD=true` ENV must be set in Stage 2 of Dockerfile. |
| SSL Law | `NET::ERR_CERT_DATE_INVALID` | NEVER manually place SSL certs. Certbot manages `/etc/letsencrypt/live/`. |
| UTF-8 Law | Bengali text corrupted (Mojibake) | ALWAYS `encoding='utf-8'` on every Python file open. |
| Node v22 Law | `SyntaxError` on PM2 start | NEVER use `node_modules/.bin/next` on Node v22+. Use direct `dist/bin/next --interpreter node`. |

---

## 📊 Tech Stack

<div align="center">

**Backend**
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat-square&logo=fastapi&logoColor=white)
![Python](https://img.shields.io/badge/Python_3.11-3776AB?style=flat-square&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-316192?style=flat-square&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-FCA121?style=flat-square&logo=sqlalchemy&logoColor=black)
![WebSocket](https://img.shields.io/badge/WebSocket-010101?style=flat-square&logo=socketdotio&logoColor=white)

**Frontend**
![Next.js](https://img.shields.io/badge/Next.js_16-000000?style=flat-square&logo=next.js&logoColor=white)
![React](https://img.shields.io/badge/React_19-20232A?style=flat-square&logo=react&logoColor=61DAFB)
![TypeScript](https://img.shields.io/badge/TypeScript-007ACC?style=flat-square&logo=typescript&logoColor=white)
![Tailwind](https://img.shields.io/badge/Tailwind_CSS-38B2AC?style=flat-square&logo=tailwind-css&logoColor=white)
![WebRTC](https://img.shields.io/badge/WebRTC-333333?style=flat-square&logo=webrtc&logoColor=white)

**DevOps & Infrastructure**
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=flat-square&logo=github-actions&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white)
![Nginx](https://img.shields.io/badge/Nginx-009639?style=flat-square&logo=nginx&logoColor=white)
![PM2](https://img.shields.io/badge/PM2-2B037A?style=flat-square&logo=pm2&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu_24.04-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![Let's Encrypt](https://img.shields.io/badge/Let's_Encrypt-003A70?style=flat-square&logo=letsencrypt&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=flat-square&logo=git&logoColor=white)

</div>

---

## 📈 GitHub Stats

<div align="center">

![GitHub Stats](https://github-readme-stats.vercel.app/api?username=milkbaqara-code&show_icons=true&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=00D4FF&icon_color=00D4FF&text_color=FFFFFF)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=milkbaqara-code&layout=compact&theme=tokyonight&hide_border=true&bg_color=0D1117&title_color=00D4FF&text_color=FFFFFF)

</div>

---

<div align="center">

*Every system above is live, documented, and defended by Iron Laws written from real production incidents.*

*"Build once. Deploy anywhere. Learn from every incident."*

**Vigilant IT Solution Ltd. — Engineering Sovereign Systems Since 2018**

</div>
