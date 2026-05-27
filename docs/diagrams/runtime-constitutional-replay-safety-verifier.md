# Deterministic Replay‑Safety Verifier — Internal Architecture

This diagram specifies the **replay‑safety verifier** and the
**global convergence model** that ensure all clusters converge to the same
constitutional state under replay, recovery, or cold‑start reconstruction.

The verifier MUST satisfy:

- deterministic replay evaluation
- deterministic lineage reconstruction
- deterministic state comparison
- deterministic divergence detection
- deterministic convergence enforcement
- deterministic cluster symmetry

No nondeterministic replay behavior is permitted.

## Replay‑Safety Verifier Components

- **Lineage Reconstructor**  
  Rebuilds governance state from lineage deterministically.

- **State Replayer**  
  Replays constitutional events deterministically.

- **State Comparator**  
  Compares replayed state vs. live state deterministically.

- **Divergence Detector**  
  Identifies any mismatch between replayed and live state.

- **Convergence Enforcer**  
  Forces deterministic convergence or triggers constitutional freeze.

- **Replay Auditor**  
  Records replay‑visible events for audit and verification.

- **Cluster Symmetry Checker**  
  Ensures all clusters converge to identical state.

## Global Convergence Requirements

Replay MUST reconstruct:

- **governance rule stores**  
- **constitutional metadata**  
- **schema version graph**  
- **identity and key lineage**  
- **policy and config state**  
- **LawRef index**  
- **dependency graph**  
- **activation schedule**  
- **freeze state**  
- **fallback history**  

Replay MUST produce:

- identical state across clusters  
- identical lineage  
- identical ordering  
- identical activation ticks  
- identical dependency graph  
- identical metadata  

## Mermaid Diagram — Replay‑Safety Verifier & Global Convergence Model

```mermaid
flowchart LR

    subgraph Inputs["Replay Inputs"]
        IN_LIN["Lineage History"]
        IN_STATE["Live Governance State"]
        IN_META["Constitutional Metadata"]
        IN_GRAPH["Dependency Graph"]
    end

    subgraph Verifier["Replay‑Safety Verifier"]
        REC["Lineage Reconstructor"]
        REP["State Replayer"]
        CMP["State Comparator"]
        DIV["Divergence Detector"]
        ENF["Convergence Enforcer"]
        AUD["Replay Auditor"]
        SYM["Cluster Symmetry Checker"]
    end

    subgraph Outputs["Replay Outputs"]
        OUT_OK["Replay‑Safe"]
        OUT_FAIL["Replay Divergence"]
        OUT_AUD["Replay Lineage Events"]
    end

    IN_LIN --> REC --> REP --> CMP --> DIV --> ENF --> SYM --> OUT_OK
    SYM --> OUT_FAIL
    ENF --> AUD --> OUT_AUD
