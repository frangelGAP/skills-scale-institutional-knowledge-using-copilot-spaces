# Doc Change Request Process

This document describes how to propose, review, and approve changes to the process documents in `docs/`. For authoring standards, see [process-docs-guidelines.md](./process-docs-guidelines.md).

---

## When to File a Change Request

File a change request whenever you want to:
- Add a new process document
- Update an existing document (new sections, revised guidance, corrected information)
- Retire or archive a document

Small fixes (typos, broken links) can go directly to a PR without a prior issue.

---

## Step-by-Step Process

### 1. Open an Issue

Use the issue template: **[Add/Update Content to Process Docs](.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml)**

Fill in:
- **Which process document** — existing file path or `[new document]`
- **Summary of new content** — what you want to add or change, and why
- **Why is this update needed** — the gap or problem being addressed
- **Suggested content** (optional) — draft text or outline

**Example:**
> **Which document:** `docs/octoacme-project-planning.md`
> **Summary:** Add a section on dependency tracking, including a table template for capturing external dependencies with owner and target resolution date.
> **Why:** Teams frequently miss dependencies during planning because there is no standard place to capture them.

### 2. Issue Triage (≤ 2 business days)

A doc maintainer will:
- Confirm the request is in scope
- Assign it to a milestone or sprint
- Label it `documentation` (and `process improvement` if applicable)
- Comment with any clarifying questions

### 3. Implement the Change

1. Branch from `main` using the pattern `improve/<short-description>` (e.g., `improve/add-dependency-tracking`).
2. Make the changes following the authoring guidance in [process-docs-guidelines.md](./process-docs-guidelines.md).
3. Open a PR and link the issue (include `Closes #<issue-number>` in the PR description).
4. Request review from the document owner and at least one additional maintainer.

### 4. Review & Approval (≤ 3 business days)

Reviewers will check:
- Accuracy and consistency with existing docs
- Clear, concise language; no jargon
- Proper naming and file placement
- Links are valid

If a reviewer has not responded within **3 business days**, escalate by mentioning the document owner in the PR.

### 5. Merge

- At least **one approving review** is required before merging.
- The PR author (or a maintainer) merges after approval.
- The linked issue is closed automatically by the `Closes #` reference.

### 6. Post-merge

- `docs/README.md` is updated if a new document was added (add link to file list).
- The change is announced in the team's weekly sync if it affects current workflows.

---

## SLA Summary

| Stage | SLA |
|---|---|
| Issue triage | ≤ 2 business days |
| Review response | ≤ 3 business days |
| Escalation (no response) | Mention doc owner in PR |

---

*Questions? Open an issue using the template above or ping the doc maintainers in the team channel.*
