# SQL UPDATE Statement

The `UPDATE` statement is used to modify existing records (rows) in a table in a database.

## Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

- `table_name`: The name of the table to update.
- `column1 = value1, column2 = value2, ...`: The columns to be updated along with their new values.
- `WHERE condition`: Specifies the condition for selecting the rows to be updated.

## Examples

### Update a Single Column

```sql
UPDATE employees
SET job_title = 'Senior Manager'
WHERE employee_id = 1;
```

Update the `job_title` for the employee with `employee_id` 1 in the `employees` table.

### Update Multiple Columns

```sql
UPDATE products
SET price = price * 1.1, stock_quantity = stock_quantity - 5
WHERE category = 'Electronics';
```

Increase the price by 10% and decrease the stock quantity by 5 for all products in the 'Electronics' category.

### Update All Rows

```sql
UPDATE customers
SET status = 'Active';
```

Set the status to 'Active' for all customers in the `customers` table.

### Use Subquery in UPDATE

```sql
UPDATE employees
SET department_id = (SELECT department_id FROM departments WHERE department_name = 'IT')
WHERE job_title = 'Software Engineer';
```

Update the `department_id` for employees with the job title 'Software Engineer' based on a subquery.

## Notes

- The `WHERE` clause is crucial to prevent unintentional updates to all rows in a table. Always include a specific condition to target the desired rows.
- Be cautious when using the `UPDATE` statement, especially without a `WHERE` clause, to avoid unintended data modifications.
- It's good practice to make a backup before performing significant updates, especially in a production environment.
