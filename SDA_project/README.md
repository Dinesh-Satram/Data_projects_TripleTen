# Megaline Telecom Plan Analysis

## Project Overview

This project involves analyzing the revenue generated by two prepaid calling plans, **Surf** and **Ultimate**, offered by the telecom operator **Megaline**. The goal of this analysis is to determine which of the two plans generates higher revenue and to assess the impact of customer behavior on the profitability of each plan. The dataset includes information on 500 Megaline clients, detailing their usage patterns (calls, messages, and internet data) during 2018. Based on the analysis, we aim to provide insights to the commercial department to adjust the advertising budget.

## Data Description

The dataset is divided into several tables:

1. **megaline_users.csv**: Information about the users, such as their unique ID, name, age, plan, and city of residence.
   - Columns: `user_id`, `first_name`, `last_name`, `age`, `reg_date`, `churn_date`, `city`, `plan`

2. **megaline_calls.csv**: Details about the calls made by users, including the call duration and timestamp.
   - Columns: `id`, `user_id`, `call_date`, `duration`

3. **megaline_messages.csv**: Information on text messages sent by users, including the timestamp and number of messages.
   - Columns: `id`, `user_id`, `message_date`

4. **megaline_internet.csv**: Data on the web sessions, including the volume of data used and the timestamp.
   - Columns: `id`, `user_id`, `session_date`, `mb_used`

5. **megaline_plans.csv**: Information about the two available plans (Surf and Ultimate), including their features and costs.
   - Columns: `plan_name`, `usd_monthly_pay`, `minutes_included`, `messages_included`, `mb_per_month_included`, `usd_per_minute`, `usd_per_message`, `usd_per_gb`

## Data Preprocessing

The following preprocessing steps were applied to the data:

1. **Loading Data**: All relevant CSV files were loaded into DataFrames for analysis.
2. **Handling Missing Data**: Missing values were handled by filling in or removing any incomplete entries as needed.
3. **Data Cleaning**: Data types were corrected, and redundant or erroneous entries (e.g., zero-duration calls) were removed.
4. **Data Enrichment**: New columns were created, such as customer tenure (in days) and monthly aggregates for calls, messages, and internet data.

## Exploratory Data Analysis (EDA)

Key analyses performed include:

- **Usage Patterns**: Analyzed the distribution of calls, messages, and internet data usage by plan (Surf vs. Ultimate).
- **Revenue Calculation**: Computed the monthly revenue for each user based on their usage and plan details, including excess usage charges for calls, messages, and data.
- **Descriptive Statistics**: Calculated the mean, variance, and standard deviation of call durations, message counts, and data usage for each plan.
- **Visualizations**: Generated various plots (bar plots, histograms, box plots) to visualize the differences between Surf and Ultimate plans in terms of usage and revenue.

## Hypothesis Testing

Two hypotheses were tested in the analysis:

1. **Revenue Comparison Between Plans**:
   - Null Hypothesis: There is no significant difference in the average revenue between the Surf and Ultimate plans.
   - Alternative Hypothesis: There is a significant difference in the average revenue between the two plans.
   - **Result**: The t-test revealed a significant difference in revenue between the two plans, with the Ultimate plan generating higher revenue on average.

2. **Revenue Comparison Between Regions (NY-NJ vs Other)**:
   - Null Hypothesis: There is no significant difference in the average revenue between users from the NY-NJ region and other regions.
   - Alternative Hypothesis: There is a significant difference in revenue between users from the NY-NJ region and other regions.
   - **Result**: The t-test showed no significant difference in revenue between the NY-NJ region and other regions.

## Key Findings

- **Revenue**: The Ultimate plan generates higher average revenue compared to the Surf plan.
- **User Behavior**: Users on the Ultimate plan tend to have more consistent usage patterns, while Surf plan users show more variability in their usage.
- **Usage Patterns**: Ultimate plan users generally use more data and minutes than Surf plan users, with greater variability in usage.
- **Regional Differences**: There is no significant difference in revenue between users from the NY-NJ area and users from other regions.

## Visualizations

The project includes various plots to compare user behavior across the two plans:

- **Average Call Duration**: Bar plots showing the average call duration for each plan by month.
- **Minutes Distribution**: Histograms displaying the distribution of minutes used by users on both plans.
- **Message Count Distribution**: Boxplots comparing the number of messages sent by users of each plan.
- **Internet Usage Distribution**: Boxplots comparing the total MB of data used by users of each plan.

## Conclusion

Based on the analysis, the **Ultimate** plan generates higher average revenue compared to the **Surf** plan, making it a more profitable choice for the telecom operator. Users on the Ultimate plan exhibit more predictable usage behavior, while Surf plan users show greater variability in their call durations, message counts, and internet usage. The findings suggest that the Ultimate plan is more suitable for users who tend to exceed their plan limits, while the Surf plan caters to users with more moderate usage.

## Technologies Used

- **Pandas**: Data manipulation and aggregation.
- **Matplotlib & Seaborn**: Data visualization.
- **SciPy**: Statistical hypothesis testing.
- **Jupyter Notebook**: Interactive environment for performing EDA and hypothesis testing.

## Future Improvements

- Conduct a more detailed analysis based on customer demographics (e.g., age, region).
- Investigate the impact of churn on the profitability of each plan.
- Implement a predictive model to estimate customer churn and plan switching behavior.

---

This README provides an overview of the project, the steps taken, the results obtained, and the conclusions drawn from the analysis. You can copy this and paste it directly into your `README.md` file for your GitHub repository.
