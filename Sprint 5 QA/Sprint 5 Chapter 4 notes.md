# SQL Notes — Chapter 4

## Contents

- [Primary Key](#primary-key)
- [Foreign Key](#foreign-key)
- [Table Relationships](#table-relationships)
  - [One to One](#one-to-one)
  - [One to Many](#one-to-many)
  - [Many to Many](#many-to-many)
- [ER Diagrams](#er-diagrams)
- [JOIN](#join)
  - [INNER JOIN](#inner-join)
  - [OUTER JOIN](#outer-join)
  - [LEFT JOIN](#left-join)
  - [RIGHT JOIN](#right-join)

---

## Primary Key

A **primary key** is a column (or set of columns) that uniquely identifies each row in a table.

- Strictly unique — no duplicates allowed
- Never allowed to have `NULL` values
- Only one primary key constraint per table
- Acts as the main anchor for a database table

---

## Foreign Key

A **foreign key** links a row in one table to a primary key in another table.

- Can be `NULL` (signifies no relationship)
- Multiple foreign keys are allowed per table
- References the primary key of a parent table

---

## Table Relationships

### One to One

Each row in one table connects to only one row in the other table. Considered very secure.

### One to Many

Each row in one table connects to multiple rows in another table.

### Many to Many

Several rows from one table match several rows from another. Produces an **association/junction table** that combines the primary keys of both tables.

---

## ER Diagrams

The relationships between tables in a database can be visualized with **ER (Entity-Relationship) diagrams**.

- `PK` — Primary Key
- `FK` — Foreign Key

---

## JOIN

The `JOIN` operator is used to merge tables. There are two main types: **INNER JOIN** and **OUTER JOIN**.

---

### INNER JOIN

Selects only records that have matching values in **both** tables. Rows without a match in either table are excluded.

> 💡 With `INNER JOIN`, the order of tables does not matter — the result is the same either way.

**Syntax:**
```sql
FROM
    authors
INNER JOIN books ON authors.id = books.author_id;
```

- In the `ON` clause, specify the primary key from one table and the foreign key from the other
- In the `SELECT` block, qualify column names with their table name (e.g. `authors.first_name`) to avoid conflicts

**Example — retrieve all columns from both tables:**
```sql
SELECT
    authors.id,
    authors.first_name,
    authors.last_name,
    books.book_id,
    books.name AS book_title,
    books.genre,
    books.author_id,
    books.date_pub,
    books.pages,
    books.rating,
    books.publisher_id
FROM
    authors
INNER JOIN books ON authors.id = books.author_id;
```

> ⚠️ Not qualifying columns with the table name can cause confusion or errors if column names conflict across tables. Always specify which table each column comes from.

**Example — filter with WHERE after joining:**
```sql
SELECT 
    books.name AS name,
    authors.first_name,
    authors.last_name
FROM
    books
INNER JOIN authors ON authors.id = books.author_id
WHERE 
    authors.first_name = 'Dean'
    AND authors.last_name = 'Koontz';
```

---

### OUTER JOIN

Returns all records from one or both tables — even if the other table has no matching record. Unmatched rows are filled in with `NULL` where data is missing.

Comes in two types: `LEFT JOIN` and `RIGHT JOIN`.

---

### LEFT JOIN

Returns **all rows from the left table** and the matching rows from the right table. Where there is no match, `NULL` is returned for the right table's columns.

> The **left table** is the one listed first in the `FROM` clause.

**Example:**
```sql
FROM
    authors
LEFT JOIN books ON authors.id = books.author_id;
```

- Returns all authors, even those with no books
- For authors without books, book columns will be `NULL`
- Books without a matching author will **not** appear

> 💡 If you swap the tables so `books` is on the left, you get all books even those with no matching author — but authors without books won't appear.

---

### RIGHT JOIN

The mirror image of `LEFT JOIN`. Returns **all rows from the right table** and the matching rows from the left table.

> The **right table** is the one that appears second in the `JOIN` clause.