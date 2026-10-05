# Market Basket Analysis — Online Retail

Association rule mining on 541,909 e-commerce transactions (UCI Online Retail dataset,
Dec 2010–Dec 2011) to identify which products customers buy together, and estimate the
revenue impact of surfacing those pairings as "customers also bought" recommendations.

## What this does

- Cleans raw transaction data: removes returns, cancelled orders, guest checkouts, and
  non-product rows (396,470 clean rows retained from 541,909 raw).
- Builds a one-hot basket matrix (order × product) and mines frequent itemsets with the
  **Apriori algorithm**.
- Generates association rules (support, confidence, lift) and filters out rules that are
  just color/size variants of the same product (e.g. "red alarm clock → green alarm
  clock"), which inflate lift scores without being a useful recommendation.
- Visualizes the strongest genuine cross-sell pairs.
- Estimates the AOV (average order value) uplift from surfacing these pairs as checkout
  recommendations, with explicit, clearly-labeled assumptions rather than treating the
  estimate as a measured result.

## Key result

7 genuine cross-sell pairs survive filtering (e.g. matching lunch bags, matching jumbo
storage bags, teacup-and-saucer sets with their matching cake stand), with an estimated
~2.5% AOV uplift under conservative adoption assumptions.

## Tech stack

Python, pandas, mlxtend (Apriori / association rule mining), matplotlib.

## Files

- `market_basket_analysis.ipynb` — full analysis, runs end to end with no errors.
- `top_rules_clean.png` — chart of the top cross-sell pairs by lift.

## Data source

[UCI Machine Learning Repository — Online Retail Dataset](https://archive.ics.uci.edu/dataset/352/online+retail)
