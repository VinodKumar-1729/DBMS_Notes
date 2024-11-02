### Transactions

**Definition**:  
A transaction is a logical unit of work that consists of one or more database operations (like insert, update, delete) and is treated as a single, indivisible unit. Transactions ensure data accuracy, completeness, and integrity, particularly in concurrent and multi-user database environments. The primary goal of a transaction is to maintain data consistency.

**Key Points**:
1. **Multi-Step Process**: Transactions often involve multiple steps or operations. Each of these operations is dependent on the successful execution of the others.
2. **Commit and Rollback**: 
   - **Commit**: If all steps in the transaction complete successfully, a `commit` operation makes the changes permanent.
   - **Rollback**: If any step fails, a `rollback` operation reverses all changes to maintain the database's integrity.

**Examples**:
- **Banking**: In a bank transfer, if money is deducted from one account, it must be credited to another. If one part fails, the entire transfer should be canceled.
- **E-commerce**: During an online order, a transaction may involve updating product availability, customer order records, and payment details. Failure in any step requires rolling back all previous steps to ensure data integrity.

---

### ACID Properties

ACID is a set of properties that guarantee reliable transaction processing and maintain the database's stability.

#### 1. Atomicity
- **Definition**: Atomicity ensures that a transaction is all-or-nothing: either every operation within the transaction succeeds, or none of them do.
- **Key Aspects**:
  - **Indivisibility**: A transaction cannot be divided; it either completes entirely or fails entirely.
  - **Error Handling**: In case of failure, all operations are rolled back, restoring the database to its initial state.
- **Example**: In a fund transfer, if debit occurs but credit doesn’t, the entire transaction should fail to avoid discrepancies.

#### 2. Consistency
- **Definition**: Consistency ensures that a transaction brings the database from one valid state to another, maintaining all defined rules (like foreign keys, constraints, triggers).
- **Key Aspects**:
  - **Integrity Constraints**: Enforces predefined rules (e.g., foreign keys, primary keys) to keep the data valid.
  - **Validation**: Ensures that before and after a transaction, the database state is consistent.
- **Example**: When updating a user’s email, consistency checks ensure the new email format is valid and does not duplicate existing records.

#### 3. Isolation
- **Definition**: Isolation ensures that transactions do not interfere with each other, maintaining consistency even when multiple transactions occur simultaneously.
- **Key Aspects**:
  - **Isolation Levels**: There are four isolation levels in SQL (Read Uncommitted, Read Committed, Repeatable Read, Serializable) that balance consistency and performance.
  - **Concurrency Control**: Techniques like locking and timestamping prevent conflicts.
- **Example**: In a ticket booking system, isolation ensures two users cannot book the same seat simultaneously.

  **Isolation Levels Explained**:
  - **Read Uncommitted**: Lowest level, allowing dirty reads (one transaction sees uncommitted changes of another).
  - **Read Committed**: Prevents dirty reads by only allowing access to committed data.
  - **Repeatable Read**: Ensures repeated reads in a transaction return the same result, preventing non-repeatable (phantom) reads.
  - **Serializable**: Highest level, where transactions are executed as if sequentially, preventing all inconsistencies.

#### 4. Durability
- **Definition**: Durability guarantees that once a transaction is committed, its changes are permanent, even if the system crashes.
- **Key Aspects**:
  - **Persistence**: Data is safely stored, usually in non-volatile memory or disk.
  - **Backup and Recovery**: Techniques like write-ahead logging (WAL) or journaling ensure data can be restored after a crash.
- **Example**: In banking, once a deposit is committed, the account balance update remains intact even if the server fails.

---

### Advanced Concepts & Exam-Relevant Points

1. **Two-Phase Commit (2PC)**:
   - **Definition**: A protocol to ensure atomicity across distributed systems by coordinating commits across multiple databases.
   - **Steps**:
     1. **Prepare Phase**: All participants prepare to commit and acknowledge readiness.
     2. **Commit Phase**: If all are ready, the transaction is committed; otherwise, it’s rolled back.

2. **Concurrency Control Techniques**:
   - **Locking Mechanisms**: Shared locks for read operations, exclusive locks for write operations.
   - **Timestamp Ordering**: Assigns timestamps to ensure transaction order.
   - **Optimistic Concurrency Control**: Assumes minimal conflict, checks for issues only at the end of a transaction.

3. **Phantom Read**:
   - **Definition**: A phenomenon where new rows added by another transaction affect the results of a transaction reading multiple rows.
   - **Prevention**: Serializable isolation level prevents phantom reads.

4. **Write-Ahead Logging (WAL)**:
   - **Definition**: A logging technique where changes are written to a log before being applied to the database, enhancing durability and crash recovery.
   - **Benefit**: Allows for database restoration to the most recent committed state post-crash.

---
