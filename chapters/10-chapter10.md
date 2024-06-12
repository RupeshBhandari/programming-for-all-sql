# Chapter 10: Advanced SQL Concepts

## Subqueries

A subquery is a SQL statement that is nested inside another SQL statement. The subquery is executed first, and its results are used by the outer query to perform further processing. Subqueries can be used to simplify complex queries, to perform calculations based on intermediate results, and to retrieve data that cannot be retrieved with a single query.

There are two types of subqueries: correlated and non-correlated. In a non-correlated subquery, the subquery is executed once, and its results are used by the outer query. In a correlated subquery, the subquery is executed once for each row of the outer query. Correlated subqueries are less efficient than non-correlated subqueries, but they can be useful in certain situations.

Here is an example of a non-correlated subquery:

```sql

SELECT customer_name, balance
FROM accounts
WHERE balance > (SELECT AVG(balance) FROM accounts);

```

This query retrieves the names and balances of all customers whose balances are greater than the average balance of all customers.

## Views

A view is a virtual table that is based on the result of a SQL query. Views can be used to simplify complex queries, to restrict access to certain data, and to provide a consistent view of the data to multiple users.

A view is defined using the **`CREATE VIEW`** statement, and it can be queried just like a regular table. Views can also be updated, inserted into, and deleted from, depending on the underlying tables and the view's definition.

Here is an example of a view:

```sql

CREATE VIEW customer_summary AS
SELECT customer_name, SUM(balance) AS total_balance
FROM accounts
GROUP BY customer_name;
```

This view summarizes the balances of all customers by adding up the balances of all their accounts. The view can be queried like this:

```sql
SELECT * FROM customer_summary;
```

## Triggers

A trigger is a special type of stored procedure that is automatically executed in response to certain events, such as an insert, update, or delete operation on a table. Triggers can be used to enforce complex business rules, to maintain data integrity, and to automate tasks.

A trigger is defined using the **`CREATE TRIGGER`** statement, and it consists of a trigger event, a trigger condition, and a trigger action. The trigger event specifies the type of event that triggers the execution of the trigger. The trigger condition specifies the condition that must be true for the trigger to execute. The trigger action specifies the code that is executed when the trigger is triggered.

Here is an example of a trigger:

```sql
CREATE TRIGGER update_balance
AFTER INSERT OR UPDATE OR DELETE
ON accounts
FOR EACH ROW
BEGIN
  UPDATE customers
  SET balance = (SELECT SUM(balance) FROM accounts WHERE customer_id = NEW.customer_id)
  WHERE customer_id = NEW.customer_id;
END;
```

This trigger updates the balance of a customer whenever a new account is inserted, an existing account is updated, or an account is deleted. The trigger uses the **`NEW`** and **`OLD`** variables to access the new and old values of the affected rows, and it updates the **`balance`** column of the **`customers`** table based on the new balances of the accounts.