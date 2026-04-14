# Release Checklist Template

## Purpose
A comprehensive, step-by-step checklist to run before, during, and after each production deployment.  
Copy this file into your release branch or reference it from your release PR description.

---

## Pre-Release

### Code & Quality Gates
- [ ] All acceptance criteria for this release are met and verified
- [ ] All PRs targeting this release are merged to the release branch
- [ ] CI pipeline is green (build, unit tests, integration tests)
- [ ] Security scan (e.g., CodeQL, Dependabot alerts) shows no new critical/high findings
- [ ] Linting and code-style checks pass
- [ ] Dependency audit completed; no unresolved vulnerabilities

### Feature Flags
- [ ] New feature flags are documented in the release notes
- [ ] Flags intended for gradual rollout are set to the correct initial percentage (e.g., 0% or 5%)
- [ ] Flags that are being cleaned up / permanently enabled are confirmed with the PdM
- [ ] Flag states verified in staging environment before production deployment

### Documentation & Communication
- [ ] Release notes drafted and reviewed by PM/PdM
- [ ] Relevant runbooks and monitoring playbooks are up to date
- [ ] Support team notified of user-facing changes
- [ ] Stakeholder announcement prepared (for minor/major releases)

### Staging Sign-off
- [ ] Deployed to staging environment
- [ ] Smoke tests executed and passed in staging
- [ ] QA sign-off obtained (signature / approval comment on PR or issue)
- [ ] Performance baseline checked in staging (no regressions vs. previous release)

---

## Deployment

### Canary / Gradual Rollout
For any change that touches core user flows or infrastructure, use a canary deployment:

1. Deploy to canary slice (e.g., 5% of production traffic or a specific region).
2. Monitor for **15–30 minutes**:
   - Error rate: compare against baseline (alert if > 1% increase)
   - Latency (p50 / p95 / p99): compare against previous release
   - Key business metrics: conversion, session length, etc.
3. If metrics are healthy, promote to 25%, then 50%, then 100% with a 15-minute observation window at each step.
4. If any anomaly is detected at any step, **pause the rollout** and follow the rollback steps below.

Example rollout schedule:

| Step | Traffic% | Wait time | Go / No-go owner |
|---|---|---|---|
| Canary | 5% | 30 min | On-call engineer |
| Partial | 25% | 15 min | On-call engineer |
| Half | 50% | 15 min | PM or on-call |
| Full | 100% | — | PM or on-call |

### Deployment Steps
- [ ] Deployment window confirmed and communicated (if required)
- [ ] Database migrations (if any) run successfully in staging first
- [ ] Backup / snapshot taken (if applicable for the environment)
- [ ] Canary deployment kicked off (or full deploy if no canary required)
- [ ] Deployment pipeline completed without errors

---

## Post-Deploy Verification

### Monitoring Checks
Run these checks immediately after each rollout step:

- [ ] Application health endpoint returns `200 OK`
- [ ] Error rate (5xx responses) is within baseline ± 0.5%
- [ ] Latency p95 is within baseline ± 10%
- [ ] Key feature flows verified via smoke tests (manual or automated)
- [ ] Log aggregation (e.g., Splunk, Datadog) shows no unexpected error spikes
- [ ] Alerting rules are active and correctly configured in monitoring tool
- [ ] Feature flags at expected states in production

### Business Verification
- [ ] New features are accessible to the expected user segments
- [ ] Any data migrations validated (record counts, spot-checks)
- [ ] Analytics / tracking events firing correctly

### Stakeholder Notification
- [ ] Release announcement sent to stakeholders and support team
- [ ] Release notes published (GitHub Release, changelog, etc.)

---

## Rollback Steps

Trigger rollback if:
- Error rate increases > 1% above baseline after canary promotion, or
- Latency p99 increases > 20% above baseline, or
- A critical business metric degrades significantly, or
- The on-call engineer or PM makes a judgment call.

**Rollback procedure:**
1. Immediately pause any ongoing gradual rollout.
2. Revert the production deployment to the last known-good release tag.
3. Confirm health endpoints and monitoring return to baseline within 5 minutes.
4. Notify the team and stakeholders of the rollback.
5. Open an incident or post-mortem issue capturing:
   - Timeline of events
   - Root cause hypothesis
   - Action items with owners and due dates
6. Do **not** re-deploy until the root cause is understood and the fix is validated in staging.

---

## Sign-off

| Role | Name / Handle | Approved? | Date |
|---|---|---|---|
| QA | | | |
| PM / PdM | | | |
| On-call Engineer | | | |
