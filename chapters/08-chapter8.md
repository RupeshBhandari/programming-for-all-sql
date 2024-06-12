# Chapter 8: Stored Procedures and Functions

## Creating and Using Stored Procedures

Stored procedures are a collection of SQL statements that are saved in the database and can be called by name. Stored procedures can be used to simplify complex operations and improve database performance. Here's an example of how to create a stored procedure:

```sql
CREATE PROCEDURE sp_get_users_by_age (IN age INT)
BEGIN
    SELECT * FROM users WHERE age = age;
EN
```

In this example, we are creating a stored procedure called **`sp_get_users_by_age`** that takes an input parameter **`age`**. The stored procedure then performs a SELECT query on the **`users`** table, returning all rows where the **`age`** column matches the input parameter.

To execute the stored procedure, we can simply call it by name:

```sql
CALL sp_get_users_by_age(25);
```

This will return all users with an age of 25.

## Creating and Using User-Defined Functions

A user-defined function is similar to a stored procedure, but instead of executing a collection of statements, it returns a single value. User-defined functions can be used to perform calculations or manipulate data. Here's an example of how to create a user-defined function:

```sql
CREATE FUNCTION get_total_sales_by_user (IN user_id INT)
RETURNS INT
BEGIN
    DECLARE total_sales INT;
    SELECT SUM(sales_amount) INTO total_sales FROM sales WHERE user_id = user_id;
    RETURN total_sales;
END
```

In this example, we are creating a user-defined function called **`get_total_sales_by_user`** that takes an input parameter **`user_id`**. The function then performs a SELECT query on the **`sales`** table, calculating the sum of all sales amounts for the specified user. The result is stored in a local variable **`total_sales`**, which is then returned by the function.

To use the function, we can call it in a SELECT statement like this:

```sql
SELECT user_id, get_total_sales_by_user(user_id) as total_sales FROM sales GROUP BY user_id;
```

This will return a list of user IDs and their corresponding total sales amounts.