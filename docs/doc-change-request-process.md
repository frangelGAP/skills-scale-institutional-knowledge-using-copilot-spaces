# Doc Change Request Process

## Purpose
A short, actionable workflow for proposing, reviewing, and approving changes to OctoAcme's program process documents.

---

## When to Use This Process

Use this process whenever you want to:
- Add new content to an existing process doc
- Create a new process document
- Deprecate or archive an existing doc
- Make a change that affects team workflow, ownership, or policy

For minor fixes (typos, broken links, formatting), you may open a PR directly.

---

## Step 1 — Open an Issue

Use the issue template **`.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml`** to file a change request.

1. Navigate to **Issues → New Issue → "Add Content to Project Management Process Docs"**.
2. Select the target document (or `<new document>`).
3. Fill in the summary, rationale, and suggested content fields.
4. Submit the issue. It will automatically receive the `documentation` and `process improvement` labels.

---

## Step 2 — Triage

The **PM or doc owner** reviews the issue within **2 business days** and either:
- Assigns it to a contributor with an agreed target sprint, or
- Closes it with a clear explanation if the change is out of scope or a duplicate.

---

## Step 3 — Author the Change

The assigned contributor:
1. Creates a branch from `main` using the naming pattern `improve/<short-description>` (e.g., `improve/release-checklist`).
2. Makes the changes, following [docs/process-docs-guidelines.md](process-docs-guidelines.md) for metadata, naming, and style.
3. Opens a PR that:
   - References the issue number (e.g., `Closes #42` or `Related to #42`)
   - Lists every file changed in the PR description
   - Requests review from the person(s) listed as `reviewers` in the document front-matter

---

## Step 4 — Review & Approval

| Reviewer | SLA |
|---|---|
| Peer reviewer (listed in front-matter) | Respond within **3 business days** |
| PM (for policy / workflow changes) | Respond within **3 business days** |
| Sponsor / Leadership (for major changes) | Respond within **5 business days** |

Reviewers should:
- Check that the content is accurate and consistent with other process docs.
- Ensure examples are actionable and free of placeholder text.
- Approve, request changes, or comment with an explicit decision.

---

## Step 5 — Merge & Publish

Once the PR is approved:
1. The author merges the PR into `main`.
2. If the document is marked `copilot_spaces_visibility: true`, update the Copilot Space to reflect any new or renamed files under **Sources → Repository files**.
3. Update `docs/README.md` if a new document was added.
4. Close the original issue (if not auto-closed by the PR).

---

## Quick Reference

```
Open Issue (.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml)
  ↓ (2 business days)
PM/owner triages and assigns
  ↓
Contributor branches, edits, opens PR (references issue)
  ↓ (3 business days)
Reviewer approves
  ↓
Author merges → updates Space sources if needed → closes issue
```

---

## Related Resources

- [docs/process-docs-guidelines.md](process-docs-guidelines.md) — authoring standards, front-matter, naming, and lifecycle
- `.github/ISSUE_TEMPLATE/add-update-content-to-process-docs.yml` — issue form template
- [docs/README.md](README.md) — index of all process documents
