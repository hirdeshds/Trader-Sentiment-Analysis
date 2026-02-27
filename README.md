# Trader Sentiment Analysis

This project analyzes how trader behavior and performance change across market sentiment regimes (Fear vs Greed) using:
- `Datasets/fear_greed_index.csv`
- `Datasets/historical_data.csv`

## Repository Contents
- `notebook.ipynb` — full Part A/B/C analysis
- `charts/` — generated evidence charts
  - `fear_vs_greed_performance.png`
  - `fear_vs_greed_behavior.png`
  - `trader_segments.png`
- `analysis_summary.md` — concise write-up (methodology, insights, strategy ideas)

## Setup
Python 3.10+ recommended.

Install dependencies:
```bash
pip install pandas matplotlib numpy
```

## How to Run
1. Open `notebook.ipynb`.
2. Run all cells top-to-bottom.
3. Review generated charts in `charts/` and the summary in `analysis_summary.md`.

## Method Overview
1. Load and quality-check both datasets (shape, missing values, duplicates).
2. Convert and align timestamps to daily dates.
3. Merge trade data with sentiment by date.
4. Build key metrics:
   - daily PnL
   - win rate
   - average trade size
   - leverage proxy distribution
   - trades per day
   - long/short ratio
5. Compare Fear vs Greed outcomes.
6. Segment traders by leverage, frequency, and consistency.
7. Produce actionable strategy rules from evidence.

## Notes
- `leverage_proxy` is approximated as `abs(Size USD) / abs(Start Position)` and winsorized at the 99th percentile to reduce outlier distortion.
- Drawdown proxy is computed from cumulative daily PnL at market level.
