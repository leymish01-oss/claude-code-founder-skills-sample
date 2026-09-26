---
name: pricing-experiment
description: Design a pricing test for a small product, covering hypothesis, variant, metric, minimum sample, duration, stop rules and how to read the result without fooling yourself. Use when someone asks "should I raise or lower my price", wants to test a discount, tiers or a bundle, or has pricing data to interpret.
---
# Pricing experiment designer

## When to use
Before changing a price, adding a tier or discount, or when reading the results of a change.

## Inputs
- Current price(s) and what's included.
- Real numbers for the last 2–4 weeks: visits to the product page, checkouts started, sales, refunds.
- The idea to test (higher price, lower price, tiers, bundle, discount, pay-what-you-want).
- Constraints: can the platform split traffic? (Most small stores can't, so tests run sequentially.)

## Steps
1. **State the hypothesis** with a number: "Raising $19 → $29 will cut conversion by less than a
   third, so revenue per visitor goes up."
2. **Pick one metric: revenue per visitor** (sales × price ÷ visitors). Conversion rate alone hides
   price effects; revenue alone hides traffic swings.
3. **Check the sample.** With fewer than ~30 sales per variant, results are noise. Compute the visits
   needed from the current conversion rate. If it would take more than 6 weeks, say so and recommend a
   bigger change (bigger price gap, new tier) or a qualitative test (ask 10 buyers) instead.
4. **Design the run.** Split traffic if possible; otherwise run A then B for equal full weeks, avoiding
   launches, holidays and promotions. Change nothing else during the test.
5. **Stop rules.** Decide in advance: the end date, and a safety stop (e.g. refunds above 10%).
6. **Reading the result.** Compare revenue per visitor with a rough interval. Call it a win only if the
   difference survives the noise; otherwise call it "no detectable difference" and keep the simpler price.
7. **Honesty checks.** Discounts must be real (the "before" price was actually charged). No fake
   countdowns or fake scarcity.

## Output format
```
HYPOTHESIS:
METRIC: revenue per visitor (current: $X from N visits)
VARIANT(S):
SAMPLE NEEDED: ~N visits per variant (≈ W weeks at current traffic)
RUN PLAN: dates, what stays fixed
STOP RULES:
DECISION RULE: what result means keep / revert / inconclusive
```

## Rules
- Use only numbers you were given or can compute. If traffic is unknown, the first task is measuring it.
- Never recommend deceptive tactics (fake original prices, fake timers).

## Worked example
**Input:** "Notion templates at $12. Last 4 weeks: 2,100 product-page visits, 42 sales, 1 refund. Thinking
of $19."

**Output:**
```
HYPOTHESIS: At $19, conversion falls from 2.0% to no lower than 1.3%, so revenue per visitor rises
  from $0.24 to at least $0.25.
METRIC: revenue per visitor. Current: 42 × $12 / 2,100 = $0.24.
VARIANT: $19, same product, same page copy apart from the price.
SAMPLE NEEDED: at ~525 visits/week and ~2% conversion, 4 weeks per variant gives ~40 sales at $12
  and ~27 at $19 if the hypothesis holds. That's borderline; plan 4 weeks of B, and treat a result
  within ±25% as inconclusive.
RUN PLAN: A = the last 4 weeks (already measured). B = 4 full weeks from Monday 5 Oct at $19. No
  newsletter pushes or discounts in either period. Same traffic sources.
STOP RULES: end on 1 Nov. Stop early if refunds exceed 3 in B (they were 1 in A).
DECISION RULE:
- B revenue/visitor ≥ $0.30 → keep $19.
- $0.19–$0.30 → inconclusive. Keep $19 only if you prefer fewer, better-fit buyers; otherwise revert.
- < $0.19 → revert to $12.
Note: EARLY-style discount codes during B would contaminate it; pause them.
```
