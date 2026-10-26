
# Brief Summary

## Initial Overview:

The data set contained many NaN values (missing values), and the column names where integers instead of their actual column names which where found just below. We believe this is a data downloading quality issue, however we resolved it by 

1. Dropping the missing values
2. setting the first row as the column names. 

Afterwards, the data set was clean with a reduced ammount of missing values. 

## Initial Analysis

From initial analysis, it seems that most kickstarters failed (168221 failed and 113081 were successful). Which is shown through this barplot depicting the success, failure, and canceled rates:

![alt text](../../Graphs/successrates.png) 

It is also not unusual for kickstarters to be canceled (32354 canceled), the question is about the percentage of cancelation. 

The following is an excerpt from “Kickstarter Lesson #38: Be Mentally Prepared for Cancellations”, published on the Stonemaier Games, company website, discussing the nature of kickstarters:

>Over the course of my 28-day Kickstarter campaign for >Euphoria, 298 people canceled their pledges. If you added those backers to the final count of 4,765 backers, you would have 5,063 backers. Thus about 6% of the overall pool of backers canceled their pledges at some point during the project. Compare that to Viticulture, during which 41 backers canceled their pledges out of an overall backer pool of 983 (4%). This is a small sample size. But based on what I’ve heard from other projects, a 5% cancellation rate is pretty normal.

---

## Some Initial Statistics Concerning our Kickstarter Data:

### 1. Kickstarter Campaign Day Durations and Outcomes

The following is a breakdown of Campaign Duration Statistics:

---
**1. The Core Cluster: A Very Small Spread**

-  Q1: $$(30.00  days)$$
- Q3: $$(36.94  days)$$
- IQR: $$(6.94  days)$$

The Interquartile Range (IQR) represents the middle 50% of our data. This tells us that half of all samples fall within a tiny, 7-day window (between 30 and 37 days). 

For the bulk of our data, the spread is remarkably small and highly predictable.

---
**2. The Impact of Outliers: Why the Standard Deviation is High**

- Standard Deviation $$(12.89 days)$$
- Variance $$(166.18 days^2)$$

On average, our data points deviate from the mean by about 13 days. If the middle 50% of our data only spans 7 days, why is the standard deviation double that size?

The answer to this question is that standard deviation and variance are highly sensitive to extreme values.

---
**3. The Extremes**

- Minimum $$(1.00 days)$$
- Maximum $$(92.00 days)$$ 
- Range $$(91.00 days)$$

The total range is a massive 91 days. Having a minimum of 1 day and a maximum of 92 days means we have a few extreme anomalies on both ends of the spectrum. 

These outliers are inflating the variance 166.18, and standard deviation 12.89.

---
### 2. Successes and failures 

![alt text](../../Graphs/piechart_cs_percentages.png)

**Break Down:**
- 51.96 percent of the campaigns failed
- 34.92 percent of the campaigns were successful
- 9.99 percent of the campaigns were canceled
- 1.36 percent of the campaigns are undefined. 

### 2. Kickstarter Success Rate by Campaign Length

The Following is a bar graph comparing Kickstarter success rates across different campaign durations:

![](../../Graphs/Kickstarter_CampaignLengthBar.png)

What is demonstrates: 

Campaigns lasting 8–14 days and 15–21 days have the highest success rates, at approximately 53%. In comparison, campaigns lasting 46–60 days have the lowest success rate, at about 28%. 

The graph suggests that shorter campaigns may be associated with higher success rates in this dataset.

Due to this indication, we calculated the sample correlation coefficient defined as:

$$r=\frac{Cov(x,y)}{S_x \cdot S_y}$$

Our results:

$$r=-0.716$$

This result means that the correlation between Campaign duration and success rate is a strong negative correlation since it falls just above the -0.70 threshhold. 

However, this is an initial observation and does not prove that shorter campaigns cause projects to succeed. Other factors, such as funding goals, project categories, and audience interest, may also influence the results.

### 3. Kickstarter Success Rate by Funding Goal:

![alt text](../../Graphs/KickbyFundBar.png)

This bar graph shows a trend of Kickstarter success rates decreasing as funding goals increase.

- Projects with goals between $1 and $1,000 have the highest success rate, at 52.84%, while projects with goals above $100,000 have the lowest rate, at 8.07%. 

It is important to recognize that this observation is closed off to kickstarter campaigns ran with U.S. Dollars, and excludes other international currencies.

These results do not prove that lower goals directly cause success, because other factors, such as project category, campaign length, and audience interest, may also affect the outcome.

### 4. A Possible Bimodal distribution between Launch months and Success Rate measures:

![alt text](../../Graphs/Launchmonthsbar.png)

This graph compares Kickstarter success rates across the twelve launch months.

-  March has the highest success rate at 42.51%, followed closely by April at 42.32%. 
- July has the lowest success rate at 36.00%.

The difference suggests that launch timing may be associated with project success, although the variation across months is relatively small. 

At a glance, there appears to be a slight bimodal distribution across the graph with the highest success rate being March for the first half of the year, and October for the second half of the year.

These results do not establish that launching in a particular month causes a project to succeed. Other factors, including funding goals, campaign duration, project category, and audience interest, may also influence success.

---

### Some Lingering Questions: 

Although we have managed to grasp a broad idea of what this graph reveals concerning kickstarters, there are some questions that we have yet to explore:

1. Do we have variations between variables across categories?

By this, we inquire about how do these relationships change across categories. Examples of this would include what are the success rate correlations between the Product Design Category, Documentary, Music etc.. And what does that tell us about which categories are most likely to succeed and fail?

2. Since we found out that the outliers affect a significant portion of our data, what would the data look like if we consider it without the outliers? 

This question explores the nature of the outliers, and how it changes our exploration if we disregard them. It also arises questions of whether it should be disregarded. 

3. What are the missing values? And what impact does it make on our data summary?

Do these missing values contain any information that would be valuable? Do these missing values add or remove potential insights we could produce in our data? Ways to find this out is to create a data set of the units with missing values. 

4. What causal inferences can we make from our findings?

Once we understand more about the data set, what causal claims are we able to make? And what conclusions can we make about the population from our sample population. 

---

## Conclusion:

Overall, our initial exploratory data analysis reveals several patterns in Kickstarter campaign outcomes, durations, funding goals, and launch timing. Most notably, approximately 52% of recorded campaigns failed, while about 35% were successful. Our findings also suggest that shorter campaigns tend to have higher success rates, with campaigns lasting 8–21 days performing better than those lasting 46–60 days. Similarly, campaigns with lower funding goals generally exhibited higher success rates, whereas success rates varied only moderately across launch months. However, these relationships should be interpreted cautiously: correlation does not establish causation, and other factors, including project category, audience interest, and campaign characteristics, may influence the outcomes. Our analysis also revealed unusually extreme values in campaign durations and funding goals, as well as data quality issues that required cleaning and further consideration. These limitations raise important questions about how missing values, outliers, and differences between project categories affect our results. Therefore, our next stage of analysis will investigate these relationships in greater detail, examine the influence of outliers and missing data, and determine whether the patterns identified in this initial exploration remain consistent across different categories of projects. Ultimately, this investigation will help us develop a more reliable understanding of the factors associated with Kickstarter campaign success while distinguishing meaningful statistical relationships from conclusions that the data cannot yet support.