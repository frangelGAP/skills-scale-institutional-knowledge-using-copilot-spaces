# OctoAcme — Execution & Tracking

## Purpose
Guidance for managing day-to-day execution and tracking progress toward project milestones.

## Team Rhythm
- Daily standups (15 min) — focus on progress, blockers, dependencies
- Weekly delivery sync — show progress, updates, and flagged risks
- Demo/Review at the end of each sprint or milestone

## Workflows
- Use the project board (e.g., GitHub Projects) with columns: Backlog, Ready, In Progress, In Review, QA, Done
- Pull Request workflow:
  - Small PRs (<= 400 lines when possible); prefer focused, single-concern PRs
  - Include issue link and acceptance criteria in PR description
  - Run automated tests and linting in CI before requesting review
  - Require at least one approval before merging (or team-defined policy)

## Branching & PR Conventions

- **Branch naming patterns:**
  - `feature/<short-description>` — new features
  - `fix/<short-description>` — bug fixes
  - `improve/<short-description>` — improvements and refactors
  - `improve/process-docs` or `improve/<doc-name>` — process document updates
- **CODEOWNERS:** Add a `CODEOWNERS` file to automatically assign reviewers for key areas.
- **CI gates:** All PRs must pass CI (tests, lint) and security scans before review is requested. Do not merge PRs with failing checks.
- **Issue reference:** Every PR description must reference the linked issue (e.g., `Closes #42` or `Related to #42`). PRs without an issue reference will not be merged.
- **QA approval:** PRs that affect end-user behavior or release flows require explicit QA sign-off before merging.
- **PR size:** Keep PRs ≤ 400 lines of diff when possible. If a change is larger, split it into logical sub-PRs with a tracking issue.

## Doc & Process Changes

To propose changes to process documents in `docs/`, follow the change request process:
- File an issue using [`.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml`](.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml).
- Review authoring and naming conventions in [`docs/process-docs-guidelines.md`](./process-docs-guidelines.md).
- Use the branch pattern `improve/<doc-name>` for your PR.

## Quality & Testing
- Unit tests for new logic
- Integration tests where applicable
- End-to-end smoke tests for critical flows before release
- Security scanning in CI
- Manual QA for feature acceptance when needed

## Reporting & Metrics
- Track velocity and burndown
- Monitor success metrics identified in the Project One-pager
- Use dashboards for key signals (errors, latency, usage)

## Blocker Escalation
- Level 1: Team-level triage in daily standup
- Level 2: PM escalates to Product Lead and dependent teams
- Level 3: Sponsor-level escalation for business-impacting issues

## Execution Checklist
- [ ] Branching and PR conventions documented in repo
- [ ] CI configured for tests and lint
- [ ] Regular demos scheduled
- [ ] Risk register updated weekly
- [ ] Smoke tests run in staging before every release
- [ ] Staging sign-off obtained from QA lead
- [ ] Risk register updated after each sprint demo (new risks captured, resolved risks closed)
