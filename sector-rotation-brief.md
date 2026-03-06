# LFC MarketView: Sector Rotation Strategy

## Project Type
Solo Jupyter Notebook

## Overview
Build a quantitative sector rotation strategy using momentum signals to outperform the S&P 500. Starting from the DataCamp Python Finance Tutorial, you'll extend basic stock analysis to a multi-sector portfolio that automatically rotates capital to the strongest-performing sectors.

This project teaches you how professional quants build systematic trading strategies: data collection → feature engineering → signal generation → backtesting → performance analysis.

(Optionally you can increase the data from 11 to ~25. This or any other alterations can be done as you wish.)

## What You'll Build
A complete Jupyter notebook implementing:
1. Download 11 sector ETF data (XLK, XLF, XLE, XLV, XLI, XLP, XLY, XLU, XLB, XLRE, XLC)
2. Calculate momentum signals (3-month and 6-month returns)
3. Rank sectors and allocate to top performers
4. Backtest strategy with transaction costs
5. Compare performance vs SPY benchmark

## Important
The use of Generative AI (Claude) is encouraged, however it remains essential that the student understands and is able to explain without the use of the technology any design choices/implementations in the code.

## Learning Objectives
- Understand momentum as a quantitative signal
- Implement sector rotation logic from scratch
- Build proper backtesting framework (no lookahead bias)
- Calculate risk-adjusted performance metrics
- Visualize strategy performance vs benchmark

## PART 1: Data & Momentum Signals

**Goal**: Download sector ETF data and calculate momentum features

**Tasks**:
- Fork DataCamp Python Finance Tutorial repository
- Download 11 sector ETFs using yfinance (2015-2025)
- Calculate returns: 1-month, 3-month, 6-month
- Calculate 200-day simple moving average
- Save clean dataset as `sector_data.csv`

**Deliverables**:
- [ ] DataCamp tutorial code runs successfully
- [ ] 11 sector ETFs downloaded (10+ years data)
- [ ] Momentum features calculated for each sector
- [ ] Data exploration: correlation heatmap between sectors
- [ ] README: Explain what sector ETFs are and why rotation works

## PART 2: Strategy Logic & Backtesting

**Goal**: Implement rotation strategy and backtest

**Strategy Rules**:
```python
# Monthly rebalancing (last trading day of month)
# For each month:
1. Filter: Keep only sectors above 200-day SMA
2. Rank: Score by 6-month momentum (returns)
3. Allocate: 
   - Top 3 sectors: 30% each
   - Cash/T-bills: 10%
4. Calculate returns accounting for:
   - Transaction costs (0.1% per trade)
   - Monthly rebalancing
```

**Tasks**:
- Code sector filtering (above/below 200-day SMA)
- Rank sectors by momentum score
- Build allocation logic (top 3 = 90%, cash = 10%)
- Implement monthly rebalancing
- Calculate portfolio returns with transaction costs

**Deliverables**:
- [ ] Strategy logic coded and documented
- [ ] Backtesting engine with proper train/test split
- [ ] Transaction costs included (0.1% per trade)
- [ ] No lookahead bias (only use past data for decisions)
- [ ] README: Explain momentum ranking and why filtering by SMA matters

## PART 3: Performance Analysis & Visualization

**Goal**: Analyze results, create performance report

**Metrics to Calculate**:
```python
Annual Return (CAGR)
Sharpe Ratio = (Return - RiskFree) / Volatility
Max Drawdown = max((Peak - Trough) / Peak)
Win Rate = % of months with positive return
Turnover = average % portfolio changed per month
```

**Visualizations**:
1. Growth of $10,000 chart (strategy vs SPY)
2. Drawdown chart (strategy vs SPY)
3. Sector allocation heatmap over time
4. Monthly returns distribution histogram
5. Rolling 12-month Sharpe ratio

**Tasks**:
- Calculate all performance metrics
- Create 5 publication-quality charts
- Build performance comparison table
- Analyze when strategy outperforms vs underperforms
- Document limitations and potential improvements

**Deliverables**:
- [ ] Growth of $10k chart vs SPY benchmark
- [ ] Performance table with all metrics
- [ ] Sector allocation heatmap (shows rotation over time)
- [ ] Drawdown comparison chart
- [ ] README: Explain Sharpe ratio, max drawdown, why strategy beat/lost to benchmark


**Performance Table Example**:

| Metric | Sector Rotation | SPY Benchmark | Difference |
|--------|----------------|---------------|------------|
| CAGR | 14.2% | 11.8% | +2.4% |
| Sharpe Ratio | 1.12 | 0.89 | +0.23 |
| Max Drawdown | -22% | -28% | +6% |
| Win Rate | 58% | 54% | +4% |
| Volatility | 16.5% | 18.2% | -1.7% |

**Optional Slides** (3 slides):
1. Strategy Logic: How momentum rotation works
2. Key Results: Growth chart + performance table
3. Insights: When it works, when it doesn't, why

## Success Metrics

**Minimum Viable Product (MVP)**:
- [ ] 11 sector ETFs with 10+ years data
- [ ] Momentum strategy coded correctly
- [ ] Backtest with transaction costs
- [ ] Growth chart vs SPY
- [ ] Performance table with 5+ metrics
- [ ] Clean, documented code

**Stretch Goals (Optional)**:
- [ ] Test multiple momentum periods (3mo, 6mo, 12mo)
- [ ] Add volatility filter (avoid high-volatility sectors)
- [ ] Regime detection (bull vs bear markets)
- [ ] Compare equal-weight vs momentum-weight allocation
- [ ] Monte Carlo simulation of strategy robustness

## Resources

**Article**: https://ultimamarkets.medium.com/sector-rotation-investing-a-data-driven-investing-strategy-93d9d8906ed5

**DataCamp Tutorial**: https://github.com/datacamp/datacamp-community-tutorials/blob/master/Python%20Finance%20Tutorial%20For%20Beginners/Python%20For%20Finance%20Beginners%20Tutorial.ipynb

**Sector ETFs (SPDR)**:
- XLK (Technology)
- XLF (Financials)
- XLE (Energy)
- XLV (Healthcare)
- XLI (Industrials)
- XLP (Consumer Staples)
- XLY (Consumer Discretionary)
- XLU (Utilities)
- XLB (Materials)
- XLRE (Real Estate)
- XLC (Communication Services)

**Key Papers**:
- Faber (2007): "A Quantitative Approach to Tactical Asset Allocation"
- Moskowitz & Grinblatt (1999): "Do Industries Explain Momentum?"
