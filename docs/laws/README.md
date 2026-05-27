Colin —  
here is the **repo‑ready, constitutional‑grade Law Registry Root**, written to slot directly into:

```
docs/laws/README.md
```

This file establishes the **governance, indexing, naming, and validation rules** for every law in the CoP‑WAN Ledger Physics substrate.  
It binds the law system to TRC‑FINAL‑2026, to Vol XIII and Vol XIV, and to the test harness.

This is the authoritative root of the entire law system.

---

# **Law Registry — Root Specification**  
### *Atomic, Machine‑Addressable Invariants of the CoP‑WAN Ledger Physics*

**Status:** Active  
**Authority:** Subordinate to TRC‑FINAL‑2026  
**Scope:** All laws referenced by Volume XIII and Volume XIV  
**Version:** LR‑0.1  

---

# **0. Constitutional Binding**

The Law Registry is **governed by TRC‑FINAL‑2026**.

All laws MUST:

- conform to TRC global invariants  
- be referenced by a semantic volume  
- be testable  
- be enforceable  
- be replay‑visible  
- be machine‑addressable  

No law may contradict TRC‑FINAL‑2026.

---

# **1. Purpose of the Law Registry**

The Law Registry defines the **atomic invariants** that govern:

- deterministic execution (Vol XIII)  
- cross‑cluster continuation (Vol XIV)  
- checkpoint admissibility  
- frontier continuity  
- fan‑out convergence  
- scheduler fairness  
- plan invariants  
- replay determinism  

Each law is a **single, standalone normative file**.

Each law is **referenced by code** and **enforced by tests**.

---

# **2. Law Naming Convention**

Each law MUST follow the canonical naming pattern:

```
<Volume>-<Category><Ordinal>
```

Where:

- **Volume** ∈ {XIII, XIV}  
- **Category** ∈ {V, P, S, AR, VR, FO, …}  
- **Ordinal** ∈ {1, 2, 3, …}  

Examples:

- `XIII-V1` — Replay Determinism  
- `XIII-P6` — Plan Invariants  
- `XIII-S3` — Scheduler Fairness  
- `XIV-AR1` — Checkpoint Admissibility  
- `XIV-VR2` — Frontier Continuity  
- `XIV-FO1` — Fan‑Out Convergence  

This naming scheme is **stable**, **machine‑parseable**, and **globally unique**.

---

# **3. Law Structure Requirements**

Each law file MUST contain:

### **3.1 Header**
- Law ID  
- Status  
- Volume  
- Section reference  

### **3.2 Statement**
A precise, atomic, normative rule.

### **3.3 Conditions**
The preconditions required for the law to apply.

### **3.4 Obligations**
What the system MUST do.

### **3.5 Prohibitions**
What the system MUST NOT do.

### **3.6 Test Mapping**
A pointer to the corresponding test file(s).

Example:

```
tests/properties/replay-determinism.spec.ts → XIII-V1
```

---

# **4. Law Categories**

The registry defines the following canonical categories:

### **Execution (Volume XIII)**  
- **V** — Verifiability / Replay  
- **P** — Plan Invariants  
- **S** — Scheduler / Ordering  

### **Continuation (Volume XIV)**  
- **AR** — Admissibility Rules  
- **VR** — Frontier Rules  
- **FO** — Fan‑Out Rules  

Additional categories MAY be added if they:

- are referenced by a volume  
- are testable  
- do not violate TRC‑FINAL‑2026  

---

# **5. Law Enforcement**

Every law MUST be enforced by:

### **5.1 Code**
Subsystems MUST reference the laws they implement.

### **5.2 Tests**
Each law MUST have at least one corresponding test in:

```
tests/properties/
tests/replay/
```

### **5.3 Replay Visibility**
All law‑relevant state MUST be visible in replay.

### **5.4 Deterministic Reproduction**
Laws MUST be reproducible under deterministic replay.

---

# **6. Registry Index**

The following laws are currently defined:

### **Volume XIII — Execution Semantics**
- **XIII‑V1** — Replay Determinism  
- **XIII‑P6** — Plan Invariants  
- **XIII‑S3** — Scheduler Fairness / Latency  

### **Volume XIV — Cross‑Cluster Bridging**
- **XIV‑AR1** — Checkpoint Admissibility  
- **XIV‑VR2** — Frontier Continuity  
- **XIV‑FO1** — Fan‑Out Convergence  

Each law is located in:

```
docs/laws/<LAW-ID>.md
```

---

# **7. Forbidden Behaviors**

The following are constitutionally prohibited:

- nondeterministic replay  
- nondeterministic scheduling  
- hidden entropy  
- frontier regression  
- frontier forking  
- lineage gaps  
- checkpoint skipping  
- unverifiable commitments  
- divergent fan‑out  
- invalid segment linking  

Any subsystem exhibiting these behaviors is invalid.

---

# **8. Binding Clause**

The Law Registry is **fully subordinate** to:

1. **TRC‑FINAL‑2026**  
2. **Volume XIII**  
3. **Volume XIV**  

All code, tests, and execution traces MUST conform to the Law Registry.

This establishes the **atomic invariant layer** of the CoP‑WAN Ledger Physics.

---

# **END OF LAW REGISTRY ROOT**

---

Colin —  
the constitutional layer (TRC), the execution volume (XIII), the continuation volume (XIV), and now the law registry root are all complete.

If you want, I can now generate:

- **Frontier evolution diagram spec**  
- **Checkpoint chain diagram spec**  
- **Replay model diagram spec**  
- **Law auto‑index generator script**  

Just tell me which vector you want to open next.
