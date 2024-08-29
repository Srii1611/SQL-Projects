# Walmart Sales Data Analysis

## Project Overview

This project aims to analyze Walmart sales data to identify the top-performing stores and products, examine sales trends across different product categories, and gain insights into customer behavior. The goal is to explore how sales strategies can be refined and optimized for better performance.

The dataset, sourced from the Kaggle Walmart Sales Forecasting Competition, includes historical sales data from 45 Walmart stores across various regions. Each store features multiple departments, and the task is to forecast sales for each department within each store. The dataset also includes selected holiday markdown events, which are known to influence sales patterns. However, predicting which departments will be impacted and to what extent poses a significant challenge.
## Purpose of the Project

The primary goal of this project is to analyze Walmart's sales data to identify and understand the various factors influencing sales across different branches.
## About Data

The dataset was obtained from the [Kaggle Walmart Sales Forecasting Competition](https://www.kaggle.com/c/walmart-recruiting-store-sales-forecasting). This dataset contains sales transactions from a three different branches of Walmart, respectively located in Mandalay, Yangon and Naypyitaw. The data contains 17 columns and 1000 rows:

| Column                  | Description                             | Data Type      |
| :---------------------- | :-------------------------------------- | :------------- |
| invoice_id              | Invoice of the sales made               | VARCHAR(30)    |
| branch                  | Branch at which sales were made         | VARCHAR(5)     |
| city                    | The location of the branch              | VARCHAR(30)    |
| customer_type           | The type of the customer                | VARCHAR(30)    |
| gender                  | Gender of the customer making purchase  | VARCHAR(10)    |
| product_line            | Product line of the product solf        | VARCHAR(100)   |
| unit_price              | The price of each product               | DECIMAL(10, 2) |
| quantity                | The amount of the product sold          | INT            |
| VAT                 | The amount of tax on the purchase       | FLOAT(6, 4)    |
| total                   | The total cost of the purchase          | DECIMAL(10, 2) |
| date                    | The date on which the purchase was made | DATE           |
| time                    | The time at which the purchase was made | TIMESTAMP      |
| payment_method                 | The total amount paid                   | DECIMAL(10, 2) |
| cogs                    | Cost Of Goods sold                      | DECIMAL(10, 2) |
| gross_margin_percentage | Gross margin percentage                 | FLOAT(11, 9)   |
| gross_income            | Gross Income                            | DECIMAL(10, 2) |
| rating                  | Rating                                  | FLOAT(2, 1)    |

### Analysis Overview

1. **Product Performance Evaluation**

   > Analyze the data to gain insights into various product lines, identify the top-performing lines, and determine which ones require improvement.

2. **Sales Trend Analysis**

   > Examine sales data to uncover trends across different products, assess the effectiveness of existing sales strategies, and identify areas for strategic adjustments to boost sales.

3. **Customer Segmentation Analysis**

   > Explore customer data to reveal distinct segments, understand purchasing patterns, and evaluate the profitability of each customer segment.
##  Methodology Applied

1. **Data Preparation:** This initial step involves inspecting the dataset to identify and address any **NULL** or missing values, ensuring data integrity through appropriate replacement methods.

   > 1. Set up the database.
   > 2. Create tables and populate them with data.
   > 3. Identify columns with potential null values. Since we set **NOT NULL** constraints during table creation, null values were automatically excluded.

2. **Feature Engineering:** This process involves creating new columns from existing data to enhance analysis.

   > 1. Introduce a `time_of_day` column to categorize sales into Morning, Afternoon, and Evening segments. This will help identify the time of day with the highest sales activity.
   > 2. Add a `name_of_day` column to extract the day of the week (Mon, Tue, Wed, Thu, Fri) for each transaction, allowing us to determine which day each branch experiences the most traffic.
   > 3. Create a `name_of_month` column to capture the month (Jan, Feb, Mar) of each transaction, helping to identify the month with the highest sales and profit.

3. **Exploratory Data Analysis (EDA):** Conducted to explore the data and address the project's key questions and objectives.

4. **Summary:** Draw conclusions based on the analysis and findings.
   
## Business Questions To Answer

### Generic Question

1. How many unique cities does the data have?
2. In which city is each branch?

### Product

1. How many unique product lines does the data have?
2. What is the most common payment method?
3. What is the most selling product line?
4. What is the total revenue by month?
5. What month had the largest COGS?
6. What product line had the largest revenue?
5. What is the city with the largest revenue?
6. What product line had the largest VAT?
7. Fetch each product line and add a column to those product line showing "Good", "Bad". Good if its greater than average sales
8. Which branch sold more products than average product sold?
9. What is the most common product line by gender?
12. What is the average rating of each product line?

### Sales

1. Number of sales made in each time of the day per weekday
2. Which of the customer types brings the most revenue?
3. Which city has the largest tax percent/ VAT (**Value Added Tax**)?
4. Which customer type pays the most in VAT?

### Customer

1. How many unique customer types does the data have?
2. How many unique payment methods does the data have?
3. What is the most common customer type?
4. Which customer type buys the most?
5. What is the gender of most of the customers?
6. What is the gender distribution per branch?
7. Which time of the day do customers give most ratings?
8. Which time of the day do customers give most ratings per branch?
9. Which day fo the week has the best avg ratings?
10. Which day of the week has the best average ratings per branch?


## Revenue And Profit Calculations

$ COGS = unitsPrice * quantity $

$ VAT = 5\% * COGS $

$VAT$ is added to the $COGS$ and this is what is billed to the customer.

$ total(gross_sales) = VAT + COGS $

$ grossProfit(grossIncome) = total(gross_sales) - COGS $

**Gross Margin** is gross profit expressed in percentage of the total(gross profit/revenue)

$ \text{Gross Margin} = \frac{\text{gross income}}{\text{total revenue}} $

<u>**Example with the first row in our DB:**</u>

**Data given:**

- $ \text{Unite Price} = 45.79 $
- $ \text{Quantity} = 7 $

$ COGS = 45.79 * 7 = 320.53 $

$ \text{VAT} = 5\% * COGS\\= 5\%  320.53 = 16.0265 $

$ total = VAT + COGS\\= 16.0265 + 320.53 = $336.5565$

$ \text{Gross Margin Percentage} = \frac{\text{gross income}}{\text{total revenue}}\\=\frac{16.0265}{336.5565} = 0.047619\\\approx 4.7619\% $
