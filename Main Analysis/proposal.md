# Project Proposal

## Investigation 1

### A: Setting the Target

The results above show that failed Games campaigns have a much higher average funding goal ($71,898.32) than successful campaigns ($17,028.63). However, the median funding goals are much lower: $10,000 for failed campaigns and $5,000 for successful campaigns.

The large differences between the means and medians suggest that a relatively small number of campaigns with very high funding goals are pulling the averages upward. This demonstrates why founders should be cautious about using the average funding goal as their main reference when setting a target. A few highly publicized, million-dollar Kickstarter campaigns can make the average appear much higher than what is typical for most projects.

The variance is also substantially higher among failed campaigns, indicating much greater variation in their funding goals. Overall, the median provides a more useful picture of a typical campaign's funding target than the mean in this dataset.

### B: How Much Successful Campaigns Actually Raise

The pledged amount percentiles show that successful Games campaigns generally raise relatively modest amounts. The 25th percentile is $4,053.56, the median is $11,236.77, and the 75th percentile is $32,921. This means that 75% of successful campaigns raised $32,921 or less.

Out of the 7,445 successful campaigns, only 1,331 raised at least $50,000. This represents approximately 17.88% of successful campaigns, meaning that 82.12% did not reach the manufacturer's minimum production requirement.

These findings suggest that a successful Kickstarter campaign does not necessarily generate enough funding to support large-scale production. The manufacturer should therefore be realistic about the amount most independent projects can raise and should not assume that reaching a funding goal automatically means having sufficient funds to begin production.

## Investigation 2: The Campaign Length Myth

A novice hardware founder assumes that running a longer campaign (45 to 60 days) will yield significantly more total pledged funds than a standard short campaign (30 days or less) because it gives people more time to find it. Define your groups, state your null and alternative hypothesis, and conduct an appropriate hypothesis test (adapting your simulation methods from Lab 07). Report your p-value and conclusion. Should founders stretch their campaigns out?

### Central Question: Can we assume that longer campaign durations increase pledged funds? 

### A: Definitions and Hypotheses. 

In order to answer this question, it is necessary to define what we mean by longer campaign durations versus short campaign durations. 

These are the following campaign duration definitions:

**Definition 1:** Short Campaigns are 30 days and below.
**Definition 2:** Long campaigns are between 45 and 60 days. 

Because we are aiming to answer whether there is a correlation between longer campaign durations and higher ammounts of pledged funds, we will set this to be our alternative hypothesis. Conversely, our null hypothesis will predict little to no correlations between longer days and high pledge funds. In short:

$$H_0: \mu_{\text{long}} = \mu_{\text{short}}$$

$$H_A: \mu_{\text{long}} > \mu_{\text{short}}$$

* Null hypothesis: Longer campaigns do not generate more average pledged funding.
* Alternative hypothesis: Longer campaigns generate more average pledged funding.

When creating subsets, findings conclude there to be a total of $$205310$$ short campaigns and $$56075$$ long campaigns.

The following are there descriptive means and their observed difference:

* Short campaign mean: 6268.75
* Long campaign mean: 7781.08
* Observed difference: 1512.33

Observed difference= $$\bar{x}_{long}-\bar{x}_{short}$$

Keep in mind that as we have set campaings longer than 60 days as not part of our Long campaign subset we must continue to acknowledge that 5126 observations longer than 60 days are not being included as part of our analysis.

Moreover, 7 rows where ommitted due to malformed data. 

* Original cleaned dataset: 319328
* Dataset after removing malformed dates: 319321

### B: Simulations, Observed Differences and Probabilities.

Given our hypothesis test: We reject the null hypothesis.

Number of simulations:5,0000

$$\alpha=0.05\:$$

$$p=0.0001999600079984003<0.05$$

However, Kickstarter funding amounts are likely highly skewed: a relatively small number of campaigns may raise exceptionally large amounts. Our permutation procedure also assumes exchangeability of the observations under the null, which is stronger than simply assuming equal population means.

