# Chapter 9: Transactions and Concurrency

## Transactions

A transaction is a logical unit of work that represents a sequence of database operations that are performed as a single unit of work. The transaction is a fundamental feature of database systems that ensures data consistency and integrity. The SQL standard defines the concept of a transaction, and all modern database management systems support transactions.

Transactions provide several important benefits, including:

- Atomicity: Transactions ensure that all operations are completed successfully or not at all. If a transaction fails, all changes made by the transaction are rolled back to the previous state, ensuring data consistency.
- Consistency: Transactions ensure that the database remains in a consistent state throughout the transaction. Any changes made to the database during a transaction must be consistent with the rules defined by the database schema.
- Isolation: Transactions ensure that each transaction is isolated from other transactions, so that each transaction sees a consistent snapshot of the database.
- Durability: Once a transaction is committed, its changes are persistent and will survive system failures.

To execute a transaction in SQL, you use the BEGIN TRANSACTION, COMMIT, and ROLLBACK statements. The BEGIN TRANSACTION statement marks the beginning of a transaction, and the COMMIT statement marks the end of a successful transaction. The ROLLBACK statement rolls back the transaction to the beginning state in case of a failure.

## Concurrency Control

Concurrency control is the process of managing concurrent access to shared resources. In the context of database systems, concurrency control is used to manage access to the database by multiple users or applications simultaneously. The main goal of concurrency control is to ensure data consistency and integrity in the presence of concurrent access.

Concurrency control techniques can be divided into two categories: pessimistic and optimistic. Pessimistic concurrency control involves locking the resources to prevent concurrent access. Optimistic concurrency control involves allowing concurrent access to resources and detecting conflicts after they occur.

In SQL, transactions are used to ensure consistency and integrity, while concurrency control techniques are used to manage concurrent access. SQL provides several concurrency control mechanisms, including locking, timestamping, and multiversion concurrency control (MVCC).

Locking is a pessimistic concurrency control technique that involves acquiring locks on resources to prevent concurrent access. SQL provides several types of locks, including shared locks and exclusive locks.

Timestamping is an optimistic concurrency control technique that involves assigning a timestamp to each transaction. SQL provides built-in support for timestamping, including the use of the TIMESTAMP data type and the SET TRANSACTION statement.

MVCC is a concurrency control technique that involves maintaining multiple versions of a data item to allow concurrent access. SQL databases that support MVCC use a snapshot isolation technique, where each transaction sees a consistent snapshot of the database.

In summary, transactions and concurrency control are critical components of database management systems. Transactions provide a way to ensure data consistency and integrity, while concurrency control techniques manage concurrent access to shared resources. SQL provides several mechanisms for both transactions and concurrency control, including locking, timestamping, and MVCC.

An example scenario to illustrate how concurrency control can be used to ensure data consistency in a database system:

Suppose a bank has a database with two tables: **`accounts`** and **`transactions`**. The **`accounts`** table has columns **`account_number`**, **`balance`**, and **`customer_name`**. The **`transactions`** table has columns **`transaction_id`**, **`account_number`**, **`transaction_type`**, and **`amount`**.

Suppose two transactions are executed simultaneously:

Transaction 1: Transfer $100 from account A to account B

```sql

BEGIN TRANSACTION;

UPDATE accounts SET balance = balance - 100 WHERE account_number = A;
UPDATE accounts SET balance = balance + 100 WHERE account_number = B;
INSERT INTO transactions (account_number, transaction_type, amount) VALUES (A, 'debit', 100);
INSERT INTO transactions (account_number, transaction_type, amount) VALUES (B, 'credit', 100);

COMMIT;

```

Transaction 2: Deposit $200 into account A

```sql

BEGIN TRANSACTION;

UPDATE accounts SET balance = balance + 200 WHERE account_number = A;
INSERT INTO transactions (account_number, transaction_type, amount) VALUES (A, 'credit', 200);

COMMIT;

```

Without concurrency control, it is possible that the two transactions will interfere with each other and result in an inconsistent database state. For example, if transaction 1 executes the first **`UPDATE`** statement to subtract $100 from account A's balance, but before it commits, transaction 2 executes the **`UPDATE`** statement to add $200 to account A's balance, then the final balance of account A will be incorrect.

To prevent such inconsistencies, a concurrency control mechanism such as locking can be used. For example, the database system can acquire an exclusive lock on account A's row when transaction 1 starts, so that no other transaction can modify the row until transaction 1 is committed or rolled back. Similarly, the database system can acquire an exclusive lock on account B's row when transaction 1 starts, so that no other transaction can modify the row until transaction 1 is committed or rolled back.

Alternatively, a database system that supports MVCC can use snapshot isolation to allow concurrent access while still ensuring data consistency. In this approach, each transaction sees a consistent snapshot of the database at the time it starts, and changes made by other transactions after that time are not visible to the transaction. Thus, in the example scenario, transaction 1 would see the initial balance of account A, and transaction 2 would see the initial balance of account A as well, even if transaction 1 modifies the balance before transaction 2 finishes.

Both locking and MVCC have their pros and cons, and the choice of concurrency control mechanism depends on the specific requirements of the application. The key is to ensure that the database system can handle concurrent access in a way that maintains data consistency and integrity.