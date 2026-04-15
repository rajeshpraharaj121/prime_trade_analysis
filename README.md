# 📊 Trader Performance vs Market Sentiment — Primetrade.ai Round-0 Assignment

**Author:** Rajesh Praharaj  
**Role Applied:** Data Science / Analytics Intern  
**Company:** Primetrade.ai

---

## 🗂️ Project Structure

```
├── primetrade_analysis.ipynb   # Main analysis notebook
├── fear_greed_index.csv        # Bitcoin Fear/Greed Index dataset
├── historical_data.csv         # Hyperliquid trader data
└── README.md
```

---

## 🚀 How to Run

### Requirements
```bash
pip install pandas numpy matplotlib seaborn scipy nbformat jupyter
```

### Run the Notebook
```bash
jupyter notebook primetrade_analysis.ipynb
```

> Place both CSV files in the same directory as the notebook before running.

---

## 📋 Methodology

### Data Preparation
- Loaded and explored both datasets (211,224 raw trade rows; 2,644 Fear/Greed entries)
- Parsed `Timestamp IST` with `dayfirst=True` to get daily dates
- Filtered out non-trade rows (Spot Dust Conversion, Liquidations, Settlements)
- Merged on `date` → 211,066 matched trades across 475 days (May 2023 – May 2025)
- Created daily aggregates per trader: PnL, win rate, trade count, avg size, long ratio

### Analysis
- Compared performance (PnL, win rate) and behavior (frequency, size, bias) across all 5 sentiment classes
- Statistical significance tested via independent t-test (Fear vs Greed PnL)
- Segmented 32 traders into High/Low Risk and High/Low Frequency groups
- Heatmapped win rates across top 15 most-active traders × 3 sentiment buckets

---

## 🔑 Key Insights

| # | Insight | Evidence |
|---|---------|----------|
| 1 | Fear markets generate higher average daily PnL | $5,468 (Fear) vs $3,295 (Greed) |
| 2 | Traders trade more aggressively during Fear | 134 trades/day (Extreme Fear) vs 77 (Extreme Greed) |
| 3 | Long bias peaks during Fear (contrarian behaviour) | 60% long ratio in Extreme Fear |
| 4 | Win rate peaks at Extreme Greed, not PnL | 39.3% win rate but lower position sizes |
| 5 | High-risk traders benefit most from Fear volatility | ~2x outperformance vs low-risk segment |

---

## 💡 Strategy Recommendations

**Strategy 1 — "Fear is Opportunity"**  
During Fear days (FGI < 40), high-risk traders should scale position size 1.3–1.5x vs their Neutral-day baseline, maintaining a long bias with tighter stop-losses.

**Strategy 2 — "Greed = Precision, Not Volume"**  
During Greed days (FGI > 60), high-frequency traders should cut daily trade count by 30–40% and focus only on high-conviction setups to improve win rate over raw volume.

---

*Total trades analyzed: 211,066 | Unique traders: 32 | Period: May 2023 – May 2025*
