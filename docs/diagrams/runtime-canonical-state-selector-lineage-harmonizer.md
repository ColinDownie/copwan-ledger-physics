# Deterministic Canonical State Selector & Lineage Harmonization Engine — Internal Architecture

This diagram specifies the **canonical state selector** and the
**lineage harmonization engine**, which together determine the authoritative
constitutional state and rewrite all cluster lineages to match it.

The selector MUST satisfy:

- deterministic canonical‑state selection
- deterministic lineage harmonization
- deterministic rewrite rules
- deterministic replay equivalence
- deterministic cluster symmetry
- deterministic conflict resolution

No nondeterministic canonical‑state selection or lineage rewrite is permitted.

## Canonical State Selector Components

- **State Comparator**  
  Compares normalized cluster states deterministically.

- **Ranking Engine**  
  Applies deterministic ranking rules to choose the canonical state.

- **Tie‑Breaker Engine**  
  Applies deterministic tie‑breakers (hash ordering, lineage depth).

- **Canonical State Committer**  
  Commits the canonical state to global lineage.

## Lineage Harmonization Components

- **Lineage Diff Analyzer**  
  Computes deterministic diffs between canonical and non‑canonical lineages.

- **Rewrite Planner**  
  Plans deterministic lineage rewrites.

- **Rewrite Executor**  
  Applies deterministic lineage rewrites to all clusters.

- **State Rebuilder**  
  Rebuilds governance state from rewritten lineage.

- **Cluster Synchronizer**  
  Ensures all clusters adopt the canonical state at the same logical tick.

- **Harmonization Recorder**  
  Emits replay‑visible harmonization events.

## Canonical State Ranking Rules

Canonical state is selected by:

1. **Lineage Depth**  
2. **Lineage Integrity Score**  
3. **Metadata Consistency**  
4. **Activation Tick Ordering**  
5. **Lexicographic Hash Ordering**  

These rules guarantee:

- determinism  
- replay‑equivalence  
- cluster symmetry  
- no forks  

## Mermaid Diagram — Canonical State Selector & Lineage Harmonization Engine

```mermaid
flowchart LR

    subgraph Inputs["Selector Inputs"]
        IN_STATES["Cluster States"]
        IN_LIN["Cluster Lineages"]
        IN_META["Constitutional Metadata"]
    end

    subgraph Selector["Canonical State Selector"]
        CMP["State Comparator"]
        RANK["Ranking Engine"]
        TIE["Tie‑Breaker Engine"]
        COM["Canonical State Committer"]
    end

    subgraph Harmonizer["Lineage Harmonization Engine"]
        DIFF["Lineage Diff Analyzer"]
        PLAN["Rewrite Planner"]
        EXEC["Rewrite Executor"]
        REB["State Rebuilder"]
        SYN["Cluster Synchronizer"]
        AUD["Harmonization Recorder"]
    end

    subgraph Outputs["Selector Outputs"]
        OUT_CAN["Canonical State"]
        OUT_REW["Rewritten Lineages"]
        OUT_AUD["Harmonization Lineage Events"]
    end

    IN_STATES --> CMP --> RANK --> TIE --> COM --> OUT_CAN
    IN_LIN --> DIFF --> PLAN --> EXEC --> REB --> SYN --> OUT_REW
    SYN --> AUD --> OUT_AUD
