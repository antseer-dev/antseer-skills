---
name: "macro-crypto-impact-tracker"
description: "Macro-Crypto Correlation Analysis"
strategy_agent: "analysis"
version: "1.0.0"
created_at: "2026-03-26T00:00:00Z"
skill_lifecycle: "draft"
author: "creator-agent"
---

# Macro-Crypto Impact Tracker

Tracks traditional macroeconomic indicators and analyzes their real-time correlation with cryptocurrency markets, integrating on-chain metrics with TradFi data for actionable investment insights.

## Overview

This skill monitors conventional macroeconomic indicators (inflation, employment, interest rates, oil prices) and analyzes their relationship with cryptocurrency markets. It provides real-time correlation analysis and actionable insights for crypto investors.

## Demand Context

**Source Gap:** gap_002
**Opportunity Type:** Macro-Crypto Correlation Analysis
**Target User Personas:** casual, researcher
**Sentiment:** disapproval (intensity: 0.8)

### Evidence Signals
- Economy: -28% (inflation indicator)
- Inflation: -34% - lowest since Nov
- Job growth is negative and inflation is accelerating
- Gas prices 4-5x normal levels

### L1 Cluster Labels
- Economic & Political Discontent: Trump, Biden, Inflation, Gas

## Features (Data Inputs)

| Feature | Source | Description |
|---------|--------|-------------|
| cpi_yoy | BLS/FRED | Consumer Price Index year-over-year |
| unemployment_rate | BLS | U.S. unemployment rate |
| fed_funds_rate | FOMC | Federal funds target rate |
| wti_oil_price | EIA | West Texas Intermediate crude price |
| 10y_treasury_yield | USTreasury | 10-year Treasury yield |
| dollar_index_dxy | ICE | U.S. Dollar Index |
| sp500_change | YahooFinance | S&P 500 daily change |
| btc_price | CoinGecko | Bitcoin price |
| eth_price | CoinGecko | Ethereum price |
| total_crypto_mcap | CoinGecko | Total cryptocurrency market cap |
| active_addresses_24h | Blockchain.com | Active wallet addresses |
| exchange_netflow_24h | CryptoQuant | Net exchange inflow/outflow |
| stablecoin_supply | Glassnode | Total stablecoin supply |

## Entry Conditions

Triggered when macro indicators show significant crypto correlation:

```yaml
entry_conditions:
  - condition: cpi_yoy
    operator: ">"
    threshold: 5.0
    weight: 0.20
  - condition: unemployment_rate
    operator: ">"
    threshold: 5.5
    weight: 0.15
  - condition: fed_funds_rate
    operator: ">"
    threshold: 4.5
    weight: 0.20
  - condition: btc_sp500_correlation_30d
    operator: ">"
    threshold: 0.65
    weight: 0.25
  - condition: stablecoin_supply_change
    operator: ">"
    threshold: 3
    weight: 0.20
```

## Exit Conditions

```yaml
exit_conditions:
  take_profit:
    - condition: macro_regime_change
      operator: "=="
      value: "easing"
    - condition: correlation_btc_sp500
      operator: "<"
      threshold: 0.4
  stop_loss:
    - condition: crypto_mcap_loss
      operator: ">="
      value: -15
    - condition: time_days
      operator: ">="
      value: 21
```

## Action Specification

```yaml
action:
  type: ADJUST_ALLOCATION
  size: 25
  priority: 7
  instruments:
    - BTC
    - ETH
    - stablecoins
  signals:
    long: dollar_weakness + rate_cut_expectations
    short: strong_dollar + inflation_acceleration
    neutral: low_correlation_regime
```

## Risk Parameters

```yaml
risk:
  max_position_size: 15
  max_portfolio_risk: 2.5
  stop_loss: 12
  take_profit: 25
  time_based_exit_days: 21
  rebalance_threshold: 0.15
```

## Correlation Analysis Framework

The skill continuously monitors:
1. **BTC-TradFi Correlation:** Rolling 30/90-day correlation with S&P 500
2. **Crypto-USD Correlation:** Inverse relationship with DXY
3. **Inflation Hedge Score:** BTC performance vs CPI changes
4. **Risk-On/Risk-Off Regime:** Market regime classification
5. **Leading/Lagging Analysis:** Which markets lead crypto price discovery

## Backtest Expectations

- Expected Win Rate: 55-62%
- Max Drawdown: 10%
- Sharpe Ratio Target: 1.5
- Trade Frequency: 3-5 signals/month

## Use Cases

1. Tracking inflation data releases and crypto market reactions
2. Monitoring Fed rate decisions and their impact on risk assets
3. Analyzing employment reports for consumer spending signals
4. Correlating oil price shocks with crypto market movements

## Data Integration

- On-chain metrics (active addresses, exchange flows) combined with macro data
- Real-time sentiment from social media correlated with price action
- Historical pattern matching against similar macro regimes
