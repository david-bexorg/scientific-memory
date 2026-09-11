# Shared scientific memory

Questions, claims, evidence and sources. All evidence sources cite exact LaminDB artifacts.

## Active questions

- [[QUE-001_canonical_cortex_sample_metadata]]: Which Cortex artifacts are the current sample and perfusion metadata sources?
- [[QUE-9cb01101fcc84a19a2d4a59a4c02f49c]]: Does human donor age change over calendar time?
- [[QUE-789b42f8e971412c97d0d8013345a958]]: What is the average brain flow in hours 6-12 for the last 30 perfusions?

## Claims

- [[CLM-001_stage3_sample_wide_is_current_sample_grain]] (supported, moderate): Stage 3 `sample_wide` is the current sample-grain table.
- [[CLM-002_silver_sample_metadata_is_not_equivalent]] (supported, moderate): June `silver_sample_metadata` is still latest on its key but is not equivalent.
- [[CLM-ee9f6c31c96d4c42879799889d9ad679]] (inconclusive, moderate): Donor age versus calendar time is specification-dependent in the 2026-09-11 HumanBrainProfile snapshot.
- [[CLM-9e7636eb9fbe4b35ab7018f0ebd368fc]] (supported, moderate): Mean BOS `brain_flow_measured` in hours 6-12 after connection is 161.66 on 24 of 30 recent perfusions.

## Pinned identities as of 2026-09-11

| Role | Key | UID |
|---|---|---|
| Current sample grain (label) | `silver/cortex_tiered/stage3/label/sample_wide.parquet` | `ymCWXt7cf6ZmzLpJ001O` |
| Current sample grain (code) | `silver/cortex_tiered/stage3/code/sample_wide.parquet` | `Ovhduhgw84jZgb6V001O` |
| Current perfusion grain (label) | `silver/cortex_tiered/stage3/label/perfusion_wide.parquet` | `3iT9wimnEbhx4oPs001Q` |
| Deprecated sample snapshot | `silver/cortex_metadata/silver_sample_metadata.parquet` | `WeLk7yZ5hvZSwMTl000N` |
| Inventory output | `research/runs/Phlz7GaqR7YqX8h3/inventory.json` | `ryrBa58bwN7SAA690000` |
| Current perfusion grain (code) | `silver/cortex_tiered/stage3/code/perfusion_wide.parquet` | `8ukQHk0n1XrM22ll001Q` |
| Brain-flow hours 6-12 summary | `research/runs/NJpejIJdRfiJwFJb/brain_flow_hours_6_12_summary.json` | `93BMNghm4JOGOVZE0000` |
| Brain-flow hours 6-12 per-perfusion | `research/runs/NJpejIJdRfiJwFJb/brain_flow_hours_6_12_per_perfusion.parquet` | `RxFRfdQEvhaM3pMY0000` |

Re-resolve logical keys before using them as if they were still latest. Yesterday's DOX-001 source `ymCWXt7cf6ZmzLpJ001N` is already not current.
