# Multi Agent Stock Trader

An autonomous multi-agent financial research and stock analysis system powered by the **CrewAI** agentic framework.

Agentic Stock Trader simulates a collaborative research team of AI agents that autonomously discover, analyze, and recommend the best investment opportunities in the stock market. Each agent specializes in a task, from tracking trending companies to conducting deep financial research, and works together under a hierarchical structure to produce high-quality investment insights.

---

## Overview

The system operates as an autonomous CrewAI pipeline, where specialized AI agents perform distinct roles:

1. **Trending Company Finder** – Scans financial news to identify trending companies.  
2. **Financial Researcher** – Performs detailed financial and market analysis.  
3. **Stock Picker** – Evaluates and selects the most promising stock for investment.  
4. **Manager Agent** – Delegates tasks, ensures workflow consistency, and synthesizes final outputs.

Once the decision is made, the system delivers:
- A comprehensive market report  
- A real-time push notification with investment recommendations (via Pushover API)

---


Each agent is defined in `config/agents.yaml`, while their corresponding objectives and tasks are outlined in `config/tasks.yaml`.

---

## Key Features

- Multi-Agent Collaboration — Each agent performs a unique, specialized task.  
- Hierarchical Workflow — A manager agent coordinates and verifies work.  
- RAG-Based Memory System — Combines short-term and long-term storage using ChromaDB and SQLite.  
- Real-Time Notifications — Sends stock alerts through Pushover API.  
- Persistent Context Awareness — Agents remember prior analyses and avoid duplicate companies.  
- Configurable Framework — Easily modify or add new agents and tasks.

---

## Tech Stack

| Category | Tools / Frameworks |
|-----------|--------------------|
| Language | Python |
| Agent Framework | CrewAI |
| LLM Integration | OpenAI GPT Models |
| Data Retrieval | SerperDevTool |
| Memory Storage | RAG (ChromaDB) · SQLite |
| Notifications | Pushover API |
| Validation / Models | Pydantic |
| Dependency Management | UV / pip |

---

## Setup Instructions
1. Clone the repository:
   ```bash
   git clone https://github.com/jualam/Multi_Agent_Stock_Trader.git
   cd CrewAI_Debate_System
   
2. Install dependencies:
   ```bash
   pip install -r requirements.txt or uv sync
   
3. Add your API keys in a .env file:

OPENAI_API_KEY=your_openai_key
CHROMA_OPENAI_API_KEY=your_openai_key
PUSHOVER_USER=your_pushover_user_key
PUSHOVER_TOKEN=your_pushover_token
SERPER_API_KEY=your_serper_key
MODEL=gpt-4o-mini

5. Start the application: crewai run


