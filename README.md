# InterviewMate

**AI-Powered Interview & Viva Preparation Platform**

InterviewMate is a free, AI-powered web application that helps students and job seekers prepare for viva examinations, technical interviews, and HR interviews through interactive, adaptive practice sessions. An AI system generates context-aware questions, evaluates answers, gives feedback, and adapts future questions based on performance — instead of relying on static question lists or generic chatbots.

| | |
|---|---|
| **Version** | 1.0 |
| **Project Phase** | Week 1 |
| **Target Users** | Students, job seekers, interview and viva candidates |
| **Primary Platform** | Web Application |

## Table of Contents

- [Problem It Solves](#problem-it-solves)
- [Key Features (MVP)](#key-features-mvp)
- [Out of Scope for MVP](#out-of-scope-for-mvp)
- [Tech Stack](#tech-stack)
- [System Architecture](#system-architecture)
- [Getting Started](#getting-started)
- [Environment Variables](#environment-variables)
- [Project Structure](#project-structure)
- [API Overview](#api-overview)
- [Development Workflow](#development-workflow)
- [Documentation](#documentation)
- [Team](#team)

## Problem It Solves

Students and job seekers often prepare for interviews using static question lists, videos, or generic chatbots — approaches that rarely offer structured practice, consistent evaluation, personalized feedback, or a measurable record of progress. InterviewMate provides a structured interview simulation where an AI system generates questions, evaluates answers, gives feedback, and adapts future questions to the user's performance.

## Key Features (MVP)

- User registration, login, and secure authenticated access
- Interview type selection: **Viva**, **Technical**, **HR**
- Subject/topic, difficulty, and question-count configuration
- AI-generated interview questions
- Text-based answer submission
- AI-based answer scoring and feedback (strengths, weaknesses, improvement tips)
- Adaptive question selection based on prior performance
- Final interview summary with overall score
- Interview history and a basic performance dashboard

## Out of Scope for MVP

Voice-based interviews & speech recognition, video interviews & facial-expression analysis, real-time emotion detection, AI interviewer avatar, automatic resume parsing, mobile app, advanced multilingual speech interaction, complex administrator analytics. See `docs/InterviewMate_SRS.docx` §3.2 / §12.2 for the full future-enhancements list.

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React.js (Vite), plain CSS / Tailwind CSS |
| Backend | Node.js, Express.js |
| Database | MongoDB (Mongoose) |
| Auth | JWT, bcrypt |
| AI | External LLM API (e.g. Claude), structured prompt/response handling |
| Version Control | Git + GitHub |
| UI Design | Figma / AI-assisted design tool |
| Deployment | Vercel (frontend) + Render/Railway (backend), or equivalent |

## System Architecture

Users (examinees, and optionally an administrator in a later release) interact with the **frontend** web app, which talks to the **backend** over a REST API. The backend handles authentication, interview session management, question management, and answer evaluation/analytics, and delegates AI work to a dedicated **AI & Agentic Services** layer:

- **Interview Manager** — controls interview state, question count, performance context, and the next action
- **Question Agent** — generates a question given topic, interview type, and target difficulty
- **Evaluation Agent** — analyzes the user's answer and produces a score
- **Feedback Agent** — produces strengths, weaknesses, and actionable improvement advice
- **Adaptive Decision Logic** — uses performance signals to influence the next question's difficulty/focus

All persistent data lives in MongoDB. External services (LLM/AI API, email, cloud storage, monitoring/logging) are integrated at the system's edges.

```
User (1) ───< Interview (1) ───< InterviewQuestion
```

## Getting Started

> Prerequisites: Node.js (LTS), npm, a MongoDB instance (local or Atlas), and an API key for the AI service.

```bash
# Clone the repository
git clone https://github.com/<org>/interviewmate.git
cd interviewmate

# Backend
cd backend
npm install
cp .env.example .env   # fill in your local values
npm run dev

# Frontend (in a separate terminal)
cd frontend
npm install
npm run dev
```

The frontend will typically run on `http://localhost:5173` and the backend API on `http://localhost:5000` (adjust per your local `.env`).

## Environment Variables

Never commit real secrets — copy `.env.example` to `.env` and fill in your own values locally.

```
MONGODB_URI=
JWT_SECRET=
AI_API_KEY=
PORT=
```

## Project Structure

```
interviewmate/
├── frontend/     # React + Vite web app
├── backend/      # Node.js + Express API, AI agent services, MongoDB models
├── docs/         # SRS, tasks.md, AI usage log, diagrams
└── scripts/      # Utility/dev scripts
```

## API Overview

REST-style HTTP APIs. Initial groups:

| API Group | Example Operations |
|---|---|
| Authentication | `POST /api/auth/register`, `POST /api/auth/login` |
| Interviews | `POST /api/interviews`, `GET /api/interviews`, `GET /api/interviews/:id` |
| Questions / Answers | `POST /api/interviews/:id/questions`, `POST /api/questions/:id/answer` |
| Dashboard | `GET /api/dashboard` |

AI service requests carry only the context needed for the current operation (interview type, subject, difficulty, prior performance, the user's answer). AI credentials are stored server-side only and are never exposed to the frontend.

## Development Workflow

This project follows an Agile, sprint-based workflow with GitHub Issues, a project board, feature branches, and mandatory PR review. See **[CONTRIBUTING.md](./CONTRIBUTING.md)** for the full branching model, commit conventions, PR process, Definition of Done, and AI-assisted development policy, and **[docs/tasks.md](./docs/tasks.md)** for the current task backlog.

## Documentation

- `docs/InterviewMate_SRS.docx` — full Software Requirements Specification (functional/non-functional requirements, use cases, data model, risks)
- `docs/tasks.md` — task backlog, organized by sprint week
- `docs/ai-usage-log.md` — log of how AI tools contributed to the project (to be maintained throughout development)

## Team

Project team members and roles TBD — see `docs/tasks.md` for task ownership as work is assigned.
