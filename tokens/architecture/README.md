# Woodfine Media Assets: Architecture Ledgers

**Classification:** Operational Execution, Corporate Governance, and Asset Ledgers (Customer)
**Objective:** Maintain absolute data parity and act as the Single Source of Truth for all entity registries, jurisdictional constraints, and architectural narratives prior to visual rendering.

## The Data Governance Workflow

This directory contains the immutable text assets required to build an institutional architecture. **Do not write code or touch HTML here.** This repository dictates *what* is being built; PointSav dictates *how* it looks.

### The Core Tokens
1. **`WCP-MASTER-ENTITY-REGISTRY.csv` (The Database)**
   - The universal Rolodex of all approved corporate entities, SPVs, direct-hold solutions, and administrative bodies.
   - *Data Schema:* `NODE_ID`, `ENTITY_TITLE`, `OP_CODE`, `ALIAS_OR_ROLE`, `JURISDICTION`, `TOKEN_SHAPE`, `EXTRA_METADATA_LEGAL`.
   - *Rule of Engagement:* Before adding an entity to a manifest, verify its exact legal spelling and operational code in this registry.

2. **`WCP-ARCHITECTURE-MANIFEST.txt` (The Blueprint Template)**
   - The blank text ledger used to define a new chart or transaction flow.
   - *Sections:* - `[GLOBAL_TOKENS]`: Titles, preambles, and disclaimers.
     - `[DATA_LEDGERS]`: Floating operational constraints and rules.
     - `[COMPONENT_LEDGER]`: The specific entities pulled from the Master Registry for this chart.
     - `[ROUTING_MARKERS]`: The capital and ownership vectors connecting the components.
   - *Rule of Engagement:* Fill this out entirely before opening an HTML canvas. It must be approved as structurally and legally sound before PointSav renders it.

## Execution Sequence
1. Identify the need for a new architectural diagram or transaction flow.
2. Duplicate `WCP-ARCHITECTURE-MANIFEST.txt` and assign a new Document ID.
3. Query `WCP-MASTER-ENTITY-REGISTRY.csv` to source the correct entity names and parameters.
4. Complete the manifest.
5. Transmit the finalized manifest to the engineering layer (PointSav) for HTML assembly.
