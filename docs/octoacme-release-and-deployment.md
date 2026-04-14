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

For the full, detailed release checklist (including feature-flag checks, canary rollout steps, and monitoring thresholds), use the template: [docs/templates/release-checklist.md](./templates/release-checklist.md).

Quick reference:
- [ ] Deployment window scheduled (if needed)
- [ ] Backup or snapshot (if applicable)
- [ ] Deploy to staging and run smoke tests; obtain QA sign-off
- [ ] Deploy to production (automated pipeline preferred)
- [ ] Run post-deploy verifications
- [ ] Announce release to stakeholders and support

## Canary Deployment Steps

Use a phased rollout to limit blast radius for high-risk changes:

1. **5%** — deploy to canary slice; monitor for 15 min (error rate delta < 0.5%, p95 latency delta < 10%)
2. **25%** — expand if metrics are healthy; monitor for 30 min
3. **50%** — expand; monitor for 30 min
4. **100%** — full rollout; monitor for 1 hour post-deploy

*Pause or rollback at any step if thresholds are exceeded.*

## Monitoring Checks After Deploy

- Confirm error rate and latency are within baseline thresholds
- Check key dashboards (errors, latency p95/p99, throughput)
- Verify feature flags are in the intended state
- Confirm runbook is valid and accessible to on-call

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
