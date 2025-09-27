# Allora AI Edge Beta - Full Working MVP

**What this repo contains (MVP):**
- Frontend (React + Vite) — simple, responsive UI using Tailwind CDN.
- Backend (FastAPI) — endpoints:
  - `GET /price?symbol=btc` -> current price from CoinGecko
  - `GET /predict?symbol=btc&horizon=24h` -> simple forecast using recent returns (deterministic baseline)
- docker-compose for local testing (frontend + backend).

**Quickstart (Linux / macOS / WSL / Windows with Docker):**
1. Install Docker and Docker Compose.
2. From repo root:
   ```bash
   docker-compose up --build
   ```
3. Open `http://localhost:5173` for the frontend. Backend runs at `http://localhost:8000`.

**If you prefer to run locally without Docker:**

_Backend:_
```bash
cd backend
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
uvicorn app.main:app --host 0.0.0.0 --port 8000
```

_Frontend:_
```bash
cd frontend
npm install
npm run dev
```

**Notes:**
- This MVP uses CoinGecko public API to fetch prices. No API key required for low-volume usage.
- Prediction endpoint is a deterministic, lightweight baseline (moving-average based) to keep the service immediately runnable without heavy ML libraries. You can replace it with the LSTM/Transformer model training pipeline later (folder `optional_model/` contains a starter notebook and training script).
- This software is for demo purposes. Not investment advice.

Enjoy — Muammer / Allora team.
