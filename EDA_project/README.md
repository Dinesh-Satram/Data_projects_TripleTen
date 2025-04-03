# Instacart EDA and Product Analysis

## Project Overview

This project involves performing Exploratory Data Analysis (EDA) on a dataset from Instacart, a popular grocery delivery platform. The goal of the project is to clean, analyze, and derive insights into the shopping habits of Instacart customers. The dataset consists of various CSV files representing orders, products, aisles, and departments. We aim to understand customer behavior, product preferences, and the frequency of reorders through analysis.

## Data Description

The dataset is divided into five main files:

1. **instacart_orders.csv**  
   Contains details about orders placed by customers.  
   Columns:  
   - `order_id`: Unique identifier for each order  
   - `user_id`: Unique identifier for each customer  
   - `order_number`: Number of orders placed by the customer  
   - `order_dow`: Day of the week when the order was placed  
   - `order_hour_of_day`: Hour of the day when the order was placed  
   - `days_since_prior_order`: Days since the last order  

2. **products.csv**  
   Contains details about products available for purchase.  
   Columns:  
   - `product_id`: Unique identifier for each product  
   - `product_name`: Name of the product  
   - `aisle_id`: Aisle category ID  
   - `department_id`: Department category ID  

3. **order_products.csv**  
   Contains details about individual items in each order.  
   Columns:  
   - `order_id`: Unique identifier for each order  
   - `product_id`: Unique identifier for each product  
   - `add_to_cart_order`: Sequential order in which the item was added to the cart  
   - `reordered`: Indicates if the product was reordered  

4. **aisles.csv**  
   Contains information about aisles.  
   Columns:  
   - `aisle_id`: Unique identifier for each aisle  
   - `aisle`: Name of the aisle  

5. **departments.csv**  
   Contains information about departments.  
   Columns:  
   - `department_id`: Unique identifier for each department  
   - `department`: Name of the department  

## Data Preprocessing

The following preprocessing steps were performed on the dataset:

- **Removing duplicates**: Duplicate rows were identified and removed to ensure data integrity.
- **Handling missing values**: Missing values in the `product_name` column were filled with "Unknown." Missing values in `days_since_prior_order` and `add_to_cart_order` were appropriately handled with default values.
- **Data type correction**: Ensured all ID columns are in integer format for consistency.

## Exploratory Data Analysis (EDA)

Key analyses performed in this project include:

- **Order Analysis**:
  - Examined the distribution of orders by hour of the day and day of the week.
  - Analyzed the time customers typically wait before placing another order.

- **Customer Behavior**:
  - Investigated the distribution of the number of orders per customer.
  - Identified top products ordered most frequently and top reordered items.

- **Product Analysis**:
  - Examined the typical number of items bought in one order.
  - Analyzed the top 20 products that are reordered frequently.
  - Investigated which products are added first to customers' carts.

## Insights & Findings

- **Shopping Habits**:
  - The majority of orders are placed on Sundays, with a peak in the late morning (around 10 AM).
  - Customers tend to wait an average of 11 days before placing another order.
  
- **Product Trends**:
  - Bananas are among the top products ordered and reordered.
  - Most customers order fewer products, with 1 to 5 orders being the most common.
  - A significant number of products are reordered, with organic products like avocados, strawberries, and milk being highly reordered.

- **Top 20 Products**:
  - The top 20 products include frequently ordered items like bananas, organic strawberries, and organic baby spinach.

## Visualizations

This project includes various plots, such as:

- **Bar charts** showing orders by hour of the day and day of the week.
- **Histograms** representing the distribution of days since prior orders and the number of items in each order.
- **Top 20 Products** visualized through bar charts and frequency distributions.

## Technologies Used

- **Pandas**: Data manipulation and analysis.
- **Matplotlib**: Data visualization.
- **Jupyter Notebook**: Interactive environment for performing EDA.

## Future Improvements

- Explore customer segmentation to provide more personalized insights.
- Implement advanced machine learning models to predict customer behavior, such as product reordering probabilities.
- Perform sentiment analysis on product reviews (if available) to gather more customer insights.

## Conclusion

This project provided valuable insights into Instacart’s customer behavior, highlighting the importance of product popularity, reorder frequency, and timing in customer purchases. The findings can help optimize inventory management, marketing strategies, and customer engagement initiatives.
