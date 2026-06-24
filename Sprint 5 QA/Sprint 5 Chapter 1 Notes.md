# Chapter 1: Tables, Databases, and SQL

Welcome to the Chapter 1 study guide. This document contains a comprehensive index summary of SQL fundamentals, strict layout rules, and interactive challenge examples to test your knowledge.

## 📋 Index Summary
Click on any link below to jump directly to that section:
* [1. Core Database Concepts](#1-core-database-concepts) — Databases, Relational vs Non-Relational, and DBMS.
* [2. SQL Syntax & Rules](#2-sql-syntax--rules) — Basic operations, comments, and uppercase conventions.
* [3. Data Types Reference](#3-data-types-reference) — Storage sizes, literal quotes, and data safety.
* [4. Filtering with WHERE](#4-filtering-with-where) — The exact order of operations, slices, and operators.
* [5. Range & List Operators](#5-range--list-operators) — Simplifying complex filtering logic using `BETWEEN` and `IN`.
* [6. Interactive Coding Sandbox](#6-interactive-coding-sandbox) — Practice challenges with hidden answers.

---

## 1. Core Database Concepts
* **SQL (Structured Query Language):** A specialized language used to request information from databases. It allows you to filter, combine information from multiple tables, and summarize large datasets quickly.
* **Database:** An organized collection of structured information that consists of tables.
* **Relational Database:** Organizes data into tables with rows and columns. Tables are related to each other, meaning data in one table connects to data in another through a column they share.
* **Non-Relational Database:** Stores data in non-tabular formats, such as:
  * Documents
  * Key-value pairs
  * Graphs
* **DBMS (Database Management System):** A set of software programs that allows you to create a database, fill it with new tables, display the content, and edit existing records.
  * *Most Popular DBMS Examples:* PostgreSQL, Oracle, MySQL, Microsoft SQL Server.

---

## 2. SQL Syntax & Rules

### Basic Rules
* SQL operates through simple commands, also known as **statements** or **queries**.
* A semicolon `;` marks the exact end of your statement.
* An asterisk `*` stands for **all columns**.

### Code Comments
* For short, single-line comments, use two dashes `--`.
* For longer, multi-line explanations, use `/*` to start and `*/` to end:
  ```sql
  /* 
  This is a multi-line comment 
  explaining the code logic below 
  */
  ```

### Formatting Styles
While SQL is not case-sensitive (meaning `SELECT` and `select` mean the same thing), there are some conventions that make your code easier to read:
* Write SQL keywords in **UPPERCASE** (e.g., `SELECT`, `FROM`).
* Keywords should be on their own line.
* It's okay to include an argument on the same line as the keyword if there is exactly one argument.
* **Arguments:** A value you give to a command to tell it what to work with. For example, in `SELECT units`, `units` is the argument.

---

## 3. Data Types
Data types are categories of information. Choosing the correct data type ensures the database knows how much space to reserve, how to compare data, and what operations are valid. Knowing these types prevents errors like trying to compare text strings to numbers.

### Core Data Types
* **Integers:** Whole numbers without decimals.
* **Decimal or Numeric:** Stores decimal numbers or floats.
* **Text:** Used for strings of any length. Statements go in single quotes in SQL (`'text'`).
* **varchar(n):** Variable character data that stores text data with a custom character limit `(n)`. Great for usernames, emails, and short bios.
* **Timestamp:** Stores both date and time. Often used to store rapid events like login logs.
* **Date:** Stores calendar dates.
* **Time:** Stores clock times.
* **Boolean:** A logical data type that can have 3 values: `TRUE`, `FALSE`, or `NULL`.

> [!WARNING]
> All text and date values must be wrapped in single quotes. Do not use quotes for numerical, boolean, or `NULL` data types.

> [!TIP]
> In most cases, you can assume what data type each column might be just by looking at the table:
> * Names and descriptions → **Text types**
> * Amounts, counts, measurements → **Number types**
> * Calendar dates or timestamps → **Date types**
> * Yes/no flags → **Boolean type**

---

## 4. Filtering with WHERE
The `WHERE` clause lets us filter data from a table based on specific conditions. When you use `WHERE` to receive a filtered view of the table, this view is called a **data slice**.

### Strict Query Order
The structural layout of an SQL query must always follow this order:
1. `SELECT` (what columns you want)
2. `FROM` (what table to get them from)
3. `WHERE` (what conditions must be met)

> [!NOTE]
> The `WHERE` clause allows you to set conditions based on any column, regardless of whether it appears in your final `SELECT` list.

### Comparison Operators

| Comparison Operator | Description |
| :--- | :--- |
| `<` | Less than |
| `>` | Greater than |
| `<=` | Less than or equal to |
| `>=` | Greater than or equal to |
| `=` | Equal to |
| `!=` or `<>` | Not equal to |

> [!CAUTION]
> **Syntax Error Warning:** `=<` is not recognized in SQL grammar rules.
> * ❌ **Incorrect:** `=<`
> * **How to fix:** SQL expects `<=`, not `=<`

---

## 5. Range & List Operators
You can filter values that fall within a specific range or match specific items from a list using the `BETWEEN` and `IN` operators.

### The BETWEEN Operator
The `BETWEEN` operator specifies a range of values. This selects all products with prices from $1 to $3, **inclusive**.

```sql
SELECT name, price 
FROM products_data 
WHERE price BETWEEN 1 AND 3;

-- It works the same as writing:
SELECT name, price 
FROM products_data 
WHERE price >= 1 AND price <= 3;
```

### The IN Operator
The `IN` operator allows you to specify multiple possible values for a column.

```sql
SELECT name, category 
FROM products_data 
WHERE category IN ('milk', 'butter');

-- It works the same as writing:
SELECT name, category 
FROM products_data 
WHERE category = 'milk' OR category = 'butter';
```

### The NOT IN Operator
The `NOT IN` operator returns only the rows where the value is not in the list.

```sql
SELECT name, category 
FROM products_data 
WHERE category NOT IN ('butter');

-- It works the same as writing:
SELECT name, category 
FROM products_data 
WHERE category != 'butter';
```

---

## 6. Interactive Coding Sandbox

Test your SQL formatting and filtering layout skills below. Click **"Reveal Answer"** to verify your solution.

### 🏋️ Challenge 1: Finding Syntax Errors
**Scenario:** You want to find all items from a table named `store_inventory` where the stock level is less than or equal to 5 units, but your current query is crashing. Find and fix all errors in the query below:

```sql
SELECT * FROM store_inventory WHERE stock =< '5'
```

<details>
<summary>🔍 Reveal Answer</summary>

**Identified Errors:**
1. The comparison operator `=<` is invalid. It must be written as `<=`.
2. The numeric value `5` should not be wrapped in single quotes.

**Corrected Query:**
```sql
SELECT * 
FROM store_inventory 
WHERE stock <= 5;
```
</details>

### 🏋️ Challenge 2: Cleaning List Code
**Scenario:** Rewrite this multi-line `OR` statement using an `IN` operator list to make it clean, readable, and properly structured according to standard keywords conventions:

```sql
select item_name, region from warehouse where region = 'North' or region = 'East' or region = 'West';
```

<details>
<summary>🔍 Reveal Answer</summary>

**Corrected Query:**
```sql
SELECT item_name, region 
FROM warehouse 
WHERE region IN ('North', 'East', 'West');
```
</details>
