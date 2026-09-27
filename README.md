# Portfolio Construction & Risk Management in Python

My work from the EDHEC Business School course **Introduction to Portfolio Construction and Analysis with Python** (Coursera, *Investment Management with Python and Machine Learning* specialization).

The repository contains a reusable analytics module and 18 notebooks, from basic return statistics to Monte Carlo simulations of dynamic allocation strategies.

## Contents

| # | Notebook | Topic |
|---|----------|-------|
| 01 | `first_look_drawdown` | Loading Fama-French data, wealth index, previous peaks, drawdown |
| 02 | `returns_volatility_drawdown` | Annualized returns and volatility, maximum drawdown (small caps vs large caps) |
| 03 | `deviations_from_normality` | Skewness, kurtosis and the Jarque-Bera test on hedge fund indices |
| 04 | `efficient_frontier_2_assets` | Return and volatility of a portfolio; the 2-asset frontier |
| 05 | `efficient_frontier_n_assets` | N-asset efficient frontier with a quadratic optimizer (SLSQP) |
| 06 | `max_sharpe_ratio` | Maximum Sharpe ratio portfolio and the Capital Market Line |
| 07 | `lack_of_robustness` | How sensitive MSR weights are to expected returns; EW and GMV portfolios |
| 08 | `limits_of_diversification` | Cap-weighted market index, rolling returns, rolling correlations |
| 09 | `portfolio_insurance_cppi` | CPPI backtest, with a fixed floor and with a drawdown constraint |
| 10 | `random_walk_gbm` | Simulating prices with Geometric Brownian Motion (and vectorizing the simulation) |
| 11 | `interactive_gbm_cppi` | Interactive GBM and Monte Carlo CPPI simulations with ipywidgets |
| 12 | `present_value_funding_ratio` | Present value of liabilities and the funding ratio |
| 13 | `cir_model_cash_vs_zc_bonds` | CIR interest-rate model; hedging liabilities with cash vs zero-coupon bonds |
| 14 | `liability_driven_investing` | Bond pricing, Macaulay duration, duration matching, funding ratio |
| 15 | `ldi_lab_session` | LDI lab: cash flows, discounting, duration |
| 16 | `bond_price_simulation` | Bond prices and total returns under simulated interest rates |
| 17 | `naive_psp_ghp_mix` | Fixed-mix and glide-path allocations between equities and bonds |
| 18 | `dynamic_risk_budgeting` | Floor- and drawdown-based CPPI allocators, simulated with CIR and GBM |

### `portfolio_analytics.py`

One module that gathers every function the notebooks use:

- **Risk metrics**: drawdown, semideviation, skewness, kurtosis, historic, Gaussian and Cornish-Fisher VaR, CVaR, Sharpe ratio, `summary_stats`
- **Portfolio optimization**: `minimize_vol`, `msr`, `gmv`, `plot_ef` (with CML, EW and GMV overlays)
- **Simulation**: Geometric Brownian Motion (`gbm`), CIR interest-rate model (`cir`), CPPI backtest (`run_cppi`)
- **Fixed income / LDI**: `bond_price`, `macaulay_duration`, `match_durations`, `funding_ratio`
- **Allocators**: `bt_mix`, `fixedmix_allocator`, `glidepath_allocator`, `floor_allocator`, `drawdown_allocator`, `terminal_stats`

## Getting started

```bash
git clone https://github.com/Katbejr/edhec-portfolio-construction.git
cd edhec-portfolio-construction
pip install -r requirements.txt
jupyter notebook notebooks/
```

### Data

The CSV files are not included in this repository. Put them in a `data/` folder at the root:

| File | Source |
|------|--------|
| `ind30_m_vw_rets.csv`, `ind30_m_nfirms.csv`, `ind30_m_size.csv` | [Kenneth R. French Data Library](https://mba.tuck.dartmouth.edu/pages/faculty/ken.french/data_library.html), *30 Industry Portfolios* |
| `Portfolios_Formed_on_ME_monthly_EW.csv` | Kenneth R. French Data Library, *Portfolios Formed on Size* |
| `edhec-hedgefundindices.csv` | [EDHEC-Risk Institute](https://risk.edhec.edu/), hedge fund indices |

Course participants can also get these files from the Coursera course materials.

## Credits

The course structure and a large part of the base code come from Vijay Vaidyanathan and Lionel Martellini (EDHEC Business School) through the Coursera course. On top of the lab work, I:

- merged several versions of the risk kit into one documented module
- added type hints and docstrings
- fixed bugs in `plot_ef` (hard-coded risk-free rate, wrong GMV label, missing return value) and in `bond_price`
- put the data paths in one place (`DATA_DIR`)

## Author

**Joud Katbe**, software engineering student at Polytechnique Montréal
[GitHub](https://github.com/Katbejr) · [LinkedIn](https://www.linkedin.com/in/joud-katbe/)
