# Chapter 12: SQL for Data Analysis

In this chapter, we'll explore how SQL can be utilized for data analysis purposes. We'll cover techniques for analyzing data, including the use of window functions and common table expressions (CTEs), which are powerful tools for gaining insights from your datasets.

## Analyzing Data with SQL

SQL provides a rich set of features for data analysis, allowing users to aggregate, filter, and manipulate datasets to extract valuable insights. Whether you're working with transactional data, log files, or sensor readings, SQL can help you uncover patterns, trends, and anomalies within your data.

### Aggregation Functions:
   - SQL offers built-in aggregation functions such as SUM, AVG, COUNT, MIN, and MAX, which enable you to summarize data across rows or groups of rows.
   - These functions are useful for calculating metrics such as total sales, average revenue, or the number of transactions within a given time period.
    ```sql
    -- Calculate total sales for each product category
    SELECT category, SUM(sales_amount) AS total_sales
    FROM sales
    GROUP BY category;
    ```

### Filtering Data:
   - SQL's WHERE clause allows you to filter rows based on specific criteria, such as dates, categories, or numerical ranges.
   - By applying filters, you can focus your analysis on relevant subsets of data and exclude outliers or irrelevant observations.
   ```sql
    -- Filter transactions for the month of January 2024
SELECT *
FROM transactions
WHERE transaction_date BETWEEN '2024-01-01' AND '2024-01-31';
```

### Join Operations:
   - SQL's JOIN operations enable you to combine data from multiple tables based on common keys or relationships.
   - Joins are essential for integrating data from different sources or tables, allowing you to perform cross-sectional analysis and gain a comprehensive view of your data.
```sql
-- Combine sales data with product information
SELECT s.*, p.product_name
FROM sales s
JOIN products p ON s.product_id = p.product_id;

```

## Window Functions

Window functions are a powerful feature in SQL that allow you to perform calculations across a set of rows related to the current row. They provide a flexible way to calculate aggregated values, rankings, and moving averages without the need for complex subqueries or self-joins.

### Example of Window Functions:
   - Calculate cumulative totals or running sums over a time series or ordered dataset.
   - Rank rows based on specific criteria, such as sales performance or customer satisfaction scores.
   - Compute moving averages or rolling averages to smooth out fluctuations in your data.
```sql
-- Calculate cumulative sales over time
SELECT transaction_date, sales_amount,
       SUM(sales_amount) OVER (ORDER BY transaction_date) AS cumulative_sales
FROM sales;

```
## Common Table Expressions (CTEs)

Common Table Expressions (CTEs) provide a way to define temporary result sets within a SQL query, making complex queries more readable and maintainable. CTEs are particularly useful for breaking down complex analysis tasks into smaller, more manageable steps.

### Advantages of CTEs:
   - Improve query readability by breaking down complex logic into smaller, named components.
   - Facilitate code reuse by defining common subqueries that can be referenced multiple times within a single query.
   - Enhance query performance by optimizing the execution plan for recursive or iterative operations.

### Example of CTEs in Data Analysis:
   - Recursive queries to traverse hierarchical data structures, such as organizational charts or product category hierarchies.
   - Preprocessing steps to transform or filter data before performing further analysis.
   - Multi-step analysis workflows involving multiple queries or data transformations.
```sql
--Employees Table:

| employee_id | manager_id | employee_name |
|-------------|------------|---------------|
| 1           | NULL       | John          |
| 2           | 1          | Alice         |
| 3           | 1          | Bob           |
| 4           | 2          | Charlie       |
| 5           | 2          | David         |
| 6           | 3          | Emma          |
| 7           | 4          | Frank         |

--Employee Hierarchy Table:
| employee_id | manager_id | employee_name | level |
|-------------|------------|---------------|-------|
| 1           | NULL       | John          | 1     |
| 2           | 1          | Alice         | 2     |
| 3           | 1          | Bob           | 2     |
| 4           | 2          | Charlie       | 3     |
| 5           | 2          | David         | 3     |
| 6           | 3          | Emma          | 3     |
| 7           | 4          | Frank         | 4     |

-- Calculate hierarchical structure of employees
WITH RECURSIVE employee_hierarchy AS (
    SELECT employee_id, manager_id, employee_name, 1 AS level
    FROM employees
    WHERE manager_id IS NULL
    UNION ALL
    SELECT e.employee_id, e.manager_id, e.employee_name, eh.level + 1
    FROM employees e
    JOIN employee_hierarchy eh ON e.manager_id = eh.employee_id
)
SELECT * FROM employee_hierarchy;

```

```sql
| employee_id | manager_id | employee_name | level |
|-------------|------------|---------------|-------|
| 1           | NULL       | John          | 1     |
| 2           | 1          | Alice         | 2     |
| 3           | 1          | Bob           | 2     |
| 4           | 2          | Charlie       | 3     |
| 5           | 2          | David         | 3     |
| 6           | 3          | Emma          | 3     |
| 7           | 4          | Frank         | 4     |

```
By leveraging SQL's analytical capabilities, including aggregation functions, window functions, and common table expressions, you can perform a wide range of data analysis tasks directly within your database environment. Whether you're exploring trends in sales data, identifying outliers in financial transactions, or conducting cohort analysis on user behavior, SQL provides the tools you need to extract actionable insights from your datasets.