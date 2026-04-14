# Retrospective Action Item Template

## Purpose
Capture concrete, trackable improvements identified during a retrospective.  
Fill in one block per action item; convert each item to a GitHub Issue for visibility and assignment.

---

## Action Item

**Title:** _Short, verb-first description (e.g., "Add smoke tests to staging pipeline")_

| Field | Value |
|---|---|
| **Owner** | @github-username |
| **Due Date** | YYYY-MM-DD |
| **Success Criteria** | _Measurable outcome that confirms the action is complete (e.g., "Smoke test suite runs in CI for every staging deploy with < 2 min runtime")_ |
| **Status** | `Not Started` / `In Progress` / `Done` / `Blocked` |
| **Linked Issue** | #issue-number (created after the retro) |

**Notes / Context:**  
_Optional: why this action was raised, which theme it addresses._

---

## Example

**Title:** Automate post-deploy smoke tests in staging

| Field | Value |
|---|---|
| **Owner** | @dev-lead |
| **Due Date** | 2025-02-14 |
| **Success Criteria** | Smoke test job runs automatically on every staging deployment; failures block the rollout |
| **Status** | In Progress |
| **Linked Issue** | #42 |

**Notes / Context:**  
Raised in the Q1 retrospective after two incidents where staging smoke tests were skipped due to time pressure.

---

## Instructions

1. **During the retro:** Use sticky notes / voting to identify the top 2–3 improvement actions.  
   Avoid capturing more than 3 action items per retro — focus beats volume.

2. **After the retro:** For each action item, open a GitHub Issue using the repository's issue templates (or a plain issue) and fill in the **Linked Issue** field above.

3. **Assign a clear owner.** An action item without an owner is unlikely to get done.

4. **Review at the next retro or weekly sync.** Update the **Status** field and close the issue when the success criteria are met.

5. **Archive completed action items** in the retrospective notes doc (e.g., `docs/octoacme-retrospective-and-continuous-improvement.md`) so the team can celebrate wins and see the improvement trend over time.
