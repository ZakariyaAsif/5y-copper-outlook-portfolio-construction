# Five-Year Copper Outlook & Portfolio Reconstruction

An evidence-based research project evaluating a five-year copper investment thesis and its implications for portfolio construction.

**Research horizon:** 1 September 2026 to 31 August 2031  
**Status:** In progress, data construction and validation

## Objective

This project investigates whether copper is likely to deliver a positive real return over the next five years, then evaluates how that outlook may translate into returns and risk exposures for copper-mining equities and related securities.

The project has three objectives:

1. Test the fundamental copper-market hypothesis.
2. Establish a baseline analysis of the current portfolio.
3. Develop two to three alternative allocation strategies centred on the copper thesis.

The work is also intended as a practical application of CFA Level I concepts, including financial statement analysis, portfolio management, and quantitative methods.

## Copper Hypothesis

> Copper will deliver a positive real return over the next five years because expected refined-copper demand growth and supply constraints will tighten the market relative to its historical balance.

Scenario framework:

- **Bull:** sustained refined-market deficits, declining inventories, delayed supply response, and strong electrification/grid demand.
- **Base:** broadly balanced market with modest, cyclical copper appreciation.
- **Bear:** weak industrial activity, Chinese construction weakness, substitution or recycling, or faster-than-expected mine supply.

## Methodology

The project combines quantitative analysis and qualitative industry research.

Core areas include:

- Copper-price and real-return analysis.
- Refined copper production, usage, market balance, mine supply, and secondary supply.
- LME, COMEX, and SHFE exchange inventories.
- Chinese copper imports, treatment and refining charges, and other market-tightness indicators.
- Supply-demand and inventory analysis.
- CAPM and multi-factor analysis of the existing portfolio and prospective copper-related securities.
- Portfolio allocation analysis under alternative risk-return assumptions.

## Repository Structure

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
│   │   ├── copper_fundamentals_annual_analysis.csv
│   │   ├── icsg_world_copper_production_usage_annual_clean.csv
│   │   ├── lme_copper_inventory_canonical_clean.csv
│   │   └── ...
│   └── raw/
│       ├── lme_inventory_reports/
│       ├── alfredgraph.csv
│       ├── cochilco_copper_inventories_exchanges.xls
│       ├── icsg_factbook_2025_raw_annex.pdf
│       └── ...
├── src/
│   └── data_processing.ipynb
└── README.md
```

## Data Design

Raw source files are preserved without modification. Each source is cleaned into a source-specific processed dataset before being used in a canonical series or final analysis.

The repository uses:

- `config/assumptions.yaml` — project, date-handling, and modelling assumptions.
- `data/metadata/data_dictionary.csv` — definitions, units, frequencies, transformations, and expected coverage for each variable.
- `data/metadata/source_register.csv` — source provenance, access details, methodology notes, and revision policy.
- Validation outputs — checks for coverage, duplicates, missing data, source agreement, and frequency transitions.

No interpolation or forward-filling is used unless explicitly documented.

## Current Data Coverage

Current processed datasets include:

- Monthly copper prices from ALFRED/IMF (`PCOPPUSDM`), in USD per metric tonne.
- Annual ICSG mine production, refined production, and refined copper usage data.
- Derived refined-copper market balance.
- Secondary refined-copper production, digitized from an ICSG chart and labelled as approximate.
- Annual exchange inventories through 2022.
- A canonical LME copper inventory series combining:
  - annual Copper Council observations through 2022; and
  - monthly Cochilco/Reuters observations from January 2023 onward.

The annual-to-monthly LME transition is retained explicitly through source and observation-frequency fields. Annual data is not artificially converted into monthly data.

## Validation Principles

- Dates are standardized to calendar year-end or month-end.
- Observations are checked for duplicates, missing values, and expected coverage.
- Cross-source validation is performed where sources overlap.
- Source-transition boundary diagnostics are performed where direct overlap is unavailable.
- Digitized chart data is treated as approximate, not exact.
- Source-specific cleaned datasets remain available after canonical series are created.

## Running the Notebook

Install the required Python packages in your environment:

```bash
pip install pandas numpy pdfplumber lxml xlrd jupyter
```

Then launch Jupyter and open the data-processing notebook:

```bash
jupyter notebook src/data_processing.ipynb
```

Run the notebook from top to bottom when reproducing the data-cleaning workflow.

## Key Sources

- [ALFRED / IMF Primary Commodity Prices](https://alfred.stlouisfed.org/series?seid=PCOPPUSDM)
- [International Copper Study Group](https://icsg.org/)
- [Chilean Copper Commission (Cochilco)](https://www.cochilco.cl/)
- [London Metal Exchange](https://www.lme.com/)
- Copper Council exchange-stock tables
- Statista refinery-production data, used as a validation source

## Limitations

Exchange inventories are visible exchange stocks, not total global physical inventories. Some fundamental series are annual while market series are monthly. Source data may be revised, restricted, or subject to different reporting conventions. These limitations are documented in the project metadata and considered in interpretation.

## Disclaimer

This repository is for educational and research purposes only. It does not constitute investment research, investment advice, or a recommendation to buy or sell any security, derivative, commodity, or fund.
