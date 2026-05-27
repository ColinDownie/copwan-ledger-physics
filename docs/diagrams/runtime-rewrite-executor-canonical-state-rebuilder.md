# Deterministic Rewrite Executor & Canonical State Rebuilder — Internal Architecture

This diagram specifies the **rewrite executor** and the
**canonical state rebuilder**, which together apply deterministic lineage
rewrites and reconstruct the authoritative governance state.

The executor MUST satisfy:

- deterministic rewrite execution
- deterministic event application
- deterministic state reconstruction
- deterministic commit‑tick alignment
- deterministic replay equivalence
- deterministic cluster symmetry

No nondeterministic rewrite or rebuild behavior is permitted.

## Rewrite Executor Components

- **Rewrite Operation Loader**  
  Loads deterministic rewrite operations from the rewrite plan.

- **Event Rewriter**  
  Applies deterministic insertions, deletions, and replacements of lineage events.

- **Rewrite Validator**  
  Ensures rewritten lineage satisfies constitutional invariants.

- **Commit‑Tick Aligner**  
  Ensures all rewrite operations commit at deterministic logical ticks.

- **Rewrite Committer**  
  Commits rewritten lineage segments to global lineage.

## Canonical State Rebuilder Components

- **State Reset Engine**  
  Resets governance state to a deterministic baseline.

- **Event Replayer**  
  Replays rewritten lineage deterministically from genesis.

- **Metadata Reconstructor**  
  Rebuilds constitutional metadata deterministically.

- **Dependency Graph Rebuilder**  
  Reconstructs dependency graph deterministically.

- **Activation Schedule Rebuilder**  
  Recomputes activation ticks deterministically.

- **Cluster Synchronizer**  
  Ensures all clusters rebuild to the same canonical state.

- **Rebuild Recorder**  
  Emits replay‑visible rebuild events.

## Deterministic Rewrite Operations

- **Insert**  
  Add missing lineage events.

- **Delete**  
  Remove invalid or contradictory events.

- **Replace**  
  Replace entire lineage segments with canonical versions.

- **Reorder**  
  Apply deterministic topological ordering.

All operations must be deterministic, lineage‑anchored, and replay‑equivalent.

## Mermaid Diagram — Rewrite Executor & Canonical State Rebuilder

```mermaid
flowchart LR

    subgraph Inputs["Rewrite Inputs"]
        IN_PLAN["Deterministic Rewrite Plan"]
        IN_CAN["Canonical Lineage"]
        IN_META["Constitutional Metadata"]
    end

    subgraph Executor["Rewrite Executor"]
        LOAD["Rewrite Operation Loader"]
        REW["Event Rewriter"]
        VAL["Rewrite Validator"]
        TICK["Commit‑Tick Aligner"]
        COM["Rewrite Committer"]
    end

    subgraph Rebuilder["Canonical State Rebuilder"]
        RESET["State Reset Engine"]
        REP["Event Replayer"]
        META["Metadata Reconstructor"]
        DEP["Dependency Graph Rebuilder"]
        ACT["Activation Schedule Rebuilder"]
        SYN["Cluster Synchronizer"]
        AUD["Rebuild Recorder"]
    end

    subgraph Outputs["Rewrite Outputs"]
        OUT_LIN["Rewritten Lineage"]
        OUT_STATE["Canonical Governance State"]
        OUT_AUD["Rewrite/Rebuild Lineage Events"]
    end

    IN_PLAN --> LOAD --> REW --> VAL --> TICK --> COM --> OUT_LIN
    COM --> RESET --> REP --> META --> DEP --> ACT --> SYN --> OUT_STATE
    SYN --> AUD --> OUT_AUD
