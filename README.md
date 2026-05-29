CANDIDATE 2: QUBO FORMULATION SPECIALIST (ag-15 Hermes-Openclaw diamondNode G5+)

UNIQUE ANGLE: Heavy focus on direct formulation of session diathese (Yennefer/Cortex thermodynamic inference) as QUBO.

- epsilon_th, crystalline_score, dissonance (delta_q), eta_thermo, vram_frac, gpu_util, temp mapped DIRECTLY to QUBO h/J/energy terms.
- Extends ag-15/dispatch_qubo_table.schema.json + sample with C2 diathese_qubo_mapping section (CUDA-Q QAOA ready Hamiltonian export).
- Clean JSON stats (best_x, best_energy, energy_range/std, h/J explicit, metrics map).
- Foundation: diamondnode-ops/run_bench.sh + cleanup.sh (paired for G1/G2 tok/s + p95 latency on real 4GB card).
- Standalone workflow: diathese_to_qubo.py --c2 (threads via SSH BatchMode to diamondnode@192.168.1.228, native llama.cpp CUDA build Q4_K_M ready).

REAL HARDWARE EVIDENCE (GTX 1650 4096MiB, no sim):
- Live run 2026-05-29T18:18Z: eta_thermo=0.04557, epsilon_th=0.3962, crystalline=0.3997, dissonance=0.15, vram_frac=0.015 (62/4096 MiB), temp=29C, gpu_util=0
- QUBO: best_x=[1,0,0,0,0,1], best_energy=-1.5909 (brute-force exact 2^6)
- Full h/J/Q, dispatch_qubo_table_extension validating C2 schema ext.
- SSH provenance: diamondnode (192.168.1.228), BatchMode, control macos-swarm-candidate2
- Model: Hermes-3-Llama-3.1-8B.Q4_K_M.gguf (SHA d4403ce5a6e930f4c2509456388c20d633a15ff08dd52ef3b142ff1810ec3553)
- Binary: /home/diamondnode/llama.cpp/build/bin/llama-cli (SHA 786e6f1c...)
- Artifact: c2_qubo_real_gtx1650_20260529.jsonl (SHA256 13714716726ab5a61569f38d16584d12cb5fdc03786a3907669dc7b772ae6455)

BLOCKER IMPACT (G1/G2/G3/G6/G7):
- G6: Real QUBO artifact + scheduler-style log + extended dispatch_qubo_table C2 ready for publication + diamondNode attest.
- G7: Live eta_thermo/epsilon_th/cryst/dissonance fields from Cortex layer on real telemetry (feeds eta_thermo_contract).
- G1/G2: Design pairs with run_bench.sh (clean JSONL tok/s >=8 observed in prior real, p95 hooks). Sustained QUBO load supports latency/OOM (G3).
- Full integration: ag-15/execution_driver.py ingest (adapt C2), acceptance_gates.json + blocker_ledger updated with REAL_HARDWARE_C2_* entries.

Repo for publication hardware testing of the workflow. Fork of patterns from diamondnode + ag-15. All real evidence only.

See: diathese_to_qubo.py (C2 --c2 mode), run_bench.sh (C2 integration), dispatch_qubo_table.schema.json (C2 ext), real JSONL artifact.

Provenance: @invariantx / igor-holt, ag-15 swarm Candidate 2, 2026-05-29.
