---
type: claim
id: CLM-002_silver_sample_metadata_is_not_equivalent
answers: "[[QUE-001_canonical_cortex_sample_metadata]]"
status: supported
confidence: moderate
direction: negative
created: 2026-09-11
---
# @Claim: Latest silver_sample_metadata is a stale June snapshot, not equivalent to stage 3 sample_wide

### Summary
`silver/cortex_metadata/silver_sample_metadata.parquet` is still marked
`is_latest` (`WeLk7yZ5hvZSwMTl000N`, created 2026-06-23) with 80,557 unique
`sample_id` values. Relative to today's stage 3 `sample_wide`, 15,649 sample IDs
are only in stage 3 and 164 are only in the June snapshot. Using that key as
"canonical" silently drops post-June samples and does not match stage 3
identity.

### Supporting Evidence
- [[EVD-002_deprecated_silver_divergence]]: Row counts and `sample_id` set difference versus stage 3.

### Opposing / Caveat Evidence
- [[EVD-003_join_and_lineage_limits]]: This is a stored-table comparison, not proof that every extra stage 3 row is a valid Cortex sample.

### Mechanistic Interpretation
`is_latest=true` on a deprecated key only means no newer artifact was written
to that key. It does not mean the table is current relative to stage 3. The
knowledge-base statement that this file is canonical is therefore not
supported by the 2026-09-11 datalake contents.
