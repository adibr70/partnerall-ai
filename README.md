# partnerall-ai

Intelligent B2B matchmaking assistant for partnerall.eu.

## Purpose
- Find matching partners by service/interest
- Community and event recommendations
- Marketplace search (services offered/needed)
- Matchmaking session suggestions

## Data Sources
- Laravel/MySQL backend (direct DB or API)
- Communities, organizations, marketplace
- Events and matchmaking sessions

## Stack
- FastAPI + Uvicorn (port 8083)
- vLLM Ministral 14B
- Qdrant vector DB (similarity search)
- nomic-embed embeddings
- WireGuard VPN direct to partnerall.eu VPS
- MySQL connector

## Qdrant Collections (planned)
- partnerall_orgs - organization profiles
- partnerall_services - marketplace offerings
- partnerall_interests - needs/interests
- partnerall_events - events and sessions

## Setup
cp .env.example .env
# Edit .env with your settings
uvicorn main:app --host 0.0.0.0 --port 8083
