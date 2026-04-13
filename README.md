# SAPM Monte Carlo — Groundwater (Ogallala) / Recharge Floor

**Public replication repository for quantitative results in:**

> Postnieks, E. (2026). *Groundwater (Ogallala) (Recharge Floor).* SAPM Working Paper. SSRN.

This repository provides everything needed to independently reproduce, audit,
and extend the Monte Carlo simulation underlying the paper's core results.
The paper is available on SSRN.

---

## Results (N = 100,000 draws, seed = 42)

| Statistic | Value |
|-----------|-------|
| **β_W median** | **3.46** |
| β_W mean | 3.55 |
| β_W std | 0.88 |
| **90% CI** | **[2.3, 5.1]** |
| 99% CI | [1.8, 6.0] |
| P(β_W < 1) | 0.0060% |
| **ΔW median** | **$32.9B/yr** |
| Π (revenue) | $9.5B/yr |

**β_W = 3.46** means the groundwater (ogallala) industry destroys **$3.46 in system
welfare for every $1.00 in revenue** — across 6 channels and 100,000 Monte Carlo draws.

**Classification**: Class 1 — Impossibility

---

## What Is β_W?

```
β_W = ΔW / Π
```

- **ΔW** = total annualized welfare destruction ($B/yr) across all channels
- **Π** = annual industry **revenue** ($B/yr) — not profit

β_W > 1: industry destroys more welfare than it captures in revenue.
β_W > 3: Strong Intractability threshold — reform requires structural replacement.

---

## Quick Start

```bash
git clone https://github.com/epostnieks/sapm-mc-groundwater.git
cd sapm-mc-groundwater
pip install numpy scipy
python mc_simulation.py
```

Expected output: `β_W median : 3.46` and `ΔW median : $32.9B/yr`

---

## Welfare Channels

| Channel | Median ($B/yr) | 90% CI | Distribution |
|---------|---------------|--------|--------------|
| C1_irrigation_premium | $5.8B | [$3.4B, $10.0B] | Lognormal |
| C2_rural_economic_cascade | $3.2B | [$0.9B, $5.5B] | Normal |
| C3_ecological_decoupling | $2.5B | [$1.3B, $5.0B] | Lognormal |
| C4_climate_acceleration | $4.1B | [$1.1B, $7.1B] | Normal |
| C5_intergenerational_asset_destruction | $12.8B | [$7.5B, $21.9B] | Lognormal |
| C6_governance_failure | $3.8B | [$2.1B, $7.0B] | Lognormal |
| **Total ΔW** | **$32.9B** | **[$21.4B, $48.7B]** | Correlated (ρ=0.3) |

---

## Impossibility Floor

The floor β_W ≥ 1.5 cannot be breached by any policy while the
industry continues to operate. In 100,000 draws, only **0.1500%**
fall below this floor — confirming the structural constraint.

## Repository Contents

| File | Description |
|------|-------------|
| `mc_simulation.py` | Self-contained simulation — no private pipeline imports |
| `mc_results.json` | Pre-run results (100K draws, seed=42) — matches paper |
| `mc_histogram.json` | Binned β_W distribution (80 bins) for companion chart |
| `assumptions.md` | Every parameter: value, derivation, source |
| `data_sources.md` | Full citation list for all empirical inputs |

---

## Replication Notes

Results are seeded and deterministic. Tested with:
```
numpy==1.26.4  scipy==1.12.0  Python 3.11.9
```

The `median` and `ci_90` (to 1 decimal) match exactly across compatible versions.

---

## License

CC BY 4.0. Cite as:

> Postnieks, E. (2026). *SAPM Monte Carlo — Groundwater (Ogallala) (Recharge Floor)*.
> GitHub: epostnieks/sapm-mc-groundwater.
> https://github.com/epostnieks/sapm-mc-groundwater
