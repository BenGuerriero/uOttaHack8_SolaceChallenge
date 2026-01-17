# Career Coach AI - Solace Hackathon Project

An event-driven career coaching platform using Solace Agent Mesh and SurveyMonkey for invisible feedback collection.

## Quick Start

### Keep SAM Running (Choose One Method)

#### Method 1: Simple Background Window (Easiest)
```bash
# Double-click this file or run:
run-sam-background.bat
```
This runs SAM in a minimized window. Close the window to stop SAM.

#### Method 2: Windows Service (Recommended for Development)
```powershell
# Run PowerShell as Administrator, then:
.\install-sam-service.ps1
```
This installs SAM as a Windows service that auto-starts with Windows.

#### Method 3: Manual Background Process
```bash
# In PowerShell:
Start-Process -NoNewWindow -FilePath "sam" -ArgumentList "run"
```

### Project Structure

```
primal-zenith/
├── backend/
│   ├── orchestrator.py          # Top Level Agent (WebSocket + Solace)
│   ├── agents/
│   │   ├── profile_agent.py     # User profile management
│   │   ├── market_agent.py      # Job market data
│   │   ├── resume_agent.py      # Resume parsing
│   │   ├── application_agent.py # Cover letter generation
│   │   ├── visuals_agent.py     # Chart generation
│   │   └── surveyor_agent.py    # SurveyMonkey integration
│   ├── services/
│   │   ├── solace_client.py     # Solace PubSub+ connection
│   │   └── surveymonkey_client.py
│   └── tests/
├── frontend/
│   ├── index.html               # Main UI
│   ├── styles.css               # Premium design
│   └── app.js                   # WebSocket + interactions
├── shared/
│   └── event-schemas.json       # Event definitions
└── docs/
    ├── ARCHITECTURE.md
    └── EVENT_CATALOG.md
```

## Installation

```bash
# Install Python dependencies
pip install -r requirements.txt

# Set up environment variables
cp .env.example .env
# Edit .env with your API keys
```

## Running the Application

```bash
# Start SAM (if not running as service)
sam run

# Start backend
python backend/orchestrator.py

# Open frontend
# Navigate to frontend/index.html in browser
```

## Architecture

The system uses event-driven architecture with Solace Agent Mesh:

1. **User** → Interacts with frontend
2. **Orchestrator** → Routes events via Solace
3. **Agents** → Process events independently
4. **Surveyor** → Captures insights to SurveyMonkey

See [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md) for details.

## API Keys Required

- Solace PubSub+ Cloud credentials
- SurveyMonkey API key
- OpenAI API key (or Ollama for local LLM)
