# Discrete Hull–White Caplet and Floorlet Pricing

R implementation accompanying the working paper:

**Backward-Looking Caplet Pricing in a Discrete Hull–White Model: Closed Forms, Variance Decomposition, and the Backward–Forward Price Gap**

Sebastiano Pinotti  
WU Vienna University of Economics and Business  
October 2026

[Working paper on SSRN](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7374959)

## Overview

This repository contains the numerical implementation and sensitivity analysis accompanying a working paper on backward- and forward-looking caplet and floorlet pricing in a fully discrete-time Hull–White framework.

The short rate follows a Gaussian first-order autoregression, with coefficients corresponding to the exact discretization of the continuous-time Hull–White short-rate process. Bond pricing, overnight compounding, and discounting are defined consistently within the discrete-time market.

The Gaussian structure allows closed-form pricing without stochastic calculus, using truncated Gaussian exponential moments.

## Main Results

The paper establishes:

- **Closed-form pricing:** Analytical expressions for backward-looking caplets and floorlets at valuation dates before or within the accrual period, alongside their forward-looking counterparts.
- **Variance decomposition:** An exact decomposition of the backward-looking variance into pre-accrual and in-accrual components, `ν_X = ν_W + ν_{m,N}`.
- **Price dominance:** Backward-looking caplets are at least as valuable as otherwise equivalent forward-looking caplets before and at the start of accrual.
- **Backward–forward price gap:** An exact integral representation, an at-the-money closed form, and an analytical characterization of the strike maximizing the gap.
- **Sensitivity analysis:** Numerical investigation of the gap with respect to accrual length, mean reversion, volatility, and strike.

## Repository Contents

**`paper-caplet-sensitivity-analysis.R`**

Self-contained R script reproducing the figures and numerical results of Section 4 of the working paper.

The script includes:

- Closed-form computation of the pre-accrual, in-accrual, and total variances.
- Backward- and forward-looking caplet pricing.
- Exact and leading-order expressions for the at-the-money price gap.
- Computation of the strike maximizing the backward–forward gap.
- Sensitivity plots and numerical verification of the results reported in the paper.

The generated figures are saved as PNG files in the `figures/` directory.

## Requirements and Reproducibility

- Base R only; no external packages required.
- All numerical parameters are specified in the script.
- Each figure and numerical check can be reproduced by running the script.

From the repository directory, run:

`Rscript paper-caplet-sensitivity-analysis.R`

The script generates the figures and prints numerical checks to the console.

The baseline parameter configuration is:

| Parameter | Value |
|---|---|
| Time step | Δ = 1/360 |
| Mean reversion | a = 0.75 |
| Short-rate volatility | σ = 0.01 |
| Pre-accrual length | 90 days |
| Accrual length | 90 days |
| ATM forward rate | 3.5% |

These parameters are used for the illustrative numerical analysis and are not presented as an empirical calibration.

## Reference

Pinotti, S. (2026). *Backward-Looking Caplet Pricing in a Discrete Hull–White Model: Closed Forms, Variance Decomposition, and the Backward–Forward Price Gap.* Working paper, WU Vienna University of Economics and Business.

[SSRN Preprint](https://papers.ssrn.com/sol3/papers.cfm?abstract_id=7374959)

## License

This repository is distributed under the MIT License. See [LICENSE](LICENSE) for details.
