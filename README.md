# Option Pricing under Jump-Diffusion: The Merton Model
## A Theoretical and Empirical Framework: From Black-Scholes to Jump Risk

This repository contains the complete implementation and empirical analysis of the **Merton Jump-Diffusion Model** for option pricing. Developed as a collaborative professional research initiative for **Bocconi Students Quantitative Finance (BSQF) — Spring Semester 2025/2026**, this project extends the classical continuous-path Black-Scholes paradigm to accurately account for asset price discontinuities ("shocks" or "jumps") frequently observed in financial markets.


## Overview

The repository provides a streamlined quantitative framework comparing the classical Black–Scholes (Geometric Brownian Motion) model against the Merton Jump-Diffusion model using a continuous-time Monte Carlo engine.  
The analysis is executed dynamically using historical data from the EURO STOXX 50 index.

### Research Workflow:
The following research pipelie was implemented:
1. **Data Acquisition**: Fetches daily historical time-series data for the EURO STOXX 50 index via the Yahoo Finance API (yfinance).  
2. **Empirical Diagnostics**: Computes statistical moments (skewness, excess kurtosis) and evaluates tail frequencies ($|z| > 3$) to verify deviations from Gaussian normality.
3. **Heuristic Calibration**:
    * **GBM**: Calibrated via the empirical mean ($\mu$) and standard deviation ($\sigma$) of log-returns.
    * **Merton**: Employs a return-based absolute threshold filter ($|z| > 2.5$) to classify large moves as discrete jumps, calculating jump parameters ($\lambda, \mu_J, \delta_J$) directly from outliers.
4. **Path Simulation**: Generates independent paths over a 1-year horizon ($T=1.0$, $N=252$ steps) using vectorized log-return simulation via standard normal and Poisson random variables.
5. **Distribution & Option Valuation**: Compares simulated terminal empirical return distributions against actual returns and prices European At-The-Money (ATM) options using a Monte Carlo pricing framework.

The final emprirical results are then visualised and analysed.

## Code Usage

### Prerequisites
Ensure your local environment matches the specific python dependencies inside requirements.txt:
```bash
pip install -r requirements.txt
```

### Quick Run
Launch and view the full empirical process by running the primary Jupyter notebook:
```bash
jupyter notebook eurostoxx_merton_vs_black_scholes_mc.ipynb
```


## Further Notes & Acknowledgements
The full theoretical research will soon be available on the [BSQF Research Archive](https://www.bocconistudentsquantitativefinance.com/research-papers).



#### Project Team (BSQF Analyst Team)
* **Luca Saracho** — Project Director
* **Federico Ferrantino** — Analyst
* **Zhi Yi Chen** — Analyst
* **Toni Vodopija** — Analyst
* **Fu Qiang Teo** — Analyst