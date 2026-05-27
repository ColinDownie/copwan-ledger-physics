# Deterministic Genesis Event Injector & Root‑Lineage Model — Internal Architecture

This diagram specifies the **genesis event injector** and the
**root‑lineage model**, which together define the deterministic origin of the
constitutional timeline.

The genesis injector MUST satisfy:

- deterministic genesis event construction
- deterministic root‑lineage anchoring
- deterministic metadata initialization
- deterministic replay equivalence
- deterministic cluster symmetry
- deterministic immutability of genesis

No nondeterministic genesis behavior is permitted.

## Genesis Event Injector Components

- **Genesis Template Loader**  
  Loads the immutable genesis template (schema 0, version 0, identity root).

- **Genesis Event Constructor**  
  Constructs deterministic genesis events from the template.

- **Genesis Metadata Initializer**  
  Initializes constitutional metadata to genesis definitions.

- **Genesis Lineage Anchor**  
  Creates the root lineage anchor (L0).

- **Genesis Committer**  
  Commits genesis events to lineage deterministically.

- **Genesis Recorder**  
  Emits replay‑visible genesis events.

## Root‑Lineage Model Components

- **Root Event Sequencer**  
  Orders genesis events deterministically.

- **Root Hash Generator**  
  Computes deterministic hash of the genesis lineage.

- **Root Integrity Validator**  
  Ensures genesis lineage satisfies constitutional invariants.

- **Root State Builder**  
  Constructs the initial governance state from genesis lineage.

- **Cluster Genesis Synchronizer**  
  Ensures all clusters start from identical genesis state.

- **Root Recorder**  
  Emits lineage events for root‑state construction.

## Deterministic Genesis Template

The genesis template includes:

- **schema version 0**  
- **constitutional metadata v0**  
- **identity root key**  
- **empty policy set**  
- **empty config set**  
- **empty dependency graph**  
- **empty activation schedule**  
- **genesis lineage anchor (L0)**  
- **genesis timestamp = logical tick 0**  

This template MUST be identical across all clusters and all time.

## Mermaid Diagram — Genesis Event Injector & Root‑Lineage Model

```mermaid
flowchart LR

    subgraph Inputs["Genesis Inputs"]
        IN_TMP["Genesis Template"]
        IN_META["Genesis Metadata"]
    end

    subgraph Injector["Genesis Event Injector"]
        TMP["Genesis Template Loader"]
        CON["Genesis Event Constructor"]
        MINIT["Genesis Metadata Initializer"]
        ANCH["Genesis Lineage Anchor"]
        COM["Genesis Committer"]
        AUD["Genesis Recorder"]
    end

    subgraph Root["Root‑Lineage Model"]
        SEQ["Root Event Sequencer"]
        HASH["Root Hash Generator"]
        VAL["Root Integrity Validator"]
        BUILD["Root State Builder"]
        SYN["Cluster Genesis Synchronizer"]
        RAUD["Root Recorder"]
    end

    subgraph Outputs["Genesis Outputs"]
        OUT_LIN["Root Lineage (L0)"]
        OUT_STATE["Genesis Governance State"]
        OUT_AUD["Genesis Lineage Events"]
    end

    IN_TMP --> TMP --> CON --> MINIT --> ANCH --> COM --> OUT_LIN
    COM --> SEQ --> HASH --> VAL --> BUILD --> SYN --> OUT_STATE
    SYN --> RAUD --> OUT_AUD
    AUD --> OUT_AUD
