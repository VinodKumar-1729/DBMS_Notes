**Relational Database Model and Key Concepts**

---

### Introduction to Relational Database Model
The relational database model, developed by Dr. E.F. Codd, presents data in a tabular form using the concept of relations (two-dimensional tables). Its primary features include:

#### Key Features:
1. **Simplicity:** Simplifies implementation and operations on data.
2. **Linking:** Interlinks tables using primary and foreign keys.
3. **Normalization:** Designs efficient, non-redundant data models using normalization.
4. **Data Processing:** Manipulates relations through Relational Algebra and Relational Calculus.

---

### Key Elements of a Relational Database:

1. **Relations (Tables):** Basic structure for storing data, organized into rows and columns.
2. **Rows (Tuples):** Represent individual records in a table.
3. **Columns (Attributes):** Represent properties or attributes of the data.
4. **Primary Key:** Unique identifier for rows in a table.

#### Example:
```
STUDENT (StudNo, Sname, Special)
ENROLLMENT (StudNo, Subcode, Marks)
SUBJECT (Subcode, Subname, MaxMarks, FacCode)
FACULTY (FacCode, Fname, Dept)
```

---

### Terminologies:

1. **Relational Schema:**
   - Defines the structure of a relation.
   - Example: `STUDENT(STUD_NO, STUD_NAME, STUD_PHONE, STUD_STATE, STUD_COUNTRY, STUD_AGE)`

2. **Relational Instance:**
   - Set of values in a relation at a specific instance of time.

3. **Attribute:**
   - Properties of a relation (e.g., `STUD_NO`, `STUD_NAME`).

4. **Domain:**
   - The range of possible values for an attribute.
   - Example: The domain of `STUD_AGE` is 18-40.

5. **Tuple:**
   - Each row in a relation.

6. **NULL Values:**
   - Represent unknown, missing, or undefined values. Each NULL is considered unique.

#### Example Tables:
**STUDENT TABLE**
| STUD_NO | STUD_NAME | STUD_PHONE | STUD_STATE | STUD_COUNTRY | STUD_AGE |
|---------|-----------|------------|------------|--------------|----------|
| 1       | RAM       | 9716271721 | Haryana    | India        | 20       |
| 2       | RAM       | 9898291281 | Punjab     | India        | 19       |
| 3       | SUJIT     | 7898291981 | Rajasthan  | India        | 18       |
| 4       | SURESH    | 9985286317 | Punjab     | India        | 21       |

**STUDENT COURSE TABLE**
| STUD_NO | COURSE_NO | COURSE_NAME       |
|---------|-----------|-------------------|
| 1       | C1        | DBMS             |
| 2       | C2        | Computer Networks|
| 1       | C2        | Computer Networks|

---

### RDBMS Vendors:
1. **Oracle:** Robust, scalable, reliable; widely used in enterprises.
2. **Microsoft SQL Server:** Includes features like data mining, BI, and reporting.
3. **IBM DB2:** Enterprise-grade with disaster recovery and scalability features.
4. **MySQL:** Open-source, cost-effective, flexible.
5. **PostgreSQL:** Open-source, supports complex transactions.
6. **SAP HANA:** In-memory RDBMS for high-performance analytics.

---

### Relational Algebra:
A procedural language comprising operators for manipulating relations. These operators form the foundation for SQL and other query languages.

#### Operators in Relational Algebra:
1. **UNION (∪):** Combines values from two relations, avoiding duplicates.
   - Syntax: `A UNION B`
   - Example:
     ```
     A = {clerk, manager, salesman}
     B = {president, clerk, manager}
     A UNION B = {clerk, manager, salesman, president}
     ```

2. **INTERSECTION (∩):** Displays common elements in two relations.
   - Syntax: `A INTERSECT B`
   - Example:
     ```
     A = {clerk, manager, salesman}
     B = {president, clerk, manager}
     A INTERSECT B = {clerk, manager}
     ```

3. **DIFFERENCE (−):** Displays elements in one relation but not in another.
   - Syntax: `A MINUS B`
   - Example:
     ```
     A = {clerk, manager, salesman}
     B = {president, clerk, manager}
     A MINUS B = {salesman}
     ```

4. **CARTESIAN PRODUCT (×):** Combines all pairwise combinations of tuples from two relations.
   - Syntax: `A TIMES B`
   - Example:
     ```
     A = {clerk, manager}
     B = {president, clerk}
     A X B = {(clerk, president), (clerk, clerk), (manager, president), (manager, clerk)}
     ```

5. **SELECTION (σ):** Filters tuples based on a condition.
   - Syntax: `σcondition(relation)`

6. **PROJECTION (π):** Selects specific columns from a relation.
   - Syntax: `π(col1, col2, ...)Relation`

7. **JOIN (⋈):** Combines two relations based on a condition. Includes:
   - Inner Join
   - Outer Join
   - Left Outer Join
   - Right Outer Join

8. **DIVISION (÷):** Divides tuples from one relation by another.
   - Syntax: `A DIVIDE B`

