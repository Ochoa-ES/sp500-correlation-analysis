# S&P 500 Correlation Structure Analysis
### Master's Thesis — UNAM, 2018
**Author:** Elsa Susana Ochoa

---

## Overview
This project analyzes the correlation matrix structure of 293 S&P 500
stocks over the period 1992–2014, using techniques from econophysics
to identify genuine dependencies between assets and filter statistical
noise. A key contribution is the application of Power Mapping to resolve
matrix singularity, combined with Correlated Wishart Ensembles for
robust signal/noise separation.

## Key Findings
- The empirical correlation matrix was singular due to a large number
  of zero eigenvalues — a common problem when the number of assets
  exceeds the number of observations (N=293 > T=44).
- **Power Mapping** resolved the singularity, eliminating zero eigenvalues
  and producing a well-conditioned positive definite matrix.
- Two **Correlated Wishart Ensemble (CWE)** benchmarks were implemented
  and compared: uniform background correlation and sector-specific
  background correlation.
- **Eigenvalue analysis** against the CWE benchmark identified which
  market modes carry genuine information versus statistical noise.
- **Eigenvector analysis** via Participation Ratio, Intensity, and
  Overlap Spectral Contribution (OSC) revealed the underlying market
  structure — global market mode, sectoral modes, and individual stock
  effects.
- **Window size sensitivity analysis** confirmed that T=44 days optimally
  balances matrix conditioning and temporal resolution.

## Methods
- Daily return calculation: R_t = (P_t / P_{t-1}) - 1
- Empirical correlation matrix estimation (293 assets, 1992–2014)
- Rolling windows: 44-day window, 22-day shift (262 windows total)
- **Power Mapping**: non-linear filter ρ_ij → sign(ρ_ij)|ρ_ij|^q,
  1 < q < 2, resolving matrix singularity (zero eigenvalues)
- **Correlated Wishart Ensemble (CWE)** — two implementations:
  - Constant background correlation (uniform ρ across all assets)
  - Constant correlation by sector (sector-specific ρ)
- Eigenvalue spectral analysis vs CWE benchmark (Random Matrix Theory)
- Eigenvector analysis:
  - **Participation Ratio (PR)**: measures how many assets contribute
    to each market mode
  - **Intensity**: identifies which specific assets dominate each
    eigenvector
  - **Overlap Spectral Contribution (OSC)**: quantifies how Power
    Mapping perturbs the eigenvector structure

## Tech Stack
- Python 3.x
- NumPy, SciPy
- Matplotlib

## Repository Structure
```
sp500-correlation-analysis/
│
├── README.md
├── data/
│   └── sp500_prices.csv
│
├── notebooks/
│   ├── 01_correlation_matrix_power_mapping.ipynb
│   ├── 02-1_CWE_constant_correlation.ipynb
│   ├── 02-2_CWE_constant_correlation_by_sector.ipynb
│   ├── 03_eigenvalue_analysis.ipynb
│   ├── 04_eigenvector_analysis.ipynb
│   └── 05_window_size_sensitivity.ipynb
│
└── figures/
    └── *.png
```
## Relevance to Portfolio Risk Management
The methods developed in this thesis are directly applicable to
portfolio risk management:
- Power Mapping produces well-conditioned covariance matrices,
  essential for stable VaR estimation in large portfolios.
- RMT/CWE analysis identifies the true factor structure of market
  returns, separating systematic risk from noise.
- Eigenvector analysis via PR and Intensity maps directly to factor
  risk models used in practice (e.g. Barra, BlackRock Aladdin).
- Results cover multiple market regimes including the dot-com bubble
  (2000) and the 2008 financial crisis.
