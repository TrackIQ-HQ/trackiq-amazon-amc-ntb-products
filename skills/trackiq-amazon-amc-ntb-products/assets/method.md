# Method

## 1. Per ASIN, per month

```
ntb_share   = ntb_users / all_users
ntb_revenue = ntb_total_product_sales
```

Drop to a **thin** list any ASIN with fewer than **50** `all_users` in the
focus month. It is shown, never classified.

## 2. Classify against the account

Take the median `ntb_share` of the non-thin ASINs in the focus month.

| Class | Rule |
|---|---|
| **Gateway** | `ntb_share` at least 10 points above the median |
| **Retention** | `ntb_share` at least 10 points below the median |
| **Mixed** | everything between |

Use the two earlier months as a check, not an input: a gateway in all three
months is **steady**; one that only qualifies in the focus month is
**new this month** and gets a note, not a funding recommendation.

## 3. Their share of new customers

```
ntb_contribution = asin ntb_users / sum of ntb_users across non-thin ASINs  (focus month only)
```

This is the share of the month's new customers who started with that
product. It sums to 100% within one month and must never be computed across
months.

## 4. The funding gap

```
spend_share = asin ad spend (SP + SD) / total SP + SD spend on non-thin ASINs
gap         = ntb_contribution - spend_share
```

- **Underfunded gateway**: a steady gateway with `gap` above **+5 points**.
  These are the recommendations.
- **Overfunded retention**: a retention product with `gap` below
  **−5 points**. Name it; recommend moving the difference, not cutting it.

The recommended move is the smaller of the two gaps in dollars, in two
steps, because a gateway's new-to-brand share tends to fall as its spend
rises. State that assumption.

## 5. The headline

"New customers most often start with X and Y — together N% of the month's
new-to-brand customers, on M% of the ad spend." Name the month.