9. **RENAME (ρ):** Renames relations or attributes.
   - Syntax: `ρ(OLD_RELATION, NEW_RELATION)`

---

### Features of the Relational Model:

1. **Tables/Relations:** Fundamental data structures representing related data.
2. **Primary Keys:** Unique row identifiers.
3. **Foreign Keys:** Maintain referential integrity between tables.
4. **Normalization:** Ensures data consistency and reduces redundancy.
5. **Codd’s Rules:** A set of 12 rules defining true RDBMS characteristics.
6. **ACID Properties:** Ensure reliable transaction processing:
   - **Atomicity:** Transactions are all-or-nothing.
   - **Consistency:** Maintain database integrity.
   - **Isolation:** Transactions do not interfere with each other.
   - **Durability:** Data remains intact post-transaction.

---

### Advantages of Relational Algebra
Relational Algebra is a formal language used to specify queries to retrieve data from a relational database. It has several advantages that make it a popular choice for managing and manipulating data:

1. **Simplicity:**
   - Relational Algebra provides a simple and easy-to-understand set of operators for data manipulation.
   - Based on mathematical concepts, it is intuitive and straightforward for users familiar with mathematics.

2. **Formality:**
   - A formal and standardized way of expressing queries ensures correctness and consistency.
   - Facilitates easier debugging and verification of queries.

3. **Abstraction:**
   - Provides a high-level abstraction of the underlying database structure.
   - Focuses on the logical structure rather than physical storage details, aiding work with complex databases.

4. **Portability:**
   - Independent of any specific database management system.
   - Queries can be easily transferred across systems, ensuring flexibility and vendor independence.

5. **Efficiency:**
   - Optimized for performance, allowing queries to execute quickly with minimal resources.
   - Especially beneficial for large and complex databases.

6. **Extensibility:**
   - A flexible framework that can be extended with custom operators and functions.
   - Developers can adapt it to meet specific application needs.

### Disadvantages of Relational Algebra
While Relational Algebra has many advantages, it also has limitations:

1. **Complexity:**
   - The mathematical basis and syntax can be challenging for non-experts.
   - Requires significant training and experience for effective use.

2. **Limited Expressiveness:**
   - The set of operators is limited, making some queries difficult to express directly.
   - Complex queries may require advanced techniques like nested subqueries or joins.

3. **Lack of Flexibility:**
   - Designed specifically for relational databases, limiting its applicability to other data storage systems like NoSQL or hierarchical databases.

4. **Performance Limitations:**
   - Performance can degrade with very large datasets or highly complex queries.
   - Resource-intensive operations may become bottlenecks in some cases.

5. **Limited Data Types:**
   - Primarily supports simple data types like integers, strings, and dates.
   - Handling multimedia, spatial data, or complex types can be challenging.

6. **Integration Challenges:**
   - Often used alongside other programming languages and tools.
   - Requires additional effort for seamless integration with other systems.

### Codd’s Twelve Rules of Relational Database
E.F. Codd proposed 13 rules (known as Codd’s 12 rules) to evaluate the quality of a relational database management system (RDBMS). These rules ensure adherence to the relational model:

1. **Rule 0: Foundation Rule**
   - A system must manage databases entirely through relational capabilities to be considered an RDBMS.

2. **Rule 1: Information Rule**
   - All data is stored as values in tables (relations).

3. **Rule 2: Guaranteed Access Rule**
   - Each data element is accessible by table name, primary key, and attribute name.

4. **Rule 3: Systematic Treatment of NULL Values**
   - NULL values represent missing, unknown, or inapplicable data and must be handled systematically.

5. **Rule 4: Active Online Catalog**
   - The database structure must be stored in an online catalog accessible to authorized users via queries.

6. **Rule 5: Comprehensive Data Sub-language Rule**
   - The database must support a language for definition, manipulation, and transaction management.

7. **Rule 6: View Updating Rule**
   - Views must be updatable automatically by the system without manual intervention.

8. **Rule 7: High-level Insert, Update, and Delete Rule**
   - Must support operations like insert, update, and delete, along with set operations like union, intersection, and difference.

9. **Rule 8: Physical Data Independence**
   - Changes in physical storage should not require application-level modifications.

10. **Rule 9: Logical Data Independence**
    - Changes in the logical schema (e.g., merging tables) should not impact applications accessing the database.

11. **Rule 10: Integrity Independence**
    - Integrity constraints should be definable and modifiable at the database level without affecting applications.

12. **Rule 11: Distribution Independence**
    - Data distribution across various locations should remain invisible to users.

13. **Rule 12: Non-Subversion Rule**
    - Low-level data access should not bypass integrity constraints.

### Conclusion
Relational Algebra is a robust and formal language for relational database management, offering simplicity, abstraction, and portability. Despite its limitations, it remains fundamental for query formulation and database design. Codd’s rules provide a benchmark for evaluating RDBMS compliance with relational principles, ensuring consistency and reliability in database systems.

**GFG Link :** https://www.geeksforgeeks.org/introduction-of-relational-model-and-codd-rules-in-dbms/?ref=lbp
