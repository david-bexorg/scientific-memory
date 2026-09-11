---
type: evidence
id: EVD-003_join_and_lineage_limits
supports: []
opposes:
  - "[[CLM-001_stage3_sample_wide_is_current_sample_grain]]"
  - "[[CLM-002_silver_sample_metadata_is_not_equivalent]]"
source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
modality: datalake_inventory
target_gene: null
p_value: null
log2_fc: null
biological_n: null
observation_locator: "inventory.json artifacts[].run_status, donor_id_nulls, perfusion_ids_only_in_sample_wide, perfusion_ids_only_in_perfusion_wide, limitations[]"
verification:
  - claim: "[[CLM-001_stage3_sample_wide_is_current_sample_grain]]"
    relation: opposes
    determination: qualified
    checked_at: 2026-09-11
    checked_by: Cursor agent using bexorg-research (agent-reviewed, not human-endorsed)
    claim_statement: Current sample-grain Cortex metadata is stage 3 sample_wide.
    evidence_statement: Stage 3 label sample_wide has donor_id null on 24608/96042 rows; 64 perfusion_id values occur only in sample_wide and 83 only in perfusion_wide (823 vs 804); all inventoried silver producing runs were scheduled or started, not completed.
    context: Identifier completeness and LaminDB run status for the same pinned tables, 2026-09-11.
    sources_checked:
      - source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
        record: "ryrBa58bwN7SAA690000"
        locator: donor_id_nulls; perfusion_ids_only_in_sample_wide; perfusion_ids_only_in_perfusion_wide; artifacts[].run_status; limitations
        version: "run Phlz7GaqR7YqX8h3, sha256 4d6df9daee35f4ca5710cac072841f91cf5e13c6b488e9afecd068f8d7488d37"
    source_fidelity: The JSON records those missingness and join-cardinality counts and lists upstream run-status as a limitation.
    claim_fit: These facts do not refute which table is current. They oppose treating stage 3 sample_wide as a complete donor-level or nested perfusion map, and they block promoting the upstream silver files themselves as completed-run Sources.
    limitations:
      - Opposition is to over-interpretation of completeness and lineage, not to the identity of the current key.
    freshness: Frozen output of run Phlz7GaqR7YqX8h3.
  - claim: "[[CLM-002_silver_sample_metadata_is_not_equivalent]]"
    relation: opposes
    determination: qualified
    checked_at: 2026-09-11
    checked_by: Cursor agent using bexorg-research (agent-reviewed, not human-endorsed)
    claim_statement: Latest silver_sample_metadata is not equivalent to stage 3 sample_wide.
    evidence_statement: The comparison is of stored identifier sets only; upstream producing runs were not completed, so extra or missing IDs were not independently recomputed from Cortex.
    context: Same inventory JSON, lineage limitation.
    sources_checked:
      - source: "[[SRC-0614e43dd8da43f5ac9bea033ad3fdcc]]"
        record: "ryrBa58bwN7SAA690000"
        locator: limitations[1]; artifacts[].run_status
        version: "run Phlz7GaqR7YqX8h3, sha256 4d6df9daee35f4ca5710cac072841f91cf5e13c6b488e9afecd068f8d7488d37"
    source_fidelity: The JSON states counts are from loaded parquet bytes, not a Cortex recompute, and that upstream Run.status values were not completed.
    claim_fit: This qualifies the non-equivalence claim as a stored-table difference, not a certified list of valid versus invalid samples.
    limitations:
      - Does not restore the June snapshot as canonical.
    freshness: Frozen output of run Phlz7GaqR7YqX8h3.
created: 2026-09-11
---
# @Evidence: Stage 3 identity is current but incomplete at donor grain, and upstream runs are not completed

- **Experimental Context:** Same pinned Cortex metadata inventory.
- **Perturbation / Exposure:** None.
- **Quantitative Findings:**
  - `donor_id` nulls on today's label `sample_wide`: 24,608 of 96,042 rows (405 non-null donors).
  - Perfusion identifier join: 804 IDs in `sample_wide`, 823 in `perfusion_wide`; 64 only in sample, 83 only in perfusion.
  - Inventoried silver producing `Run.status`: `scheduled` (stage 3) or `started` (June snapshot).
- **Observation:** These limits constrain how the current tables may be used. They challenge completeness and lineage, not the conclusion that stage 3 is the current key.
- **Methodological Caveats:** Sample-weighted summaries are not donor-weighted. A `perfusion_id` in one table is not guaranteed to exist in the other.

### Evidence-to-Claim Verification
Qualified opposition to over-reading both claims was checked against the inventory JSON on 2026-09-11.
