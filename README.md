# partnerall-ai

Intelligent B2B matchmaking assistant for partnerall.eu platform.

## Purpose
AI-powered matchmaking that connects organizations based on services offered,
needs, interests and community membership on partnerall.eu.

## Features
- Intelligent B2B partner matching via vector similarity
- Search organizations by service/interest/sector/country
- Community-based recommendations
- Event and matchmaking session suggestions
- "Why this match?" explanations
- Marketplace search (services offered and needed)
- Streaming responses (SSE)

## Tech Stack
- FastAPI + Uvicorn (port 8083)
- vLLM Ministral 14B (port 8000)
- Qdrant vector DB (port 6333) - similarity search
- nomic-embed-text-v1.5 embeddings
- MySQL connector (Laravel backend)
- WireGuard VPN direct to partnerall.eu VPS

## Data Sources
- MySQL database (Laravel backend)
  - Communities (paid + free)
  - Organizations and user profiles
  - Marketplace: services offered
  - Marketplace: interests/needs
  - Events and matchmaking sessions
  - Jitsi meeting records
- Company websites (scraped)

## Project Structure
partnerall-ai/
├── main.py                 → FastAPI app entry point
├── .env                    → Environment variables (not in git)
├── .env.example            → Environment template
├── models/
│   └── schemas.py          → Pydantic models
├── routers/
│   ├── chat.py             → Chat endpoints
│   ├── match.py            → Matchmaking endpoints
│   └── ingest.py           → Data ingestion endpoints
├── services/
│   ├── llm.py              → vLLM client + streaming
│   ├── embeddings.py       → nomic-embed service
│   ├── qdrant.py           → Vector search + matching
│   ├── mysql.py            → MySQL/Laravel DB connector
│   ├── matching.py         → Matchmaking algorithm
│   └── webscraper.py       → Company website scraper
└── utils/
└── chunker.py          → Text chunking utilities

## API Endpoints
POST /chat/                     → Chat with platform data (stream=true|false)
POST /match/find                → Find matching partners
POST /match/explain             → Explain why two orgs match
POST /ingest/sync/organizations → Sync organizations from MySQL
POST /ingest/sync/marketplace   → Sync marketplace listings
POST /ingest/sync/events        → Sync events and sessions
POST /ingest/sync/all           → Full sync
POST /ingest/scrape/all         → Scrape company websites
GET  /health                    → Health check

## Qdrant Collections
partnerall_orgs       → Organization profiles + website content
partnerall_services   → Marketplace services offered
partnerall_interests  → Marketplace needs/interests
partnerall_events     → Events and matchmaking sessions
partnerall_communities → Community profiles

## Matchmaking Logic

Embed organization profile (description + services + interests)
Search Qdrant for similar organizations
Filter by community, sector, country
Score matches (similarity + complementarity)
Return ranked list with explanation


## Environment Variables
VLLM_API_URL=http://localhost:8000/v1
VLLM_API_KEY=vllm-secret-key
VLLM_MODEL=ministral-14b
QDRANT_URL=http://localhost:6333
MYSQL_HOST=PARTNERALL_VPS_IP
MYSQL_PORT=3306
MYSQL_DB=partnerall
MYSQL_USER=your_user
MYSQL_PASSWORD=your_password
