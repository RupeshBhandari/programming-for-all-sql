# Chapter 3: SQL Data Types

## Understanding Data Types

Data types are an important aspect of SQL, as they determine what type of data can be stored in each column of a table. Different data types are designed to store different kinds of data, such as numbers, dates, strings, and more. Understanding data types is crucial for designing tables and queries that work effectively with the data in the database.

### **Common SQL Data Types**

Some of the most common data types in SQL include:

- **`INTEGER`**: Used for whole numbers, such as 1, 2, 3, etc.
- **`FLOAT`** or **`REAL`**: Used for decimal numbers, such as 1.23, 4.56, etc.
- **`CHAR`** or **`VARCHAR`**: Used for character strings, such as "hello", "world", etc.
- **`DATE`**: Used for dates, such as "2022-03-14".

There are many other data types available in SQL, depending on the specific database system being used. In addition, some databases may have variations on these basic data types, such as **`TEXT`** instead of **`VARCHAR`**, or **`TIMESTAMP`** instead of **`DATE`**.

## 

## Creating Tables with the Correct Data Types

When creating a new table in SQL, it's important to choose the correct data types for each column to ensure that the data is stored and manipulated correctly. For example, if we were creating a table to store customer information, we might use the following SQL code:

```sql
CREATE TABLE customers (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(255),
    phone VARCHAR(20)
);
```

In this example, we've created a table called **`customers`** with four columns: **`id`**, **`name`**, **`email`**, and **`phone`**. We've specified that **`id`** is the primary key for the table, and we've used **`VARCHAR`** data types for the **`name`**, **`email`**, and **`phone`** columns. The length of the **`name`** column is limited to 50 characters, while the length of the **`email`** column is limited to 255 characters. The **`phone`** column is limited to 20 characters, which should be enough to store most phone numbers.

It's important to choose appropriate data types for each column in the table to ensure that the data is stored accurately and efficiently. For example, using a **`FLOAT`** data type instead of an **`INTEGER`** data type to store whole numbers would result in wasted storage space and slower query performance. Similarly, using a **`VARCHAR`** data type with a length that is too short to store a particular value would result in truncated data and potential data loss.

By choosing the correct data types for each column, we can ensure that our SQL queries work efficiently and accurately with the data in our database.