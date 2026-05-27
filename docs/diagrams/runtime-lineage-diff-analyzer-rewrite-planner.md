# Deterministic Lineage Diff Analyzer & Rewrite Planning Model — Internal Architecture

This diagram specifies the **lineage diff analyzer** and the
**rewrite planning engine**, which together compute deterministic diffs between
canonical and non‑canonical lineages and produce a deterministic rewrite plan.

The system MUST satisfy:

- deterministic diff computation
- deterministic rewrite planning
- deterministic rewrite ordering
- deterministic lineage reconstruction
- deterministic replay equivalence
- deterministic cluster symmetry

No nondeterministic lineage rewriting is permitted.

## Lineage Diff Analyzer Components

- **Lineage Normalizer**  
  Converts lineage into canonical, comparable form.

- **Event Comparator**  
  Compares lineage events deterministically.

- **Diff Generator**  
  Produces deterministic diffs between canonical and non‑canonical lineages.

- **Conflict Detector**  
  Identifies conflicting or invalid lineage segments.

- **Diff Classifier**  
  Categorizes diffs (missing events, extra events, reordered events, invalid events).

## Rewrite Planning Components

- **Rewrite Strategy Engine**  
  Selects deterministic rewrite strategy (patch, rollback, replace).

- **Rewrite Sequencer**  
  Orders rewrite operations deterministically.

- **Rewrite Validator**  
  Ensures rewrite plan satisfies constitutional invariants.

- **Rewrite Commit Planner**  
  Determines deterministic commit ticks for rewrite operations.

- **Rewrite Recorder**  
  Emits replay‑visible rewrite planning events.

## Deterministic Rewrite Strategies

- **Patch**  
  Insert missing events or remove invalid ones.

- **Rollback**  
  Revert lineage to nearest valid canonical point.

- **Replace**  
  Replace entire lineage segment with canonical version.

Strategy selection is deterministic and lineage‑anchored.

## Mermaid Diagram — Lineage Diff Analyzer & Rewrite Planning Model

```mermaid
flowchart LR

    subgraph Inputs["Lineage Inputs"]
        IN_CAN["Canonical Lineage"]
        IN_NON["Non‑Canonical Lineage"]
        IN_META["Constitutional Metadata"]
    end

    subgraph Diff["Lineage Diff Analyzer"]
        NORM["Lineage Normalizer"]
        COMP["Event Comparator"]
        DIFF["Diff Generator"]
        CON["Conflict Detector"]
        CLASS["Diff Classifier"]
    end

    subgraph Planner["Rewrite Planning Engine"]
        STRAT["Rewrite Strategy Engine"]
        SEQ["Rewrite Sequencer"]
        VAL["Rewrite Validator"]
        COM["Rewrite Commit Planner"]
        AUD["Rewrite Recorder"]
    end

    subgraph Outputs["Rewrite Outputs"]
        OUT_PLAN["Deterministic Rewrite Plan"]
        OUT_AUD["Rewrite Lineage Events"]
    end

    IN_CAN --> NORM --> COMP --> DIFF --> CON --> CLASS --> STRAT --> SEQ --> VAL --> COM --> OUT_PLAN
    COM --> AUD --> OUT_AUD
