# Contributing to InterviewMate

Guidelines for the project team so our GitHub history stays clean and reviewable — this matters for the lab's evaluation of process (Agile workflow, GitHub collaboration, code review, testing, documentation), not just the final product.

## Repository Setup (do this once)

1. Create a GitHub repository named `interviewmate`.
2. Add all team members as collaborators.
3. Protect the `main` branch: **Settings → Branches → Add rule** →
   - Require a pull request before merging
   - Require at least 1 approval
   - Do not allow direct pushes to `main`
4. Add this file, the README, `docs/tasks.md`, and a `.gitignore` (Node) as the first commit.
5. Create the initial folder structure: `frontend/` (React + Vite), `backend/` (Node + Express), `docs/`, `scripts/`.

## Branching Model

Per the SRS §14.2:

- `main` — stable release branch. Always working, always demo-able. Never commit directly.
- `develop` — integration branch for completed sprint work; feature branches merge here first, `develop` merges to `main` at sprint/week checkpoints.
- `feature/<short-description>` — individual feature development branches (e.g. `feature/interview-config`, `feature/answer-evaluation`)
- `fix/<short-description>` — bug fixes
- `docs/<short-description>` — documentation-only changes

## Commit Messages

Use [Conventional Commits](https://www.conventionalcommits.org/) style:

```
feat: add AI question generation endpoint
fix: correct scoring range validation on evaluation agent
docs: update SRS with adaptive difficulty policy
refactor: extract Interview Manager into services/interviewManager.js
test: add duplicate-answer submission test
```

Keep commits small and scoped to one change. Don't bundle unrelated files.

## Pull Request and Review Process (SRS §14.3)

1. Create or select a GitHub Issue.
2. Create a feature branch off `develop`.
3. Implement and locally test the feature.
4. Commit changes using a clear Conventional Commits message.
5. Open a Pull Request against `develop`.
   - Description must state: what changed, why, and how it was tested.
   - Link the related issue (e.g. `Closes #12`).
6. A different team member reviews the changes.
7. Fix review comments if required.
8. Merge after approval and successful testing (squash-merge to keep history readable).

## GitHub Project Board (SRS §14.4)

Recommended columns: `Backlog` → `Todo` → `In Progress` → `Code Review` → `Testing` → `Done`.

## Definition of Done (SRS §14.5)

A task is only "Done" when:

- [ ] Requirement implemented.
- [ ] Code committed to the appropriate branch.
- [ ] Relevant tests completed.
- [ ] Pull Request created and reviewed.
- [ ] Critical review comments resolved.
- [ ] Feature merged into `develop`.
- [ ] Documentation updated where necessary.

## Issues / Task Tracking

- Every task in `docs/tasks.md` should become a GitHub Issue once work starts on it.
- Use labels: `frontend`, `backend`, `ai-agent`, `database`, `auth`, `docs`, `bug`, `week-1` … `week-N`.
- Assign an owner and a rough estimate before starting.
- Reference the requirement ID (e.g. `FR-08`, `NFR-03`) in the issue title or description where applicable.

## Code Style

- **Backend (Node.js/Express):** consistent `async/await`, no unhandled promise rejections; run existing lint config if present; keep AI integration, auth, and database logic in separate modules (NFR-05).
- **Frontend (React + Vite):** functional components with hooks; keep styling consistent (plain CSS or Tailwind — team agreement before adding new UI libraries).
- **AI/Agent code:** keep the Interview Manager, Question Agent, Evaluation Agent, Feedback Agent, and Adaptive Decision Logic as separate, testable modules (see SRS §9.2, Table 8) rather than one monolithic prompt handler.
- **Validation:** always validate and sanitize AI responses before storing or displaying them (structured JSON output, score-range checks, retry on invalid output — SRS §9.4).

## Environment & Secrets

- Never commit `.env`, API keys, JWT secrets, or the AI service (e.g. Claude) API credentials.
- Provide a `.env.example` with variable names only (e.g. `MONGODB_URI`, `JWT_SECRET`, `AI_API_KEY`).
- Each teammate keeps their own local `.env`.
- API credentials must be stored and used server-side only — never exposed in frontend code or bundles (SRS §7.3).
- Never commit real personal user data; use synthetic/test accounts for development and demos.

## AI-Assisted Development (SRS §14.6)

- AI tools may assist with requirement drafting, README creation, code scaffolding, test generation, diagram generation, and weekly summaries.
- All AI-generated code and documentation must be reviewed by the team before inclusion.
- The team remains responsible for correctness, security, testing, and final decisions — AI output is a starting point, not an approval.
- Maintain an AI usage log (e.g. `docs/ai-usage-log.md`) documenting how AI tools contributed to the project, per lab requirements.

## Security & Privacy Checklist (before merging auth/data-related PRs)

- Passwords hashed (never stored in plain text) — FR-03.
- Private user data and interview history restricted to the authenticated owner — FR-05, NFR-08.
- AI responses validated before storage/display — no unvalidated AI output reaches the database or UI.
- Errors from the AI service or database handled gracefully, without crashing the app — FR-20, NFR-04.

## Weekly Checkpoint

Aligned with the sprint schedule in SRS §14.1 (requirements Week 1, architecture/wireframes Week 2, core development Weeks 3–4, CRUD/API/AI functionality Weeks 5–6):

1. Merge `develop` → `main` once the week's demo is stable.
2. Tag the commit (`git tag week-1`, `week-2`, …).
3. Update `docs/tasks.md` — check off completed items, add next week's backlog.
