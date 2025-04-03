# Video Game Sales Forecasting

## Project Overview

The video game industry is one of the largest and fastest-growing entertainment sectors worldwide. This project analyzes historical data from the online store Ice, which sells video games globally. The goal is to identify the factors that contribute to a game’s success based on user reviews, expert ratings, sales across different platforms, and other features such as genre and ESRB ratings. By uncovering patterns in this data, the project helps in forecasting which video games have the potential to succeed, aiding in planning future advertising campaigns.

## Project Structure


- **README.md**: This file containing the project description, installation instructions, and project details.
- **video_game_sales_analysis.ipynb**: The Jupyter notebook with code for data analysis, hypothesis testing, and results.
- **datasets/games.csv**: The dataset containing video game sales data including platform, genre, release year, and ratings.

## Project Description

### 1. Data Exploration and Cleaning

The dataset consists of video games released from various years and across different platforms. The columns contain:
- Game title (`name`), platform, genre, release year, and sales data (NA_sales, EU_sales, JP_sales, Other_sales).
- Review data: Critic Score and User Score, along with ESRB ratings.
- The dataset has missing values and potential duplicates which were addressed during the data cleaning phase.

### 2. Data Cleaning Steps
- **Column Renaming**: Columns were renamed to lowercase to maintain consistency.
- **Handling Missing Values**: 
  - `critic_score` and `user_score` were left as NaN where missing values occurred.
  - Rows with missing `name` or `genre` were dropped as they are essential for analysis.
- **Handling "TBD" Values**: "TBD" in `user_score` was replaced with NaN.
- **Removing Duplicates**: Duplicate entries based on `name`, `platform`, `year_of_release`, and `rating` were removed.
- **Total Sales Calculation**: Total sales were calculated as the sum of sales in all regions (`na_sales`, `eu_sales`, `jp_sales`, and `other_sales`).

### 3. Exploratory Data Analysis (EDA)
- **Platform Analysis**: Identified the most successful platforms and tracked their sales trends from 2012 to 2016.
- **Genre Analysis**: Analyzed the most successful genres, revealing that genres like Action and Sports dominated the sales across regions.
- **Sales Analysis**: Boxplots and histograms were used to assess the distribution of total sales across platforms.
- **Impact of Reviews on Sales**: Analyzed the correlation between critic and user scores and total sales for popular platforms.

### 4. Hypothesis Testing
Two hypotheses were tested using t-tests:
1. **H₀**: Average user ratings of the Xbox One and PC platforms are the same.
2. **H₀**: Average user ratings for the Action and Sports genres are different.

### 5. Results and Insights
- **Platform Trends**: PS4 and Xbox One showed strong performance between 2012-2016, while older platforms like PS2 and X360 experienced declines in sales.
- **Genre Trends**: Action and Sports genres saw the highest sales, while genres like Adventure and Puzzle had lower sales.
- **ESRB Rating Impact**: In North America and Europe, Mature-rated games had the highest sales, while Japan favored Family-friendly rated games.
- **Correlation Analysis**: Critic scores were found to have a moderate positive correlation with sales, while user scores showed a weaker correlation.

### 6. Conclusion
The analysis of video game sales data from 2012-2016 has provided insights into the factors influencing video game success:
- **Platform and Genre Preferences**: Platforms like PS4 and Xbox One, as well as genres like Action and Sports, were the most successful.
- **Review Scores**: Critic reviews played a significant role in driving sales, whereas user reviews had less influence.
- **Regional Preferences**: Regional differences were observed in the sales and market share of platforms and genres.
- **Hypothesis Testing**: It was concluded that there is a significant difference in user ratings between Xbox One and PC, and between the Action and Sports genres.

## Technologies Used

- **Python**: Core programming language used for data cleaning, analysis, and visualization.
- **Pandas**: Data manipulation and analysis library.
- **Matplotlib**: Data visualization library used for creating graphs and plots.
- **Scipy**: Statistical library used for hypothesis testing.

## Installation Instructions

1. **Clone the Repository**:
   ```bash
   git clone <repository_url>
