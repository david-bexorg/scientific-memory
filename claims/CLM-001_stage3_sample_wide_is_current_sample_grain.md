---
type: claim
id: CLM-001_stage3_sample_wide_is_current_sample_grain
answers: "[[QUE-001_canonical_cortex_sample_metadata]]"
status: supported
confidence: moderate
direction: positive
created: 2026-09-11
---
# @Claim: Current sample-grain Cortex metadata is stage 3 sample_wide, not the June silver snapshot

### Summary
As of 2026-09-11, the latest `silver/cortex_tiered/stage3/label/sample_wide.parquet`
(`ymCWXt7cf6ZmzLpJ001O`) and matching code table (`Ovhduhgw84jZgb6V001O`) each
contain 96,042 unique `sample_id` rows and 804 `perfusion_id` values. These are
the current sample-grain tables to join from. This does not assert biological
effects, completeness of `donor_id`, or that upstream Dagster runs finished
cleanly.

### Supporting Evidence
- [[EVD-001_stage3_sample_counts]]: 96,042 sample rows on today's stage 3 label and code tables, with identical `sample_id` sets.

### Opposing / Caveat Evidence
- [[EVD-003_join_and_lineage_limits]]: `donor_id` is missing on 24,608 sample rows; sample vs perfusion identifier sets are not nested subsets; upstream producing runs are not `completed`.

### Mechanistic Interpretation
"Current" here means the latest stored stage 3 artifacts loaded on 2026-09-11,
not a re-derivation from Cortex. Confidence is moderate because the counts are
from pinned bytes, but the silver pipeline's producing runs remain
`scheduled`. Logical keys must be re-resolved: yesterday's
`ymCWXt7cf6ZmzLpJ001N` is already not latest.
