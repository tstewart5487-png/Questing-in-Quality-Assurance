# SQL Functions Cheat Sheet

A comprehensive quick-reference guide for SQL limiting operators, string manipulation, date/time adjustments, and mathematical operations.

---

## Result Limiting

* **`OFFSET`**: Specifies how many records to skip before starting to return rows.
* **`LIMIT`**: Restricts the maximum number of records returned in the result set.

```sql
-- Skips the first 5 rows
SELECT title, my_rating 
FROM table 
OFFSET 5;

-- Prints 3 items after skipping the first 5 rows (returns rows 6, 7, and 8)
SELECT title, my_rating 
FROM films_i_watched 
LIMIT 3 OFFSET 5;
```

---

## String Functions

String functions allow you to combine multiple text fields, modify appearance, delete characters, or calculate string lengths.

* **`LENGTH(string)`**: Returns the total number of characters within a string. 
  * *Note:* It counts all characters, including leading, trailing, and middle spaces. Useful for filtering out incorrect records.
* **`REPLACE(string, old_substring, new_substring)`**: Replaces a target substring with a new substring of any size. 
  * *Note:* This does not modify the source data in the database; it only affects how the data is displayed.
* **`INITCAP(string)`**: Capitalizes the first letter of each word and forces all other letters to lowercase.
* **`LOWER(string)`**: Returns the string with all characters converted to lowercase.
* **`UPPER(string)`**: Returns the string with all characters converted to uppercase.
* **`LTRIM(string, [characters])`**: Deletes specified characters from the left side of a string (removes empty spaces by default).
* **`RTRIM(string, [characters])`**: Deletes specified characters from the right side of a string (removes empty spaces by default).
* **`CONCAT(str1, str2, ...)`**: Concatenates strings into a single value. It combines them without spaces automatically, so explicit spaces must be passed as arguments.

### Examples

```sql
SELECT LENGTH('I study SQL');
-- Result: 11

SELECT REPLACE('Winston/Salem', '/', '-');
-- Result: Winston-Salem

SELECT INITCAP('kay layla smith');
-- Result: Kay Layla Smith

SELECT LOWER('ProBLEms wiTh striNGS');
-- Result: problems with strings

SELECT UPPER('ProBLEms wiTh striNGS');
-- Result: PROBLEMS WITH STRINGS

SELECT LTRIM('Kayak', 'Ka');
-- Result: yak

SELECT RTRIM('Kayak', 'ak');
-- Result: Kay

SELECT CONCAT('SQL', ' ', 'Masters', ' ', 'Rule');
-- Result: SQL Masters Rule
```

---

## Date and Time Functions

* **`CURRENT_DATE`**: Returns the current system date.
* **`CURRENT_TIME`**: Returns the current system time.
* **`CURRENT_TIMESTAMP`**: Returns both the current system date and time.
* **`DATE_TRUNC('time_period', field)`**: Shortens/rounds date and time down to the first day or unit of a specified value (e.g., year, month, day). Returns data with a **timestamp** data type.
* **`EXTRACT(time_period FROM field)`**: Extracts a specific numerical subpart of a date/time field. Returns data with a **double precision (float8)** data type.

> ⚠️ **Time Zone Note:** Both functions automatically convert date and time types into `timestamp with time zone`. The displayed time adapts to the user's specific time zone configuration, meaning values might shift based on location.

### Valid Time Periods

| Context | Allowed Time Periods / Units |
| :--- | :--- |
| **`DATE_TRUNC`** | `'microseconds'`, `'milliseconds'`, `'second'`, `'minute'`, `'hour'`, `'day'`, `'week'`, `'month'`, `'quarter'`, `'year'`, `'decade'`, `'century'` |
| **`EXTRACT`** | `CENTURY`, `YEAR`, `QUARTER`, `MONTH`, `WEEK`, `DAY`, `HOUR`, `MINUTE`, `SECOND`, `MILLISECOND`, `DOY` (day of year 1-365/366), `DOW` (day of week 0-6, 0=Sunday), `ISODOW` (ISO day of week 1-7, 1=Monday) |

### Date Truncation Examples

Assuming `birth_date` contains standard timestamp data (e.g., `1962-02-18 00:00:00`):

```sql
-- Rounds the date down to the first day of the year
SELECT DATE_TRUNC('year', birth_date) FROM staff LIMIT 5;
-- Result: 01.01.1962 00:00:00

-- Rounds the date down to the first day of the month
SELECT DATE_TRUNC('month', birth_date) FROM staff LIMIT 5;
-- Result: 01.02.1962 00:00:00
```

---

## Mathematical Functions

| Function | Description | Example | Result |
| :--- | :--- | :--- | :--- |
| **`ABS(x)`** | Returns the absolute magnitude of a number (converts negative values to positive; positive stays unchanged). | `ABS(-14)` | `14` |
| **`CEILING(x)`** | Rounds a number up to the nearest whole number. | `CEILING(42.8)` | `43` |
| **`FLOOR(x)`** | Rounds a number down to the nearest whole number. | `FLOOR(42.8)` | `42` |
| **`ROUND(x)`** | Rounds a value to the nearest whole number. | `ROUND(42.4)` | `42` |
| **`ROUND(x, d)`** | Rounds a number to a specific number of decimal places `d`. | `ROUND(42.4382, 2)` | `42.44` |
| **`TRUNC(x)`** | Shortens the value to a whole number by dropping all decimals without rounding. | `TRUNC(42.4)` | `42` |
| **`TRUNC(x, d)`** | Shortens a number to a specified amount of decimal places `d` without rounding. | `TRUNC(42.4382, 2)` | `42.43` |
| **`POWER(x, y)`** | Returns the number `x` raised to the `y`-th power. | `POWER(9, 3)` | `729` |
| **`SQRT(x)`** | Takes the square root of a number. Throws an error if the input argument is negative. | `SQRT(9)` | `3` |

### Math Query Examples

```sql
SELECT number, FLOOR(number) FROM table_1;
SELECT number, CEILING(number) FROM table_1;
SELECT number, ROUND(number) FROM table_1;
SELECT ROUND(21.5595743, 2);
SELECT number, POWER(number, 2) FROM table_1;

-- Using ABS inside SQRT to prevent errors from negative inputs
SELECT number, SQRT(ABS(number)) FROM table_1;
```
