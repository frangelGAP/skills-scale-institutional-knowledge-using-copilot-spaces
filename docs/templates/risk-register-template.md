# Risk Register Template

## Purpose
A lightweight table to capture, assess, and track project risks throughout the delivery lifecycle.  
Copy this table into your project's planning doc or maintain it as a standalone file under `docs/`.

---

## Risk Register Table

| ID | Risk Description | Likelihood (H/M/L) | Impact (H/M/L) | Severity | Owner | Mitigation / Response | Status | Last Updated |
|---|---|---|---|---|---|---|---|---|
| R-001 | _Example: Third-party API may change authentication schema before launch_ | M | H | High | @dev-lead | Spike scheduled for week 2 to validate API contract; fallback auth method identified | Open | 2025-01-15 |

### Column Descriptions

| Column | Description |
|---|---|
| **ID** | Sequential identifier, e.g., `R-001`. Use this to reference risks in status updates. |
| **Risk Description** | Brief, factual statement of what could go wrong. |
| **Likelihood** | Probability of occurrence: **H**igh / **M**edium / **L**ow |
| **Impact** | Business/project impact if the risk materialises: **H**igh / **M**edium / **L**ow |
| **Severity** | Derived from Likelihood × Impact. High × High = Critical; H × M or M × H = High; all others lower. |
| **Owner** | GitHub username of the person responsible for monitoring and mitigating this risk. |
| **Mitigation / Response** | Action(s) taken or planned to reduce likelihood or impact. |
| **Status** | `Open`, `Mitigated`, `Accepted`, or `Closed` |
| **Last Updated** | ISO date of the last status change. |

---

## Severity Matrix

|  | **Impact: H** | **Impact: M** | **Impact: L** |
|---|---|---|---|
| **Likelihood: H** | 🔴 Critical | 🟠 High | 🟡 Medium |
| **Likelihood: M** | 🟠 High | 🟡 Medium | 🟢 Low |
| **Likelihood: L** | 🟡 Medium | 🟢 Low | 🟢 Low |

---

## Usage Notes

- Review the risk register at each weekly delivery sync and update the **Status** and **Last Updated** columns.
- After every sprint demo, check whether any new risks surfaced and add them.
- Escalate 🔴 Critical risks to the sponsor immediately; 🟠 High risks within one business day.
- Archive closed risks by moving them below a `## Closed Risks` heading rather than deleting them.
