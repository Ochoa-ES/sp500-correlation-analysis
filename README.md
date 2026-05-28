# sp500-correlation-analysis

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
  exceeds the number of observations.
- **Power Mapping** (raising correlation matrix elements to an exponent
  q, where 1 < q < 2) resolved the singularity, eliminating zero
  eigenvalues and producing a well-conditioned positive definite matrix.
- Two **Correlated Wishart Ensemble (CWE)** benchmarks were implemented
  and compared: uniform background correlation and sector-specific
  background correlation.
- **Eigenvalue analysis** against the CWE benchmark identified which
  market modes carry genuine information versus statistical noise.
- **Eigenvector analysis** via Participation Ratio and Intensity revealed
  the underlying market structure — global market mode, sectoral modes,
  and individual stock effects.

## Methods
- Daily return calculation: R_t = (P_t / P_{t-1}) - 1
- Empirical correlation matrix estimation (293 assets, 1992–2014)
- **Power Mapping**: non-linear filter ρ_ij → |ρ_ij|^q, 1 < q < 2,
  resolving matrix singularity (zero eigenvalues)
- **Correlated Wishart Ensemble (CWE)** — two implementations:
  - Constant background correlation (uniform ρ across all assets)
  - Constant correlation by sector (sector-specific ρ)
- Eigenvalue spectral analysis vs CWE benchmark (Random Matrix Theory)
- Eigenvector analysis:
  - **Participation Ratio (PR)**: measures how many assets contribute
    to each market mode
  - **Intensity**: identifies which specific assets dominate each
    eigenvector

## Tech Stack
- Python 3.x
- NumPy, pandas, SciPy
- Matplotlib, Seaborn

## Repository Structure

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
│   ├── 04-1_eigenvector_analysis.ipynb
│   ├── 04-2_eigenvector_analysis_Intensity.ipynb
│   └── 05_figures.ipynb
