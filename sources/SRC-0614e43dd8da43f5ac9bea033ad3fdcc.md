---
type: source
id: SRC-0614e43dd8da43f5ac9bea033ad3fdcc
title: Tracked inventory of current vs deprecated Cortex metadata artifacts (2026-09-11)
date: 2026-09-11
authors: []
uri: "s3://bexorg-ai-datalake/research/runs/Phlz7GaqR7YqX8h3/inventory.json"
doi_or_pmid: null
source_version: "run Phlz7GaqR7YqX8h3 / transform XBfnel0Ad5cP0000"
retrieved_at: 2026-09-11
artifact:
  instance: anonymous/bexorg-ai-datalake
  uid: ryrBa58bwN7SAA690000
  key: research/runs/Phlz7GaqR7YqX8h3/inventory.json
  hash: HyJmQUQIWGzcVGYZxmdhOQ
  sha256: 4d6df9daee35f4ca5710cac072841f91cf5e13c6b488e9afecd068f8d7488d37
  run_uid: Phlz7GaqR7YqX8h3
  transform_uid: XBfnel0Ad5cP0000
source_kind: data
acquisition_artifact: null
---
# @Source: Cortex metadata identity inventory (2026-09-11)

### Summary & Provenance
Tracked LaminDB run `Phlz7GaqR7YqX8h3` of transform `XBfnel0Ad5cP0000`
(`inventory_cortex_metadata.py`) loaded five pinned parquet versions from
`anonymous/bexorg-ai-datalake` and wrote identifier counts plus set-overlap
statistics. This JSON is the analysis output, not a Cortex rebuild. A companion
table from the same run is `t9cGe6iG56cZ9FVX0000`
(`research/runs/Phlz7GaqR7YqX8h3/artifact_rows.parquet`); it is the same
underlying inventory, not independent evidence.

Pinned inputs (logical keys resolved once):
- `ymCWXt7cf6ZmzLpJ001O` — `silver/cortex_tiered/stage3/label/sample_wide.parquet`
- `Ovhduhgw84jZgb6V001O` — `silver/cortex_tiered/stage3/code/sample_wide.parquet`
- `3iT9wimnEbhx4oPs001Q` — `silver/cortex_tiered/stage3/label/perfusion_wide.parquet`
- `WeLk7yZ5hvZSwMTl000N` — `silver/cortex_metadata/silver_sample_metadata.parquet`
- `ymCWXt7cf6ZmzLpJ001N` — previous version of stage3 label `sample_wide`

### Verification Provenance
Bytes and producing run of this JSON were read back at
`2026-09-11T14:23:30.717804+00:00` (`sha256`
`4d6df9daee35f4ca5710cac072841f91cf5e13c6b488e9afecd068f8d7488d37`).
Upstream silver artifacts had producing `Run.status` of `scheduled` or
`started`, so they were used as frozen inputs and were not registered as
verified Sources.
