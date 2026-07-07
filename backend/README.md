# JobGuard AI

JobGuard AI is a full-stack web platform that helps job seekers spot fake and scam job postings. It combines AI-powered risk analysis (via the Anthropic Claude API) with a rule-based fallback engine, alongside a job search interface with filters and bookmarking.

## Features

- **AI Risk Analysis** — submits a job listing to Claude, which returns a risk score (0–100), verdict (Safe / Suspicious / Fake), confidence level, red flags, positive signals, and a detailed breakdown across salary, company, description, and contact information.
- **Rule-Based Fallback** — if the AI service is unavailable, a rule-based detector automatically takes over using pattern matching (urgency language, upfront payment requests, free-email contacts, unrealistic salaries, etc.), so the app degrades gracefully instead of failing.
- **Job Search** — search and filter job postings by keyword, location, and job type.
- **Bookmarking** — save jobs locally via `localStorage` for later review.

## Tech Stack

- **Backend:** Node.js, Express.js
- **AI:** Anthropic Claude API (`@anthropic-ai/sdk`)
- **Frontend:** HTML, CSS, vanilla JavaScript
- **Data:** JSON flat-file storage

## Project Structure

```
jobguard-ai/
├── backend/
│   ├── routes/        # API route handlers (jobs, search, detect)
│   ├── services/       # AI detection logic + fallback engine
│   ├── data/           # JSON flat-file datastore
│   └── server.js       # Express app entry point
└── frontend/
    ├── index.html
    ├── css/
    └── js/             # app.js, search.js, detect.js, api.js
```

## Setup & Run Locally

1. Clone the repo

   ```bash
   git clone https://github.com/Ayushidasar22/jobguard-ai.git
   cd jobguard-ai/backend
   ```

2. Install dependencies

   ```bash
   npm install
   ```

3. Configure environment variables

   ```bash
   cp .env.example .env
   ```

   Then open `.env` and add your own Claude API key from [console.anthropic.com](https://console.anthropic.com/):

   ```
   ANTHROPIC_API_KEY=your_key_here
   ```

4. Start the backend

   ```bash
   npm start
   ```

   Server runs at `http://localhost:5000`

5. Open the frontend
   Open `frontend/index.html` in your browser (or serve it with a simple static server).

## API Endpoints

| Method | Endpoint            | Description                            |
| ------ | ------------------- | -------------------------------------- |
| GET    | `/api/health`       | Health check                           |
| GET    | `/api/jobs`         | List job postings                      |
| POST   | `/api/jobs`         | Create a job posting                   |
| POST   | `/api/detect`       | Analyze a job listing for fraud risk   |
| POST   | `/api/detect/quick` | Quick analysis from raw pasted text    |
| GET    | `/api/search`       | Search jobs by keyword, location, type |

## Known Limitations

- CORS is currently open (`origin: "*"`) for local development; this should be restricted to a specific frontend origin before production use.
- Data is stored in flat JSON files rather than a database — fine for a demo/portfolio scale, not for production traffic.

## Future Improvements

- Deploy backend (Render/Railway) and frontend (Vercel/Netlify)
- Move from flat-file JSON storage to MongoDB
- Add automated test suite with a labeled dataset of real/fake postings to measure detection accuracy
