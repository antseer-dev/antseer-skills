---
name: "geopolitical-risk-scanner"
description: "Macro Risk Synthesis & Impact Quantification for crypto investors"
strategy_agent: "risk"
version: "1.0.0"
created_at: "2026-03-26T00:00:00Z"
skill_lifecycle: "draft"
author: "creator-agent"
---

# Geopolitical Risk Scanner

Synthesizes macroeconomic and geopolitical events into quantifiable uncertainty indicators, providing direct portfolio impact analysis tailored for cryptocurrency investors.

## Overview

This skill monitors global macroeconomic indicators and geopolitical developments to assess their impact on cryptocurrency markets. It synthesizes multiple data sources to generate actionable risk scores for portfolio allocation decisions.

## Demand Context

**Source Gap:** gap_001
**Opportunity Type:** Macro Risk Synthesis & Impact Quantification
**Target User Personas:** researcher, investor
**Sentiment:** fear (intensity: 0.712)

### Evidence Signals
- Economists have pulled up their risk assessments of a U.S. cont
- Zero or negative returns in last 2 years in stock market
- The war is starting to make its mark on the global economy

### L1 Cluster Labels
- Economic Downturn and Market Impact Concerns
- Inflation, Interest Rates, and Systemic Financial Stability

## Features (Data Inputs)

| Feature | Source | Description |
|---------|--------|-------------|
| geopolitical_tension_index | Macromicro/OurCurrency | Geopolitical risk index |
| macro_uncertainty_vix | CBOE | Economic policy uncertainty VIX |
| inflation_expectation_5y | Fed/USTreasury | 5-year inflation breakeven |
| recession_probability | Atlanta Fed GDPNow | Recession probability estimate |
| global_risk_sentiment | LunarCrush | Social sentiment for risk assets |
| crypto_correlation_sp500 | CoinMetrics | BTC-SPX 30-day correlation |
| fear_greed_index | Alternative.me | Market fear/greed indicator |
| bond_yield_spread | FRED | Yield curve inversion indicator |

## Entry Conditions

Triggered when geopolitical risk signals exceed threshold:

```yaml
entry_conditions:
  - condition: geopolitical_tension_index
    operator: ">"
    threshold: 75
    weight: 0.25
  - condition: macro_uncertainty_vix
    operator: ">"
    threshold: 25
    weight: 0.20
  - condition: recession_probability
    operator: ">"
    threshold: 40
    weight: 0.20
  - condition: fear_greed_index
    operator: "<"
    threshold: 30
    weight: 0.20
  - condition: crypto_correlation_sp500
    operator: ">"
    threshold: 0.6
    weight: 0.15
```

## Exit Conditions

```yaml
exit_conditions:
  take_profit:
    - condition: risk_indicator
      operator: "<"
      threshold: 0.3
    - condition: time_days
      operator: ">="
      value: 14
  stop_loss:
    - condition: portfolio_drawdown
      operator: ">="
      value: -8
```

## Action Specification

```yaml
action:
  type: REDUCE_EXPOSURE
  size: 40
  slippage_tolerance: 0.5
  priority: 9
  instruments:
    - BTC
    - ETH
    - high_beta_alts
  hedges:
    - stablecoin_allocation
    - short_dated_treasuries
```

## Risk Parameters

```yaml
risk:
  max_position_size: 10
  max_portfolio_risk: 3
  stop_loss: 8
  take_profit: null
  time_based_exit_days: 14
  correlation_threshold: 0.7
```

## Portfolio Impact Analysis

For each detected geopolitical event, the skill calculates:
1. **Direct Impact Score:** 0-100 scale on crypto market exposure
2. **Contagion Channels:** Identifies which crypto sectors are most affected
3. **Time Horizon:** Short-term (hours), medium-term (days), long-term (weeks)
4. **Historical Analogs:** Similar events and their typical market responses

## Backtest Expectations

- Expected Win Rate: 58-65%
- Max Drawdown: 7%
- Sharpe Ratio Target: 1.8
- Trade Frequency: 2-4 signals/month

## Use Cases

1. War/conflict escalation affecting energy prices and inflation
2. Central bank policy pivots causing risk-off sentiment
3. Sovereign debt crises triggering liquidity withdrawals
4. Election/political instability in major economies

## Risk Mitigation

- Always maintain minimum 20% stablecoin reserve during high-risk periods
- Correlate crypto with traditional risk assets before reducing exposure
- Consider BTC as potential safe-haven during geopolitical shocks
