
# Data Analysis Project: 

## Initial Overview:

> The unit of observation is an individual Kickstarter campaign. Each row represents one campaign, while the columns contain information about its characteristics, including its funding goal, amount pledged, number of backers, country, launch date, deadline, and final status.

The data set contained many NaN values (missing values), and the column names where integers instead of their actual column names which where found just below. We believe this is a data downloading quality issue, however we resolved it by 

1. Dropping the missing values
2. setting the first row as the column names. 

Afterwards, the data set was clean with a reduced ammount of missing values. 

## Initial Analysis

From initial analysis, it seems that most kickstarters failed (168221 failed and 113081 were successful). Which is shown through this barplot depicting the success, failure, and canceled rates:

![Kickstarter Campaign Success Rates](https://raw.githubusercontent.com/Key6767/cmpsc105-project/25683da2c899bf9657365e890985cdb54c966eea/Main%20Analysis/Graphs/successrates.png)

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

![Pie Chart](https://raw.githubusercontent.com/Key6767/cmpsc105-project/25683da2c899bf9657365e890985cdb54c966eea/Main%20Analysis/Graphs/piechart_cs_percentages.png)

**Break Down:**
- 51.96 percent of the campaigns failed
- 34.92 percent of the campaigns were successful
- 9.99 percent of the campaigns were canceled
- 1.36 percent of the campaigns are undefined. 

### 2. Kickstarter Success Rate by Campaign Length

The Following is a bar graph comparing Kickstarter success rates across different campaign durations:

![Campaign Length Bar](https://raw.githubusercontent.com/Key6767/cmpsc105-project/25683da2c899bf9657365e890985cdb54c966eea/Main%20Analysis/Graphs/Kickstarter_CampaignLengthBar.png)

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

![Kickstarter Funding](https://raw.githubusercontent.com/Key6767/cmpsc105-project/25683da2c899bf9657365e890985cdb54c966eea/Main%20Analysis/Graphs/KickbyFundBar.png)

This bar graph shows a trend of Kickstarter success rates decreasing as funding goals increase.

- Projects with goals between $1 and $1,000 have the highest success rate, at 52.84%, while projects with goals above $100,000 have the lowest rate, at 8.07%. 

It is important to recognize that this observation is closed off to kickstarter campaigns ran with U.S. Dollars, and excludes other international currencies. 

These results do not prove that lower goals directly cause success, because other factors, such as project category, campaign length, and audience interest, may also affect the outcome.

### 4. Kickstarter Success Rate and Average Funding Goal by Country:

Converted to U.S. Dollar, this is what Kikstarter Success Rates and Average Funding Goal by Country reveals about our data. 

![Success by Country and Funds](https://raw.githubusercontent.com/Key6767/cmpsc105-project/25683da2c899bf9657365e890985cdb54c966eea/Main%20Analysis/Graphs/RevealingSuccessbyCountry%2BFunds.png)

Moreover, this plot accounts for the disparity between the results shown in the Kickstarter Success Rate by Funding Goal plot, and the Correlation coefficient between funding goal and success: $$r=-0.0253$$

Which indicates an extremely weak negative correlation between funding goal and success rates. 

Additionally, we can note that the U.S. has a higher success rate, and one of the lowest funding goals. Yet, we have sweden as the highest funding goals, yet placed around the medium range of between success and failure rate. Which may explain the weak negative correlation coefficient result. 

### 5. A Possible Bimodal distribution between Launch months and Success Rate measures:

![Launch by Month](https://raw.githubusercontent.com/Key6767/cmpsc105-project/25683da2c899bf9657365e890985cdb54c966eea/Main%20Analysis/Graphs/Launchmonthsbar.png)

This graph compares Kickstarter success rates across twelve launch months.

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

Overall, our initial exploratory data analysis reveals several patterns in Kickstarter campaign outcomes and their relationships with campaign duration, funding goals, geographical location, and launch timing. Of the campaigns analyzed, approximately 51.96% failed, while 34.92% were successful, suggesting that failure was more common than success within this dataset. Our analysis also identified a relatively concentrated distribution of campaign durations, with the middle 50% lasting approximately 30 to 37 days, alongside extreme values that may influence our statistical summaries.

One of our most notable findings concerns campaign duration. Campaigns lasting between 8 and 21 days had success rates of approximately 53%, compared with approximately 28% for campaigns lasting 46 to 60 days. The reported correlation coefficient of -0.716 suggests a strong negative relationship between campaign duration and success rate in our analysis. Funding goals also appeared to be associated with campaign outcomes: projects with lower goals generally exhibited higher success rates, while projects with goals exceeding $100,000 had substantially lower success rates. However, the correlation coefficient of -0.0253 indicates an extremely weak negative linear relationship between funding goal and success rate in the analysis where it was calculated. This difference highlights the importance of examining how variables are measured and grouped before drawing conclusions. Our geographical analysis also revealed variation between countries in success rates and average funding goals, while launch-month success rates showed comparatively modest differences, ranging from 36.00% in July to 42.51% in March.

Despite these findings, our analysis remains exploratory, and the observed relationships do not establish causation. Differences in project categories, audience interest, currency, funding expectations, and other campaign characteristics may help explain the patterns we observed. Furthermore, the data-cleaning process, missing values, and extreme observations introduce additional considerations that may affect the reliability and interpretation of our results. These limitations motivate several directions for further investigation: comparing success rates across project categories, examining how outliers and missing values influence our findings, and investigating whether the relationships between campaign characteristics and success remain consistent across different groups. We should also examine how the definitions and calculations of our correlation coefficients affect their interpretation, particularly when comparing categorical outcomes with numerical variables.

Ultimately, this initial analysis provides a foundation for a more detailed investigation into the characteristics associated with Kickstarter campaign success and the limitations of predicting outcomes from individual variables alone.