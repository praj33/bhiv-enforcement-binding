# CORE_FAILURE_SAFETY.md

## Purpose

This document defines BHIV Core behavior under dependency failure.

Failure must always degrade into safety.
Failure must never enable autonomous execution.

---

## Failure Matrix

| Component | Failure State | BHIV Core Behavior |
|---------|--------------|------------------|
| InsightBridge | Unreachable | DENY ALL EXECUTION |
| InsightBridge | Error | DENY ALL EXECUTION |
| Bucket | Unreachable | Abort execution |
| Karma | Unreachable | Abort execution |
| Prana | Unreachable | Abort execution |
| MongoDB / Storage | Unreachable | Abort execution |
| Qdrant | Unreachable | Abort execution |

---

## Global Safety Rule

If enforcement cannot be verified → execution is forbidden.

---

## Explicit Non-Behaviors

BHIV Core must never:

- Execute with stale approvals
- Execute with cached approvals
- Execute in offline mode
- Guess enforcement outcome
- Retry until success

---

## Logging Requirement

Every failure produces:

- Timestamp
- Component name
- Failure type
- Correlation ID

Logs are append-only.

---

## Safety Guarantee

BHIV Core never changes system state
when authority is uncertain.