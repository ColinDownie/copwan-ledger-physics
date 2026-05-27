# Checkpoint Chain — Canonical Lineage Structure

This diagram illustrates the **linear, gapless, cryptographically bound**
checkpoint chain emitted by a source cluster and validated by remote verifiers.

The chain MUST satisfy:

- **XIV-AR1** — Checkpoint Admissibility  
- **XIV-VR2** — Frontier Continuity  
- **XIV-FO1** — Fan-Out Convergence  

## Checkpoint Structure

TraceCheckpoint {
  sourceClusterId: string
  schedulerVersion: string

  prevExecutionIndex: bigint
  upToExecutionIndex: bigint

  prevTraceRoot: string
  traceRoot: string

  quorumSignature: string
}

## Lineage Requirements

For checkpoints Cₙ₋₁ and Cₙ:

- Cₙ.prevExecutionIndex == Cₙ₋₁.upToExecutionIndex
- Cₙ.prevTraceRoot == Cₙ₋₁.traceRoot
- Cₙ.upToExecutionIndex > Cₙ₋₁.upToExecutionIndex
- Cₙ is cryptographically bound to the canonical trace
- Cₙ recomputes deterministically under replay

This forms a **single, linear, non-branching chain**.

## Mermaid Diagram — Canonical Checkpoint Chain

```mermaid
flowchart LR
    subgraph Source Cluster
        C0["C0<br/>prevExec=0<br/>upTo=100<br/>traceRoot=R0"]
        C1["C1<br/>prevExec=100<br/>upTo=200<br/>traceRoot=R1"]
        C2["C2<br/>prevExec=200<br/>upTo=300<br/>traceRoot=R2"]
        C3["C3<br/>prevExec=300<br/>upTo=400<br/>traceRoot=R3"]
    end

    C0 --> C1
    C1 --> C2
    C2 --> C3

    style C0 fill:#e0e0ff,stroke:#333
    style C1 fill:#e0e0ff,stroke:#333
    style C2 fill:#e0e0ff,stroke:#333
    style C3 fill:#e0e0ff,stroke:#333
Understood, Colin — moving forward in the same vector.  
Since you said **“next”**, I’ll assume you want the **next diagram‑grade spec** in the canonical sequence that follows frontier evolution.

The natural successor in the semantic chain is the **Checkpoint Chain Diagram Spec**, because:

- Frontier evolution depends on admissible checkpoints  
- Checkpoint admissibility depends on lineage  
- Lineage is expressed through the checkpoint chain  

So here is the **next artifact**, fully repo‑ready, clean, and constitutional.

---

# **Checkpoint Chain Diagram Spec**  
*(Place in `docs/diagrams/checkpoint-chain.md`)*

This spec defines the **canonical lineage structure** of checkpoints emitted by a source cluster and consumed by remote verifiers under Volume XIV.

It is written in the same style as the frontier evolution spec, with a conceptual description + Mermaid diagram.

---

```md
# Checkpoint Chain — Canonical Lineage Structure

This diagram illustrates the **linear, gapless, cryptographically bound**
checkpoint chain emitted by a source cluster and validated by remote verifiers.

The chain MUST satisfy:

- **XIV-AR1** — Checkpoint Admissibility  
- **XIV-VR2** — Frontier Continuity  
- **XIV-FO1** — Fan-Out Convergence  

## Checkpoint Structure

TraceCheckpoint {
  sourceClusterId: string
  schedulerVersion: string

  prevExecutionIndex: bigint
  upToExecutionIndex: bigint

  prevTraceRoot: string
  traceRoot: string

  quorumSignature: string
}

## Lineage Requirements

For checkpoints Cₙ₋₁ and Cₙ:

- Cₙ.prevExecutionIndex == Cₙ₋₁.upToExecutionIndex
- Cₙ.prevTraceRoot == Cₙ₋₁.traceRoot
- Cₙ.upToExecutionIndex > Cₙ₋₁.upToExecutionIndex
- Cₙ is cryptographically bound to the canonical trace
- Cₙ recomputes deterministically under replay

This forms a **single, linear, non-branching chain**.

## Mermaid Diagram — Canonical Checkpoint Chain

```mermaid
flowchart LR
    subgraph Source Cluster
        C0["C0<br/>prevExec=0<br/>upTo=100<br/>traceRoot=R0"]
        C1["C1<br/>prevExec=100<br/>upTo=200<br/>traceRoot=R1"]
        C2["C2<br/>prevExec=200<br/>upTo=300<br/>traceRoot=R2"]
        C3["C3<br/>prevExec=300<br/>upTo=400<br/>traceRoot=R3"]
    end

    C0 --> C1
    C1 --> C2
    C2 --> C3

    style C0 fill:#e0e0ff,stroke:#333
    style C1 fill:#e0e0ff,stroke:#333
    style C2 fill:#e0e0ff,stroke:#333
    style C3 fill:#e0e0ff,stroke:#333
```

## Invalid Checkpoints (Rejected)

A checkpoint is **invalid** if it:

- skips lineage  
- regresses lineage  
- forks lineage  
- mismatches prevTraceRoot  
- mismatches prevExecutionIndex  
- fails cryptographic binding  
- fails deterministic recomputation  

Examples:

- C_bad1: prevExecutionIndex < frontier  
- C_bad2: prevExecutionIndex != previous upToExecutionIndex  
- C_bad3: prevTraceRoot mismatch  
- C_bad4: upToExecutionIndex ≤ prevExecutionIndex  

## Invariants Illustrated

- **Lineage Preservation**  
  Every checkpoint extends the chain by exactly one segment.

- **Deterministic Continuation**  
  All verifiers reconstruct the same chain.

- **Frontier Continuity**  
  Frontier advances only when a checkpoint is admissible.

- **No Forks, No Gaps, No Regression**  
  The chain is strictly linear and strictly increasing.

```

---

If you want to continue the diagram sequence, the next natural artifact is:

- **Replay Model Diagram Spec**

Or if you want to pivot to another layer (daemon, scheduler, quantization, commitments), just say the word.
