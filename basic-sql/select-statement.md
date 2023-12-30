# SQL SELECT Statement

The `SELECT` statement is used to query a database and retrieve data from one or more tables. It is one of the most fundamental and commonly used SQL commands.

## Syntax

```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

- `column1, column2, ...`: The columns you want to retrieve.
- `table_name`: The name of the table from which to retrieve data.
- `WHERE condition`: Optional. Specifies a condition to filter the rows returned.

## Examples

### Select All Columns from a Table

```sql
SELECT *
FROM employees;
```

This query retrieves all columns from the `employees` table.

### Select Specific Columns

```sql
SELECT first_name, last_name, job_title
FROM employees;
```

Retrieve only the `first_name`, `last_name`, and `job_title` columns from the `employees` table.

### Filter Data with WHERE Clause

```sql
SELECT product_name, price
FROM products
WHERE category = 'Electronics';
```

Retrieve the `product_name` and `price` columns from the `products` table where the `category` is 'Electronics'.

### Alias for Columns

```sql
SELECT product_name AS 'Product', price AS 'Price'
FROM products;
```

Use aliases for column names to make the result set more readable.

### Distinct Values

```sql
SELECT DISTINCT category
FROM products;
```

Retrieve distinct values from the `category` column in the `products` table.

### Limiting Rows

```sql
SELECT *
FROM orders
LIMIT 10;
```

Limit the result set to the first 10 rows.

## Notes

- The `SELECT` statement is case-insensitive, so `SELECT` and `select` are equivalent.
- Use caution with the `SELECT *` statement, especially in large tables, as it may retrieve more data than necessary.
- Always sanitize user inputs to prevent SQL injection attacks when using the `WHERE` clause.

