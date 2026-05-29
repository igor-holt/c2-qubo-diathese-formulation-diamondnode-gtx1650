## Candidate 2 Approach Summary

1. Extended ag-15/dispatch_qubo_table.schema.json with diathese_qubo_mapping (direct metrics incl. epsilon_th).
2. Enhanced diamondnode-ops/diathese_to_qubo.py with --c2: direct formulas h/J from epsilon_th, cryst, dissonance etc; clean c2_stats JSON; dispatch_qubo_table_extension in output; C2 branded for publication.
3. Integrated into run_bench.sh (auto C2 QUBO for paired stats).
4. Rsynced to diamondnode, executed via SSH BatchMode (active sessions): cleanup + C2 --once + bench.
5. Captured real JSONL on 4GB card (low VRAM, native build).
6. Published this repo with harness + real log + docs.
7. (Next) Update ag-15 acceptance_gates/blocker_ledger with C2 evidence entries for G1-7 progress (real only).

No sim labels. All traceable to live nvidia-smi + SSH + exact binary/model SHA.

Enables G6 real QUBO pub artifacts on constrained hardware, G7 thermodynamic fields from Cortex, G1-3 via paired bench+load.
