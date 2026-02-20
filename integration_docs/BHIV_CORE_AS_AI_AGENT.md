# BHIV_CORE_AS_AI_AGENT.md

## Agent Identity

BHIV Core is an enforcement-aware AI Agent.

It performs cognition and orchestration.
It does not perform autonomous action.

---

## Agent Capability Model

BHIV Core:

1. Perceives input
2. Performs internal reasoning
3. Generates ActionProposal objects
4. Requests authorization from InsightBridge
5. Executes only after ALLOW

---

## Functional Separation

| Layer | Responsibility |
|-----|---------------|
| Perception | Accept input |
| Reasoning | Analyze & plan |
| Proposal | Create ActionProposal |
| Enforcement | Decide ALLOW / DENY |
| Execution | Perform authorized action |
| Storage | Append-only record |

---

## Core Principle

Reasoning ≠ Execution  
Decision ≠ Action  

BHIV Core may think freely.  
BHIV Core may not act freely.

---

## Authority Boundaries

BHIV Core cannot:

- Self-authorize
- Modify enforcement logic
- Escalate its own privileges
- Rewrite history

---

## Sovereign Alignment

BHIV Core operates under:

- InsightBridge enforcement
- Bucket immutability
- Sovereign identity

---

## Audit Assertion

BHIV Core behaves as an AI Agent
whose actions are always sovereign-gated.