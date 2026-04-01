<div align="center">
  <h1>🚀 ProfitPilot (Intelligent Business Agent)</h1>
  <p><strong><em>Your AI Business Partner that Thinks Before You Act.</em></strong></p>
</div>

---

## 💡 The Problem
Small business owners have to make countless decisions daily: pricing, marketing budgets, hiring, and expansion. Usually, these decisions are made based on **guesswork, emotion, or pressure** because their data is scattered across spreadsheets, notebooks, and various apps. 

The tragic result? **Wasted money, cash flow crises, and stressful stagnation.** 

*There currently exists no system that simply says: "Stop, this decision is risky" before an owner makes a mistake.*

## 🌟 Our Solution
**ProfitPilot** is not just a chatbot—it’s an **AI-powered Business Partner** tailored for small to medium enterprises. 

By unifying all an owner's financial, operational, and performance data, our AI analyzes the current situation and provides real-time, human-like advice. Before a business owner executes a potentially harmful decision, ProfitPilot evaluates it, provides a **Business Health Score**, and issues proactive warnings.

### Why ProfitPilot Wins 🏆
- **Preventative Intelligence:** Instead of retroactive analytics, we offer **preventative advice**. (e.g., "⚠️ *Risky: You only have enough cash flow for 40 days, wait on that $3k ad spend.*")
- **Omnichannel Access:** Talk to your business directly via a **Dashboard**, **Personal WhatsApp Number**, or **Telegram**.
- **Agentic Workflows:** Powered by a deeply integrated LangGraph and LLM backend connecting directly to your live SQL databases, Grafana metrics, and daily logs.
- **Dynamic Dashboard:** A rich Next.js dashboard that visualizes the AI's insights, generates full markdown reports, and acts on recommendations.

---

## ✨ Key Features
1. **Understand The Business:** AI stores past decisions, current metrics (sales, expenses, profit), and live problems to retain full context.
2. **"Before-Action" Checks:** Type in a planned action, and get a clear response:  ✅ Safe | ⚠️ Risky | ❌ Do Not Proceed.
3. **Health Dashboard & Monitoring:** A unified interface scoring overall business health, highlighting metrics like revenue vs. expenses, employee stats, and live alerts.
4. **WhatsApp & Telegram Bots:** Real-time conversational interface proxying right into our Flask backend for mobile, on-the-go decisions.
5. **Continuous Threat Warning:** Automatically flags runaway expenses and dangerous cash flow trends.

---

## 🛠 Tech Stack
- **Frontend & Dashboard:** Next.js (Standalone), React, Tailwind CSS, Vite (TanStack for Landing Page).
- **Agentic Backend:** Python, Flask, LangGraph, Ollama (LLM orchestration).
- **Database:** PostgreSQL (with `pgAdmin` for UI management), SQLite (for chat history).
- **Observability:** Prometheus, Grafana Loki, Promtail (for real-time metrics and logs).
- **Gateways:** `whatsapp-web.js` (Custom WhatsApp integration without official Cloud API costs).

---

## 🚀 Getting Started

### Prerequisites
- [Docker](https://www.docker.com/) & Docker Compose installed.
- [Ollama](https://ollama.ai/) installed locally and running `llama3.2:3b`.

### 1. Environment Variables Configuration
In the `agent_code` directory, ensure you have an `.env` file with the following database connection string:
```bash
DATABASE_URL=postgresql://admin:root@db:5432/test_db
```

### 2. Boot up the Ecosystem
Clone the repository and instantly spin up the entire multi-container environment:
```bash
docker compose up -d --build
```
*This spins up PostgreSQL, pgAdmin, the Next.js Dashboard, the Vite Landing Page, the Flask Agent, Prometheus, Loki, and Grafana.*

### 3. Database Initialization
Once the containers are running, you need to seed the database with the schema and initial AI test data.

1. **Copy Schema & Data to Postgres Container:**
   ```bash
   docker cp company_db_schema.sql <postgres_container_name>:/company_db_schema.sql
   docker cp inserts.sql <postgres_container_name>:/inserts.sql
   ```
2. **Execute the SQL scripts inside the container:**
   ```bash
   docker exec -it <postgres_container_name> psql -U admin -d test_db -f /company_db_schema.sql
   docker exec -it <postgres_container_name> psql -U admin -d test_db -f /inserts.sql
   ```
   *(Ensure to replace `<postgres_container_name>` with your actual running `db` container name, usually `intelligent-business-agent-db-1`)*.

### 4. Access the Ecosystem
- **Landing Page & Onboarding:** `http://localhost:5173`
- **Next.js Dashboard:** `http://localhost:3001` *(Your main hub)*
- **Agent Backend API:** `http://localhost:5000`
- **Postgres UI (pgAdmin):** `http://localhost:5050` (Email: `mohitmolela@gmail.com` / Pass: `root`)
- **Grafana Metrics:** `http://localhost:3000`

---

## 📱 Integration Guides
We support extensive messaging integrations so you can ask business questions from anywhere! 
Refer to the dedicated documentation for setup:
- [WhatsApp Setup Guide](./WHATSAPP_INTEGRATION_GUIDE.md)
- [Telegram Setup Guide](./TELEGRAM_INTEGRATION_GUIDE.md)
- [Full Project Architecture Context](./PROJECT_CONTEXT.md)

---

**Built to give Small Business Owners peace of mind and data-driven confidence.** 💡

