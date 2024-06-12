# Chapter 5: Inserting, Updating, and Deleting Data

## Inserting Data into a Table

To insert data into a table in SQL, you use the **`INSERT INTO`** statement. Here's an example:

```sql
INSERT INTO users (id, username, email)
VALUES (1, 'john_doe', 'john_doe@example.com')
```

In this example, we're inserting a new row into the **`users`** table. The values we're inserting are **`1`** for the **`id`** column, **`'john_doe'`** for the **`username`** column, and **`'john_doe@example.com'`** for the **`email`** column.

You can also insert multiple rows at once:

```sql
INSERT INTO users (id, username, email)
VALUES (2, 'jane_doe', 'jane_doe@example.com'),
       (3, 'bob_smith', 'bob_smith@example.com');
```

In this example, we're inserting two new rows into the **`users`** table.

## Updating Data in a Table

To update data in a table in SQL, you use the **`UPDATE`** statement. Here's an example:

```sql
UPDATE users
SET email = 'new_email@example.com'
WHERE id = 1;
```

In this example, we're updating the **`email`** column for the row with **`id`** equal to **`1`**. We're setting the new value for **`email`** to **`'new_email@example.com'`**.

You can update multiple columns at once:

```sql
UPDATE users
SET email = 'new_email@example.com',
    username = 'new_username'
WHERE id = 1
```

In this example, we're updating both the **`email`** and **`username`** columns for the row with **`id`** equal to **`1`**.

## Deleting Data from a Table

To delete data from a table in SQL, you use the **`DELETE FROM`** statement. Here's an example:

```sql
DELETE FROM users
WHERE id = 1;
```

In this example, we're deleting the row with **`id`** equal to **`1`** from the **`users`** table.

You can also delete all rows from a table:

```sql
DELETE FROM users;
```

In this example, we're deleting all rows from the **`users`** table. Be careful when using this statement, as it will permanently delete all data in the table. Make sure you have a backup of your data before using **`DELETE FROM`**.