 Creating a Database in SQL

In SQL, a database is a container that holds one or more tables and other database objects. Here is a guide on how to create a database.

## Syntax

```sql
CREATE DATABASE database_name;
```

- `database_name`: The name you want to give to your database.

## Example

```sql
CREATE DATABASE CompanyDB;
```

This example creates a database named `CompanyDB`.

## Adding Parameters

You can add parameters such as character set and collation during the creation of the database.

```sql
CREATE DATABASE CompanyDB
    CHARACTER SET utf8
    COLLATE utf8_general_ci;
```

This example specifies the character set as `utf8` and the collation as `utf8_general_ci` for the `CompanyDB` database.

## Notes

- Make sure to choose an appropriate character set and collation based on your application requirements.
- Ensure that you have the necessary privileges to create a database.
- Be cautious when creating databases in a production environment to avoid overwriting existing databases.

## Switching to a Database

After creating a database, you can switch to it using the `USE` statement.

```sql
USE CompanyDB;
```

This statement instructs the database management system to use the `CompanyDB` database for subsequent SQL queries.

## Dropping a Database

To delete a database, you can use the `DROP DATABASE` statement.

```sql
DROP DATABASE CompanyDB;
```

This statement permanently removes the `CompanyDB` database and all its associated tables and data. Exercise caution when using this statement.

## Example with User and Permissions

You can create a database and assign a user with specific permissions to it.

```sql
CREATE DATABASE CompanyDB;

CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON CompanyDB.* TO 'app_user'@'localhost';
```

This example creates a database, a user named `app_user` with the password 'password', and grants all privileges on the `CompanyDB` database to this user.

