---
type: question
id: QUE-001_canonical_cortex_sample_metadata
status: answered
priority: high
tags:
  - cortex
  - metadata
  - lamindb
  - sample-identity
created: 2026-09-11
---
# @Question: Which Cortex artifacts are the current sample and perfusion metadata sources?

### Context & Objective
Agents and notes still disagree. The knowledge base lists
`silver/cortex_metadata/silver_sample_metadata.parquet` as canonical, while
internal Cortex-tiered notes mark that key deprecated in favor of
`silver/cortex_tiered/stage3/{code,label}/sample_wide.parquet` and
`perfusion_wide.parquet`. Joins, Neurolens metadata projection, and DOX-001
graphs all depend on pinning the live version UIDs rather than a logical key.

This question is about **which stored tables currently carry sample and
perfusion identity**, not about drug effects or assay outcomes.

### Candidate Claims
- [[CLM-001_stage3_sample_wide_is_current_sample_grain]]: Stage 3 `sample_wide` is the current sample-grain table.
- [[CLM-002_silver_sample_metadata_is_not_equivalent]]: The still-latest deprecated silver snapshot is not a drop-in equivalent.

### Synthesis & Conclusion
As of 2026-09-11, use the pinned stage 3 UIDs below for sample/perfusion
identity. Do not treat `is_latest` on the June silver snapshot as currency.
Re-resolve UIDs when the live table matters: this morning's rebuild already
added 12 `sample_id` values versus yesterday's version cited in the DOX-001
graph (`ymCWXt7cf6ZmzLpJ001N`).