Because of this, a second test with a higher number of simulations was conducted. The following are the results:

* Number of simulations: 20000
* Observed difference: 1512.33
* Simulations as extreme or more extreme: 0

$$P= 0.00004999750012499375$$

### C: Statistical and Comparison Summary

| Statistic | Short campaigns (≤30 days) | Long campaigns (45–60 days) |
|-----------|----------------------------|-----------------------------|
| count     |                  205310.00 |                    56075.00 |
| mean      |                    6268.75 |                     7781.08 |
| std       |                   56655.34 |                    92167.76 |
| min       |                       0.00 |                        0.00 |
| 25%       |                      20.00 |                       10.00 |
| 50%       |                     460.00 |                      255.00 |
| 75%       |                    3150.00 |                     2500.00 |
| max       |                 8782571.99 |                 13285226.36 |

### Conclusion

The results provide statistically significant evidence that Kickstarter campaigns lasting 45–60 days receive higher average funding than campaigns lasting 30 days or fewer. The observed difference was approximately $1,512, and a randomization test using 20,000 simulations produced a p-value of approximately 0.00005. Therefore, I reject the null hypothesis in favor of the alternative hypothesis.

However, further analysis reveals that longer campaigns have a lower median funding amount ($255 versus $460). Additionally, after temporarily excluding the top 1% of campaigns in each group, the difference in average funding decreases from approximately $1,512 to just $108. This suggests that the higher average among longer campaigns is substantially influenced by exceptionally successful projects.

Ultimately, although longer campaigns are associated with higher average funding, this does not necessarily translate into better outcomes for the typical creator. Since this analysis cannot establish causation, founders should not automatically extend their campaigns. Instead, they should consider campaign duration alongside other factors, such as marketing, audience reach, and project characteristics.

## Investigation 3: The Goal-to-Funding Reality

Explaining the dangers of basing target goals on few highly publicized, million-dollar Kickstarter outliers.

### A: Million-dollar Generalization

For this investigation, all 323,118 campaigns with numerical goal values where utilized, including every outcome and outliers. 

632 rows where removed because they held unusable values.

- Sample covariance: $$694,333,865.36$$
- Pearson correlation: $$r = 0.0068$$

As seen above, we can determine that the covarience was positive, however its quantity depends on the scale of ammounts. Moreover, the correlation value is nearly zero. Thus, we can conclude that setting a higher funding goal does not generally or reliably correspond to higher funds.

### B: Successful vs. failed campaigns

| Outcome | Campaigns | Correlation (r) |
| --- | ---: | ---: |
| Successful | 113,081 | 0.5125 |
| Failed | 168,221 | 0.0227 |

Successful campaigns have a moderate positive relationship: larger goals tend to correspond with larger pledged amounts. For failed campaigns, the correlation is almost zero. Consequently, the linear relationship breaks down.

The manufacturer is advised to communicate with kickstarter designers to set reliable goals based on the funding needed in order to produce the product. 

An artificially high goal, aiming a facade of ambition is not supported by the data. Ultimately successful campaigns already have to meet their goals, thus, their positive correlations do not demonstrate a causal relationship between raising funding goals and ammount of pledges. 

---
These calculations use the requested original `goal` and `pledged` columns, which mix currencies. Outliers can also affect the results. The graphs use symlog axes for readability, but the correlations use the original values. These are associations, not proof of causality.


## Overall Summary of Investigations

Across all three investigations, the findings highlight the importance of realistic crowdfunding expectations. **Investigation 1** showed that failed campaigns generally had higher funding goals, while most successful campaigns raised less than $50,000. **Investigation 2** found that longer campaigns had higher average pledges, but lower median funding, suggesting that exceptionally successful projects influenced the results. **Investigation 3** revealed almost no overall correlation between funding goals and pledged amounts.

Ultimately, founders should avoid relying on exceptional Kickstarter successes when setting funding targets. Instead, they should consider typical campaign outcomes, realistic production costs, and the limitations of campaign duration when making financial decisions.