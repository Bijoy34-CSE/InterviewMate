# InterviewMate — Task Backlog

This file is the source of truth for planned work. When a task is picked up, create a matching GitHub Issue (reference the task ID here), assign an owner, add an estimate, and label it per `CONTRIBUTING.md`.

Legend: `[ ]` not started · `[~]` in progress · `[x]` done

---

## Week 1 — Requirements & Planning

- [x] T1.1 — Draft and finalize Software Requirements Specification (SRS)
- [ ] T1.2 — Set up GitHub repository, branch protection, labels, and project board
- [ ] T1.3 — Write `README.md` (project overview, setup instructions, tech stack)
- [ ] T1.4 — Write `CONTRIBUTING.md` (this workflow doc)
- [ ] T1.5 — Create initial folder structure: `frontend/`, `backend/`, `docs/`, `scripts/`
- [ ] T1.6 — Define data model: User, Interview, InterviewQuestion (see SRS §8)
- [ ] T1.7 — Set up `.env.example` for backend (MONGODB_URI, JWT_SECRET, AI_API_KEY)

## Week 2 — Architecture & Wireframes

- [ ] T2.1 — Design system architecture diagram (frontend / backend / AI services / data layer — SRS §2.5)
- [ ] T2.2 — Wireframe: Landing/Home Page
- [ ] T2.3 — Wireframe: Registration Page
- [ ] T2.4 — Wireframe: Login Page
- [ ] T2.5 — Wireframe: Dashboard
- [ ] T2.6 — Wireframe: Interview Configuration flow
- [ ] T2.7 — Wireframe: Question / Answer view
- [ ] T2.8 — Wireframe: Answer Evaluation/Feedback view
- [ ] T2.9 — Wireframe: Interview Result Page
- [ ] T2.10 — Wireframe: Interview History Page
- [ ] T2.11 — Wireframe: Profile Page
- [ ] T2.12 — Scaffold backend (Express app, MongoDB connection, project structure)
- [ ] T2.13 — Scaffold frontend (Vite + React app, routing, base layout)

## Week 3–4 — Core Development

### Authentication
- [ ] T3.1 — FR-01: User Registration endpoint (`POST /api/auth/register`)
- [ ] T3.2 — FR-02: User Login endpoint (`POST /api/auth/login`)
- [ ] T3.3 — FR-03: Password hashing with bcrypt
- [ ] T3.4 — FR-04: Logout (JWT invalidation / client-side token clear)
- [ ] T3.5 — FR-05: Auth middleware to protect private routes and user data
- [ ] T3.6 — Frontend: Registration page + form validation
- [ ] T3.7 — Frontend: Login page + form validation
- [ ] T3.8 — Frontend: Auth state management (JWT storage, protected routes)

### Interview Setup
- [ ] T3.9 — FR-06: Interview configuration UI (type, subject/topic, difficulty, question count)
- [ ] T3.10 — FR-07: `POST /api/interviews` — create interview session from configuration
- [ ] T3.11 — Interview model/schema (SRS §8.2, Table 6)
- [ ] T3.12 — Question/Answer model/schema (SRS §8.3, Table 7)

### Dashboard & History (scaffolding)
- [ ] T4.1 — FR-19: `GET /api/dashboard` — basic stats endpoint
- [ ] T4.2 — Frontend: Dashboard page (total interviews, average score, recent results)
- [ ] T4.3 — FR-18: `GET /api/interviews` — list user's interview history
- [ ] T4.4 — Frontend: Interview History page

## Week 5–6 — AI Integration, Adaptive Logic & Completion

### AI / Agentic Services (SRS §9, Table 8)
- [ ] T5.1 — Design structured prompt/response format for all AI agents (validated JSON schema)
- [ ] T5.2 — Implement Question Agent — FR-08: generate question from context
- [ ] T5.3 — Implement Evaluation Agent — FR-11/FR-12: evaluate answer, produce score
- [ ] T5.4 — Implement Feedback Agent — FR-13: strengths, weaknesses, improvement suggestions
- [ ] T5.5 — Implement Interview Manager to coordinate agents and track state
- [ ] T5.6 — Implement Adaptive Decision Logic — FR-14: adjust next question by performance
- [ ] T5.7 — FR-20: AI failure/error handling (invalid response retry, user-friendly error state)
- [ ] T5.8 — Validate AI outputs stay within defined scoring range before storage/display

### Interview Flow
- [ ] T5.9 — FR-09: Display current question to user
- [ ] T5.10 — FR-10: `POST /api/questions/:id/answer` — submit text answer
- [ ] T5.11 — FR-15: Track completed/remaining questions within a session
- [ ] T5.12 — FR-16: Complete interview after configured question count reached
- [ ] T5.13 — FR-17: Calculate and display final interview summary/overall score
- [ ] T5.14 — Frontend: Answer Evaluation/Feedback view (per-question)
- [ ] T5.15 — Frontend: Interview Result page (final summary)

### Testing & Hardening
- [ ] T6.1 — Unit tests: auth (registration, login, password hashing)
- [ ] T6.2 — Unit tests: Interview Manager / adaptive logic
- [ ] T6.3 — Integration tests: full interview flow (config → questions → evaluation → result)
- [ ] T6.4 — Security pass: verify FR-05/NFR-08 (no cross-user data access)
- [ ] T6.5 — Error-handling pass: AI/API/database failure scenarios (FR-20, NFR-04)

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
- [ ] Optional administrator role (topic management, usage monitoring, aggregated stats)

---

## How to use this file

1. Pick a task, create a GitHub Issue referencing its ID (e.g. `T5.3`) and the related requirement ID (e.g. `FR-11`).
2. Assign an owner and a rough estimate on the issue.
3. Move it through the project board columns: `Backlog → Todo → In Progress → Code Review → Testing → Done`.
4. At each weekly checkpoint, check off completed items here and add next week's backlog, per `CONTRIBUTING.md`.
