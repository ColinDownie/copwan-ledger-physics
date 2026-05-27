# Deterministic Global Symmetry Analyzer — Internal Architecture

This diagram specifies the **global symmetry analyzer** and the
**canonical state selection model** that determine the authoritative
constitutional state when clusters disagree.

The analyzer MUST satisfy:

- deterministic canonical‑state computation
- deterministic divergence classification
- deterministic state‑ranking rules
- deterministic lineage‑anchored selection
- deterministic replay equivalence
- deterministic cluster symmetry

No nondeterministic canonical‑state selection is permitted.

## Symmetry Analyzer Components

- **State Normalizer**  
  Converts each cluster’s state into canonical form.

- **State Hasher**  
  Computes deterministic hashes of normalized states.

- **Divergence Classifier**  
  Categorizes differences deterministically.

- **Canonical State Selector**  
  Selects the authoritative state using deterministic ranking rules.

- **Lineage Harmonizer**  
  Aligns lineage to the canonical state.

- **Cluster Rewriter**  
  Rewrites all non‑canonical clusters to the canonical state.

- **Symmetry Recorder**  
  Emits replay‑visible symmetry events.

## Canonical State Selection Rules

Canonical state is selected by:

1. **Lineage Depth**  
   Deepest valid lineage wins.

2. **Lineage Integrity**  
   If depths equal, lineage with highest integrity score wins.

3. **Metadata Consistency**  
   If integrity equal, metadata‑consistent state wins.

4. **Activation Alignment**  
   If metadata equal, state with earliest valid activation tick wins.

5. **Hash Ordering**  
   If all else equal, lexicographically smallest state hash wins.

These rules guarantee:

- determinism  
- replay‑equivalence  
- cluster symmetry  
- no forks  

## Mermaid Diagram — Global Symmetry Analyzer & Canonical State Selection Model

```mermaid
flowchart LR

    subgraph Inputs["Symmetry Inputs"]
        IN_STATES["Cluster States"]
        IN_LIN["Lineage Histories"]
        IN_META["Constitutional Metadata"]
    end

    subgraph Analyzer["Global Symmetry Analyzer"]
        NORM["State Normalizer"]
        HASH["State Hasher"]
        DIV["Divergence Classifier"]
        SEL["Canonical State Selector"]
        HAR["Lineage Harmonizer"]
        REW["Cluster Rewriter"]
        AUD["Symmetry Recorder"]
    end

    subgraph Outputs["Symmetry Outputs"]
        OUT_CAN["Canonical Constitutional State"]
        OUT_REW["Rewritten Cluster States"]
        OUT_AUD["Symmetry Lineage Events"]
    end

    IN_STATES --> NORM --> HASH --> DIV --> SEL --> HAR --> REW --> OUT_REW
    SEL --> OUT_CAN
    REW --> AUD --> OUT_AUD
