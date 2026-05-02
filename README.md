# AI-Powered Employee Onboarding Chatbot System

A comprehensive web-based platform with an integrated AI chatbot that assists employees during onboarding, collects information, answers questions, and supports HR staff with monitoring and management capabilities.

## Tech Stack

- **Frontend:** React.js, Tailwind CSS, Chatbot UI
- **Backend:** Node.js with Express
- **Database:** MongoDB
- **AI:** Python microservice (FastAPI) - NLP, intent classification, sentiment analysis, document summarization

## Quick Start

### Prerequisites

- Node.js 18+
- Python 3.10+
- MongoDB 6+
- npm or yarn

### 1. Backend Setup

```bash
cd backend
npm install
cp .env.example .env  # Configure MongoDB URI, JWT secret
npm run dev
```

### 2. AI Service Setup

```bash
cd ai-service
python -m venv venv
# Windows: venv\Scripts\activate
# Unix: source venv/bin/activate
pip install -r requirements.txt
python -m spacy download en_core_web_sm  # For NLP
uvicorn main:app --reload --port 8001
```

### 3. Frontend Setup

```bash
cd frontend
npm install
npm run dev
```

### 4. Seed Sample Data

```bash
cd backend
npm run seed
```

### 5. Sync Policies to AI (optional, for chatbot answers)

```bash
cd backend
npm run sync-ai
```
Ensure the AI service is running first.

## Default Credentials (Development)

| Role | Email | Password |
|------|-------|----------|
| Employee | employee@company.com | password123 |
| HR Specialist | hr@company.com | password123 |
| HR Manager | hrmanager@company.com | password123 |
| System Admin | admin@company.com | password123 |

## Project Structure

```
Onboarding/
├── backend/           # Node.js Express API
├── frontend/          # React application
├── ai-service/        # Python FastAPI AI microservice
├── ARCHITECTURE.md    # System architecture
└── README.md
```

## Features

- Employee Profile Setup & Document Upload
- Document Compliance & Alerts
- Pre-Hire Coordination & Progress Tracking
- AI Chatbot Q&A (onboarding, IT, policies)
- Leave & Policy Summaries
- Personalized Onboarding Schedules
- HR Assistance & Conversation Escalation
- Sentiment Analysis & Department Comparison
- Knowledge Base Management
- Policy Management & Version Control
