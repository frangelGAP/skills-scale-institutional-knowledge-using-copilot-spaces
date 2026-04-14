# Process Docs Guidelines

**Title:** Process Docs Guidelines
**Summary:** How to author, review, and maintain program process documents used by Copilot Spaces.
**Owner:** OctoAcme Project Management Team

---

## Purpose

This document provides guidance for contributors on how to create, review, update, and retire process documents in the `docs/` folder. Following these guidelines ensures that all process documentation is consistent, actionable, and trustworthy.

---

## Authoring a New Process Document

1. **Check for existing docs** — Before creating a new file, review `docs/README.md` to confirm the topic is not already covered.
2. **Use a clear file name** — Follow the naming convention `octoacme-<topic>.md` (e.g., `octoacme-onboarding.md`).
3. **Start with a header block** — Include at minimum:
   - `# Title`
   - `## Purpose` — one or two sentences describing what the doc covers and who it is for.
   - `## Scope` — what is and is not covered.
4. **Keep content concise and actionable** — Use checklists, bullet points, and short sections. Avoid long prose paragraphs.
5. **Link related docs** — Reference other process documents where appropriate.
6. **Submit via pull request** — Open a PR against the `main` branch, link the relevant issue, and request review from a maintainer.

---

## Reviewing Process Documents

- **Reviewer checklist:**
  - [ ] Content is accurate and consistent with existing docs.
  - [ ] Language is clear, concise, and free of jargon.
  - [ ] All checklists and templates are complete.
  - [ ] Links to related documents are valid.
  - [ ] File name follows the naming convention.
- Approve and merge only after at least one maintainer review.
- Leave actionable comments; resolve threads before merging.

---

## Maintaining and Updating Documents

- **Minor updates** (typo fixes, small clarifications): commit directly to a short-lived branch and open a PR.
- **Major updates** (new sections, workflow changes): open an issue first using the `.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml` template, then link the PR to the issue.
- **Review cadence:** All process docs should be reviewed at least once per quarter. The document owner is responsible for triggering that review.
- **Retiring a document:** Add a deprecation notice at the top of the file before deletion, and update `docs/README.md` to remove the link.

---

## Adding Documents to Copilot Spaces Context

To make a process document available as context in Copilot Spaces:
1. Ensure the file is in the `docs/` folder.
2. Reference the file in `.copilot/` configuration if your workspace uses explicit context files.
3. Keep the document focused — Copilot Spaces works best with concise, well-structured files.

---

## Document Ownership

Each process document should have a clearly identified owner (team or individual) responsible for keeping it up to date. If ownership changes, update both the document header and `docs/README.md`.

---

*For questions or to propose changes to these guidelines, open an issue using the process-docs issue template.*
