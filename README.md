# 📧 Insight Mail – The Language of Enterprise Conversations

[![CodeBharat Armageddon](https://img.shields.io/badge/Hackathon-CodeBharat%20Armageddon-orange?style=for-the-badge)](https://github.com/NakulSingh156/codebharatarmageddon)
[![FastAPI](https://img.shields.io/badge/Backend-FastAPI-009688?style=for-the-badge&logo=fastapi)](https://fastapi.tiangolo.com/)
[![React](https://img.shields.io/badge/Frontend-React%2019-61DAFB?style=for-the-badge&logo=react)](https://react.dev/)
[![Vite](https://img.shields.io/badge/Build-Vite-646CFF?style=for-the-badge&logo=vite)](https://vitejs.dev/)
[![Tailwind CSS](https://img.shields.io/badge/Styling-Tailwind%20CSS-38B2AC?style=for-the-badge&logo=tailwind-css)](https://tailwindcss.com/)
[![PyTorch](https://img.shields.io/badge/ML-PyTorch-EE4C2C?style=for-the-badge&logo=pytorch)](https://pytorch.org/)
[![Supabase](https://img.shields.io/badge/Database-Supabase-3ECF8E?style=for-the-badge&logo=supabase)](https://supabase.com/)

> **Insight Mail** is an AI-powered email analytics and support triage platform designed to streamline enterprise communications, detect customer intent and sentiment in real time, auto-summarize long email threads, and assist support teams with automated escalation and smart resolution memory.

---

## 🖼️ Dashboard Preview

[<img width="1330" height="755" alt="Insight Mail Dashboard Preview" src="https://github.com/user-attachments/assets/539cec86-7716-4fe3-9792-229cb034f387" />](https://github.com/NakulSingh156/codebharatarmageddon/issues/1#issue-3805566130)

---

## 💡 Problem Statement & Solution

**Problem:** Enterprise support desks are flooded daily with high volumes of unorganized emails. Support agents spend hours manually reading, categorizing, prioritizing, and escalating tickets—leading to delayed response times, agent fatigue, and missed high-priority escalation threats.

**Solution:** **Insight Mail** automates email triage using custom Machine Learning models and Large Language Models. It ingests incoming support emails, summarizes their core content, evaluates tone and urgency, flags legal/compliance risks, and suggests past successful resolutions to enable support agents to respond faster and smarter.

---

## ✨ Key Features

- **📥 Live Gmail Integration:** Syncs with Gmail via OAuth2, extracts plain text from multi-part emails, and prevents duplicate processing.
- **🤖 AI-Powered Summarization:** Uses Transformer models (`philschmid/bart-large-cnn-samsum`) to condense long support emails into concise, actionable summaries.
- **🧠 Multi-Model Intent & Sentiment Classification:** Employs `SentenceTransformers` (`all-MiniLM-L6-v2`) paired with classifier models to predict customer intent, sentiment (e.g., *angry*, *neutral*, *satisfied*), and priority (*high*, *medium*, *low*).
- **🚨 Compliance & Legal Risk Alerts:** Scans emails for high-risk legal terms (*sue*, *lawyer*, *scam*, *cheat*) and raises compliance warnings.
- **💡 Resolution Memory (Smart Caching):** Automatically queries past resolved support tickets with matching intent to suggest proven resolution steps for new unresolved tickets.
- **🔀 Intelligent Agent Assist & Escalation:** Automatically routes tickets to specialized departments (*Finance*, *Tech Support*) or escalates high-risk/angry tickets to Team Leads.
- **📊 Real-Time Analytics Dashboard:** Interactive web UI with charts (built with Recharts, React 19, and Tailwind CSS) to track overall sentiment distributions, urgency breakdowns, and ticket resolution states.

---

## 🏗️ System Architecture

```
                                 ┌─────────────────────────┐
                                 │     Gmail OAuth API     │
                                 └────────────┬────────────┘
                                              │ Sync & Fetch Emails
                                              ▼
┌─────────────────────────┐      ┌─────────────────────────┐      ┌─────────────────────────┐
│     React 19 + Vite     │ ◄──► │     FastAPI Backend     │ ◄──► │       Supabase DB       │
│   Tailwind CSS Frontend │ REST │  (Python 3.10+ Server)  │ PostgreSQL Storage & Vector Cache
└─────────────────────────┘      └────────────┬────────────┘      └─────────────────────────┘
                                              │
                                              ▼
                                 ┌─────────────────────────┐
                                 │    AI / ML Pipelines    │
                                 │ • Sentence Transformers │
                                 │ • BART Summarizer (CNN) │
                                 │ • Joblib Classifiers    │
                                 └─────────────────────────┘
```

---

## 🛠️ Tech Stack

| Domain | Technology / Library | Description |
| :--- | :--- | :--- |
| **Frontend** | React 19, Vite | Fast SPA framework with Rolldown-Vite tooling |
| **Styling** | Tailwind CSS, Lucide React | Modern responsive UI components & iconography |
| **Data Viz** | Recharts | Interactive dashboards and sentiment analytics charts |
| **Backend** | FastAPI, Uvicorn | High-performance asynchronous Python REST API |
| **Database** | Supabase (PostgreSQL) | Cloud database for emails, metadata, and analysis logs |
| **AI / ML** | PyTorch, Transformers, SentenceTransformers | Local NLP embedding, BART summarization & classification |
| **Classifiers** | XGBoost, Scikit-Learn, Joblib | Model inference for intent, priority & sentiment |
| **Integrations**| Google OAuth2 & Gmail API | Automated retrieval and sync of live email threads |

---

## 🌐 API Endpoints Summary

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `POST` | `/sync-gmail` | Triggers background sync & AI analysis pipeline for recent Gmail messages |
| `GET` | `/emails` | Fetches analyzed emails; supports `filter_priority` & `filter_sentiment` parameters |
| `POST` | `/escalate/{email_id}` | Escalates a ticket to Team Lead or marks it resolved with resolution details cached |
| `POST` | `/mark-read/{email_id}` | Updates email read status in the database |

---

## 🚀 Setup & Installation Guide

### 📦 Prerequisites

- **Python:** `3.10` or higher
- **Node.js:** `18.x` or higher (with `npm`)
- **Gmail API Credentials:** `client_secret.json` from Google Cloud Console

---

### 1️⃣ Download Machine Learning Models

To keep the repository lightweight, trained ML models are hosted externally.

1. **Download Models:** [Google Drive Download Link](https://drive.google.com/drive/folders/1jGTwio7Sh--XGW63LjVSjORPYjAbm8Jb?usp=share_link)
2. **Place Models:** Create a `models/` directory inside `Backend/` and extract all downloaded `.pkl` files there:
   ```
   Backend/models/
   ├── model_intent.pkl
   ├── model_sentiment.pkl
   ├── model_priority.pkl
   ├── le_intent.pkl
   ├── le_sentiment.pkl
   └── le_priority.pkl
   ```

---

### 2️⃣ Backend Setup

```bash
# Navigate to Backend folder
cd Backend

# Create a virtual environment (optional but recommended)
python -m venv venv
# On Windows:
venv\Scripts\activate
# On Linux/macOS:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Place Google Client Secret inside Backend/
# Make sure your file is named client_secret.json or updated in main.py

# Run the FastAPI server
python main.py
```
> The backend server will start at `http://localhost:8000`.

---

### 3️⃣ Frontend Setup

```bash
# Open a new terminal and navigate to Frontend folder
cd Frontend

# Install node dependencies
npm install

# Start Vite development server
npm run dev
```
> The frontend application will be live at `http://localhost:5173`.

---

## 📁 Repository Structure

```
codebharatarmageddon/
├── Backend/
│   ├── models/                 # Downloaded ML model binaries (.pkl)
│   ├── auth_gmail.py           # Gmail OAuth helper script
│   ├── generate_data.py        # Synthetic dataset generation tool
│   ├── main.py                 # FastAPI server & AI pipeline implementation
│   ├── requirements.txt        # Python backend dependencies
│   └── sample_dataset.json     # Sample email datasets
├── Frontend/
│   ├── public/                 # Static assets
│   ├── src/                    # React components, dashboard views & UI
│   ├── package.json            # Frontend dependencies & scripts
│   ├── tailwind.config.js      # Tailwind CSS configuration
│   └── vite.config.js          # Vite build configuration
└── README.md                   # Project documentation
```

---

## 👥 Team & Contributors

Developed with ❤️ for the **CodeBharat Armageddon Hackathon**:

- 👤 **Nakul Singh**
- 👤 **Satwik Maharana**
- 👤 **Riya Magadum**
- 👤 **Udita Banchhode**

---

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

