# Investigation 3: The Goal-to-Funding Reality

## Part A: All campaigns

I used all 323,118 campaigns with numeric goal and pledged values, including every outcome and all outliers. I removed 632 rows with unusable values.

- Sample covariance: **694,333,865.36**.
- Pearson correlation: **r = 0.0068**.

The covariance is positive, but its size depends on the scale of the amounts. The correlation is almost zero, so asking for more money does not reliably track with raising more money overall.

## Part B: Successful vs. failed campaigns

| Outcome | Campaigns | Correlation (r) |
| --- | ---: | ---: |
| Successful | 113,081 | 0.5125 |
| Failed | 168,221 | 0.0227 |

Successful campaigns have a moderate positive relationship: larger goals tend to go with larger pledged amounts. For failed campaigns, the correlation is almost zero, so the linear relationship essentially breaks down.

I would advise the manufacturer to tell the designer to set a realistic goal based on the funding needed to make the product. An artificially high goal just to look ambitious is not supported by these results. Successful campaigns already have to meet their goals, so their positive correlation does not show that raising a goal causes more pledges.

These calculations use the requested original `goal` and `pledged` columns, which mix currencies. Outliers can also affect the results. The graphs use symlog axes for readability, but the correlations use the original values. These are associations, not proof of cause and effect.
