# IBNR Chain Ladder (chainladder package)

Estimates IBNR (incurred but not reported) for a Motor Private claims listing using the Basic Chain Ladder method, built with the Python [`chainladder`](https://chainladder-python.readthedocs.io) package.

## Method

- **Origin period:** month of loss (Jan to Dec 2025)
- **Development period:** reporting lag in months (loss date to intimation date)
- **Valuation date:** 31 Dec 2025
- **Triangles:** cumulative claim counts and cumulative incurred amount
- **Factors:** volume-weighted age-to-age factors, tail factor 1.0
- **Sensitivity:** volume, simple and regression averages compared

## Results

| | Reported | Ultimate | IBNR | IBNR % |
|---|---|---|---|---|
| Claim count | 527 | 573.9 | 46.9 | 8.9% |
| Incurred amount | 18,767,475 | 20,987,674 | 2,220,199 | 11.8% |

The package output reconciles exactly to a manual pandas chain ladder calculation.

## Data cleaning

- Dates parsed from the raw text columns because the sheet's computed date columns contain Excel errors
- Dropped rows with impossible dates, claims reported before the loss, and exact duplicates
- Only 2025 losses used, since intimations start in Jan 2025 and earlier loss months are only partly observed

## Files

- `IBNR_chain_ladder_package.ipynb`: full analysis

## Requirements

```
pip install pandas openpyxl matplotlib chainladder
```

Update the `PATH` variable at the top of the notebook to point to your Excel file.
