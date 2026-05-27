# Deterministic Constitutional Rejection Engine — Internal Architecture

This diagram specifies the **rejection engine** and the **governance failure‑mode
model** that ensure the system rejects illegal, ambiguous, or nondeterministic
constitutional changes in a deterministic, lineage‑anchored manner.

The rejection engine MUST satisfy:

- deterministic rejection criteria
- deterministic failure classification
- deterministic fallback behavior
- deterministic lineage anchoring
- deterministic replay equivalence
- deterministic cluster symmetry

No nondeterministic failure behavior is permitted.

## Rejection Engine Components

- **Violation Detector**  
  Identifies violations of constitutional invariants.

- **Failure Classifier**  
  Categorizes failures deterministically (schema, version, identity, policy, lawRef).

- **Fallback Planner**  
  Determines deterministic fallback actions (rollback, quarantine, freeze).

- **Rollback Engine**  
  Performs deterministic rollback to last valid lineage point.

- **Quarantine Engine**  
  Isolates invalid governance changes deterministically.

- **Freeze Engine**  
  Freezes constitutional evolution until invariants are restored.

- **Lineage Recorder**  
  Emits replay‑visible lineage events for all rejections and fallbacks.

## Failure‑Mode Categories

- **Schema Violation**  
  Schema change incompatible with constitutional metadata.

- **Version Violation**  
  Version transition invalid or out of order.

- **Identity Violation**  
  Key rotation or identity change violates lineage or activation rules.

- **Policy Violation**  
  Policy contradicts existing policy or constitutional constraints.

- **LawRef Violation**  
  LawRef change invalidates dependent governance rules.

- **Dependency Violation**  
  Change violates dependency graph ordering.

## Deterministic Fallback Actions

- **Rollback**  
  Revert to last valid lineage point.

- **Quarantine**  
  Isolate invalid change; prevent propagation.

- **Freeze**  
  Halt constitutional evolution until invariants restored.

- **Reject**  
  Fully reject change; emit deterministic rejection event.

## Mermaid Diagram — Constitutional Rejection Engine & Failure‑Mode Model

```mermaid
flowchart LR

    subgraph Inputs["Rejection Inputs"]
        IN_CHG["Constitutional Change"]
        IN_RULES["Unified Governance Rules"]
        IN_META["Constitutional Metadata"]
        IN_GRAPH["Dependency Graph"]
    end

    subgraph Engine["Rejection Engine"]
        DET["Violation Detector"]
        CLASS["Failure Classifier"]
        PLAN["Fallback Planner"]
        ROLL["Rollback Engine"]
        QUAR["Quarantine Engine"]
        FRZ["Freeze Engine"]
        LIN["Lineage Recorder"]
    end

    subgraph Outputs["Rejection Outputs"]
        OUT_REJ["Rejected Change"]
        OUT_FALL["Fallback Action"]
        OUT_AUD["Rejection Lineage Events"]
    end

    IN_CHG --> DET --> CLASS --> PLAN
    PLAN --> ROLL --> OUT_FALL
    PLAN --> QUAR --> OUT_FALL
    PLAN --> FRZ --> OUT_FALL

    CLASS --> OUT_REJ
    PLAN --> LIN --> OUT_AUD
