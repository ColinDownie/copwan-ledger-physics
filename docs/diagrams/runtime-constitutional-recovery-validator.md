# Deterministic Recovery Validator — Internal Architecture

This diagram specifies the **recovery validator** and the
**invariant‑restoration model** that determine when the constitutional subsystem
has returned to a valid, deterministic, replay‑safe state.

The validator MUST satisfy:

- deterministic invariant evaluation
- deterministic dependency revalidation
- deterministic lineage integrity checks
- deterministic metadata consistency checks
- deterministic replay‑safety verification
- deterministic cluster symmetry

No nondeterministic recovery evaluation is permitted.

## Recovery Validator Components

- **Invariant Scanner**  
  Recomputes all constitutional invariants deterministically.

- **Dependency Revalidator**  
  Rebuilds and revalidates the dependency graph.

- **Lineage Integrity Checker**  
  Ensures lineage is continuous, reconstructable, and replay‑safe.

- **Metadata Consistency Checker**  
  Ensures schema, version, identity, policy, config, and lawRef metadata align.

- **Replay‑Safety Verifier**  
  Ensures replay produces identical governance state.

- **Recovery Decision Engine**  
  Determines whether invariants are restored.

- **Lineage Recorder**  
  Emits replay‑visible recovery events.

## Constitutional Invariants Revalidated

- **Acyclic Dependency Graph**  
  No cycles permitted.

- **Schema/Version Compatibility**  
  Schema evolution must match version transitions.

- **Identity/Activation Validity**  
  Identity metadata must satisfy activation rules.

- **Policy Consistency**  
  No contradictory or overlapping policy rules.

- **LawRef Consistency**  
  LawRefs must map deterministically to governance rules.

- **Lineage Continuity**  
  Lineage must be reconstructable from genesis to present.

- **Cluster Symmetry**  
  All clusters must hold identical governance state.

## Mermaid Diagram — Recovery Validator & Invariant‑Restoration Model

```mermaid
flowchart LR

    subgraph Inputs["Recovery Inputs"]
        IN_STATE["Governance State"]
        IN_META["Constitutional Metadata"]
        IN_LIN["Lineage History"]
        IN_GRAPH["Dependency Graph"]
    end

    subgraph Validator["Recovery Validator"]
        INV["Invariant Scanner"]
        DEP["Dependency Revalidator"]
        LINCHK["Lineage Integrity Checker"]
        META["Metadata Consistency Checker"]
        REP["Replay‑Safety Verifier"]
        DEC["Recovery Decision Engine"]
        REC["Lineage Recorder"]
    end

    subgraph Outputs["Recovery Outputs"]
        OUT_OK["Recovery Approved"]
        OUT_FAIL["Recovery Denied"]
        OUT_AUD["Recovery Lineage Events"]
    end

    IN_STATE --> INV --> DEP --> LINCHK --> META --> REP --> DEC
    DEC --> OUT_OK
    DEC --> OUT_FAIL
    DEC --> REC --> OUT_AUD
