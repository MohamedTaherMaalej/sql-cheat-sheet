# SQL DELETE Statement

The `DELETE` statement is used to remove records (rows) from a table in a database.

## Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

- `table_name`: The name of the table from which to delete records.
- `WHERE condition`: Specifies the condition for selecting the rows to be deleted.

## Examples

### Delete a Single Row

```sql
DELETE FROM employees
WHERE employee_id = 1;
```

Delete the employee with `employee_id` 1 from the `employees` table.

### Delete Multiple Rows

```sql
DELETE FROM products
WHERE category = 'Obsolete';
```

Delete all products in the 'Obsolete' category from the `products` table.

### Delete All Rows

```sql
DELETE FROM customers;
```

Delete all rows from the `customers` table. Use with caution.

### Use Subquery in DELETE

```sql
DELETE FROM employees
WHERE department_id IN (SELECT department_id FROM departments WHERE department_name = 'Closed');
```

Delete employees belonging to a department that has been marked as 'Closed' using a subquery.

## Notes

- The `WHERE` clause is crucial to prevent unintentional deletion of all rows in a table. Always include a specific condition to target the desired rows.
- Be cautious when using the `DELETE` statement without a `WHERE` clause, as it will remove all rows from the specified table.
- It's good practice to make a backup before performing significant deletions, especially in a production environment.

