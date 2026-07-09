# 🛡️ JobGuard AI — Fake Job Detector & Job Search Platform

A full-stack web application that helps job seekers search for legitimate job listings and detect fake or scam job postings before applying.

---

## 📌 Project Type

Full-Stack Web Development with NLP API Integration

## 🎯 Problem It Solves

Fake job postings are one of the top cybercrime categories in India. Thousands of job seekers lose money and personal data to fraudulent listings every year. JobGuard AI helps users verify any job listing instantly before they apply or share personal information.

---

## ✨ Features

- 🔍 **Job Search** — Search listings by keyword, location, type, and category
- 🤖 **AI Fake Job Detection** — Paste any job listing and get a fraud risk score (0–100)
- 📊 **Detailed Analysis** — Verdict (SAFE / SUSPICIOUS / FAKE), red flags, trust signals, and recommendation
- ⚡ **Quick Paste Mode** — Paste raw job text directly from WhatsApp or email
- 📋 **Post a Job** — Employers can add new listings through a form
- 🔖 **Save Jobs** — Bookmark listings using browser localStorage
- 🛡️ **Fallback Detection** — Rule-based detection works even without API key
- 📱 **Responsive Design** — Works on mobile, tablet, and desktop

---

## 🛠️ Tech Stack

| Layer    | Technology                      |
| -------- | ------------------------------- |
| Backend  | Node.js, Express.js             |
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| AI / NLP | Anthropic Claude API            |
| Database | JSON flat-file (jobs.json)      |
| Tools    | dotenv, cors, uuid, npm         |

---

## 📁 Project Structure

    JobGuard-AI/
    ├── backend/
    │   ├── server.js
    │   ├── package.json
    │   ├── .env
    │   ├── routes/
    │   │   ├── jobs.js
    │   │   ├── detect.js
    │   │   └── search.js
    │   ├── services/
    │   │   └── aiDetector.js
    │   └── data/
    │       └── jobs.json
    └── frontend/
        ├── index.html
        ├── css/
        │   └── style.css
        └── js/
            ├── api.js
            ├── app.js
            ├── search.js
            └── detect.js

---

## ⚙️ How to Run Locally

**Prerequisites**

- Node.js v18 or above
- An Anthropic API key from console.anthropic.com

**Steps**

1.  Clone the repository

        git clone https://github.com/Ayushidasar22/jobguard-ai.git

2.  Go to backend folder

        cd jobguard-ai/backend

3.  Install dependencies

        npm install

4.  Open .env file and add your API key

        ANTHROPIC_API_KEY=your_key_here

5.  Start the server

        node server.js

6.  Open frontend/index.html in your browser or use Live Server in VS Code

---

## 🔌 API Endpoints

| Method | Endpoint                | Description               |
| ------ | ----------------------- | ------------------------- |
| GET    | /api/health             | Server status check       |
| GET    | /api/jobs               | Get all job listings      |
| GET    | /api/jobs/:id           | Get single job by ID      |
| POST   | /api/jobs               | Post a new job listing    |
| DELETE | /api/jobs/:id           | Delete a job listing      |
| GET    | /api/jobs/stats/summary | Get platform statistics   |
| GET    | /api/search             | Search jobs with filters  |
| GET    | /api/search/suggestions | Autocomplete suggestions  |
| POST   | /api/detect             | Full AI fraud analysis    |
| POST   | /api/detect/quick       | Quick paste text analysis |

---

## 🧠 How the Detection Works

1. User submits a job listing through the form or quick paste
2. Backend sends it to the NLP API for analysis
3. API evaluates 10+ fraud indicators including unrealistic salary, upfront fee requests, free email addresses, missing company info, urgency language, and guaranteed income claims
4. Returns a Risk Score from 0 to 100 with full detailed analysis
5. If API is unavailable the rule-based fallback engine runs automatically

---

## 📊 Risk Score Guide

| Score    | Verdict       | Meaning                               |
| -------- | ------------- | ------------------------------------- |
| 0 – 39   | ✅ SAFE       | Listing appears legitimate            |
| 40 – 69  | 🟡 SUSPICIOUS | Some concerns, verify before applying |
| 70 – 100 | ❌ FAKE       | Strong fraud indicators, do not apply |

---

## 👩‍💻 Developer

**Ayushi**
B.E. Computer Science and Engineering (Data Science)
Gyan Ganga Institute of Technology and Sciences, Jabalpur
GitHub: https://github.com/Ayushidasar22

---

## 📄 License

This project is open source and available under the MIT License.
