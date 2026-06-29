# SQL Notes — Chapter 3

## Contents

- [GROUP BY](#group-by)
- [WHERE with GROUP BY](#where-with-group-by)
- [ORDER BY](#order-by)
- [LIMIT](#limit)
- [NULL Values](#null-values)
- [CASE](#case)
- [LIKE](#like)
- [HAVING](#having)
  - [WHERE vs. HAVING](#where-vs-having)
- [Full Query Order of Operations](#full-query-order-of-operations)

---

## GROUP BY

`GROUP BY` gathers rows with the same value in a specified column into groups, then performs calculations on those groups.

**How SQL processes GROUP BY:**
1. Identifies all unique values in the column(s) you're grouping by
2. Creates a separate group for each unique value
3. Applies aggregate functions (COUNT, SUM, AVG, etc.) to each group

**Basic syntax:**
```sql
SELECT 
    column_to_group_by,
    AGGREGATE_FUNCTION(column_to_calculate) AS result_name
FROM
    table_name
GROUP BY 
    column_to_group_by;
```

**Example — count books per author:**
```sql
SELECT 
    author, 
    COUNT(name) AS cnt
FROM
    books_all
GROUP BY 
    author;
```

> ⚠️ Without `GROUP BY`, selecting a column alongside an aggregate function will throw an error.

**Important rules:**
- Any column in your `SELECT` statement that is **not** inside an aggregate function **must** be in your `GROUP BY` clause
- Columns used **inside** aggregate functions should **not** be in `GROUP BY`
- `GROUP BY` can be used with any aggregate function
- Multiple aggregate functions can be called simultaneously

**Example — average and max pages per author:**
```sql
SELECT 
    author, 
    AVG(pages) AS avg_pages,
    MAX(pages) AS max_pages
FROM
    books_all
GROUP BY 
    author;
```

---

## WHERE with GROUP BY

`WHERE` filters individual rows **before** grouping occurs.

**Example — average milk product price per store:**
```sql
SELECT
    name_store,
    AVG(price) AS avg_price
FROM
    products_data
WHERE
    category = 'milk'
GROUP BY
    name_store;
```

---

## ORDER BY

Sorts query results by one or more columns. Default is ascending order.

- `ASC` — ascending (A to Z, small to large)
- `DESC` — descending (Z to A, large to small)

**Example — authors ranked by book count:**
```sql
SELECT 
    author,
    COUNT(name) AS book_count
FROM
    books_all
GROUP BY
    author
ORDER BY
    book_count DESC;
```

**Sorting by multiple columns** (hierarchical — sorts by first column, then second for ties, etc.):
```sql
SELECT 
    author,
    genre,
    rating
FROM books_all    
ORDER BY
    author ASC,
    genre ASC,
    rating DESC;
```

---

## LIMIT

Restricts the number of rows returned. Always comes at the end of a statement.

**Example — top 3 longest books:**
```sql
SELECT 
    name, 
    pages
FROM
    books_all
ORDER BY
    pages DESC
LIMIT 
    3;
```

---

## NULL Values

**Find rows where a value IS NULL:**
```sql
SELECT
    name,
    publisher_id
FROM
    books_all
WHERE 
    publisher_id IS NULL;
```

**Exclude NULL rows with IS NOT NULL:**
```sql
SELECT
    name,
    publisher_id
FROM
    books_all
WHERE 
    publisher_id IS NOT NULL;
```

> ⚠️ `IS NULL` requires both words — `NULL` alone won't work.

---

## CASE

Used to apply conditional logic inside a query. Every `CASE` expression must end with `END`.

**Syntax:**
```sql
CASE
    WHEN condition_1 THEN result_1
    WHEN condition_2 THEN result_2
    WHEN condition_3 THEN result_3
    ELSE result_4
END
```

**Example — replace NULL publisher IDs with -1:**
```sql
SELECT
    name,
    CASE WHEN publisher_id IS NULL THEN -1
    ELSE publisher_id END AS publisher_id_full
FROM
    books_all;
```

> `CASE` can also replace other values, not just NULLs — for example, scanning for negative numbers and replacing them with NULL or a positive value.

---

## LIKE

Searches for fragments of text within a column. Uses wildcard characters for flexible pattern matching.

**Wildcards:**
- `%` — any sequence of characters (including none)
- `_` — exactly one character

**Examples:**
- `'Vampire%'` — starts with "Vampire"
- `'%Vampire'` — ends with "Vampire"
- `'%Vampire%'` — contains "Vampire" anywhere

**Example — find books with "Vampire" in the title:**
```sql
SELECT * 
FROM 
    books_all
WHERE 
    name LIKE '%Vampire%';
```

**NOT LIKE — inverse match:**
```sql
SELECT * 
FROM 
    books_all
WHERE 
    name NOT LIKE '%Vampire%';
```

> ⚠️ **Case sensitivity:** `LIKE` behavior depends on the database system. In **PostgreSQL** it is case-sensitive by default — `'%vampire%'` will NOT match "Vampire". In **MySQL** it is case-insensitive by default. To do a case-insensitive search in PostgreSQL, use `ILIKE` instead:
> ```sql
> WHERE name ILIKE '%vampire%';
> ```
> This will match "Vampire", "VAMPIRE", "vampire", and any other variation.

---

## HAVING

Filters data **after** grouping. Allows filtering based on aggregate functions, which `WHERE` cannot do.

**Example — authors with more than one book:**
```sql
SELECT 
    author_id, 
    COUNT(name) AS book_count
FROM
    books
GROUP BY 
    author_id
HAVING 
    COUNT(name) > 1;
```

### WHERE vs. HAVING

| | WHERE | HAVING |
|---|---|---|
| When it runs | Before grouping | After grouping |
| Can use aggregate functions | ❌ No | ✅ Yes |
| Use for | Conditions on individual rows | Conditions on grouped results |

**Example — both WHERE and HAVING in one query:**
```sql
SELECT 
    name_store, 
    AVG(price) AS avg_price
FROM 
    products_data
WHERE 
    category = 'milk'
GROUP BY 
    name_store
HAVING 
    AVG(price) > 3.40;
```

**Multiple conditions in HAVING using AND / OR:**
```sql
SELECT 
    name_store, 
    AVG(price) AS avg_price, 
    COUNT(id_product) AS product_count
FROM 
    products_data
GROUP BY 
    name_store
HAVING 
    AVG(price) > 1.50 
    AND COUNT(id_product) > 40;
```

**HAVING with CASE — compare category counts:**
```sql
SELECT 
    name_store,
    SUM(CASE WHEN category = 'milk' THEN 1 ELSE 0 END) AS milk_count,
    SUM(CASE WHEN category = 'butter' THEN 1 ELSE 0 END) AS butter_count
FROM 
    products_data
GROUP BY 
    name_store
HAVING 
    SUM(CASE WHEN category = 'butter' THEN 1 ELSE 0 END) > 
    SUM(CASE WHEN category = 'milk' THEN 1 ELSE 0 END) * 0.25;
```

---

## Full Query Order of Operations

Clauses must appear in this exact order or the query will throw a syntax error:

```sql
SELECT 
    column1, 
    column2, 
    AGGREGATE_FUNCTION(column) AS alias
FROM
    table_name
WHERE 
    condition_for_rows          -- Filters individual rows
GROUP BY 
    column1, column2            -- Groups data
HAVING
    AGGREGATE_FUNCTION(column) > value  -- Filters groups
ORDER BY 
    column_or_alias             -- Sorts results
LIMIT 
    n;                          -- Limits rows returned
```
