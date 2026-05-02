# AI-Powered Employee Onboarding Chatbot System - Architecture

## System Overview

```
┌─────────────────────────────────────────────────────────────────────────────┐
│                           CLIENT LAYER                                        │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐      │
│  │   Employee   │  │ HR Specialist│  │  HR Manager  │  │   Sys Admin  │      │
│  │   Portal     │  │   Dashboard  │  │   Dashboard  │  │   Panel      │      │
│  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘  └──────┬───────┘      │
└─────────┼─────────────────┼─────────────────┼─────────────────┼─────────────┘
          │                 │                 │                 │
          └─────────────────┴────────┬────────┴─────────────────┘
                                     │
┌────────────────────────────────────┼────────────────────────────────────────┐
│                           API GATEWAY LAYER                                   │
│                    ┌────────────────▼────────────────┐                       │
│                    │   Node.js Express Backend       │                       │
│                    │   - REST APIs                   │                       │
│                    │   - JWT Authentication          │                       │
│                    │   - Role-based Access Control   │                       │
│                    └────────────────┬────────────────┘                       │
└─────────────────────────────────────┼────────────────────────────────────────┘
                                      │
          ┌───────────────────────────┼───────────────────────────┐
          │                           │                           │
┌─────────▼─────────┐    ┌────────────▼────────────┐    ┌─────────▼─────────┐
│    MongoDB        │    │   Python AI Microservice │    │   File Storage    │
│  - Users          │    │   (FastAPI)              │    │   (Documents)     │
│  - Employees      │    │   - Intent Classification│    │                   │
│  - Documents      │    │   - Sentiment Analysis   │    │                   │
│  - Conversations  │    │   - Document Summarization│   │                   │
│  - Policies       │    │   - Q&A Generation       │    │                   │
│  - Notifications  │    │   - Knowledge Base Index  │    │                   │
│  - KB Versions    │    │                          │    │                   │
└───────────────────┘    └─────────────────────────┘    └───────────────────┘
```

## AI Processing Workflow

```
Employee Query → Backend API → AI Microservice
                                    │
                    ┌───────────────┼───────────────┐
                    │               │               │
                    ▼               ▼               ▼
            Intent Classifier  Sentiment      Knowledge Base
            (route to handler)  Analyzer      (RAG/Vector Search)
                    │               │               │
                    └───────────────┼───────────────┘
                                    │
                                    ▼
                            Response Generation
                                    │
                                    ▼
                    Backend → Store Conversation → Client
```

## Component Communication

| Component | Port | Purpose |
|-----------|------|---------|
| Frontend | 3000 | React SPA |
| Backend API | 5000 | Express REST API |
| AI Service | 8000 | FastAPI NLP/AI endpoints |
| MongoDB | 27017 | Primary database |

## Security Flow

1. User authenticates → JWT issued with role claim
2. Each API request validates JWT and checks role permissions
3. Document access controlled by ownership + role
4. AI service receives sanitized context only
