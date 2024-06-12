# Chapter 4: Creating and Modifying Database Objects

## Creating Tables

Creating tables is one of the fundamental tasks in SQL. A table is a collection of related data that is organized into rows and columns. In order to create a table in SQL, you use the **`CREATE TABLE`** statement. Here's an example:

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  username VARCHAR(50),
  email VARCHAR(100)
);
```

In this example, we're creating a table called **`users`**. The table has three columns: **`id`**, **`username`**, and **`email`**. The **`id`** column is the primary key, which means it uniquely identifies each row in the table. The **`username`** and **`email`** columns are both **`VARCHAR`** data types, which means they can store up to 50 and 100 characters respectively.

## Altering Tables

Sometimes you may need to modify an existing table, either to add new columns or to change the structure of an existing column. To do this, you use the **`ALTER TABLE`** statement. Here are some examples:

### **Adding a Column**

```sql
ALTER TABLE users ADD COLUMN full_name VARCHAR(100);
```

In this example, we're adding a new column called **`full_name`** to the **`users`** table.

### **Modifying a Column**

```
sqlCopy code
ALTER TABLE users MODIFY COLUMN email VARCHAR(255);

```

In this example, we're modifying the **`email`** column to increase the maximum length from 100 to 255 characters.

### **Renaming a Column**

```sql
ALTER TABLE users RENAME COLUMN username TO user_name;
```

In this example, we're renaming the **`username`** column to **`user_name`**.

## Dropping Tables

If you no longer need a table, you can use the **`DROP TABLE`** statement to delete it from the database. Here's an example:

```sql
DROP TABLE users;
```

In this example, we're dropping the **`users`** table from the database. Be careful when using this statement, as it will permanently delete all data in the table. Make sure you have a backup of your data before using **`DROP TABLE`**.