---
name: "deflationary-asset-analyzer"
description: "Deflationary Finance Analysis"
strategy_agent: "analysis"
version: "1.0.0"
created_at: "2026-03-26T00:00:00Z"
skill_lifecycle: "draft"
author: "creator-agent"
---

# Deflationary Asset Analyzer

Evaluates assets based on their deflationary characteristics, analyzing supply mechanisms and burn mechanisms against Bitcoin's deflationary standard for sound money assessment.

## Overview

This skill analyzes cryptocurrency assets through the lens of sound money principles, evaluating their deflationary attributes, supply mechanics, and burn mechanisms against Bitcoin's proven scarcity model.

## Demand Context

**Source Gap:** gap_003
**Opportunity Type:** Deflationary Finance Analysis
**Target User Personas:** researcher, investor
**Sentiment:** curiosity (intensity: 0.553)

### Evidence Signals
- Creates an automatic deflationary layer at the protocol level
- Exciting times for the Internet Computer
- Inflation isn't a bug, it's a feature

### L1 Cluster Labels
- Predicting asset performance amidst recession and inflation
- Inflation, Interest Rates, and Systemic Financial Stability
- Predicting Market Trends with Volatility Contraction Patterns

## Features (Data Inputs)

| Feature | Source | Description |
|---------|--------|-------------|
| current_supply | CoinGecko | Current circulating supply |
| max_supply | CoinGecko | Maximum supply cap |
| supply_inflation_rate | CoinGecko | Annual inflation rate |
| token_burn_24h | Project APIs | Tokens burned in 24h |
| burn_rate_vs_emission | TokenTerminal | Burn rate relative to emission |
| held_supply_1y | Glassnode | Supply not moved in 1+ year |
| issuance_per_year | CoinMetrics | New tokens issued annually |
| real_volume_24h | CoinGecko | Real trading volume |
| fee_burn_24h | Ethereum API | ETH burned via EIP-1559 |
| supply_dilution_score | Internal | Calculated dilution resistance |

## Entry Conditions

Triggered when asset shows strong deflationary characteristics:

```yaml
entry_conditions:
  - condition: supply_inflation_rate
    operator: "<"
    threshold: 3.0
    weight: 0.25
  - condition: held_supply_1y
    operator: ">"
    threshold: 60
    weight: 0.25
  - condition: burn_rate_vs_emission
    operator: ">"
    threshold: 0.8
    weight: 0.30
  - condition: supply_dilution_score
    operator: ">"
    threshold: 70
    weight: 0.20
```

## Exit Conditions

```yaml
exit_conditions:
  take_profit:
    - condition: supply_deflation_rate
      operator: ">="
      value: -2
    - condition: time_months
      operator: ">="
      value: 6
  stop_loss:
    - condition: inflation_rate_change
      operator: ">"
      value: 5
    - condition: max_supply_removed
      operator: "=="
      value: false
```

## Action Specification

```yaml
action:
  type: ACCUMULATE
  size: 15
  priority: 6
  instruments:
    - high_deflation_assets
    - fee_burning_protocols
  criteria:
    min_supply_cap: true
    min_burn_rate: 0.5
    min_held_supply: 50
```

## Risk Parameters

```yaml
risk:
  max_position_size: 12
  max_portfolio_risk: 2.5
  stop_loss: 20
  take_profit: 50
  time_based_exit_months: 12
  rebalance_threshold: 0.20
```

## Deflationary Assessment Framework

Each asset is evaluated on:

1. **Supply Scarcity Score (0-100)**
   - Max supply cap existence (20 pts)
   - Current inflation rate (25 pts)
   - Supply growth trajectory (20 pts)
   - Historical supply reduction events (15 pts)

2. **Burn Mechanism Effectiveness (0-100)**
   - 24h burn volume vs emission (30 pts)
   - Sustainable burn funding (25 pts)
   - Protocol-level automatic burns (25 pts)
   - Community-governed burn proposals (20 pts)

3. **Sound Money Compliance (0-100)**
   - Predictable issuance schedule (25 pts)
   - Finite or decreasing supply (30 pts)
   - Resistance to political manipulation (20 pts)
   - Store of value utility (25 pts)

4. **Bitcoin Standard Comparison**
   - Inflation rate vs BTC
   - Supply certainty vs BTC
   - Adoption curve similarity

## Backtest Expectations

- Expected Win Rate: 52-60%
- Max Drawdown: 15%
- Sharpe Ratio Target: 1.3
- Holding Period: 6-18 months

## Use Cases

1. Identifying assets with strong deflationary tokenomics
2. Comparing ETH EIP-1559 burn mechanics to BTC halving
3. Finding early-stage deflationary protocols with high upside
4. Portfolio allocation based on sound money principles

## Sound Money Principles

Assets are evaluated against the historical properties of sound money:
- **Scarcity:** Limited supply creates value retention
- **Durability:** Token must maintain integrity over time
- **Portability:** Easy transfer across jurisdictions
- **Fungibility:** Uniform units without distinction
- **Censorship Resistance:** Immune to external control
