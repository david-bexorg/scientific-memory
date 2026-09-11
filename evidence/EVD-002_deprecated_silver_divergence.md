---
type: evidence
id: EVD-002_deprecated_silver_divergence
supports:
  - "[[CLM-002_silver_sample_metadata_is_not_equivalent]]"
opposes: []
source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
modality: datalake_inventory
target_gene: null
p_value: null
log2_fc: null
biological_n: null
observation_locator: "inventory.json artifacts[role=deprecated_silver_sample_metadata] plus sample_id_overlap_stage3_vs_deprecated / sample_id_only_stage3 / sample_id_only_deprecated"
verification:
  - claim: "[[CLM-002_silver_sample_metadata_is_not_equivalent]]"
    relation: supports
    determination: verified
    checked_at: 2026-09-11
    checked_by: Cursor agent using bexorg-research (agent-reviewed, not human-endorsed)
    claim_statement: Latest silver_sample_metadata is a stale June snapshot and is not equivalent to stage 3 sample_wide.
    evidence_statement: WeLk7yZ5hvZSwMTl000N remains is_latest on silver/cortex_metadata/silver_sample_metadata.parquet with 80557 unique sample_id, created 2026-06-23; overlap with today's stage 3 sample_id set is 80393; 15649 sample_id values are only in stage 3 and 164 are only in the June snapshot.
    context: Same datalake instance, sample_id string comparison of two pinned tables as of 2026-09-11.
    sources_checked:
      - source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
        record: "ryrBa58bwN7SAA690000"
        locator: artifacts[role=deprecated_silver_sample_metadata]; sample_id_overlap_stage3_vs_deprecated; sample_id_only_stage3; sample_id_only_deprecated
        version: "run Phlz7GaqR7YqX8h3, sha256 4d6df9daee35f4ca5710cac072841f91cf5e13c6b488e9afecd068f8d7488d37"
    source_fidelity: The JSON reports created_at 2026-06-23, 80557 rows, is_latest true, and the three set-difference counts above.
    claim_fit: Non-identical sample_id sets show the June key is not a substitute for stage 3 identity. The observation does not decide which extra IDs are biologically valid.
    limitations:
      - Set difference is not a clinical or QC judgment on the extra rows.
      - Deprecated table has 311 columns vs 65 on stage 3; schema mismatch is additional, not quantified here beyond column counts.
    freshness: Frozen output of run Phlz7GaqR7YqX8h3.
created: 2026-09-11
---
# @Evidence: June silver_sample_metadata still latest on its key, but 15,649 sample_ids exist only in stage 3

- **Experimental Context:** Stored Cortex metadata comparison, sample grain.
- **Perturbation / Exposure:** None.
- **Quantitative Findings:**
  - Deprecated snapshot (`WeLk7yZ5hvZSwMTl000N`): 80,557 unique `sample_id`, 744 `perfusion_id`, 311 columns, created 2026-06-23, still `is_latest` on that key.
  - Overlap with today's stage 3 `sample_id` set: 80,393.
  - Only in stage 3: 15,649. Only in the June snapshot: 164.
- **Observation:** Keeping `silver_sample_metadata` as the canonical join table drops a large post-June sample set and retains 164 IDs absent from stage 3.
- **Methodological Caveats:** No attempt to classify the 164 deprecated-only IDs as errors versus retired samples.

### Evidence-to-Claim Verification
Source fidelity and claim fit for [[CLM-002_silver_sample_metadata_is_not_equivalent]] were checked against the published inventory JSON on 2026-09-11.
