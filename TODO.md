# partnerall-ai TODO

## ✅ Completed
- [x] Project structure created
- [x] GitHub repository
- [x] Documentation

## 🔜 Next Steps (Priority Order)

### 1. Infrastructure
- [ ] Connect partnerall.eu VPS via WireGuard (direct tunnel)
- [ ] MySQL access from AI server (via VPN)
- [ ] Configure VPS firewall (allow 10.8.0.100)
- [ ] Add VPS to network-map.md
- [ ] Test DB connectivity

### 2. MySQL Data Ingestion
- [ ] MySQL connector setup (aiomysql)
- [ ] Organizations and profiles sync
- [ ] Communities sync
- [ ] Marketplace services offered sync
- [ ] Marketplace interests/needs sync
- [ ] Events and matchmaking sessions sync
- [ ] Automatic periodic sync (cron - every 6 hours)
- [ ] Incremental sync (updated_at tracking)

### 3. Company Website Scraping
- [ ] Extract company info from website URLs
- [ ] Store enriched data in Qdrant
- [ ] Periodic re-scrape (monthly)

### 4. Matchmaking Engine
- [ ] Organization profile embedding strategy
- [ ] Vector similarity search in Qdrant
- [ ] Matching score algorithm
  - [ ] Service/interest complementarity
  - [ ] Sector alignment
  - [ ] Geographic proximity
  - [ ] Community membership
- [ ] Match explanation generator ("Why this partner?")
- [ ] Filter and ranking system

### 5. Chat
- [ ] RAG chat endpoint
- [ ] Streaming responses (SSE)
- [ ] Natural language matching queries
- [ ] Source citations
- [ ] Session context (remember user's organization)

### 6. Frontend Integration
- [ ] Chat widget for partnerall.eu (Laravel/Blade)
- [ ] Matchmaking results UI
- [ ] Integration with Jitsi meeting scheduler
- [ ] Mobile-friendly UI
- [ ] Rate limiting

### 7. Infrastructure
- [ ] Reverse proxy on partnerall.eu VPS
- [ ] SSL certificate
- [ ] Add to startup-ai.sh (port 8083)
- [ ] GitHub Actions auto-deploy

## 📋 Future Improvements
- [ ] Real-time matching during matchmaking events
- [ ] Pre-event match suggestions (sent by email)
- [ ] Post-event feedback collection
- [ ] Match history and analytics
- [ ] AI-powered meeting agenda suggestions
- [ ] Integration with Jitsi for in-platform meetings
