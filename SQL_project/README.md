# Zuber Ride-Sharing Data Analysis

## Project Overview

This project analyzes the impact of weather conditions, particularly rainy Saturdays, on ride durations for Zuber, a new ride-sharing company launching in Chicago. The analysis includes retrieving data on weather and taxi rides, performing exploratory data analysis (EDA), and testing the hypothesis: "The average duration of rides from the Loop to O'Hare International Airport changes on rainy Saturdays."

### Objective:
- Understand passenger preferences and the impact of external factors like weather on ride frequency and duration.
- Analyze taxi ride patterns from competitors.
- Test the hypothesis regarding ride duration differences on rainy Saturdays.

## Project Structure


- **README.md**: This file containing the project description, instructions, and conclusions.
- **ride_sharing_analysis.ipynb**: The Jupyter notebook containing the analysis, visualizations, and hypothesis testing.
- **datasets/project_sql_result_01.csv**: Taxi company rides data for November 15-16, 2017.
- **datasets/project_sql_result_04.csv**: Neighborhood drop-off data for November 2017.
- **datasets/project_sql_result_07.csv**: Rides from the Loop to O'Hare with weather conditions data.
- **weather_data/chicago_weather_2017.csv**: Weather data for Chicago in November 2017.

## Project Description

### 1. Data Retrieval and Preparation
The project begins by retrieving data from multiple sources, including:
- **Taxi Rides**: Data on rides, taxi companies, neighborhoods, and weather conditions.
- **Weather Data**: Data on weather conditions (e.g., "rain," "clear skies") for each hour in November 2017.

Data is cleaned and processed to merge relevant datasets for analysis. The **weather_records** data is linked with the **trips** table using the start time of the ride (`start_ts`) and the weather timestamp (`ts`).

### 2. Exploratory Data Analysis (EDA)
Exploratory analysis focuses on:
- Identifying the number of rides for different taxi companies in Chicago.
- Analyzing the most popular neighborhoods in terms of drop-offs.
- Visualizing the distribution of taxi rides by company and neighborhood.

#### Key Findings:
- Flash Cab is the dominant player in the market.
- The Loop and River North are the busiest neighborhoods in terms of drop-offs.

### 3. Testing Hypotheses
The hypothesis tested is whether the average ride duration from the **Loop** to **O'Hare International Airport** changes on rainy Saturdays. The following steps were performed:
- Data for rainy and non-rainy Saturdays was extracted.
- A t-test was performed to compare the average ride duration between rainy and non-rainy Saturdays.

#### Hypothesis Formulation:
- **Null Hypothesis (H₀)**: The average duration of rides from the Loop to O'Hare does not change on rainy Saturdays.
- **Alternative Hypothesis (H₁)**: The average duration of rides from the Loop to O'Hare changes on rainy Saturdays.

The t-test showed a statistically significant difference, indicating that ride durations are longer on rainy Saturdays.

### 4. Results and Insights
- **Rainy Saturdays**: There is a significant increase in ride durations during rainy Saturdays.
- **Taxi Companies**: Flash Cab and Taxi Affiliation Services dominate the market.
- **Top Neighborhoods**: The Loop and River North have the highest average drop-offs.
- **Recommendations**: Zuber should consider increasing driver availability or implementing dynamic pricing on rainy days to accommodate the increased ride duration.

## Technologies Used

- **Python**: Used for data cleaning, analysis, and visualization.
- **Pandas**: Data manipulation and analysis.
- **Matplotlib**: Data visualization (bar charts, histograms).
- **SciPy**: Statistical hypothesis testing (t-test).

## Installation Instructions

1. **Clone the Repository**:
   ```bash
   git clone <repository_url>
