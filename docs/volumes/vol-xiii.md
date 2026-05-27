Colin —  
here is the **repo‑ready, constitutional‑grade header for Volume XIII**, written in the correct semantic style, aligned with TRC‑FINAL‑2026, and ready to paste directly into:

```
docs/volumes/vol-xiii.md
```

This is the **Execution Semantics Volume Header** — the governing document for the entire execution kernel (`src/execution/`), the scheduler, the replay engine, the quantization layer, and the trace model.

No drift. No filler. Pure semantic law.

---

# **Volume XIII — Execution Semantics**  
### *Governing Document for Deterministic Execution, Replay Physics, and Canonical Trace Formation*

**Status:** Active  
**Authority:** Subordinate to TRC‑FINAL‑2026  
**Scope:** All execution engines, schedulers, replay systems, quantizers, and trace emitters  
**Version:** XIII‑0.1  

---

# **0. Constitutional Binding**

This volume is **governed by TRC‑FINAL‑2026**.

All execution semantics defined herein MUST conform to:

- the determinism boundary  
- the canonical trace model  
- the explicit entropy admission rules  
- the lineage and replay requirements  
- the global invariants defined in TRC‑FINAL‑2026  

No subsystem may override or weaken TRC‑FINAL‑2026.

---

# **1. Purpose of Volume XIII**

Volume XIII defines the **execution physics** of the CoP‑WAN Ledger:

- how intents become executable plans  
- how plans become deterministic schedules  
- how schedules produce canonical traces  
- how traces produce checkpoints  
- how replay reconstructs execution exactly  

This volume governs the **execution kernel** located at:

```
src/execution/
```

---

# **2. Execution Boundary**

Execution occurs within a **deterministic boundary** defined by:

- intent graph  
- quantization rules  
- schedulerVersion  
- replay inputs  
- frontier state  

Within this boundary, execution MUST be:

- deterministic  
- reproducible  
- observable  
- law‑anchored  

No hidden entropy is permitted.

---

# **3. Execution Phases**

Execution is decomposed into four constitutional phases:

### **3.1 Intent Ingestion**
The system receives intents and binds them to:

- law references  
- quantization rules  
- execution context  

### **3.2 Plan Compilation**
Intents are transformed into executable plans.  
Compilation MUST be deterministic.

### **3.3 Deterministic Scheduling**
The scheduler MUST:

- produce a single canonical ordering  
- respect fairness constraints  
- avoid nondeterministic branching  
- emit replay‑visible ordering metadata  

### **3.4 Trace Emission**
Execution produces:

- ordered events  
- canonical traceRoots  
- lineage‑preserving checkpoints  

Trace emission MUST be deterministic.

---

# **4. Replay Semantics**

Replay MUST reconstruct:

- identical ordering  
- identical traceRoots  
- identical checkpoints  
- identical replay‑visible state  

Replay MUST NOT:

- diverge  
- reorder  
- introduce entropy  
- skip lineage  

Replay determinism is governed by **Law XIII‑V1**.

---

# **5. Quantization Semantics**

Quantization rules MUST:

- be deterministic  
- be replay‑visible  
- be law‑anchored  
- be invariant under re‑execution  

Quantization MUST NOT introduce nondeterminism.

---

# **6. Canonical Trace Model**

Execution MUST produce a **canonical trace**, consisting of:

- ordered `ExecutionTraceEvent` entries  
- deterministic `traceRoot`  
- lineage‑preserving `prevTraceRoot`  
- cryptographically bound commitments  

The canonical trace model is implemented in:

```
src/shared/trace.ts
src/shared/types.ts
```

---

# **7. Checkpoint Formation**

Checkpoints MUST:

- be derived from canonical traces  
- preserve lineage  
- be cryptographically bound  
- be admissible under Volume XIV rules  

Checkpoint formation is subordinate to:

- **Law XIII‑V1** (Replay Determinism)  
- **Law XIV‑AR1** (Checkpoint Admissibility)  

---

# **8. Law Registry Integration**

Volume XIII references the following laws:

- **XIII‑V1 — Replay Determinism**  
- **XIII‑P6 — Plan Invariants**  
- **XIII‑S3 — Scheduler Fairness / Latency**  

All execution engines MUST enforce these laws.

---

# **9. Forbidden Behaviors**

The following are constitutionally prohibited within Volume XIII:

- nondeterministic scheduling  
- nondeterministic replay  
- hidden entropy  
- lineage gaps  
- trace divergence  
- scheduler nondeterminism  
- quantization nondeterminism  

Any subsystem exhibiting these behaviors is invalid.

---

# **10. Binding Clause**

Volume XIII is **fully subordinate** to TRC‑FINAL‑2026.

All execution semantics MUST conform to:

- TRC global invariants  
- Volume XIV continuation rules  
- the law registry  
- the canonical trace model  

This establishes the **execution half** of the CoP‑WAN Ledger Physics.

---

# **END OF VOLUME XIII HEADER**

---

Colin —  
this header is ready to paste directly into your repo.

If you want, I can now generate:

- **Volume XIV header**  
- **Law registry root**  
- **Frontier evolution diagram spec**  

Just tell me which vector you want to open next.
