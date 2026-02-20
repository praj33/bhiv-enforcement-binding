# BHIV_CORE_DEMO_BOUNDARY.md

## Purpose

This document defines strict boundaries for what is demonstrated
in BHIV Core enforcement-aware agent demo.

The demo must not exhibit any behavior that bypasses Sovereign Enforcement.

---

## What Is Demoed

- Input reception
- Internal reasoning (observable via logs if needed)
- ActionProposal generation
- InsightBridge authorization (ALLOW / DENY)
- Authorized execution
- Append-only Bucket write
- Result returned to caller

---

## What Is NOT Demoed

- Learning or self-training
- Reinforcement tuning
- Autonomous retries
- Self-modification
- Retroactive correction
- History mutation
- Hidden override flags
- Debug bypass switches

---

## Demo Locks

- No mutable history
- No enforcement shortcuts
- No privileged developer mode
- No hardcoded ALLOW paths
- No cached authorization

---

## Integrity Guarantee

Demo environment behavior is identical
to production enforcement behavior.

No special-case demo logic exists.