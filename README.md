# BHIV Core — Sovereign Enforcement Binding (Architecture)

This repository contains the **architectural binding specification** that defines how BHIV Core must behave as an **enforcement-aware AI Agent system** under Sovereign Enforcement.

This is a **design-binding repository**, not an implementation repository.

No application code is included here.

---

## 🎯 Purpose

To formally specify:

- Where execution occurs inside BHIV Core  
- How execution must be gated by Sovereign Enforcement (InsightBridge)  
- How BHIV Core behaves as an AI Agent  
- How failures degrade safely  
- What is allowed and not allowed in demos  
- What integration expectations exist for Bucket, InsightBridge, and Sovereign systems  

This binding ensures:

> BHIV Core never executes outside sovereign gates.

---

## 📦 Repository Scope

This repository contains **only architectural documents**.

It does NOT contain:

- BHIV Core source code  
- Enforcement implementation  
- InsightBridge implementation  
- Bucket internals  
- Agent code  

Those live in their respective repositories.

---

## 📁 Structure
```
integration_docs/
├── CORE_EXECUTION_SURFACES.md
├── CORE_ENFORCEMENT_BINDING.md
├── BHIV_CORE_AS_AI_AGENT.md
├── CORE_FAILURE_SAFETY.md
├── BHIV_CORE_DEMO_BOUNDARY.md
└── RAJ_BHIV_CORE_INTEGRATION_SIGNOFF.md
```

---

## 📄 Document Descriptions

### CORE_EXECUTION_SURFACES.md
Enumerates every location where:
- Execution occurs  
- Decisions finalize  
- Side-effects happen  

Acts as the authoritative execution surface map.

---

### CORE_ENFORCEMENT_BINDING.md
Defines the canonical flow:

Input → Reasoning → Proposal → Enforcement → Execution → Bucket

Specifies temporal enforcement invariants and binding guarantees.

---

### BHIV_CORE_AS_AI_AGENT.md
Formally defines BHIV Core as an AI Agent:

Perceive → Reason → Propose → Request Authorization → Execute

Ensures reasoning ≠ execution.

---

### CORE_FAILURE_SAFETY.md
Defines system behavior under dependency failures.

Failure always degrades into safety.

---

### BHIV_CORE_DEMO_BOUNDARY.md
Locks demo scope and forbids unsafe shortcuts.

---

### RAJ_BHIV_CORE_INTEGRATION_SIGNOFF.md
Single authoritative readiness and integration statement.

---

## ⚠️ Important

This repository specifies **how BHIV Core must behave**.

It does NOT claim that enforcement is already implemented in code.

Implementation is a separate, future phase.

---

## ✅ Task Compliance

All six deliverables defined in the task:

“BHIV Core — Enforcement-Aware Agentic Integration”

are present in this repository.

---

## 📜 License

MIT
