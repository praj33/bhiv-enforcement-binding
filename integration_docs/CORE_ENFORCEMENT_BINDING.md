# CORE_ENFORCEMENT_BINDING.md

## Purpose

This document defines the binding between BHIV Core and Sovereign Enforcement
(via InsightBridge). It ensures that no execution or side effect may occur
unless explicitly authorized.

BHIV Core is prohibited from executing actions autonomously.

---

## Canonical Execution Flow

Input  
→ BHIV Core Reasoning  
→ Action Proposal Creation  
→ InsightBridge.validate(ActionProposal)  
→ ALLOW → Execution  
→ Bucket Append  
→ Return Result  

DENY → Abort  
→ Log Denial  
→ Return Error  

---

## Action Proposal Object

All executable intent must be represented as:

ActionProposal:
- id
- agent_id
- intent
- target
- payload
- risk_level
- timestamp

BHIV Core may only emit ActionProposal objects.  
BHIV Core may not emit executable commands.

---

## Enforcement Gate

All Direct Execution Points listed in CORE_EXECUTION_SURFACES.md  
must be reachable only after:

InsightBridge returns: ALLOW

---

## Enforcement Rules

- No execution without ALLOW  
- No fallback execution path  
- No cached approvals  
- No offline approvals  
- No implicit trust  

---

## Execution Guard

Execution functions must require:

- Valid enforcement decision  
- Correlation to ActionProposal ID  

Calls without enforcement proof must fail.

---

## Temporal Enforcement Invariant

Enforcement authorization must be evaluated **immediately prior to execution**.

Validation earlier in the pipeline (e.g., during planning or proposal)
does not confer permission to execute.

Execution functions must:

- Invoke InsightBridge.validate(ActionProposal) at time-of-execution  
- Reject execution if validation is not contemporaneous  
- Treat any stale or prior approval as invalid  

This prevents authorization drift between proposal and execution.

---

## Temporal Binding Guarantee

At the instant execution occurs:

ALLOW must be freshly obtained.

No execution may rely on:

- Earlier-stage approvals  
- Cached decisions  
- Pre-validated proposals  

Authorization is single-use and time-bound to execution.

---

## Binding Guarantee

BHIV Core cannot:

- Self-authorize  
- Override enforcement  
- Bypass InsightBridge  
- Execute during enforcement failure  

---

## Failure Behavior

If InsightBridge is unreachable:

Execution is forbidden.

---

## Audit Assertion

All execution inside BHIV Core is sovereign-gated.  
Unauthorized execution is structurally impossible.