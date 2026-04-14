# Retrospective Action Item Template

Use one instance of this template per action item identified in a retrospective. Convert each action item to a GitHub Issue and link it here.

---

## Action Item

| Field | Value |
|---|---|
| **Title** | Short, imperative description (e.g., "Add smoke tests to staging pipeline") |
| **Owner** | @github-username |
| **Due Date** | YYYY-MM-DD |
| **Success Criteria** | How will we know this is done? (e.g., "PR merged, CI smoke tests run on every staging deploy") |
| **Status** | Open / In Progress / Done / Cancelled |
| **GitHub Issue** | [#issue-number](link-to-issue) |

---

## How to Use

1. After the retrospective, create one GitHub Issue per action item.
2. Assign the issue to the owner and set a due date via the milestone or custom field.
3. Add the `retro-action` label to the issue for tracking.
4. Reference the issue number in the table above.
5. Review open action items at the start of the next retrospective.

### Recommended GitHub Issue fields

| Field | Recommended value |
|---|---|
| Title | Same as action item title |
| Assignee | Action item owner |
| Label | `retro-action` |
| Milestone | Sprint or quarter the item is due |
| Body | Paste the full action item table above |

---

## Example

| Field | Value |
|---|---|
| **Title** | Add smoke tests to staging pipeline |
| **Owner** | @dev-lead |
| **Due Date** | 2026-05-01 |
| **Success Criteria** | Smoke test suite runs automatically on every staging deployment; failures block promotion to production |
| **Status** | In Progress |
| **GitHub Issue** | [#42](https://github.com/org/repo/issues/42) |
