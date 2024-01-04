# Creating Tables in SQL

In SQL, tables are used to store data in a structured format. Here is a guide on how to create tables.

## Syntax

```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    column3 datatype,
    ...
);
```

- `table_name`: The name you want to give to your table.
- `column1, column2, column3, ...`: The columns in the table.
- `datatype`: The data type for each column.

## Example

```sql
CREATE TABLE employees (
    employee_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    job_title VARCHAR(100),
    hire_date DATE,
    salary DECIMAL(10, 2)
);
```

This example creates a table named `employees` with columns for `employee_id`, `first_name`, `last_name`, `job_title`, `hire_date`, and `salary`. The `employee_id` is specified as the primary key.

## Adding Constraints

You can add constraints to columns to enforce rules on the data.

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100) NOT NULL,
    price DECIMAL(8, 2) CHECK (price >= 0),
    category VARCHAR(50),
    UNIQUE (product_name, category)
);
```

In this example, the `products` table has a unique constraint on the combination of `product_name` and `category`. The `price` column has a check constraint to ensure it is not negative.

## Specifying Default Values

You can specify default values for columns.

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    order_date DATE DEFAULT CURRENT_DATE,
    customer_id INT,
    total_amount DECIMAL(10, 2) DEFAULT 0
);
```

Here, the `order_date` column has a default value of the current date, and the `total_amount` column has a default value of 0.

## Notes

- Choose appropriate data types for your columns based on the nature of the data.
- Primary keys uniquely identify each row in a table.
- Constraints help maintain data integrity by enforcing rules on the data.
- Specify default values for columns when it makes sense for your application.

## Adding Indexes

You can add indexes to columns to improve query performance.

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50),
    email VARCHAR(100) UNIQUE,
    INDEX idx_last_name (last_name)
);
```

In this example, an index named `idx_last_name` is created on the `last_name` column to improve the speed of queries that involve searching or sorting by last name.


