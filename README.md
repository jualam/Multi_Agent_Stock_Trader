# Multi Agent Stock Trader

Multi Agent Stock Trader is a CrewAI-based research workflow that uses specialized AI agents to identify trending technology companies, research their investment potential, and select one company for further consideration.

The project combines market news search, structured agent handoffs, persistent memory, and optional Pushover notifications to produce a concise investment decision report.

> This project is for educational and research purposes only. It does not provide financial advice.

## Features

- Multi-agent workflow built with CrewAI
- Hierarchical manager agent for task coordination
- News search using Serper
- Structured outputs with Pydantic models
- Persistent long-term and short-term memory
- Optional push notification for the final stock decision
- Generated JSON and Markdown reports saved locally

## Agent Workflow

The crew is organized into three specialist agents and one manager:

1. **Trending Company Finder** searches recent market news and identifies 2-3 trending companies in the configured sector.
2. **Financial Researcher** analyzes each company, including market position, outlook, and investment potential.
3. **Stock Picker** compares the research results, selects one company, sends a notification, and writes the final decision report.
4. **Manager Agent** coordinates the hierarchical workflow and delegates tasks.

Agent roles are configured in `src/multi_agent_stock_trader/config/agents.yaml`, and task definitions are configured in `src/multi_agent_stock_trader/config/tasks.yaml`.

## Tech Stack

- Python 3.10+
- CrewAI
- OpenAI models
- Serper search
- ChromaDB-backed RAG memory
- SQLite long-term memory
- Pushover notifications
- uv for dependency management

## Project Structure

```text
src/multi_agent_stock_trader/
  crew.py                 # CrewAI agents, tasks, memory, and process setup
  main.py                 # Application entry point
  config/
    agents.yaml           # Agent roles, goals, backstories, and models
    tasks.yaml            # Task descriptions, outputs, and dependencies
  tools/
    pushover_tool.py      # Custom Pushover notification tool

memory/                   # Local CrewAI memory storage
output/                   # Generated reports and final decision
```

## Setup

Clone the repository and install dependencies:

```bash
git clone https://github.com/jualam/Multi_Agent_Stock_Trader.git
cd Multi_Agent_Stock_Trader
uv sync
```

Create a `.env` file in the project root:

```env
OPENAI_API_KEY=your_openai_api_key
CHROMA_OPENAI_API_KEY=your_openai_api_key
SERPER_API_KEY=your_serper_api_key
PUSHOVER_USER=your_pushover_user_key
PUSHOVER_TOKEN=your_pushover_app_token
MODEL=gpt-4o-mini
```

`PUSHOVER_USER` and `PUSHOVER_TOKEN` are required only if you want push notifications enabled.

## Usage

Run the crew:

```bash
uv run crewai run
```

You can also run the project script directly:

```bash
uv run multi_agent_stock_trader
```

By default, the workflow analyzes the technology sector. The sector input is defined in `src/multi_agent_stock_trader/main.py`.

## Outputs

The workflow writes results to the `output` directory:

- `output/trending_companies.json` - companies identified from recent news
- `output/research_report.json` - detailed research for each company
- `output/decision.md` - final stock selection and rationale

Memory data is stored in the `memory` directory so the agents can retain context across runs.
