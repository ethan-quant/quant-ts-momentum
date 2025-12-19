# Quant Research Memo

**Strategy:** Time-Series Momentum with Risk Regime Filter  
**Author:** Ethan M
**Status:** Research / Educational  
**Date:** _(add today’s date if you want)_

---

## 1. Strategy Objective

The objective of this strategy is to capture medium-term trends across liquid asset classes while maintaining strict risk control. The strategy prioritizes capital preservation and consistency over maximizing raw returns, making it suitable as a low-risk systematic allocation or portfolio sleeve rather than a standalone return-maximizing strategy.

---

## 2. Investment Hypothesis

Assets that have exhibited positive returns over the past 12 months tend to continue trending due to behavioral and structural market effects such as underreaction, gradual information diffusion, and risk premia. However, time-series momentum strategies are known to underperform during broad market drawdowns and non-trending regimes. Introducing a simple market regime filter can reduce exposure during unfavorable environments and improve overall risk-adjusted performance.

---

## 3. Asset Universe

The strategy trades a diversified set of highly liquid exchange-traded funds (ETFs) representing major asset classes:

- **SPY** — US equities  
- **EFA** — Developed ex-US equities  
- **EEM** — Emerging market equities  
- **TLT** — Long-duration US Treasuries  
- **IEF** — Intermediate-duration US Treasuries  
- **GLD** — Gold  

This universe provides cross-asset diversification and sufficient historical data for robust backtesting.

---

## 4. Signal Construction

A time-series momentum signal is computed for each asset using 12-month total return (approximately 252 trading days), excluding the most recent trading day to avoid look-ahead bias.

- **Signal = 1 (long)** if trailing 12-month return > 0  
- **Signal = 0 (flat)** otherwise  

The strategy is long-only and may hold cash when signals are inactive.

---

## 5. Risk Regime Filter

A market regime filter is applied to reduce exposure during unfavorable conditions:

- **Risk-on:** SPY price above its 200-day moving average  
- **Risk-off:** SPY price below its 200-day moving average  

When the filter is risk-off, all positions are closed and the portfolio holds cash until the regime turns favorable again.

---

## 6. Portfolio Construction and Risk Management

- **Rebalancing frequency:** Quarterly  
- **Position sizing:** Inverse volatility weighting across active signals  
- **Volatility targeting:** 10% annualized portfolio volatility  
- **Position limits:** Maximum 30% per asset (applied after volatility scaling)  
- **Cash management:** Residual capital remains in cash when constraints bind  
- **Transaction costs:** 5 basis points per unit of turnover  

Risk constraints are applied conservatively to prioritize drawdown control and portfolio stability.

---

## 7. Backtest Results (Net of Transaction Costs)

Over the full backtest period, the strategy exhibited the following characteristics:

- **Annualized return:** ~0.8%  
- **Annualized volatility:** ~1.1%  
- **Sharpe ratio:** ~0.70  
- **Maximum drawdown:** ~−1.6%  
- **Average annual turnover:** ~5%  

The strategy displays low volatility, shallow drawdowns, and stable risk-adjusted returns.

---

## 8. Interpretation of Results

Although absolute returns are modest, the strategy demonstrates strong capital preservation and risk efficiency. The addition of the risk regime filter materially improves drawdown behavior and Sharpe ratio by avoiding periods when momentum signals historically underperform. The resulting performance profile is consistent with a defensive systematic allocation rather than an aggressive return-seeking strategy.

---

## 9. Limitations and Future Research

Key limitations include:

- Conservative risk constraints that limit return potential  
- Dependence on a single regime filter definition  
- No use of leverage or short exposure  

Potential extensions include:

- Combining this strategy with complementary signals (e.g., mean reversion)  
- Testing alternative regime indicators (volatility or macro-based filters)  
- Introducing controlled leverage within strict drawdown limits  

---

## 10. Conclusion

This research demonstrates that a simple and transparent time-series momentum strategy, when paired with disciplined risk management and regime awareness, can produce stable and defensible risk-adjusted performance. The results highlight the importance of risk controls and environmental context in systematic trading strategies.
