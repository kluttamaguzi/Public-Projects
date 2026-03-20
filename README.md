# Public-Projects
This Repository stores all projects meant for the general public
 ## Evaluating Stock Return Predictability and Trading Performance Using LASSO

## Objective
This project investigates whether next-day stock returns can be predicted using historical price data and technical indicators, and whether such predictions can be translated into a profitable trading strategy.

---

## Approach

### Data
- Historical stock price data (Yahoo Finance via `yfinance`)
- Daily frequency

### Feature Engineering
The following features were constructed:
- Returns
- Lagged returns (Lag_1, Lag_2)
- Moving averages (MA5, MA10)
- MA Ratio (MA5 / MA10)
- Rolling volatility (10-day standard deviation)

### Target
- Next-day return using:
target = Returns.shift(-1)
- 
### Model
- LASSO regression
- Time-series split (train: up to 2022, test: 2023 onward)
- Baseline comparison included

---

## Evaluation Metrics

- RMSE (Root Mean Squared Error)
- Directional Accuracy
- Strategy Return vs Market Return
- Sharpe Ratio
- Maximum Drawdown

---

## Trading Strategy

A simple long-only strategy was implemented:

- Go long when predicted return > 0
- Stay out of the market otherwise

Strategy performance was compared against a buy-and-hold benchmark.

---

## Results

- **Market Return:** ~49.8%
- **Strategy Return:** ~49.8%
- **Directional Accuracy:** ~56%
- **Sharpe Ratio:** 0.13
- **Max Drawdown:** -14.9%

---

## Key Insights

- The model demonstrates **slight predictive power**, as directional accuracy exceeds random chance.
- However, this **does not translate into improved trading performance** under a naive strategy.
- The model generates signals too frequently, effectively replicating a buy-and-hold strategy.
- This highlights the difficulty of extracting economically meaningful signals from financial time series.

---

## Limitations

- No transaction costs or slippage considered
- Linear model (LASSO) may not capture nonlinear market dynamics
- Daily returns are highly noisy and difficult to predict

---

## Future Improvements

- Apply threshold-based trading to filter weak signals
- Incorporate transaction costs
- Explore nonlinear models (e.g., tree-based methods)
- Test across multiple assets and time periods

---

## Conclusion

While machine learning can identify weak predictive signals in financial data, translating these signals into consistent trading profits remains challenging. This project demonstrates the importance of linking predictive modeling to economic outcomes.

---
