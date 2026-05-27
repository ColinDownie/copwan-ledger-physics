# Deterministic State Reset Engine & Genesis‑Reconstruction Model — Internal Architecture

This diagram specifies the **state reset engine** and the
**genesis‑reconstruction model**, which together reset the system to a
deterministic baseline and rebuild the entire constitutional state from
rewritten lineage.

The reset engine MUST satisfy:

- deterministic baseline initialization
- deterministic genesis state reconstruction
- deterministic event replay
- deterministic metadata regeneration
- deterministic dependency graph reconstruction
- deterministic activation schedule regeneration
- deterministic replay equivalence
- deterministic cluster symmetry

No nondeterministic reset or genesis reconstruction is permitted.

## State Reset Engine Components

- **Baseline Loader**  
  Loads the deterministic genesis baseline (schema 0, version 0, identity 0).

- **State Purger**  
  Removes all non‑canonical state deterministically.

- **Metadata Reset Unit**  
  Resets constitutional metadata to genesis definitions.

- **Lineage Anchor Reset**  
  Resets lineage pointers to genesis anchor.

- **Reset Validator**  
  Ensures reset state satisfies constitutional invariants.

## Genesis‑Reconstruction Components

- **Genesis Event Injector**  
  Injects deterministic genesis events.

- **Lineage Replayer**  
  Replays rewritten lineage deterministically from genesis.

- **Metadata Rebuilder**  
  Reconstructs schema, version, identity, policy, config, and lawRef metadata.

- **Dependency Graph Rebuilder**  
  Reconstructs dependency graph deterministically.

- **Activation Schedule Rebuilder**  
  Recomputes activation ticks deterministically.

- **Cluster Synchronizer**  
  Ensures all clusters rebuild to identical canonical state.

- **Reconstruction Recorder**  
  Emits replay‑visible reconstruction events.

## Deterministic Genesis Baseline

Genesis baseline includes:

- **schema version 0**  
- **constitutional metadata v0**  
- **identity root key**  
- **empty policy set**  
- **empty config set**  
- **empty dependency graph**  
- **empty activation schedule**  
- **genesis lineage anchor**  

This baseline MUST be identical across all clusters and all time.

## Mermaid Diagram — State Reset Engine & Genesis‑Reconstruction Model

```mermaid
flowchart LR

    subgraph Inputs["Reset Inputs"]
        IN_PLAN["Rewrite Plan"]
        IN_CAN["Canonical Lineage"]
        IN_META["Constitutional Metadata"]
    end

    subgraph Reset["State Reset Engine"]
        BASE["Baseline Loader"]
        PURGE["State Purger"]
        MRES["Metadata Reset Unit"]
        LRES["Lineage Anchor Reset"]
        RVAL["Reset Validator"]
    end

    subgraph Genesis["Genesis‑Reconstruction Engine"]
        GINJ["Genesis Event Injector"]
        REP["Lineage Replayer"]
        MREB["Metadata Rebuilder"]
        DREB["Dependency Graph Rebuilder"]
        AREB["Activation Schedule Rebuilder"]
        SYN["Cluster Synchronizer"]
        AUD["Reconstruction Recorder"]
    end

    subgraph Outputs["Reset Outputs"]
        OUT_STATE["Canonical Governance State"]
        OUT_LIN["Rewritten Lineage"]
        OUT_AUD["Reset/Reconstruction Lineage Events"]
    end

    IN_PLAN --> BASE --> PURGE --> MRES --> LRES --> RVAL --> GINJ --> REP --> MREB --> DREB --> AREB --> SYN --> OUT_STATE
    SYN --> AUD --> OUT_AUD
    REP --> OUT_LIN
