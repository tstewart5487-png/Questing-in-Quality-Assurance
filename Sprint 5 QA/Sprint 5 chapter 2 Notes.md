# Chapter 2: SQL Aggregate Functions & Data Types

## Table of Contents
* [Core Concepts](#core-concepts)
* [Essential Aggregate Functions](#essential-aggregate-functions)
  * [1. COUNT](#1-count)
  * [2. SUM & AVG](#2-sum--avg)
  * [3. MIN & MAX](#3-min--max)
* [Key Techniques & Operations](#key-techniques--operations)
  * [Combining Aggregates with Filtering](#combining-aggregates with-filtering)
  * [Data Typecasting (CAST)](#data-typecasting-cast)
  * [Inspecting Database Schema](#inspecting-database-schema)
* [Mathematical Applications with MIN and MAX](#mathematical-applications-with-min-and-max)
* [Quick Reference Summary](#quick-reference-summary)

---

## Core Concepts

* **NULL Marker**: Represents the **absence of data**. It is not zero, an empty string, or false. 
  * *Occurrences*: Data was unavailable during creation, is not applicable, or remains unknown.
* **Aggregate Functions**: Collect and combine all objects within a group to calculate a single summary value.
* **Aliasing (`AS`)**: Renames the output column. If omitted, SQL falls back to a default label like `count(*)`.

---

## Essential Aggregate Functions

### 1. COUNT
Counts rows or values. Requires an argument inside the parentheses (either a column name or `*`).

* **Total Rows**: Counts every row in the table.
  ```sql
  SELECT COUNT(*) AS total_products FROM products_data;
  ```
* **Specific Column Values**: Counts how many non-NULL values exist in a specific column.
  ```sql
  SELECT COUNT(price) AS price_count FROM products_data;
  ```
* **Unique Values (`DISTINCT`)**: Counts only the unique, non-repeating values in a column.
  ```sql
  SELECT COUNT(DISTINCT category) AS category_count FROM products_data;
  ```

### 2. SUM & AVG
* **`SUM`**: Adds up numeric values in a column. Only works with numeric data types.
* **`AVG`**: Calculates the mathematical average of a numeric column.

### 3. MIN & MAX
* **`MIN`**: Finds the smallest value (numbers, dates, or text boundaries) in a column.
* **`MAX`**: Finds the largest value or performance extreme in a column.

---

## Key Techniques & Operations

### Combining Aggregates with Filtering
You can combine multiple aggregate functions in a single statement and restrict the analysis to a specific subset of data using a `WHERE` clause.

```sql
SELECT 
    AVG(price) AS avg_price, 
    COUNT(*) AS product_count, 
    SUM(price) AS total_value 
FROM products_data 
WHERE name_store = 'Wise Penny' 
  AND date_upd >= '2019-06-01 00:00:00';
```

### Data Typecasting (`CAST`)
Changes the data type of a column on the fly so you can perform mathematical operations or aggregations.

* **Standard Syntax**:
  ```sql
  SELECT SUM(CAST(weight AS decimal)) AS weight_total FROM products_data_typecasting;
  ```
* **Shorthand Syntax (`::`)**:
  ```sql
  SELECT SUM(weight::decimal) AS weight_total FROM products_data_typecasting;
  ```

### Inspecting Database Schema
Use this query to quickly verify the data types of columns within a specific table.

```sql
SELECT column_name, data_type 
FROM information_schema.columns 
WHERE table_name = 'products_data_typecasting';
```

---

## Mathematical Applications with MIN and MAX

You can use standard math operators (`+`, `-`, `*`, `/`, `%`) directly on aggregate functions to reveal advanced metrics:

| Metric | SQL Formula | Purpose |
| :--- | :--- | :--- |
| **Calculate Range** | `MAX(price) - MIN(price)` | Shows the complete price spread/difference. |
| **Calculate Midpoint** | `(MAX(price) + MIN(price)) / 2` | Finds the middle point of the range. |
| **Calculate Ratio** | `MAX(price) / MIN(price)` | Shows how many times larger the maximum value is compared to the minimum. |

---

## Quick Reference Summary

* **Find Minimum**: `MIN(column_name)`
* **Find Maximum**: `MAX(column_name)`
* **Calculate Range**: `MAX(column_name) - MIN(column_name)`
* **Calculate Midpoint**: `(MIN(column_name) + MAX(column_name)) / 2`
* **Calculate Ratio**: `MAX(column_name) / MIN(column_name)`
* **Filtered Minimum**: `MIN(column_name) ... WHERE condition`
* **Filtered Maximum**: `MAX(column_name) ... WHERE condition`
