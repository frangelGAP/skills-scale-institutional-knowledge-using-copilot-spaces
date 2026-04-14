# OctoAcme — Process Docs Guidelines

## Purpose
Explain how to author, review, and maintain the program process documents used by OctoAcme and surfaced in Copilot Spaces.

---

## Front-Matter / Metadata

Every process document should begin with a YAML front-matter block (or an equivalent metadata table at the top) containing these fields:

```yaml
---
title: "Short, descriptive document title"
summary: "One-sentence description of what this doc covers."
owner: "@github-username"           # Primary author / maintainer
reviewers: ["@reviewer1", "@reviewer2"]
tags: ["execution", "release", "planning"]   # Free-form topic tags
copilot_spaces_visibility: true     # Set to true to include in Copilot Spaces context
---
```

| Field | Required | Notes |
|---|---|---|
| `title` | Yes | Matches the `# H1` heading in the document |
| `summary` | Yes | Used in the `docs/README.md` index |
| `owner` | Yes | GitHub username of the doc owner |
| `reviewers` | Recommended | At least one peer reviewer |
| `tags` | Recommended | Helps Copilot Spaces categorise context |
| `copilot_spaces_visibility` | Yes | Controls whether the file is added as a Space source |

---

## Naming & Path Conventions

| Location | When to use |
|---|---|
| `docs/` | Team-wide process docs, guidelines, and role definitions |
| `docs/templates/` | Reusable templates (checklists, tables, action-item forms) |
| `.copilot/` | Copilot Spaces-specific instruction files (e.g., `copilot-instructions.md`) |
| `.github/ISSUE_TEMPLATE/` | Issue form templates — do **not** add process docs here |

**File naming:** Use lowercase kebab-case, prefixed with the project or product name where relevant.  
Examples: `octoacme-release-and-deployment.md`, `docs/templates/release-checklist.md`

---

## When to File a Doc-Change Issue

Use the issue template **`.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml`** whenever you want to:

- Propose new content or a new document before writing it (good for large changes).
- Request a correction or clarification in an existing doc.
- Flag a gap in process coverage identified during a retrospective or incident review.

For small, self-contained fixes (typos, broken links), you may open a PR directly without an issue.  
For anything that changes workflow, policy, or ownership, **open an issue first** so stakeholders can comment before implementation begins.

See [doc-change-request-process.md](doc-change-request-process.md) for the full approval flow and SLAs.

---

## Document Lifecycle

```
Draft → Review → Approved → Merged → (Archived when superseded)
```

| Stage | Owner | Criteria to advance |
|---|---|---|
| **Draft** | Doc owner | Outline complete; first content written |
| **Review** | Reviewers listed in front-matter | Peers + PM comment; no open blockers |
| **Approved** | Doc owner | At least 1 reviewer approves in GitHub PR review |
| **Merged** | Doc owner | PR merged into `main`; Copilot Spaces updated |
| **Archived** | Doc owner | Doc is superseded or retired; move to `docs/archive/` and update links |

### Practical example

1. A developer notices the release checklist is missing canary-rollout steps.
2. They open an issue using `.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml`.
3. The PM triages the issue and assigns it to a doc owner within **2 business days**.
4. The doc owner creates a branch (`improve/release-checklist`), edits `docs/octoacme-release-and-deployment.md` or `docs/templates/release-checklist.md`, and opens a PR referencing the issue.
5. At least one reviewer approves the PR within **3 business days**.
6. The doc owner merges and updates the Copilot Space to include the new content if needed.

---

## Copilot Spaces Visibility

Files under `docs/` and `.copilot/` can be added as sources to a Copilot Space.  
Set `copilot_spaces_visibility: true` in front-matter to signal that a file is intended as Space context.  
Add or remove sources in the Space settings under **Sources → Repository files**.

---

## Style Guide

- Use `##` for top-level sections and `###` for sub-sections.
- Keep sections short; link to other docs rather than repeating content.
- Use checklist formatting (`- [ ]`) for actionable steps.
- Include at least one small example (table row, code block, or checklist item) per template section.
- Prefer concrete language ("run `npm test`") over vague guidance ("test the code").
