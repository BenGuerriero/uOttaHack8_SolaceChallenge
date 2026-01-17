# Career Coach AI - Quick Start Guide

## 🎯 What You Have Now

You've successfully set up the **Solace Agent Mesh framework** for your hackathon project! Here's what's ready:

### ✅ Core Infrastructure
- **Solace Event Mesh**: SAM running on localhost:8000
- **Event Schemas**: Complete event catalog with 12 event types
- **Solace Client**: Pub/sub wrapper for easy event handling
- **SurveyMonkey Client**: Invisible feedback collection

### ✅ Agents Built
1. **Profile Agent** - Manages user profiles and skill tracking
2. **Market Agent** - Provides job market insights and salary data
3. **Surveyor Agent** - Captures feedback to SurveyMonkey

### 📁 Project Structure
```
primal-zenith/
├── backend/
│   ├── agents/
│   │   ├── base_agent.py       ✅ Base class for all agents
│   │   ├── profile_agent.py    ✅ User profile management
│   │   ├── market_agent.py     ✅ Job market data
│   │   └── surveyor_agent.py   ✅ SurveyMonkey integration
│   └── services/
│       ├── solace_client.py    ✅ Solace connection
│       └── surveymonkey_client.py ✅ SurveyMonkey API
├── shared/
│   └── event-schemas.json      ✅ Event definitions
├── test_agent_mesh.py          ✅ Test script
└── requirements.txt            ✅ Dependencies
```

## 🚀 Next Steps

### 1. Keep SAM Running (Choose One)

**Option A: Simple Background Window**
```bash
run-sam-background.bat
```

**Option B: Windows Service (Recommended)**
```powershell
# Run PowerShell as Administrator
.\install-sam-service.ps1
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

### 3. Configure Environment
```bash
# Copy the example
copy .env.example .env

# Edit .env with your API keys
notepad .env
```

**Required Configuration:**
- `SOLACE_HOST=tcp://localhost:55555` (default for SAM)
- `SURVEYMONKEY_API_KEY=your_key`
- `SURVEYMONKEY_ACCESS_TOKEN=your_token`
- `OPENAI_API_KEY=your_key` (for AI features)

### 4. Test the Agent Mesh
```bash
python test_agent_mesh.py
```

You should see:
- ✅ Agents starting up
- 📤 Events being published
- 📥 Agents receiving and processing events
- 🎯 SurveyMonkey feedback capture (if configured)

## 🎨 What's Left to Build

### High Priority (Core Demo)
- [ ] **Orchestrator** - WebSocket server for frontend communication
- [ ] **Frontend** - Invisible onboarding + chat interface
- [ ] **Resume Agent** - PDF/DOCX parsing
- [ ] **Application Agent** - AI-powered cover letter generation

### Medium Priority (Polish)
- [ ] **Visuals Agent** - Skill gap charts
- [ ] Database integration (currently in-memory)
- [ ] Better AI prompts for coaching persona

### Low Priority (Nice to Have)
- [ ] Real job market API integration
- [ ] Advanced resume optimization
- [ ] Multi-user support

## 🔧 Troubleshooting

### SAM Won't Start
```bash
# Check if SAM is installed
sam --version

# Check if port 8000 is in use
netstat -ano | findstr :8000
```

### Solace Connection Fails
- Make sure SAM is running: `http://localhost:8000`
- Check `.env` has correct `SOLACE_HOST`
- Default credentials: `default/default/default`

### Import Errors
```bash
# Make sure you're in the project root
cd C:\Users\nguye\.gemini\antigravity\playground\primal-zenith

# Install dependencies
pip install -r requirements.txt
```

## 📚 Key Concepts

### Event-Driven Architecture
Agents don't call each other directly. Instead:
1. Agent A publishes an event to Solace
2. Solace routes it to subscribed agents
3. Agent B receives and processes the event
4. Agent B publishes a response event

### Invisible Onboarding
Instead of "Fill out this form," you ask:
> "What's the one job title you're chasing?"

As they type, you create their profile invisibly.

### The Coach Persona
The user thinks they're talking to a career coach. Behind the scenes, agents are:
- Tracking skill gaps
- Fetching market data
- Sending insights to SurveyMonkey
- Preparing tailored applications

## 🏆 Hackathon Winning Strategy

### Solace Requirements ✅
- ✅ Event-driven architecture
- ✅ Multiple agents communicating via mesh
- ✅ Real-time event processing
- ✅ Decoupled services

### SurveyMonkey Requirements ✅
- ✅ Invisible feedback collection
- ✅ High-value insights (struggles, goals, applications)
- ✅ Tagged data for analysis
- ✅ No explicit "survey" UX

### Demo Flow
1. **Landing Page**: "In 30 seconds, I'll tell you your market value"
2. **Invisible Onboarding**: User types job title → Profile created
3. **Chat Interaction**: User says "I'm struggling with Python"
   - Profile Agent updates skill gap
   - Surveyor Agent sends to SurveyMonkey
   - Coach responds with resources
4. **Market Insights**: "How do I compare?"
   - Market Agent fetches data
   - Visuals Agent generates chart
5. **Application**: "Help me apply to Google"
   - Application Agent generates cover letter
   - Surveyor captures high-value action

## 🎯 Ready to Continue?

You now have a solid foundation! The agent mesh is working. Next, you should build:

1. **Orchestrator** - The WebSocket server that connects frontend to agents
2. **Frontend** - The beautiful, invisible onboarding experience
3. **Remaining Agents** - Resume, Application, Visuals

Let me know which part you want to tackle next! 🚀
