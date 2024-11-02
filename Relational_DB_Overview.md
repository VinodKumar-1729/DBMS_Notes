### Definition
- **Relational Database Management System (RDBMS)**: A database management system that organizes data into related tables, where each table represents a specific entity or relationship. Data is stored in rows and columns, enabling structured storage, easy access, management, and modification.

### Key Features

1. **Tables (Relations)**:
   - **Structure**: Tables are the fundamental unit of storage in RDBMS. Each table consists of:
     - **Rows** (or records, tuples): Each row contains data about a single item or entity.
     - **Columns** (or attributes): Each column represents a specific attribute or characteristic of the data in rows.
   - **Keys**:
     - **Primary Key**: Uniquely identifies each record in a table (e.g., `EmployeeID` in an Employee table).
     - **Foreign Key**: Establishes relationships between tables by referencing the primary key in another table (e.g., `DepartmentID` in an Employee table referring to the Department table).
     - **Composite Key**: A primary key that consists of multiple columns.
   - **Candidate Key**: Potential choices for a primary key, with unique values and no NULLs.
   
2. **SQL (Structured Query Language)**:
   - **Standard Language**: SQL is the language used to interact with and manage RDBMS. Key SQL operations include:
     - **Data Definition Language (DDL)**: Defines database schema (e.g., `CREATE`, `ALTER`, `DROP`).
     - **Data Manipulation Language (DML)**: Modifies data within tables (e.g., `INSERT`, `UPDATE`, `DELETE`).
     - **Data Query Language (DQL)**: Primarily `SELECT` statements used for retrieving data.
     - **Data Control Language (DCL)**: Controls access to data (e.g., `GRANT`, `REVOKE`).
     - **Transaction Control Language (TCL)**: Manages transactions (e.g., `COMMIT`, `ROLLBACK`, `SAVEPOINT`).
   - **Exam Note**: Knowing SQL commands, syntax, and complex query handling (such as nested queries and joins) can give you an edge.

3. **Data Integrity**:
   - **Constraints**: Used to enforce rules on data stored in tables, ensuring reliability and accuracy:
     - **NOT NULL**: Ensures that a column cannot have a NULL value.
     - **UNIQUE**: Ensures all values in a column are unique.
     - **CHECK**: Restricts values in a column based on a condition.
     - **DEFAULT**: Assigns a default value if no value is provided.
   - **Referential Integrity**: Enforced by foreign keys to maintain consistency in relationships between tables.

4. **Normalization**:
   - **Process**: Organizes data to minimize redundancy and dependency. Key normal forms include:
     - **1NF (First Normal Form)**: Ensures each column contains atomic, indivisible values.
     - **2NF (Second Normal Form)**: Ensures all non-key columns are fully dependent on the primary key.
     - **3NF (Third Normal Form)**: Ensures no transitive dependency exists in the table.
     - **Boyce-Codd Normal Form (BCNF)**: A stricter version of 3NF where every determinant is a candidate key.
   - **Exam Tip**: Normalization concepts are common in exams for RDBMS design-related questions.

5. **Transactions**:
   - **ACID Properties**:
     - **Atomicity**: Ensures each transaction is "all or nothing."
     - **Consistency**: Ensures database remains in a valid state after transactions.
     - **Isolation**: Ensures transactions don’t interfere with each other.
     - **Durability**: Ensures completed transactions are saved permanently.
   - **Transaction States**: Active, partially committed, committed, failed, and aborted.
   - **Concurrency Control**: Mechanisms like locking and time-stamping to handle multiple transactions simultaneously.

### Additional Exam-Relevant Concepts

1. **Indexing**:
   - **Purpose**: Speeds up data retrieval but can slow down data insertion or modification.
   - **Types**:
     - **Primary Index**: Created automatically with the primary key.
     - **Secondary Index**: Created explicitly to improve query performance.
     - **Unique Index**: Ensures all values in the indexed column are unique.

2. **Joins**:
   - **Types**:
     - **INNER JOIN**: Returns records with matching values in both tables.
     - **LEFT JOIN (LEFT OUTER JOIN)**: Returns all records from the left table and matching records from the right.
     - **RIGHT JOIN (RIGHT OUTER JOIN)**: Returns all records from the right table and matching records from the left.
     - **FULL JOIN (FULL OUTER JOIN)**: Returns all records with matching values in either table.
   - **Exam Tip**: Practice query questions that require multiple join types for efficient query construction.

3. **Views**:
   - **Virtual Table**: A saved SQL query that presents data from one or more tables without storing it physically.
   - **Usage**: Useful for data security, hiding specific data, or simplifying complex queries.

4. **Stored Procedures and Triggers**:
   - **Stored Procedure**: Predefined SQL code that can be executed repeatedly.
   - **Trigger**: Executes automatically in response to certain events on a table, like `INSERT`, `UPDATE`, or `DELETE`.

### Popular RDBMS Examples

- **MySQL**: Known for its open-source nature and large-scale web applications.
- **PostgreSQL**: Known for its advanced features, such as support for complex queries and full-text search.
- **Oracle**: Popular in enterprise settings, with advanced security and large data handling.
- **Microsoft SQL Server**: Integrates well with other Microsoft products, offering robust data management solutions.

### Unique Points for Competitive Exams

1. **Data Independence**: RDBMS achieves both **physical independence** (changes in physical storage do not affect application layers) and **logical independence** (modifications in the schema do not affect application programs).

2. **Schema and Instance**:
   - **Schema**: Blueprint or structure of a database, defining tables, views, indexes, etc.
   - **Instance**: Actual data stored in the database at a particular moment.

3. **E-R Model and Mapping**:
   - **Entity-Relationship (ER) Model**: Conceptual framework used to define the structure of the database.
   - **Mapping**: Process of converting ER models to relational schemas.
