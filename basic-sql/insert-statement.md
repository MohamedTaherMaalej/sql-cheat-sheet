# SQL INSERT Statement

The `INSERT` statement is used to add new records (rows) to a table in a database.

## Syntax

```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

- `table_name`: The name of the table to insert data into.
- `(column1, column2, ...)`: The columns in which to insert data.
- `VALUES (value1, value2, ...)`: The values to be inserted into the specified columns.

## Examples

### Insert into All Columns

```sql
INSERT INTO employees
VALUES (1, 'John', 'Doe', 'Manager', '2023-01-01', 50000);
```

Insert a new employee into the `employees` table with values for all columns.

### Specify Columns Explicitly

```sql
INSERT INTO products (product_name, category, price)
VALUES ('Laptop', 'Electronics', 1200);
```

Insert a new product into the `products` table, specifying only the relevant columns.

### Insert Multiple Rows

```sql
INSERT INTO customers (customer_name, email)
VALUES
  ('Alice', 'alice@example.com'),
  ('Bob', 'bob@example.com'),
  ('Charlie', 'charlie@example.com');
```

Insert multiple rows into the `customers` table in a single `INSERT` statement.

### Insert Data from Another Table

```sql
INSERT INTO new_employees (first_name, last_name, job_title)
SELECT first_name, last_name, 'Trainee'
FROM temp_employees;
```

Insert data into the `new_employees` table by selecting values from another table.

### Use DEFAULT Keyword

```sql
INSERT INTO orders (customer_id, order_date)
VALUES (101, DEFAULT);
```

Use the `DEFAULT` keyword to insert the default value for a column.

## Notes

- Ensure that the values provided in the `INSERT` statement match the data types of the corresponding columns in the table.
- If the table has an auto-incrementing column, you don't need to provide a value for it; the database will automatically generate one.


