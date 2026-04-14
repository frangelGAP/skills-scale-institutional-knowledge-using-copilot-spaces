# OctoAcme — Release & Deployment Guide

## Purpose
Standardize how OctoAcme releases features to production to reduce risk and improve observability.

## Release Types
- Patch: hotfixes addressing critical production issues
- Minor: incremental features and improvements
- Major: significant functionality or breaking changes

## Pre-release requirements
- All acceptance criteria met and PRs merged
- Passing CI and security scans
- Release notes drafted
- Rollback / mitigation plan documented
- Smoke tests prepared

## Deployment Checklist

For a detailed, step-by-step checklist (including feature-flag checks, canary rollout, monitoring runbooks, and rollback steps), use the template at **[docs/templates/release-checklist.md](templates/release-checklist.md)**.

Quick summary:
- [ ] Deployment window scheduled (if needed)
- [ ] Backup or snapshot (if applicable)
- [ ] Deploy to staging and run smoke tests; obtain QA sign-off
- [ ] Feature flags set to correct initial state
- [ ] Canary deployment to 5% traffic; monitor for 30 minutes (see canary steps below)
- [ ] Promote to 100% once metrics are healthy
- [ ] Run post-deploy verifications (health endpoints, error rate, latency, key flows)
- [ ] Announce release to stakeholders and support

## Canary Deployment Steps

Use canary rollout for any change touching core user flows or infrastructure:

1. Deploy to canary slice (5% of production traffic or a single region).
2. Monitor for 30 minutes:
   - **Error rate** (5xx): alert if > 1% increase vs. baseline
   - **Latency p95/p99**: alert if > 10%/20% increase vs. baseline
   - **Business metrics**: conversion rate, session errors, key funnels
3. If healthy, promote in steps: 25% → 50% → 100%, with 15-minute windows at each step.
4. If any step shows an anomaly, **pause rollout** and follow the Rollback steps below.

## Monitoring Checks After Deploy

Run immediately after each promotion step:
- [ ] Application health endpoint returns `200 OK`
- [ ] Error rate within baseline ± 0.5%
- [ ] Latency p95 within baseline ± 10%
- [ ] Key feature flows pass smoke tests (automated or manual)
- [ ] Log aggregation (Datadog / Splunk) shows no unexpected error spikes
- [ ] Alerting rules active and correctly configured

## Rollback & Incident Playbook
- If a deployment fails or causes a critical issue:
  - Trigger incident response and notify on-call
  - Rollback to last known-good release if necessary
  - Triage root cause and capture action items

## Release Notes Template
- Release name / number:
- Date:
- Summary:
- Notable changes:
- Migration steps (if any):
- Known issues:
