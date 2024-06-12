
# Appendix A: SQL Syntax Reference

In this appendix, you'll find a handy reference guide for SQL syntax, covering the most commonly used statements and constructs in SQL queries.

## Data Definition Language (DDL)

### CREATE TABLE
```sql
CREATE TABLE table_name (
    column1 datatype,
    column2 datatype,
    ...
);
```

### ALTER TABLE
```sql
ALTER TABLE table_name
ADD column_name datatype;
```

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

```sql
ALTER TABLE table_name
MODIFY column_name datatype;
```

### DROP TABLE
```sql
DROP TABLE table_name;
```

## Data Manipulation Language (DML)

### INSERT INTO
```sql
INSERT INTO table_name (column1, column2, ...)
VALUES (value1, value2, ...);
```

### UPDATE
```sql
UPDATE table_name
SET column1 = value1, column2 = value2, ...
WHERE condition;
```

### DELETE FROM
```sql
DELETE FROM table_name
WHERE condition;
```

## Data Query Language (DQL)

### SELECT
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```

### DISTINCT
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

### ORDER BY
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1 ASC|DESC, column2 ASC|DESC, ...;
```

### GROUP BY
```sql
SELECT column1, COUNT(*)
FROM table_name
GROUP BY column1;
```

## Data Control Language (DCL)

### GRANT
```sql
GRANT privilege_name
ON object_name
TO {user_name | PUBLIC | role_name};
```

### REVOKE
```sql
REVOKE privilege_name
ON object_name
FROM {user_name | PUBLIC | role_name};
```

## Transaction Control Language (TCL)

### COMMIT
```sql
COMMIT;
```

### ROLLBACK
```sql
ROLLBACK;
```

### SAVEPOINT
```sql
SAVEPOINT savepoint_name;
```

### RELEASE SAVEPOINT
```sql
RELEASE SAVEPOINT savepoint_name;
```
