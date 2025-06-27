# Pairs Trading on S&P 500 using K-Means Clustering

This project implements a systematic pairs trading strategy on the S&P 500 universe, leveraging modern statistical and machine learning techniques to identify, select, and test robust trading pairs. The entire workflow and analysis are contained in a single Jupyter Notebook (`.ipynb`).

---

## Project Overview

Pairs trading is a market-neutral strategy that profits from relative price movements between two historically related assets. The strategy bets on the tendency of the price relationship between two stocks to revert to its historical average after significant divergence.

This notebook follows a structured workflow:
1. **Clustering via K-Means:** Stocks are grouped based on the similarity of their log returns, volatility, and trading volume.
2. **Correlation Analysis:** Within each cluster, pairs of stocks with high correlation in their log returns are shortlisted as potential trading candidates.
3. **Cointegration Testing:** Each shortlisted pair is statistically tested to confirm that their price relationship is mean-reverting, a crucial requirement for pairs trading.
4. **Hedge Ratio Calculation:** For each cointegrated pair, the hedge ratio is estimated so that a stationary spread can be constructed.
5. **Pair Selection:** The pair with a hedge ratio closest to 1 is selected, ensuring simplicity and balanced exposure.
6. **Signal Generation:** Trading signals are generated based on the spread’s z-score, with entry and exit thresholds set at ±1 and 0, respectively.
7. **Backtesting:** The trading strategy is simulated on historical data, and key performance metrics are calculated.

---

## Theory and Methodology

### 1. K-Means Clustering

K-Means is an unsupervised machine learning algorithm that partitions stocks into clusters based on their log returns, volatility, and volume. This ensures that only similar stocks are considered together, increasing the likelihood of finding robust pairs.

### 2. Correlation Analysis

Pairs with high correlation in their log returns are identified within each cluster. High correlation indicates that stocks tend to move together, which is necessary for pairs trading.

### 3. Cointegration Test

Cointegration testing checks if the price series of two stocks maintain a stable, mean-reverting relationship over time, rather than just moving together temporarily as in correlation.

### 4. Hedge Ratio Calculation and Pair Selection

The hedge ratio determines how much of one stock to hold against another to create a stationary spread. The pair with a hedge ratio closest to 1 is selected for simplicity and to maintain balance.

### 5. Trading Signal Generation

A spread between the two stocks is monitored, and trading signals are generated based on how far the spread deviates from its historical mean (measured by z-score). Trades are entered when the z-score moves beyond ±1, and exited when it returns to 0.

### 6. Backtesting

The strategy is tested on historical data to evaluate its performance using key financial metrics.

---

## Performance Summary

- **Backtest Period:** 2020-07-01 to 2023-07-01
- **Number of Trading Days:** 734  
- **CAGR (Compound Annual Growth Rate):** 20.749%  
- **Cumulative Return:** 73.181%  
- **Maximum Drawdown:** -10.776%  
- **Sharpe Ratio:** 1.621  
- **Frequency of Trades:** 192 trades total (≈65.92/year)

---

## File Structure

- `Pairs_Trading_S&P500.ipynb` — Complete code, analysis, and results.

---

If you made it this far, thanks for reading—hope you enjoyed the ride!
