# test_docs

## Overview

This document provides an overview of the advanced technical analysis strategy implemented in the `Algotrading_Advanced TA Backtesting.py` script. The strategy uses a combination of technical indicators to generate buy and sell signals and includes a trailing stop feature to manage trades.

## Strategy Logic

### Signal Generation

The strategy generates signals based on the market condition, which can be trending, ranging, or choppy. The signals are determined using various technical indicators:

- **Trending Market:**
  - **Buy Signal:** Generated when the market is trending, the Supertrend indicator is positive, the RSI is above 55, and the 50-period moving average is above the 200-period moving average.
  - **Sell Signal:** Generated when the market is trending, the Supertrend indicator is negative, the RSI is below 45, and the 50-period moving average is below the 200-period moving average.

- **Ranging Market:**
  - **Buy Signal:** Generated when the closing price is below the lower Bollinger Band and a volatility breakout is detected.
  - **Sell Signal:** Generated when the closing price is above the upper Bollinger Band and a volatility breakout is detected.

- **Choppy Market:**
  - **Buy Signal:** Generated only if a volatility breakout is confirmed.

### Trade Execution with Stop Loss

The strategy executes trades with stop-loss and take-profit levels, and it includes a trailing stop feature:

- **Stop Loss and Take Profit:** These levels are initially set based on the Average True Range (ATR) multiplied by a specified multiplier.
- **Trailing Stop:** If enabled, the trailing stop level is adjusted as the price moves in favor of the trade. The trailing stop is activated once the price exceeds 50% of the take-profit level.

### Performance Metrics

The strategy calculates several key performance metrics:

- **Cumulative Return:** The total return of the strategy over the backtesting period.
- **Sharpe Ratio:** A measure of risk-adjusted return, calculated as the mean return divided by the standard deviation of returns, annualized.
- **Sortino Ratio:** Similar to the Sharpe Ratio but only considers downside deviation, providing a measure of risk-adjusted return that penalizes only negative volatility.
- **Max Drawdown:** The maximum observed loss from a peak to a trough during the backtesting period.
- **Win Rate:** The proportion of trades that were profitable.
- **Number of Trades:** The total number of buy and sell signals generated during the backtesting period.

## Execution Flow

1. **Load Dataset:** The script begins by loading a dataset containing historical price data and technical indicators.
2. **Generate Signals:** The `generate_signals_advanced` function is called to generate buy, sell, or hold signals based on the strategy logic.
3. **Execute Strategy:** The `execute_strategy_with_stop_loss` function is executed to simulate trades based on the generated signals, incorporating stop-loss, take-profit, and trailing stop features.
4. **Calculate Performance Metrics:** The `calculate_performance_metrics` function computes the strategy's performance metrics, which are then printed to the console.

## Usage

To run the strategy, ensure that the dataset `backtest_data_with_indicators.csv` is available in the working directory. Execute the script to perform backtesting and view the performance metrics.

```bash
python Algotrading_Advanced TA Backtesting.py
```

This will output the performance metrics of the strategy, providing insights into its effectiveness and risk-adjusted returns.