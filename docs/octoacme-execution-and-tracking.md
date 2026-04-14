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
  - Small PRs (<= 400 lines when possible)
  - Include issue link and acceptance criteria in PR description
  - Run automated tests and linting in CI before requesting review
  - Require at least one approval before merging (or team-defined policy)

## Branching & PR Conventions

**Branch naming pattern:** `<type>/<short-description>`  
Examples: `feature/user-auth`, `fix/login-error`, `improve/release-checklist`, `docs/update-risk-register`

**Code ownership:** Assign code owners in `CODEOWNERS` for critical paths (e.g., `docs/` → `@pm-team`). PRs touching owned paths require a code-owner approval.

**Merge requirements:**
- CI pipeline must be green (build, tests, lint) before a PR can be merged.
- Security scans (e.g., CodeQL, Dependabot) must show no new critical or high findings.
- PR description must reference the related issue number (e.g., `Closes #42` or `Related to #42`).
- QA approval (comment or review) is required for PRs that are part of a release.

**PR size guidance:**
- Prefer PRs ≤ 400 lines of diff; aim for ≤ 200 lines for easier review.
- Large changes should be broken into a feature branch with stacked, focused PRs.
- If a PR must exceed 400 lines, add a summary comment explaining the structure.

## Doc & Process Changes

To propose changes to process documents (files under `docs/`):

1. Open an issue using the template: `.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml`
2. Follow the review and approval flow described in [docs/doc-change-request-process.md](doc-change-request-process.md).
3. Apply authoring standards (front-matter, naming, lifecycle stages) from [docs/process-docs-guidelines.md](process-docs-guidelines.md).

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
- [ ] Branching and PR conventions documented in repo (see **Branching & PR Conventions** above)
- [ ] CI configured for tests, lint, and security scans
- [ ] Regular demos scheduled
- [ ] Risk register updated weekly
- [ ] Smoke tests executed in staging before each demo or release candidate
- [ ] Staging sign-off obtained from QA before promoting to production
- [ ] Risk register reviewed and updated after each sprint demo (new risks added, resolved risks closed)
