# Trader Sentiment Analysis — Summary

## Methodology
I merged daily sentiment (`fear_greed_index.csv`) with per-trade history (`historical_data.csv`) by date after cleaning and timestamp normalization. I computed account/day and market/day metrics: daily PnL, win rate, average trade size, leverage proxy, trades/day, and long/short ratio. Then I compared Fear vs Greed regimes and built three trader segment views:
1. High vs low leverage
2. Frequent vs infrequent traders
3. Consistent winners vs inconsistent traders

## Evidence-Based Insights
1. **PnL differs by sentiment regime**
   - Mean daily PnL on Fear days is higher than on Greed days in this sample.
   - Chart/table: `fear_vs_greed_performance.png` and notebook performance table.

2. **Win rate is higher in Greed regimes**
   - Despite lower mean daily PnL, Greed days show higher average win rate.
   - This suggests larger but less frequent upside on Fear days, while Greed has steadier hit rate.

3. **Behavior shifts with sentiment**
   - Fear days show higher trade frequency and slightly larger average trade size in this sample.
   - Greed days show higher average leverage.
   - Chart/table: `fear_vs_greed_behavior.png` and behavior comparison table.

4. **Segment performance is not linear with leverage alone**
   - Low-leverage segment shows stronger mean total PnL than high-leverage segment in this run.
   - Frequent traders outperform infrequent traders on both mean PnL and mean win rate.
   - Chart/table: `trader_segments.png` and segmentation tables.

## Strategy Recommendations (Actionable Output)
1. **Fear-day risk control rule**
   - For weaker-consistency traders, cut leverage and reduce position size on Fear days.
   - Rationale: Fear periods exhibit larger PnL dispersion and deeper downside tails.

2. **Frequency gating rule by segment**
   - Allow higher trade frequency only for consistent winners.
   - For inconsistent traders, cap trades/day and require stronger setup filters before entry.

## Reproducibility
- Run `notebook.ipynb` top-to-bottom.
- Charts regenerate under `charts/`.
- Analysis is fully based on the provided two CSV files.
