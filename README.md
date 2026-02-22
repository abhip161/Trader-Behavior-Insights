# Trader Performance vs Market Sentiment  
## Objective
Analyze how Bitcoin market sentiment (Fear vs Greed) relates to trader behavior and performance on the Hyperliquid platform, and derive actionable trading strategies based on observed patterns.

---

## Datasets
1. **Bitcoin Fear/Greed Index**
   - Daily sentiment labels (Fear / Greed)
2. **Hyperliquid Historical Trader Data**
   - Trade-level execution data including PnL, side, size, leverage proxies, and timestamps

Datasets were aligned at a **daily level** using UTC-normalized dates.

---

## Methodology

### Data Preparation
- Cleaned missing values and removed duplicate records
- Standardized timestamps and aligned both datasets by date
- Derived key trader-level metrics:
  - Daily PnL, win rate, trade count
  - Average trade size and long/short ratio
  - Drawdown proxy using cumulative PnL
- Built trader profiles aggregating performance, risk, and activity metrics

### Analysis
- Compared performance metrics between Fear and Greed days using:
  - Boxplots and summary statistics
  - Mann–Whitney U tests for statistical significance
- Studied behavioral changes across sentiment regimes:
  - Trade frequency
  - Directional bias (long/short ratio)
  - Position sizing
- Segmented traders into interpretable groups:
  - Frequent vs Infrequent traders
  - Consistent Winners vs Inconsistent vs Losers
- Explored segment × sentiment interactions to identify differential behavior

### Bonus Analysis
- Clustered traders into behavioral archetypes using K-Means
- Built a lightweight predictive model to estimate next-day profitability using sentiment and behavior features

---

## Key Insights

1. **Fear regimes suppress trader performance**
   - Median daily PnL is significantly lower on Fear days
   - Drawdowns are deeper, especially for high-risk and high-leverage traders

2. **Risk-taking increases during Greed**
   - Traders increase trade frequency and position size on Greed days
   - Market-wide leverage and directional bias rise during Greed regimes

3. **Skill matters more during Greed**
   - Consistent Winners outperform significantly on Greed days
   - Infrequent and inconsistent traders fail to capture the same upside

---

## Strategy Recommendations

### Strategy 1 — *Fear-Day Leverage Cap*
- **Rule:** Cap leverage at ≤5× during Fear regimes  
- **Target segment:** High-leverage traders  
- **Rationale:** This segment experiences the worst tail losses during Fear days  
- **Expected outcome:** Reduced drawdowns and improved capital preservation

---

### Strategy 2 — *Greed-Day Frequency Boost for Consistent Winners*
- **Rule:** Allow up to 2× trade frequency on Greed days  
- **Eligibility filter:** Trailing 14-day win rate > 55%  
- **Target segment:** Consistent Winners only  
- **Expected outcome:** Capture momentum-driven alpha while maintaining discipline

---

## Reproducibility Notes
- All charts are saved to the `charts/` directory
- All key result tables are exported as CSV files in `tables/`
- Notebook runs end-to-end without manual intervention
- Raw datasets remain unchanged in `data/`

---

## Conclusion
Market sentiment has a clear and measurable impact on trader behavior and performance.  
By combining sentiment signals with trader segmentation, it is possible to design **simple, interpretable, and actionable trading rules** that improve risk-adjusted outcomes.

This analysis demonstrates how behavioral data and sentiment indicators can be integrated to inform smarter trading strategies.
