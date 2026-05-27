# Deterministic Fallback Planner & Rollback Lineage Model — Internal Architecture

This diagram specifies the **fallback planner** and the **rollback lineage model**
that govern how the system deterministically recovers from constitutional
violations, conflicts, or illegal governance states.

The fallback planner MUST satisfy:

- deterministic fallback selection
- deterministic rollback target selection
- deterministic lineage restoration
- deterministic quarantine behavior
- deterministic freeze behavior
- deterministic replay equivalence
- deterministic cluster symmetry

No nondeterministic recovery behavior is permitted.

## Fallback Planner Components

- **Failure Context Analyzer**  
  Extracts deterministic context from the violation.

- **Fallback Selector**  
  Chooses deterministic fallback mode (rollback, quarantine, freeze).

- **Rollback Target Resolver**  
  Determines deterministic lineage point to revert to.

- **Rollback Executor**  
  Performs deterministic rollback of governance state.

- **Quarantine Manager**  
  Isolates invalid changes deterministically.

- **Freeze Controller**  
  Freezes constitutional evolution deterministically.

- **Lineage Restorer**  
  Reconstructs lineage to the rollback target deterministically.

- **Lineage Recorder**  
  Emits replay‑visible lineage events for all fallback actions.

## Fallback Modes

- **Rollback**  
  Revert to last valid lineage point.

- **Quarantine**  
  Isolate invalid change; prevent propagation.

- **Freeze**  
  Halt constitutional evolution until invariants restored.

## Rollback Lineage Model

Rollback MUST:

- revert to the **nearest valid lineage point**  
- restore **all governance stores** to that point  
- restore **schema**, **version**, **identity**, **policy**, **config**  
- restore **dependency graph**  
- restore **activation schedule**  
- restore **constitutional metadata**  
- restore **LawRef index**  
- restore **cluster symmetry**  
- be **replay‑equivalent**  

## Mermaid Diagram — Fallback Planner & Rollback Lineage Model

```mermaid
flowchart LR

    subgraph Inputs["Fallback Inputs"]
        IN_FAIL["Failure Context"]
        IN_RULES["Unified Governance Rules"]
        IN_META["Constitutional Metadata"]
        IN_LIN["Lineage History"]
    end

    subgraph Planner["Fallback Planner"]
        CTX["Failure Context Analyzer"]
        SEL["Fallback Selector"]
        TGT["Rollback Target Resolver"]
        REX["Rollback Executor"]
        QMN["Quarantine Manager"]
        FRZ["Freeze Controller"]
        LRS["Lineage Restorer"]
        LIN["Lineage Recorder"]
    end

    subgraph Outputs["Fallback Outputs"]
        OUT_ACT["Fallback Action"]
        OUT_LIN["Updated Lineage"]
        OUT_AUD["Fallback Lineage Events"]
    end

    IN_FAIL --> CTX --> SEL
    SEL --> TGT --> REX --> LRS --> OUT_LIN
    SEL --> QMN --> OUT_ACT
    SEL --> FRZ --> OUT_ACT

    LRS --> LIN --> OUT_AUD
