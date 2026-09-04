<div align="center">

# Navigo AI

**Transform a natural-language trip request into a complete, practical travel plan.**



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

