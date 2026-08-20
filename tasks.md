# InterviewMate — Task Backlog

This file is the source of truth for planned work. When a task is picked up, create a matching GitHub Issue (reference the task ID here), assign an owner, add an estimate, and label it per `CONTRIBUTING.md`. The task backlog follows the updated SRS as the master requirements document.

**Legend:** `[ ]` not started · `[~]` in progress · `[x]` done

---

## Week 1 — Requirements & Planning

- [x] T1.1 — Draft and finalize Software Requirements Specification (SRS)
- [ ] T1.2 — Set up GitHub repository, branch protection, labels, and project board
- [x] T1.3 — Write `README.md` (project overview, setup instructions, tech stack)
- [x] T1.4 — Write `CONTRIBUTING.md` (workflow and collaboration guidelines)
- [ ] T1.5 — Create initial folder structure: `frontend/`, `backend/`, `docs/`, `scripts/`
- [ ] T1.6 — Define data model: User, Context/Document, Interview, InterviewQuestion (see SRS §8)
- [ ] T1.7 — Set up `.env.example` for backend (`MONGODB_URI`, `JWT_SECRET`, `AI_API_KEY`)

## Week 2 — Architecture & Wireframes

- [ ] T2.1 — Design system architecture diagram (frontend / backend / AI services / data layer — SRS §2.5)
- [ ] T2.2 — Wireframe: Landing/Home Page
- [ ] T2.3 — Wireframe: Registration Page
- [ ] T2.4 — Wireframe: Login Page
- [ ] T2.5 — Wireframe: Dashboard
- [ ] T2.6 — Wireframe: Context/Document Submission Page
- [ ] T2.7 — Wireframe: Interview Configuration flow
- [ ] T2.8 — Wireframe: Live Interview / Question & Answer view
- [ ] T2.9 — Wireframe: Answer Evaluation/Feedback view
- [ ] T2.10 — Wireframe: Interview Result Page
- [ ] T2.11 — Wireframe: Interview History Page
- [ ] T2.12 — Wireframe: Profile Page
- [ ] T2.13 — Scaffold backend (Express app, MongoDB connection, project structure)
- [ ] T2.14 — Scaffold frontend (Vite + React app, routing, base layout)

## Week 3–4 — Core Development

### Authentication

- [ ] T3.1 — FR-01: User Registration endpoint (`POST /api/auth/register`)
- [ ] T3.2 — FR-02: User Login endpoint (`POST /api/auth/login`)
- [ ] T3.3 — FR-03: Password hashing with bcrypt
- [ ] T3.4 — FR-04: Logout (secure session/token invalidation or client-side token clear)
- [ ] T3.5 — FR-05: Auth middleware to protect private routes and user data
- [ ] T3.6 — Frontend: Registration page + form validation
- [ ] T3.7 — Frontend: Login page + form validation
- [ ] T3.8 — Frontend: Auth state management and protected routes

### Context / Document Submission

- [ ] T3.9 — FR-06: Context submission UI (supported document upload or text/paste input)
- [ ] T3.10 — FR-07: Document processing service to extract readable text/content
- [ ] T3.11 — FR-08: Context analysis to identify interview-relevant information
- [ ] T3.12 — Context/Document model/schema (source type, original filename where applicable, extracted content, structured context, timestamps)
- [ ] T3.13 — Context APIs (`POST /api/contexts`, `POST /api/contexts/upload`, `GET /api/contexts/:id`)

### Interview Setup

- [ ] T3.14 — FR-09: Interview configuration UI (type, optional focus/topic, initial difficulty)
- [ ] T3.15 — FR-10: `POST /api/interviews` — create interview session from submitted context and configuration; initialize 5-minute timer
- [ ] T3.16 — Interview model/schema (SRS §8.2)
- [ ] T3.17 — Question/Answer model/schema (SRS §8.3)

### Dashboard & History (scaffolding)

