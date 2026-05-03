# Simulation Report: Thermal interface resistance coupled with PDN impedance creates non-uniform voltage and temperature gradients under spatially varying AI workloads

**Idea ID:** `69608c0d-5e7f-45d3-95e7-f8d1723d0b39`  
**Domain:** `cross_domain`  
**Sim Score:** `6.9/10`  
**Overall Status:** ⚠️ `WARNING`  
**Timestamp:** 2026-05-03T02:46:43.949148+00:00  
**Duration:** 524ms

---

## 📡 Data Movement  ⚠️ `WARNING`

| Achievable TFLOPS | **100.0** |
| Efficiency | **100.0%** |
| Bottleneck | **bandwidth** |
| Binding memory | **HBM3** |

**Simulation notes:**
> 100.0% efficiency, bandwidth-bound (AI=83.3 FLOP/byte)
> Arithmetic intensity: 83.3 FLOP/byte (ridge point: 83.3)
> Binding memory level: HBM3 (inf GB/s)
> Effective latency: 30.0 ns
> NoC utilization=18% — acceptable
> Effective BW: 126 GB/s (90% penalty from 1200 claimed)
> Congestion latency: +3.4ns (base 16.0ns + queue 3.4ns)
> Traffic pattern: attention_pattern (factor=1.8×)
> Memory controller contention: 100% utilization, +0.6ns

---
## Key Simulation Insights

- Coupled solution stable at T_op=35.46°C, 86% margin to runaway
- T_op=35.46°C | P_dyn=100W + P_leak=5W = 105W (5% leakage overhead)
- 100.0% efficiency, bandwidth-bound (AI=83.3 FLOP/byte)
- Arithmetic intensity: 83.3 FLOP/byte (ridge point: 83.3)
