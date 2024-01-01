# SQL Subqueries

A subquery is a query nested inside another query, allowing you to retrieve data that will be used by the main query. Subqueries can be used in various parts of a SQL statement, such as the SELECT, FROM, WHERE, and HAVING clauses.

## Subqueries in SELECT Statement

You can use subqueries in the SELECT clause to retrieve a single value or a set of values that will be displayed for each row in the result set.

```sql
SELECT product_name, (SELECT AVG(price) FROM products) AS avg_price
FROM products;
```

This query retrieves the product name and the average price of all products. The subquery is used in the SELECT clause to calculate the average price, and the result is displayed for each product.

## Subqueries in WHERE Clause

Subqueries in the WHERE clause are used to filter the results based on the outcome of the subquery.

```sql
SELECT customer_name
FROM customers
WHERE customer_id IN (SELECT customer_id FROM orders WHERE order_date >= '2023-01-01');
```

This query retrieves the names of customers who have placed orders on or after January 1, 2023. The subquery in the WHERE clause helps filter customers based on their order history.

## Subqueries in FROM Clause

You can use subqueries in the FROM clause to create a derived table or virtual table that is used in the main query.

```sql
SELECT department_name, total_employees
FROM (SELECT department_id, department_name, COUNT(*) AS total_employees FROM employees GROUP BY department_id) AS department_totals
WHERE total_employees > 10;
```

This query retrieves the department name and the total number of employees for departments with more than 10 employees. The subquery in the FROM clause is used to create a derived table containing department totals.

## Correlated Subqueries

A correlated subquery is a subquery that depends on the values from the outer query. It is executed once for each row processed by the outer query.

```sql
SELECT employee_id, first_name, salary,
  (SELECT AVG(salary) FROM employees WHERE department_id = e.department_id) AS avg_department_salary
FROM employees e;
```

This query retrieves the employee ID, first name, salary, and the average salary for the employee's department. The subquery is correlated to the outer query by referencing the department_id from the outer query.

## Subqueries with EXISTS

The EXISTS keyword is used in a subquery to check for the existence of rows that meet certain criteria.

```sql
SELECT product_name
FROM products
WHERE EXISTS (SELECT 1 FROM order_details WHERE order_details.product_id = products.product_id);
```

This query retrieves the names of products that have at least one order. The subquery with EXISTS is used to check for the existence of corresponding rows in the order_details table.

## Notes

- Subqueries can make your SQL queries more expressive and flexible, but they may impact performance. Use them judiciously, and consider optimizing your queries if performance is a concern.
- Understand the relationships between tables and the logic of your subqueries to ensure accurate and efficient results.

