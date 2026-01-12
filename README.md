# Insight Mail – The Language of Enterprise Conversations 🚀
### CodeBharat Armageddon Hackathon Project

Dashboard Preview[<img width="1330" height="755" alt="Image" src="https://github.com/user-attachments/assets/539cec86-7716-4fe3-9792-229cb034f387" />](https://github.com/NakulSingh156/codebharatarmageddon/issues/1#issue-3805566130)


## Project Overview
**Insight Mail** is a smart email analytics tool designed to streamline enterprise communication. It automatically processes incoming support emails to provide quick summaries, detect tone and urgency, extract key details, and suggest AI-generated responses.

**Problem Statement:** "Insight Mail – The Language of Enterprise Conversations"

## Key Features
- **Smart Dashboard:** A unified view of all customer interactions.
- **brain AI Summarization:** Instantly condenses long email threads into actionable points.
- **Urgency & Tone Detection:** Flags "High Priority" or "Angry" emails for immediate attention.
- **Smart Extraction:** Automatically pulls out dates, feature requests, and actionable items.
- **Suggested Responses:** Generates context-aware replies to help support teams respond faster.

---

## Tech Stack
- **Frontend:** React.js, Vite, Tailwind CSS
- **Backend:** Python (FastAPI/Flask), PyTorch/TensorFlow (for NLP models)
- **AI/ML:** Custom Transformer Models for Sentiment Analysis & Summarization

---

## Setup Instructions

### Important: Missing Files
To keep this repository lightweight, the **Machine Learning Models** and **API Keys** are not included.
1. **Download Models:** [https://drive.google.com/drive/folders/1jGTwio7Sh--XGW63LjVSjORPYjAbm8Jb?usp=share_link]
2. **Place Files:** Unzip the models and place them inside the `Backend/models/` folder.

### 1. Backend Setup
Navigate to the backend folder and install dependencies:
cd Backend
pip install -r requirements.txt
Configuration:

Place your client_secret.json and gmail_token.json inside the Backend/ folder.

Ensure the downloaded models are in Backend/models/.

Run the Server:
python main.py

2. Frontend Setup

Open a new terminal and navigate to the frontend:

cd Frontend
npm install
npm run dev
The application will launch at http://localhost:5173

👥 Contributors

Nakul Singh

Satwik Maharana

Riya Magadum

Udita Banchhode
