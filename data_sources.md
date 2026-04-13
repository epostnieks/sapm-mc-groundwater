# Data Sources — Groundwater (Ogallala) Monte Carlo Simulation

Channel parameters in `mc_simulation.py` trace to the sources listed here.
The paper (Groundwater (Ogallala): Recharge Floor) is available on SSRN and contains the full
reference list and §4 calibration narrative.

---

## Channel Sources

### `C1_irrigation_premium`

Yield differential loss ($2.1B), land value depreciation ($1.5B), transition costs ($1.4B), pumping escalation ($0.8B). Sources: World Bank, Deines et al. (2020), Sampson et al. (2019), USDA ERS.

*Full citations: paper §4 (available SSRN).*

### `C2_rural_economic_cascade`

Multiplier losses from feedlot/meatpacking relocation ($1.8B), municipal infrastructure stranding ($0.8B), population displacement ($0.6B). Sources: Hornbeck-Keskin (2012), IMPLAN, USDA ERS.

*Full citations: paper §4 (available SSRN).*

### `C3_ecological_decoupling`

530 miles stream habitat lost ($1.2B), riparian destruction ($0.5B), saline intrusion ($0.4B), land subsidence ($0.4B). Sources: Perkin et al. (2017), NOAA benefit transfer.

*Full citations: paper §4 (available SSRN).*

### `C4_climate_acceleration`

Climate-driven demand increase ($1.5B), thermal stress yield loss ($1.2B), accelerated depletion ($0.9B), lost adaptation value ($0.5B). Sources: Crosbie et al. (2013), CMIP6.

*Full citations: paper §4 (available SSRN).*

### `C5_intergenerational_asset_destruction`

Asset destruction ($4.2B from Hornbeck-Keskin $16B capitalized loss), Hotelling stock cost ($5.3B), drought insurance risk ($2.0B), food security externality ($1.3B). Dominant channel (40%).

*Full citations: paper §4 (available SSRN).*

### `C6_governance_failure`

Jevons Paradox from EQIP ($1.2B), crop insurance moral hazard ($0.9B from Sloggy et al. 2025), regulatory capture ($0.8B), Rule of Capture externality ($0.9B).

*Full citations: paper §4 (available SSRN).*

---

## Industry Revenue (Π)

The private payoff Π = $9.5B/yr is global annual industry revenue.
Source: paper §2 and §4. See paper §DA-1 (Decision Audit Field 7) for full
revenue source documentation.

---

## SAPM Framework

- Postnieks, E. (2026). *The Private Pareto Theorem*. SAPM Foundation Paper. SSRN.
- Postnieks, E. (2026). *Groundwater (Ogallala) (Recharge Floor)*. SAPM Working Paper. SSRN.

---

## Distribution Methodology

- Iman, R. L., & Conover, W. J. (1982). A distribution-free approach to
  inducing rank correlation among input variables. *Communications in
  Statistics — Simulation and Computation*, 11(3), 311–334.
- Cooke, R. M. (1991). *Experts in Uncertainty*. Oxford University Press.
