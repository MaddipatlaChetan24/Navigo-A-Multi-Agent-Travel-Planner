<div align="center">

# Navigo AI

**Transform a natural-language trip request into a complete, practical travel plan.**

Enter your travel request — get flight suggestions, hotel ideas, and a day-by-day itinerary using a multi-agent AI workflow.

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)](https://python.org)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![LangChain](https://img.shields.io/badge/LangGraph-1C3C3C?logo=langchain&logoColor=white)](https://langchain.com)
[![Groq](https://img.shields.io/badge/Groq-LLM-F55036?logo=groq&logoColor=white)](https://groq.com)

</div>

---

## Features

| Feature | Description |
|---|---|
| **Flight Research** | Live flight data and suggestions via AviationStack |
| **Hotel Discovery** | Real-time accommodation searches via Tavily |
| **Multi-Agent Orchestration** | Complex task routing using LangGraph and LangChain |
| **Structured Itineraries** | Practical, day-by-day travel plans customized to your prompt |
| **Conversation Memory** | State persistence across requests using PostgreSQL |
| **Lightning Fast LLMs** | Powered by Groq for near-instant response generation |
| **PDF Export** | Download your travel plan as a beautifully formatted PDF |
| **Modern UI** | Sleek, dark-themed HTML/CSS/JS frontend with micro-animations |

---

## Architecture

```mermaid
flowchart LR
    A["User Prompt"] --> B["FastAPI Backend"]
    B --> C{"LangGraph\nWorkflow"}
    
    C --> D["Flight Agent\n(AviationStack)"]
    C --> E["Hotel Agent\n(Tavily Search)"]
    C --> F["Itinerary Agent\n(Groq LLM)"]
    
    D --> G["Final\nResponse Agent"]
    E --> G
    F --> G
    
    G --> H["Polished\nTravel Plan"]
    H --> B
    B --> I["Web UI / PDF"]
```

---

## Tech Stack

- **Framework**: [FastAPI](https://fastapi.tiangolo.com/)
- **Frontend**: HTML5, CSS3, Vanilla JS, Jinja2 Templates
- **AI Orchestration**: [LangGraph](https://python.langchain.com/docs/langgraph) & [LangChain](https://langchain.com)
- **LLM Provider**: [Groq](https://groq.com/)
- **Database**: PostgreSQL (for LangGraph state checkpointer)
- **Search API**: [Tavily](https://tavily.com/)
- **Flight API**: [AviationStack](https://aviationstack.com/)

---

## Quick Start

### Prerequisites

- Python ≥ 3.10
- PostgreSQL running locally or accessible remotely
- API Keys for Groq, Tavily, and AviationStack

### Installation

```bash
# Clone the repository
git clone https://github.com/YOUR_USERNAME/navigo.git
cd navigo

# Create virtual environment
python -m venv .venv
source .venv/bin/activate   # macOS/Linux
# .venv\Scripts\activate    # Windows

# Install dependencies
pip install -r requirements.txt
```

### Configuration

Create a `.env` file in the root directory:

```env
DATABASE_URL=postgresql://user:password@localhost:5432/travel_db
GROQ_API_KEY=your_groq_api_key
AVIATIONSTACK_API_KEY=your_aviationstack_api_key
TAVILY_API_KEY=your_tavily_api_key
DEFAULT_ORIGIN_IATA=DAC
```

### Run

```bash
python app.py
```

The app opens at **http://127.0.0.1:8000/**.

---

## Project Structure

```text
navigo/
├── app.py                # FastAPI entry point & API routes
├── backend.py            # LangGraph multi-agent workflow definition
├── requirements.txt      # Python dependencies
├── static/               # CSS, JS, and static assets
│   ├── style.css         # Modern dark-theme styles
│   └── script.js         # Frontend interactivity & PDF export
├── templates/            # HTML templates
│   └── index.html        # Main web interface
└── tools/                # Agent tools
    └── tavily_tool.py    # Tavily web search integration
```

---

## Usage

1. Open `http://127.0.0.1:8000/` in your browser.
2. Type a travel request (e.g., *"Plan a 7-day trip to Tokyo from DAC under $1500"*).
3. Click **Generate Plan**.
4. The LangGraph agents will collaborate in the background to fetch flights, hotels, and build an itinerary.
5. Review your personalized travel plan and click **Download PDF** to save it.

---

## Environment Variables

| Variable | Required | Description |
|---|---|---|
| `DATABASE_URL` | Yes | PostgreSQL connection string for saving conversation threads |
| `GROQ_API_KEY` | Yes | Groq API key for LLM inference |
| `TAVILY_API_KEY` | Yes | Tavily API key for hotel and location research |
| `AVIATIONSTACK_API_KEY`| Yes | AviationStack API key for live flight data |
| `DEFAULT_ORIGIN_IATA` | No | Default airport IATA code (e.g., DAC, JFK, LHR) |

---

## Docker Deployment

The project includes a `Dockerfile` for containerized deployment.

```bash
# Build the image
docker build -t navigo-app .

# Run the container (ensure your .env is passed)
docker run -p 8000:8000 --env-file .env navigo-app
```

---

## License

This project is open-source and available for educational and practical travel-planning purposes.

---

<div align="center">
<sub>Built using Python, FastAPI, LangGraph, Groq & Tavily</sub>
</div>
