Colin —  
continuing the canonical chain with **no drift, no filler, only the next necessary block**.

You’ve already got:

1. Frontier Evolution  
2. Checkpoint Chain  
3. Replay Model  
4. Commitment Graph  

The **next required diagram** in the Ledger Physics substrate is the **Relay + Fan‑Out Propagation Diagram Spec**, because:

- Commitments must propagate  
- Propagation must converge  
- Convergence is governed by XIV‑FO1  
- Relay daemons enforce admissibility + ordering  
- Fan‑out ensures multi‑cluster consistency  

Below is the **repo‑ready block**, suitable for:

```
docs/diagrams/relay-fanout.md
```

---

# **Relay & Fan‑Out Propagation Diagram Spec**  
### *Deterministic Multi‑Cluster Propagation Under Volume XIV*

```md
# Relay & Fan-Out Propagation — Deterministic Multi-Cluster Continuation

This diagram illustrates how checkpoints and commitments propagate across
multiple receiving clusters via deterministic relay daemons.

Propagation MUST satisfy:

- **XIV-AR1** — Checkpoint Admissibility  
- **XIV-VR2** — Frontier Continuity  
- **XIV-FO1** — Fan-Out Convergence  

## Relay Model

A relay daemon:

- receives checkpoints from a source cluster  
- validates admissibility  
- updates its local frontier  
- forwards admissible checkpoints to downstream clusters  
- rejects divergent or stale segments  

## Fan-Out Model

Fan-out ensures:

- all receiving clusters converge to the same frontier  
- propagation order is deterministic  
- no cluster advances on invalid checkpoints  
- no forks or regressions occur  

## Mermaid Diagram — Relay & Fan-Out

```mermaid
flowchart LR

    subgraph SourceCluster["Source Cluster"]
        C1["Checkpoint C1<br/>traceRoot=R1"]
        C2["Checkpoint C2<br/>traceRoot=R2"]
        C3["Checkpoint C3<br/>traceRoot=R3"]
    end

    subgraph Relay["Relay Daemon"]
        R1["Validate C1"]
        R2["Validate C2"]
        R3["Validate C3"]
    end

    subgraph ClusterA["Receiving Cluster A"]
        A_F0["Frontier A0"]
        A_F1["Frontier A1"]
        A_F2["Frontier A2"]
        A_F3["Frontier A3"]
    end

    subgraph ClusterB["Receiving Cluster B"]
        B_F0["Frontier B0"]
        B_F1["Frontier B1"]
        B_F2["Frontier B2"]
        B_F3["Frontier B3"]
    end

    C1 --> R1 --> A_F1
    C2 --> R2 --> A_F2
    C3 --> R3 --> A_F3

    C1 --> R1 --> B_F1
    C2 --> R2 --> B_F2
    C3 --> R3 --> B_F3

    A_F0 --> A_F1 --> A_F2 --> A_F3
    B_F0 --> B_F1 --> B_F2 --> B_F3

    style A_F1 fill:#e0ffe0,stroke:#333
    style A_F2 fill:#e0ffe0,stroke:#333
    style A_F3 fill:#e0ffe0,stroke:#333

    style B_F1 fill:#e0ffe0,stroke:#333
    style B_F2 fill:#e0ffe0,stroke:#333
    style B_F3 fill:#e0ffe0,stroke:#333
```

## Interpretation

- The relay daemon validates checkpoints **once**.  
- All downstream clusters receive the **same validated sequence**.  
- Each cluster independently applies admissibility rules.  
- All clusters converge to the **same frontier**.  

## Invalid Propagation Conditions

A relay MUST reject:

- stale checkpoints  
- lineage‑breaking checkpoints  
- mismatched traceRoots  
- forks  
- regressions  
- unverifiable commitments  

A receiving cluster MUST reject:

- any checkpoint the relay should have rejected  
- any checkpoint that violates its local frontier  

## Invariants Illustrated

- **Fan-Out Convergence (XIV-FO1)**  
  All receiving clusters converge to the same frontier.

- **Frontier Continuity (XIV-VR2)**  
  Frontiers advance strictly and identically.

- **Checkpoint Admissibility (XIV-AR1)**  
  Only admissible checkpoints propagate.

- **Deterministic Relay Semantics**  
  Relay daemons MUST NOT introduce nondeterminism.

```

---

Colin —  
the next necessary block after this in the canonical chain is:

- **StateRoot Derivation Diagram Spec**  
or  
- **Scheduler Determinism Diagram Spec**  
or  
- **Quantization Boundary Diagram Spec**

If you want to continue the chain, just say **next**.
