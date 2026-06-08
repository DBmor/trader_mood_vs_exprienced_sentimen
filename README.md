# Trader Behavior Analysis vs. Market Sentiment

A quantitative behavior analysis project engineered for **Primetrade.ai** to explore the relationship between trader execution habits and prevailing market psychological regimes. This project processes over 211,000 transaction records and cross-references them against macro market sentiment data to identify trading anomalies and optimize platform safety features.

---

## 📌 Project Overview & Intent

The core objective of this project is to track how different cohorts of traders modify their risk exposure, trading frequency, and performance when the general market sentiment shifts from intense panic to euphoria. 

The data processing pipeline explicitly implements:
1. **Timestamp Alignment:** Minute/second-level trader logs are dynamically truncated to a daily format (`YYYY-MM-DD`) and inner-joined with macro sentiment logs.
2. **Behavioral Cohort Classification:** Rather than using static brackets, traders are programmatically segmented based on historical trade frequency (`Frequent` vs. `Infrequent`) and net performance (`Profitable` vs. `Loss Making`).
3. **Advanced Risk Tracking:** Computes absolute position sizing values ($Size \times Price$) alongside true win ratios across every market environment.

---

## 📈 Core Conclusions & Empirical Discoveries

Running this analysis on the transaction ledger uncovered critical behavioral anomalies that can drive smarter trading strategies:

### 1. The Position Sizing Paradox
Our metrics reveal a major risk-mitigation flaw when sentiment reaches extreme ends. During **Extreme Fear** regimes, the trading pool shrinks to **21,400** executions, but traders use an inflated position size averaging **$5,349.73** per trade. 

Conversely, during periods of market euphoria (**Extreme Greed**), trade volume doubles to **39,992** executions due to structural FOMO, but the average position size drops by over 41% to **$3,112.25**. Traders over-allocate trade frequency but under-allocate capital efficiency exactly when market trends are strongest.

### 2. High-Greed Volatility Barriers
While the visible average win rate rises cleanly to **46%** and the calculated profit factor spikes to **11.02** during Extreme Greed, the **median PnL stays pinned at exactly 0.0** across every single sentiment regime. This proves that a tiny handful of outsized outlier wins distort the baseline averages, while the vast majority of ordinary participants break even or take steady losses.

### 3. Actionable Algorithmic Application
To maximize user safety, Primetrade.ai can initialize a programmatic **Volatility Cushion Directive**:
* **Euphoria Risk Brake:** Automatically cap maximum trading frequency for retail accounts when sentiment hits Extreme Greed to prevent account churn and transaction fee drag.
* **Margin Floor Scaling:** Enforce slightly higher minimum position sizing limits on high-conviction setups during greed environments, guiding users to deploy capital efficiently rather than over-trading micro-sizes.

---

## 💾 Datasource Information

The primary transaction data used for this project is compiled from live public execution records:
* **Trader Transaction Ledger:** https://docs.google.com/spreadsheets/d/1SQqum_vPCbSC8IjFBVadZo-gSN-m-L2OLF48NUqlYMA/edit?gid=180502809#gid=180502809
* **Market Sentiment Data:** https://drive.google.com/file/d/1IAfLZwu6rJzyWKgBToqwSmmVYU6VbjVs/view

## How to run it 
pip install -r requirements.txt 
* jupyter notebook Trader_Behavior_vs_Market_Sentiment.ipynb
