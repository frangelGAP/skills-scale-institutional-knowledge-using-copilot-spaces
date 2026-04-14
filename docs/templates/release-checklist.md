# Release Checklist Template

Reference this checklist for every release. For the detailed pre-release requirements, see [octoacme-release-and-deployment.md](../octoacme-release-and-deployment.md).

---

## Release Information

| Field | Value |
|---|---|
| Release name / version | |
| Release date & time | |
| Release engineer | |
| Rollback owner | |

---

## Pre-release Checks

- [ ] All acceptance criteria met and linked PRs merged to the release branch
- [ ] CI pipeline passing (tests, lint, security scans)
- [ ] Release notes drafted and reviewed
- [ ] Rollback / mitigation plan documented and shared with on-call
- [ ] Feature flags audited — confirm which flags to enable/disable at release
- [ ] Dependent service owners notified of breaking changes (if any)
- [ ] Database migrations tested in staging

---

## Staging Sign-off

- [ ] Deployed to staging environment
- [ ] Smoke tests passed in staging
- [ ] QA sign-off received from QA lead (required for releases impacting end users)
- [ ] Performance benchmarks within acceptable range
- [ ] Security scan results reviewed; no critical or high findings open

---

## Canary / Gradual Rollout (if applicable)

Follow this phased rollout pattern to limit blast radius:

1. **5% of traffic** — deploy to canary slice; monitor for 15 min
   - Error rate delta < 0.5%
   - p95 latency delta < 10%
2. **25% of traffic** — expand; monitor for 30 min
   - Same thresholds as above
3. **50% of traffic** — expand; monitor for 30 min
4. **100% of traffic** — full rollout; monitor for 1 hour post-deploy

*Pause or rollback at any step if thresholds are exceeded.*

---

## Production Deployment

- [ ] Deployment window confirmed with stakeholders
- [ ] Backup / snapshot taken (if applicable)
- [ ] Deploy to production via automated pipeline
- [ ] Deployment log reviewed for errors

---

## Post-deploy Verification

- [ ] Smoke tests passed in production
- [ ] Key dashboards checked: error rate, latency, throughput
- [ ] Monitoring alerts firing as expected (no false positives)
- [ ] Runbook link confirmed valid and accessible to on-call
- [ ] Feature flags set to intended state in production
- [ ] Release announcement sent to stakeholders and support team

---

## Rollback Steps

If a critical issue is detected post-deploy:

1. Trigger incident response and notify on-call via pager/Slack
2. Assess impact and confirm rollback is needed
3. Revert to last known-good release (automated pipeline preferred)
4. Verify rollback success with smoke tests
5. Open a post-incident review (PIR) and capture action items in the risk register

---

## Sign-off Table

| Role | Name | Approved | Notes |
|---|---|---|---|
| Release Engineer | | | |
| QA Lead | | | |
| Product Manager | | | |
