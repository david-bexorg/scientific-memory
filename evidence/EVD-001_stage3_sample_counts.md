---
type: evidence
id: EVD-001_stage3_sample_counts
supports:
  - "[[CLM-001_stage3_sample_wide_is_current_sample_grain]]"
opposes: []
source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
modality: datalake_inventory
target_gene: null
p_value: null
log2_fc: null
biological_n: null
observation_locator: "inventory.json artifacts[role=stage3_label_sample_wide|stage3_code_sample_wide|yesterday_stage3_label_sample_wide] and code_and_label_sample_ids_equal / sample_id_added_since_yesterday; companion table t9cGe6iG56cZ9FVX0000 is the same run"
verification:
  - claim: "[[CLM-001_stage3_sample_wide_is_current_sample_grain]]"
    relation: supports
    determination: verified
    checked_at: 2026-09-11
    checked_by: Cursor agent using bexorg-research (agent-reviewed, not human-endorsed)
    claim_statement: Current sample-grain Cortex metadata is stage 3 sample_wide (today's label/code UIDs), not the June silver snapshot.
    evidence_statement: Loaded label sample_wide ymCWXt7cf6ZmzLpJ001O has 96042 unique sample_id and 804 perfusion_id; code sample_wide Ovhduhgw84jZgb6V001O has the same sample_id set; yesterday's ymCWXt7cf6ZmzLpJ001N had 96030 sample_id with 12 added and 0 removed.
    context: Human Cortex metadata tables in anonymous/bexorg-ai-datalake, as-of 2026-09-11, sample grain = one row per sample_id.
    sources_checked:
      - source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
        record: "ryrBa58bwN7SAA690000"
        locator: artifacts rows for stage3_label_sample_wide, stage3_code_sample_wide, yesterday_stage3_label_sample_wide; fields rows, sample_id_unique, code_and_label_sample_ids_equal, sample_id_added_since_yesterday
        version: "run Phlz7GaqR7YqX8h3, sha256 4d6df9daee35f4ca5710cac072841f91cf5e13c6b488e9afecd068f8d7488d37"
    source_fidelity: The JSON reports those exact counts and that code/label sample_id sets are equal. The producing analysis loaded the named UIDs rather than re-querying by logical key after the fact.
    claim_fit: The counts identify which stored tables currently hold sample grain and that the UID moved overnight. They do not prove therapeutic effects or that every row is a biologically independent unit.
    limitations:
      - Upstream silver Run.status was scheduled, not completed.
      - Live-currentness requires re-resolving the logical key after the next daily rebuild.
    freshness: Frozen output of run Phlz7GaqR7YqX8h3; refresh when asking whether these UIDs are still latest.
created: 2026-09-11
---
# @Evidence: Stage 3 sample_wide currently has 96,042 sample_id rows (12 more than yesterday)

- **Experimental Context:** Stored Cortex metadata in `anonymous/bexorg-ai-datalake`, not an assay.
- **Perturbation / Exposure:** None. This is an identity inventory of pinned artifact versions.
- **Quantitative Findings:**
  - Today's label `sample_wide` (`ymCWXt7cf6ZmzLpJ001O`): 96,042 rows / unique `sample_id`, 804 `perfusion_id`, 65 columns, `is_latest=true`, created 2026-09-11 07:04 UTC.
  - Today's code `sample_wide` (`Ovhduhgw84jZgb6V001O`): same 96,042 `sample_id` set.
  - Yesterday's label version (`ymCWXt7cf6ZmzLpJ001N`): 96,030 `sample_id`; 12 added, 0 removed.
- **Observation:** The current sample-grain tables are the stage 3 code/label `sample_wide` pair. A graph that pinned yesterday's UID is already one version behind.
- **Methodological Caveats:** Counts are from loaded parquet bytes. Independent experimental unit for later biological contrasts is not `sample_id` by default; `donor_id` is incomplete.

### Evidence-to-Claim Verification
Source fidelity and claim fit for [[CLM-001_stage3_sample_wide_is_current_sample_grain]] were checked against the published inventory JSON on 2026-09-11.
