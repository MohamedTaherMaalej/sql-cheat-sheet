# SQL Transactions

A transaction in SQL is a sequence of one or more SQL statements that are executed as a single unit of work. Transactions are used to ensure the consistency and integrity of a database.

## Basic Transaction Structure

```sql
-- Start a transaction
BEGIN TRANSACTION;

-- SQL statements go here

-- Commit the transaction
COMMIT;

-- Rollback the transaction
ROLLBACK;
```

- `BEGIN TRANSACTION`: Marks the beginning of a transaction.
- `COMMIT`: Saves the changes made during the transaction.
- `ROLLBACK`: Undoes the changes made during the transaction and restores the database to its state before the transaction started.

## Example of a Simple Transaction

```sql
BEGIN TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_id = 123;
INSERT INTO transactions (account_id, amount, transaction_type) VALUES (123, 100, 'Withdrawal');

COMMIT;
```

In this example, a transaction is used to update the balance in the `accounts` table and record a withdrawal transaction in the `transactions` table. If any part of the transaction fails, the changes are rolled back.

## Managing Transactions in Stored Procedures

Transactions are commonly used within stored procedures to ensure atomicity and consistency.

```sql
CREATE PROCEDURE TransferFunds(@fromAccount INT, @toAccount INT, @amount DECIMAL)
AS
BEGIN
    BEGIN TRANSACTION;

    UPDATE accounts SET balance = balance - @amount WHERE account_id = @fromAccount;
    UPDATE accounts SET balance = balance + @amount WHERE account_id = @toAccount;

    IF @@ERROR <> 0
        ROLLBACK;
    ELSE
        COMMIT;
END;
```

This stored procedure transfers funds from one account to another within a transaction. If any part of the transaction fails, it is rolled back, ensuring the integrity of the data.

## Isolation Levels

SQL provides different isolation levels for transactions, determining how transactions interact with each other. Common isolation levels include READ UNCOMMITTED, READ COMMITTED, REPEATABLE READ, and SERIALIZABLE.

```sql
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;
```

This statement sets the isolation level for the current session. The choice of isolation level depends on the specific requirements of the application.

## Savepoints

Savepoints allow you to create points within a transaction to which you can later roll back.

```sql
SAVE TRANSACTION Savepoint1;

-- SQL statements

ROLLBACK TO Savepoint1;
```

Savepoints are useful when you want to undo part of a transaction without rolling back the entire transaction.

## Notes

- Transactions ensure that a series of SQL statements are executed as a single, atomic unit.
- Proper error handling and rollback mechanisms are essential to maintain data consistency in case of failures.
- The choice of isolation level depends on the specific needs of the application and the desired trade-offs between consistency and performance.