- [ ] T4.1 — FR-24: `GET /api/dashboard` — basic stats endpoint
- [ ] T4.2 — Frontend: Dashboard page (total interviews, average score, recent results, progress information)
- [ ] T4.3 — FR-23: `GET /api/interviews` — list user's interview history, including early-ended sessions
- [ ] T4.4 — Frontend: Interview History page

## Week 5–6 — AI Integration, Adaptive Logic & Completion

### AI / Agentic Services (SRS §9)

- [ ] T5.1 — Design structured prompt/response format for all AI agents (validated structured output)
- [ ] T5.2 — FR-11: Implement Question Agent — generate context-aware question from submitted context, interview type, current state, and target difficulty
- [ ] T5.3 — FR-14: Implement Evaluation Agent — evaluate answer using the question and relevant interview context
- [ ] T5.4 — FR-16: Implement Feedback Agent — produce strengths, weaknesses, and improvement suggestions
- [ ] T5.5 — Implement Interview Manager — coordinate agents and track interview state, performance, topic coverage, and remaining time
- [ ] T5.6 — FR-17: Implement Adaptive Decision Logic — adjust next question difficulty/focus using context, previous answers, scores, weaknesses, covered topics, and remaining time
- [ ] T5.7 — FR-25: AI/document failure handling (invalid response retry and user-friendly recovery/error state)
- [ ] T5.8 — Validate AI outputs stay within the defined scoring range before storage/display

### Interview Flow

- [ ] T5.9 — FR-12: Display current question during an active interview
- [ ] T5.10 — FR-13: `POST /api/questions/:id/answer` — submit text answer
- [ ] T5.11 — FR-18: Implement and display the default 5-minute countdown timer
- [ ] T5.12 — FR-19: Implement user-controlled early exit (`POST /api/interviews/:id/leave`)
- [ ] T5.13 — FR-20: Automatically complete the interview when 5 minutes expire or the user leaves
- [ ] T5.14 — FR-21: Store and display interview status (in-progress, completed-by-time, voluntarily-ended)
- [ ] T5.15 — FR-22: Calculate and display final interview summary/overall score
- [ ] T5.16 — Frontend: Answer Evaluation/Feedback view (per-question)
- [ ] T5.17 — Frontend: Interview Result page (final summary, including early-ended sessions)

### Testing & Hardening

- [ ] T6.1 — Unit tests: auth (registration, login, password hashing)
- [ ] T6.2 — Unit tests: context/document processing and context analysis
- [ ] T6.3 — Unit tests: Interview Manager / adaptive logic / timer behavior
- [ ] T6.4 — Integration tests: full interview flow (context → configuration → questions → evaluation → adaptive continuation → result)
- [ ] T6.5 — Security pass: verify FR-05/NFR-08 (no cross-user data access)
- [ ] T6.6 — Error-handling pass: AI/document/database/timer/session failure scenarios (FR-25, NFR-04)

## Deployment & Wrap-up

- [ ] T7.1 — Deploy frontend (Vercel or equivalent)
- [ ] T7.2 — Deploy backend (Render/Railway or equivalent)
- [ ] T7.3 — Final documentation pass (README, SRS updates, AI usage log)
- [ ] T7.4 — Prepare demo covering all Acceptance Criteria (SRS §15)

## Backlog / Future Enhancements (Out of MVP scope — SRS §3.2, §12.2)

- [ ] Voice-based interview and speech-to-text
- [ ] Text-to-speech AI interviewer
- [ ] Video interview simulation
- [ ] Facial-expression / non-verbal behavior analysis
- [ ] Resume-based personalized interview generation
- [ ] Multilingual interview practice
- [ ] AI interviewer avatar
- [ ] Advanced analytics and learning recommendations
- [ ] Mobile application
- [ ] Optional administrator role (topic management, usage monitoring, aggregated statistics)

---

## How to use this file

1. Pick a task, create a GitHub Issue referencing its ID and the related requirement ID where applicable.
2. Assign an owner and a rough estimate before starting.
3. Move it through the project board columns: `Backlog → Todo → In Progress → Code Review → Testing → Done`.
4. At each weekly checkpoint, check off completed items and add the next week's backlog, following `CONTRIBUTING.md`.
