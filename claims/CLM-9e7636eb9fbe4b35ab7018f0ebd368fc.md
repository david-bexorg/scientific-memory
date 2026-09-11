---
type: claim
id: CLM-9e7636eb9fbe4b35ab7018f0ebd368fc
answers:
- "[[QUE-789b42f8e971412c97d0d8013345a958]]"
status: supported
confidence: moderate
direction: neutral
created: 2026-09-11
---
# @Claim: Mean BOS brain_flow_measured in hours 6-12 after connection is 161.66 across 24 of the 30 most recent perfusions

### Summary
In the 2026-09-11 Cortex `perfusion_wide` snapshot, ranking perfusions by
`actual_perfusion_time_of_connection` (else `perfusion_date`) and averaging
BOS `brain_flow_measured` in the half-open window [6, 12) hours after
connection yields an unweighted mean of per-perfusion means of 161.66
(n=24). This describes stored telemetry, not a validated physiological flow.

### Supporting Evidence
- [[EVD-3b9b9816e2cb4601a551c214be0b8981]]: Tracked run `NJpejIJdRfiJwFJb` cohort summary and per-perfusion table.

### Opposing / Caveat Evidence
None that reverse the descriptive number. Coverage is incomplete: 6/30
excluded; units undeclared; two contributing runs include near-zero/negative
minima.

### Mechanistic Interpretation
Independent unit is `perfusion_id`. Time zero is actual connection, not BOS
file start (pre-connection logging can last tens of hours). `relative_perfusion_time_hrs`
was a 999.999 sentinel on the inspected recent run and was not used.
