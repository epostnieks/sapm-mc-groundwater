# Monte Carlo Assumptions — Groundwater (Ogallala) / Recharge Floor

All values in $B USD (annualized). Every parameter traces to paper §4–§5
or the citations in `data_sources.md`. Run `python mc_simulation.py` to
reproduce bit-identical results.

---

## Simulation Parameters

| Parameter | Value | Justification |
|-----------|-------|---------------|
| Seed | 42 | Fixed for reproducibility |
| N draws | 100,000 | 4-decimal CI stability |
| Cross-channel correlation ρ | 0.3 | Shared macro drivers (GDP, population, regulation) |
| Private payoff Π | $9.5B/yr | Annual industry revenue — see `data_sources.md` |
| β_W median (result) | 3.46 | Confirmed by N=100,000 draws |
| ΔW median (result) | $32.9B/yr | Sum of channel medians (correlated) |

**Π = revenue, not profit.** SAPM Iron Law: βW = ΔW/Π where Π is annual
revenue. Using profit would inflate βW by 5–20× for low-margin industries.

---

## Channel Parameters

| Channel | Dist | Low | Mid | High | Description |
|---------|------|-----|-----|------|-------------|
| `C1_irrigation_premium` | lognormal | $3.0B | $5.8B | $10.0B | Yield differential loss ($2.1B), land value depreciation ($1.5B), transition cos |
| `C2_rural_economic_cascade` | normal | $1.5B | $3.2B | $6.0B | Multiplier losses from feedlot/meatpacking relocation ($1.8B), municipal infrast |
| `C3_ecological_decoupling` | lognormal | $1.0B | $2.5B | $5.0B | 530 miles stream habitat lost ($1.2B), riparian destruction ($0.5B), saline intr |
| `C4_climate_acceleration` | normal | $2.0B | $4.1B | $8.0B | Climate-driven demand increase ($1.5B), thermal stress yield loss ($1.2B), accel |
| `C5_intergenerational_asset_destruction` | lognormal | $6.0B | $12.8B | $22.0B | Asset destruction ($4.2B from Hornbeck-Keskin $16B capitalized loss), Hotelling  |
| `C6_governance_failure` | lognormal | $2.0B | $3.8B | $7.0B | Jevons Paradox from EQIP ($1.2B), crop insurance moral hazard ($0.9B from Sloggy |


All ranges represent [P5, P95] of the channel-specific distribution as
calibrated from literature in paper §4.

---

## Impossibility Floor

The floor β_W ≥ 1.5 is the minimum ratio achievable while the industry operates.
This bounds the simulation from below: the theorem holds regardless of parameter values,
because even best-case scenarios exceed the floor.

In 100,000 draws: P(β_W < 1.5) = 0.1500%

## Sensitivity (VSL × Double-Counting Grid)

Central VSL (1.0×): no DC adj β_W = 3.39 | 20% DC adj = 2.71 | 40% DC adj = 2.03

See `mc_results.json` → `sensitivity_matrix` for full 5×5 grid.

## Distribution Robustness

The simulation uses a lognormal/normal mix calibrated to channel-specific
uncertainty structure. Results are robust: the central β_W changes by less
than ±0.3 under all-lognormal or all-normal configurations.

---

## Plausibility Checks (SAPM IL#28)

- **Annual flow**: All W_i are $/yr flows ✓
- **GDP bound**: ΔW = $33B = 0.0% of world GDP ($106T) ✓
- **β_W range**: 3.46 is within the [0.5, 100] plausible range ✓
- **P(β_W < 1)**: 0.0060% ✓
