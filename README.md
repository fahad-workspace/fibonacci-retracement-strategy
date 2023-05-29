# Fibonacci Retracement Strategy

This script implements a robust trading strategy built on TradingView's Pine Script, which utilizes Fibonacci retracement levels for defining entry points in conjunction with the Average True Range (ATR) indicator to dynamically establish stop-loss and take-profit levels.

The strategy takes several factors into consideration: trend following, volume, volatility, overbought or oversold conditions, and drawdown management. Its primary goal is to manage risk effectively via dynamic trade size calculations and introducing a cooldown period following losing trades.

## Key Parameters
- `lookback`: Defines the period for highest high and lowest low. Adjust this to fine-tune trade entry points.
- `riskPerTrade`: Defines the risk on a single trade as 1% of the total equity.
- `volLookback`: Determines the period for volume average.
- `cooldownPeriod`: Establishes a resting period in bars post a losing trade.
- `maxConsecLosses`: Sets the maximum number of consecutive losses allowed before ceasing trading.
- `maxDrawdown`: Determines the maximum drawdown permitted before the strategy halts trading.
- `takeProfitMultiplier` and `atrMultiplier`: Control the take-profit and stop-loss levels.
- `slippage`: An estimate of the price change between trade initiation and execution.

## Key Features
1. **Trading strategy name and parameters**: The script begins by setting the name and essential parameters of the strategy.

2. **Variable definitions**: Variables for tracking highest equity, the last trade's bar, consecutive losses, and trade allowance are established.

3. **Relative Strength Index (RSI) indicator**: Used to evaluate whether the asset is in an overbought or oversold condition.

4. **Equity high and drawdown calculation**: The highest equity level and the drawdown from the peak are calculated, with `tradeAllowed` being set to false if drawdown exceeds the `maxDrawdown` threshold.

5. **Previous move calculation**: The difference between the highest high and the lowest low over the lookback period is computed.

6. **Fibonacci retracement levels**: Derived from the `previousMove` to indicate potential levels of interest.

7. **Trend and volume filters**: A 200-period Simple Moving Average (SMA) acts as a trend filter, while an average volume over `volLookback` period serves as a volume filter.

8. **Average True Range (ATR)**: Measures market volatility to help in the dynamic calculation of stop-loss and take-profit levels.

9. **Cooldown period**: Ensures no new trades are initiated during the `cooldownPeriod` after a losing trade.

10. **Trade condition definition**: Rules for initiating a long or short trade are defined.

11. **Trade execution**: If trade conditions are satisfied, the stop-loss level and trade quantity are calculated before initiating the trade and setting the stop-loss and take-profit levels.

12. **Trade annotation**: Details of each trade, including the quantity, stop-loss level, and take-profit level, are labeled on the chart.

The strategy is versatile and can be modified to suit various financial instruments, risk profiles, and market conditions. However, please remember that backtesting results do not guarantee future performance. Always align your trading strategy with your risk tolerance and investment goals.
