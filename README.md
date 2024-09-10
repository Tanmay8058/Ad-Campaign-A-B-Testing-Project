# Ad Campaign A/B Testing

## Project Overview

In this project, we are analyzing a marketing A/B testing dataset. The goal is to determine whether the marketing campaign (ads) was successful in increasing conversion rates and to assess how much of the success can be attributed to the ads specifically. We also aim to identify patterns such as the best day and time to run ads based on conversion rates.

We will be following the A/B testing methodology to compare two groups:
- **Ad Group**: Users who were shown advertisements.
- **PSA Group**: Users who were shown a public service announcement (control group).

## Objectives

1. **Determine Campaign Success**: Analyze whether the ads increased conversions.
2. **Statistical Significance**: Assess if the differences between the two groups (ad vs. PSA) are statistically significant.
3. **Understand Customer Behavior**: Investigate the best day and time slots for higher conversions.
4. **Measure Lift**: Calculate the incremental conversions attributed to ads.

## Data Dictionary

- **user id**: User ID (unique identifier)
- **test group**: `ad` indicates the person saw the advertisement, `psa` indicates they saw the public service announcement.
- **converted**: `True` if the person bought the product, `False` otherwise.
- **total ads**: Number of ads seen by a person.
- **most ads day**: Day of the week that the person saw the largest number of ads.
- **most ads hour**: Hour of the day that the person saw the largest number of ads.

## Process Overview

### 1. Data Cleaning
We started by cleaning the dataset, handling missing values, and ensuring that the data was ready for analysis.

### 2. Exploratory Data Analysis (EDA)
We explored the dataset to understand the distribution of ads shown, conversions by day and hour, and overall trends in conversion rates.

### 3. Finding Conversion Rates
We calculated the conversion rates for both the ad group and the PSA group:
- **Ad Conversion Rate** = (Number of Conversions in Ad Group) / (Total Users in Ad Group)
- **PSA Conversion Rate** = (Number of Conversions in PSA Group) / (Total Users in PSA Group)

### 4. Power Analysis
We conducted a power analysis to determine the sample size required to detect significant differences between the ad and PSA groups.

### 5. A/B Testing: Z-Statistic for Proportion Test

We performed A/B testing using the **Z-Statistic** to compare conversion rates between the two groups. The Z-Statistic for proportions helps us determine whether there is a statistically significant difference between the ad and PSA groups.

#### Formula for Z-Statistic:
\[
Z = \frac{p_{ad} - p_{psa}}{\sqrt{p_{combined}(1 - p_{combined})\left(\frac{1}{n_{ad}} + \frac{1}{n_{psa}}\right)}}
\]
Where:
- \( p_{ad} \) = Conversion rate of ad group
- \( p_{psa} \) = Conversion rate of PSA group
- \( p_{combined} \) = Combined conversion rate of both groups
- \( n_{ad} \) = Number of users in the ad group
- \( n_{psa} \) = Number of users in the PSA group

We then used the p-value corresponding to the Z-score to determine whether the difference was statistically significant. 

### 6. Chi-Square Test

To assess the relationship between the test group (ad/PSA) and conversion outcomes, we also used the **Chi-Square test** for independence. This test helps us understand whether conversion is dependent on whether the user saw an ad or a PSA.

#### Formula for Chi-Square:
\[
\chi^2 = \sum \frac{(O - E)^2}{E}
\]
Where:
- \( O \) = Observed value
- \( E \) = Expected value

### 7. Analysis of Conversion Rates by Day and Hour

We analyzed conversion rates for different days and time slots to determine which combinations performed best.

We created a new column, `day and hour`, to combine the day and hour of the ads shown:
```python
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

