# Five-Year Copper Outlook & Portfolio Reconstruction

## Overview

This project develops and tests a five-year investment thesis for copper, then uses the evidence to evaluate and reconstruct a personal portfolio around that thesis. The analysis period for the forward-looking thesis is **1 September 2026 to 31 August 2031**.

The project has three connected objectives:

1. Evaluate whether copper is likely to generate a positive real return over the five-year horizon, given refined-copper demand, supply, inventories, and related market conditions.
2. Diagnose the risk and factor characteristics of the current portfolio.
3. Develop and compare alternative, risk-aware portfolio allocations that express a bullish copper view while managing concentration, cyclicality, and downside risk.

This is an educational research project and not investment advice.

## Thesis

> Copper will deliver a positive real return over the next five years because expected refined-copper demand growth and supply constraints will tighten the market relative to its historical balance.

The thesis is evaluated through bull, base, and bear scenarios.

- **Bull:** sustained refined-market deficits, declining inventories, delayed supply response, and strong grid/electrification demand.
- **Base:** a broadly balanced market with modest but cyclical copper appreciation.
- **Bear:** weak global industrial activity, Chinese construction weakness, greater substitution or recycling, and/or a faster mine-supply response.

## Methodology

### 1. Copper-market research

The core dataset combines cleaned, auditable series on copper prices and fundamentals. It includes refined production, refined usage, derived refined balance, mine production, secondary refined production, and exchange inventory data. Series are collected, cleaned, validated, and documented individually before being merged at an appropriate common frequency.

### 2. Portfolio baseline diagnosis

The existing portfolio will be reconstructed using current holdings and CAD market values. CAPM and multi-factor regressions will assess exposure to the Canadian equity market, materials/mining sector, small-cap/speculative equities, commodity prices, USD/CAD, and other relevant macro factors.

### 3. Portfolio construction

Three alternative portfolios will be created:

- **Conservative:** controlled copper exposure with greater diversification and hedging.
- **Balanced:** meaningful copper tilt while retaining broad risk diversification.
- **High-conviction copper:** highest copper-related exposure, accepting greater concentration and drawdown risk.

The portfolios will be constructed using a **constrained Black–Litterman-style mean-variance optimisation** framework. Market-implied or CAPM-informed return estimates form the prior; scenario-based copper views provide explicit, confidence-weighted adjustments. Constraints will address long-only allocation, issuer concentration, copper-sleeve exposure, liquidity/speculation, turnover, cash/futures exposure, and a separate derivatives risk budget.

MVO outputs will be compared with simpler benchmark allocations, including the current portfolio, an equal-weighted eligible universe, and a minimum-variance portfolio. The three portfolios will then be tested under bull, base, and bear copper scenarios and specific stress events such as copper-price declines, China-demand shocks, broad-market drawdowns, and FX shocks.

## Data governance

The project follows a raw-to-processed data workflow:

1. Preserve downloaded source files in `data/raw/`.
2. Clean and validate each series in `src/data_processing.ipynb`.
3. Save cleaned outputs in `data/processed/`.
4. Maintain source, definition, units, transformations, assumptions, and validation evidence in the metadata and configuration files.

Digitised chart data are explicitly identified as approximations and are not treated as equivalent to source-tabulated observations.

## Repository structure

```text
copper_project/
├── config/
│   └── assumptions.yaml
├── data/
│   ├── metadata/
│   │   ├── data_dictionary.csv
│   │   └── source_register.csv
│   ├── processed/
│   │   ├── copper_price_monthly.csv
│   │   ├── icsg_world_copper_production_usage_annual_clean.csv
│   │   ├── secondary_refined_production_annual_digitized.csv
│   │   ├── lme_copper_inventory_canonical_clean.csv
│   │   └── ...
│   └── raw/
│       ├── lme_inventory_reports/
│       └── ...
├── src/
│   └── data_processing.ipynb
└── README.md
```

## Current data coverage

Processed data currently include:

- monthly copper price data sourced via ALFRED/IMF;
- annual ICSG global copper mine production, refined production, and refined usage data;
- an annual refined-balance series derived as refined production less refined usage;
- a digitised annual secondary-refined-production estimate, clearly labelled as approximate;
- annual copper exchange inventories through 2022;
- monthly LME inventory observations from 2023 onward; and
- a canonical LME inventory series that joins the annual historical and monthly recent segments with documented source provenance.

## Reproducibility and validation

Each processed series is accompanied by source and transformation metadata. Validation checks include date uniqueness, expected coverage, missing observations, numeric conversion, unit consistency, comparison of overlapping sources where available, and boundary diagnostics at source transitions.

Future portfolio-optimisation inputs will additionally require an explicit investible-universe table, historical CAD return series, current portfolio weights, market-cap/reference weights, risk-free-rate data, factor series, scenario views, and configurable allocation constraints.

## Planned outputs

The final written report will contain:

1. An evidence-based five-year copper outlook.
2. A risk and factor analysis of the current portfolio.
3. Three alternative portfolio allocations, their assumptions, benchmark comparisons, and scenario/stress-test results.

## Disclaimer

This repository documents a personal research and learning project. It does not constitute investment, financial, legal, or tax advice. Historical data and model outputs do not guarantee future results.
