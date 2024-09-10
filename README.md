# Marketing A/B Testing Campaign Analysis

## Project Overview

In this project, we analyze the results of an A/B test conducted for a marketing campaign. The goal is to determine whether showing ads resulted in more conversions compared to a Public Service Announcement (PSA) and evaluate how much of the campaign's success can be attributed specifically to the ads.

We will also investigate user behavior patterns, including the best days and times to show ads, and assess the statistical significance of our findings through hypothesis testing.

## Objectives

1. **Determine Campaign Success**: Analyze whether the ads increased conversion rates compared to the PSA group.
2. **Statistical Significance**: Assess if the differences between the ad and PSA groups are statistically significant.
3. **Lift Calculation**: Measure how much of the success can be attributed to the ads by calculating the lift in conversions.
4. **User Behavior Insights**: Identify the days and times when conversion rates peak to guide future ad placements.
5. **Marketing Strategy**: Provide actionable strategies based on the findings to optimize future ad campaigns.

## Data Dictionary

- **user id**: Unique identifier for each user.
- **test group**: Specifies whether a person saw an advertisement (`ad`) or a public service announcement (`psa`).
- **converted**: Indicates whether the person purchased the product (True) or not (False).
- **total ads**: Number of ads seen by the person.
- **most ads day**: Day of the week when the person saw the most ads.
- **most ads hour**: Hour of the day when the person saw the most ads.

## Steps Followed in the Analysis

### 1. Data Cleaning
We started by cleaning the dataset, handling missing values, and transforming the data to prepare it for analysis.

### 2. Exploratory Data Analysis (EDA)
We conducted an exploratory analysis to understand the general trends in the dataset, focusing on the distribution of ads seen, conversion rates across the test group (`ad` vs. `psa`), and patterns of user behavior.

### 3. Finding Conversion Rates
We calculated the conversion rates for both groups:
- **Ad Conversion Rate** = (Number of conversions in the `ad` group) / (Total users in the `ad` group)
- **PSA Conversion Rate** = (Number of conversions in the `psa` group) / (Total users in the `psa` group)

This helped us understand whether showing ads was more effective than showing PSAs in driving conversions.

### 4. Statistical Testing: Z-Statistic for Proportion Test

To determine whether the difference in conversion rates between the ad group and PSA group was statistically significant, we used the **Z-test for proportions**. This test compares the conversion rates of both groups.

#### Formula for Z-Statistic:
$'
Z = \frac{p_{ad} - p_{psa}}{\sqrt{p_{combined}(1 - p_{combined})\left(\frac{1}{n_{ad}} + \frac{1}{n_{psa}}\right)}}
'$
Where:
- \( p_{ad} \) = Conversion rate of the ad group.
- \( p_{psa} \) = Conversion rate of the PSA group.
- \( p_{combined} \) = Combined conversion rate of both groups.
- \( n_{ad} \) = Number of users in the ad group.
- \( n_{psa} \) = Number of users in the PSA group.

We then used the p-value corresponding to the Z-statistic to check for statistical significance.

### 5. Chi-Square Test for Independence

To further understand the relationship between seeing ads and conversions, we performed a **Chi-Square test for independence**. This test helped us determine whether the probability of conversion was dependent on whether the user saw an ad or a PSA.

#### Formula for Chi-Square:
\[
\chi^2 = \sum \frac{(O - E)^2}{E}
\]
Where:
- \( O \) = Observed frequency (actual conversions in each group).
- \( E \) = Expected frequency (based on overall conversion rate).

### 6. Day and Time Analysis

We created a new feature combining `most ads day` and `most ads hour` to analyze conversion rates by day and time.

data['day and hour'] = data['most ads day'].astype(str) + '_' + data['most ads hour'].astype(str)

We then analyzed conversion rates by these combinations, allowing us to identify specific days and times when ads were most effective.


### 7. Measuring Lift

**Lift** quantifies how much of the campaign's success is attributable to the ads. We calculated the lift to measure the incremental increase in conversions due to the ads compared to the PSA group.

#### Formula for Lift:
\[
\text{Lift} = \frac{p_{ad} - p_{psa}}{p_{psa}}
\]
Where:
- \( p_{ad} \) = Conversion rate of the ad group.
- \( p_{psa} \) = Conversion rate of the PSA group.

### Conclusion

After thorough analysis, we found that the marketing campaign utilizing ads significantly outperformed the PSA strategy in driving conversions. The statistical tests indicated a significant difference in conversion rates, validating the effectiveness of the ads.

Additionally, the analysis of day and time combinations revealed that certain times, such as Saturday at 5 AM and 6 AM, showed peak conversion rates. This insight into user behavior suggests that these timings could be optimal for future advertising strategies.

In summary, our findings confirm that ads effectively enhanced the conversion rate, and we gained actionable insights to inform future marketing efforts.

### Marketing Strategies

Based on the analysis, the following strategies are recommended for future campaigns:

1. **Targeted Advertising**: Focus on time slots where conversion rates are highest, particularly on weekends.
2. **Enhanced Weekend Campaigns**: Allocate more resources to ads on Saturday mornings, where engagement is notably higher.
3. **Continuous Monitoring**: Regularly analyze user behavior patterns to adapt ad placements in real-time.
4. **Segmented Campaigns**: Tailor campaigns to specific user segments based on their interaction with ads to maximize conversion rates.


