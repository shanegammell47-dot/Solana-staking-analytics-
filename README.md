# Solana Staking Analytics

Solana Staking Analytics is a secure, Ledger-integrated dashboard delivering real-time staking rewards, validator insights, and governance analytics for Solana users. This branch adds a demo frontend (Next.js pages) and an Express backend (server/) that provides a contact API and a sample staking-analytics endpoint.

Live mockup used for reference: https://dual-chain-stake.preview.emergentagent.com/

Quick status
- Branch: fix/readme-and-contact
- Frontend: pages/index.js, pages/contact.js (Next.js)
- Backend: server/index.js (Express)

Getting started (development)
1. Clone the repo and checkout the branch:
   git clone https://github.com/shanegammell47-dot/Solana-staking-analytics-.git
   cd Solana-staking-analytics-
   git checkout fix/readme-and-contact

2. Frontend (Next.js)
   - From the repo root run the Next.js dev server (if already set up in this repo):
     npm install
     npm run dev
   - The frontend expects the demo Express backend to be available at http://localhost:4000 for some demo API calls. If you run the backend on a different host or port, update the API_BASE in pages that call the server.

3. Backend (Express demo)
   - Install dependencies and start the server:
     cd server
     npm install
     npm run start
   - The server will run by default on port 4000 and exposes:
     GET  /api/stats    -> sample staking analytics JSON (uses SOLANA_RPC_URL if provided)
     POST /api/contact  -> receive contact submissions and append to server/contacts.log

Environment variables (optional)
- SOLANA_RPC_URL - If provided, the server will attempt to query the Solana RPC for basic epoch/staking info to enrich the /api/stats response.

Notes & next steps
- I copied visual assets references from the provided mockup and linked them in the frontend pages. If you want the image files checked into the repo, provide the assets or allow me to fetch them and I’ll add them to the /public folder.
- I implemented a basic Express backend that logs contact submissions to server/contacts.log. For production you should replace that with a proper persistence layer (DB) or email integration (SMTP/Nodemailer).
- I added a sample /api/stats endpoint scaffold to start adding staking aggregation logic (Solana RPC calls, validator telemetry, etc.).