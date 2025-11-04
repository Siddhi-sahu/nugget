# Nugget — Setup & Usage

Short overview
- Frontend: React + Vite app in [frontend/](frontend/) 
- Backend: FastAPI service in [backend/main.py](backend/main.py) that fetches RSS feeds, extracts article content with `newspaper3k`, caches in Redis, and generates titles/summaries via Groq Llama (see [`generate_title_and_summary`](backend/main.py) and [`redis_client`](backend/main.py)).

Prerequisites
- Node.js (18+) and npm
- Python 3.10+
- Docker (recommended for Redis) or a running Redis server
- (Optional) Groq API key for summarization

Quick start — backend
1. Create & activate a virtual environment, install deps:
```bash
python -m venv .venv
source .venv/bin/activate
pip install -r [requirements.txt](http://_vscodecontentref_/0)
```

2. Create backend environment file backend/.env with at least:
```bash
GROQ_API_KEY=your_groq_api_key_here
REDIS_URL=redis://localhost:6379
CACHE_EXPIRATION=3600
```

3. Run Redis 

4. Start the backend API:
# from project root
```bash
python -m uvicorn backend.main:app --host 0.0.0.0 --port 8000 --reload
```
