---

## ⚙️ How to Run Locally

### Prerequisites
- Node.js v18 or above
- An Anthropic API key (get one free at console.anthropic.com)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/Ayushidasar22/jobguard-ai.git

# 2. Go to backend folder
cd jobguard-ai/backend

# 3. Install dependencies
npm install

# 4. Add your API key
# Open .env file and replace the placeholder:
# ANTHROPIC_API_KEY=your_key_here

# 5. Start the server
node server.js

# 6. Open the frontend
# Open frontend/index.html in your browser
# OR right-click index.html in VS Code → Open with Live Server
```

---

## 🔌 API Endpoints

| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | /api/health | Server status check |
| GET | /api/jobs | Get all job listings |
| GET | /api/jobs/:id | Get single job by ID |
| POST | /api/jobs | Post a new job listing |
| DELETE | /api/jobs/:id | Delete a job listing |
| GET | /api/jobs/stats/summary | Get platform statistics |
| GET | /api/search | Search jobs with filters |
| GET | /api/search/suggestions | Autocomplete suggestions |
| POST | /api/detect | Full AI fraud analysis |
| POST | /api/detect/quick | Quick paste text analysis |

---

## 🧠 How the Detection Works

1. User submits a job listing (form or paste)
2. Backend sends it to the Anthropic Claude NLP API
3. API evaluates 10+ fraud indicators:
   - Unrealistic salary promises
   - Upfront fee / registration fee requests
   - Free email address used as company contact
   - Missing or unverifiable company information
   - Urgency language ("Limited slots", "Act now")
   - Guaranteed income claims
   - Requests for personal or bank details
4. Returns Risk Score (0–100) + full analysis
5. If API is unavailable → rule-based fallback runs automatically

---

## 📊 Risk Score Guide

| Score | Verdict | Meaning |
|-------|---------|---------|
| 0 – 39 | ✅ SAFE | Listing appears legitimate |
| 40 – 69 | 🟡 SUSPICIOUS | Some concerns — verify before applying |
| 70 – 100 | ❌ FAKE | Strong fraud indicators — do not apply |

---

## 👩‍💻 Developer

**Ayushi**
B.E. Computer Science & Engineering (Data Science)
Gyan Ganga Institute of Technology and Sciences, Jabalpur
GitHub: [@Ayushidasar22](https://github.com/Ayushidasar22)

---

## 📄 License
This project is open source and available under the MIT License.
