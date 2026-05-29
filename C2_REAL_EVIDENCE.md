## Real Hardware Evidence - Candidate 2

**Date**: 2026-05-29T18:18Z
**Hardware**: NVIDIA GeForce GTX 1650 (4096 MiB), Ubuntu, native llama.cpp CUDA build (GGML_CUDA=1, arch=75, nvcc 12.4)
**Model**: Hermes-3-Llama-3.1-8B.Q4_K_M.gguf (SHA d4403ce5a6e930f4c2509456388c20d633a15ff08dd52ef3b142ff1810ec3553)
**Binary**: llama-cli (SHA 786e6f1c0861a1d6a226394cbf5c3644d9a0cf8bafd21bb866f168597cc6eb0a)

**Diathese (live nvidia-smi + Yennefer/Cortex sim)**:
eta_thermo: 0.04557
epsilon_th: 0.39623 (direct C2)
crystalline_score: 0.39969
dissonance (delta_q): 0.15
vram_frac: 0.0151 (62 MiB / 4096)
gpu_util: 0.0
temp_c: 29.0

**QUBO Formulation (C2 direct map)**:
best_x: [1,0,0,0,0,1]
best_energy: -1.590898
Full h/J/Q_upper in JSONL. Energy range [-1.5909, 2.175], std 0.895

**dispatch_qubo_table C2 extension**: Validated in artifact (diathese_qubo_mapping with all metrics, energy_mapping, cudaq_ready=true).

**SHA256 of artifact**: 13714716726ab5a61569f38d16584d12cb5fdc03786a3907669dc7b772ae6455

**Ties to blockers**:
- G6_qubo_publication: This is the real qubo_json + dispatch ext for scheduler pub + attest.
- G7_eta_thermo: Exact fields (eta, epsilon_th etc) for Yennefer endpoint contract.
- G1/G2: Paired design with run_bench for decode tok/s (prior real 8.8+), latency p95.
- G3: Sustained threaded load for OOM rate <0.5% validation.

**Workflow**: diamondnode-ops/cleanup.sh ; python diathese_to_qubo.py --c2 --once --jsonl ... ; ./run_bench.sh (C2 auto)

Part of dedicated pub repo for hardware testing. ag-15 integration via driver edits/ingest.
