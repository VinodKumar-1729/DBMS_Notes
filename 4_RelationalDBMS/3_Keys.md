**Database Keys**

### **Introduction**
Keys are fundamental components of the relational database model. They uniquely identify tuples (rows) in a table and establish relationships among columns and tables in a relational database. Proper utilization of keys ensures data integrity and efficient database design.

### **Types of Database Keys**
1. **Candidate Key**
   - A minimal set of attributes that can uniquely identify a tuple.
   - Features:
     - A minimal super key.
     - Contains no redundant attributes.
     - Must have unique values.
     - Can contain NULL values (except in SQL Server, where a unique constraint allows only one NULL).
     - Every table must have at least one candidate key.
     - A table can have multiple candidate keys but only one primary key.
   - Examples:
     - `STUD_NO` in the STUDENT table is a candidate key.
     - `{STUD_NO, COURSE_NO}` is a composite candidate key in the STUDENT_COURSE table.

2. **Primary Key**
   - A selected candidate key used to uniquely identify tuples in a table.
   - Features:
     - Always unique and cannot be NULL.
     - Ensures entity integrity.
     - Can consist of a single attribute or multiple attributes (composite primary key).
   - Example:
     - `STUD_NO` in the STUDENT table is a primary key.

3. **Super Key**
   - A set of attributes that can uniquely identify a tuple.
   - Features:
     - Includes candidate keys and attributes that exceed the minimal requirements.
     - Can contain NULL values.
   - Example:
     - `{STUD_NO, PHONE}` is a super key in the STUDENT table.
   - Relationship:
     - Every candidate key is a super key, but not all super keys are candidate keys.

4. **Alternate Key**
   - A candidate key that is not chosen as the primary key.
   - Features:
     - Acts as a secondary key.
     - Provides alternative ways to access records.
   - Example:
     - If `STUD_NO` is the primary key, `PHONE` becomes an alternate key in the STUDENT table.

5. **Foreign Key**
   - An attribute in one table that references the primary key of another table.
   - Features:
     - Establishes relationships between tables.
     - The referenced attribute must be a primary key in the referenced table.
     - Can contain NULL values and duplicate entries.
   - Examples:
     - `STUD_NO` in the STUDENT_COURSE table is a foreign key referencing `STUD_NO` in the STUDENT table.
     - `DNO` as a primary key in the DEPT table can be a foreign key in the EMP table.

6. **Composite Key**
   - A combination of two or more attributes used to uniquely identify rows in a table.
   - Features:
     - Acts as a primary key when a single unique attribute is unavailable.
     - Different combinations may provide varying levels of accuracy for unique identification.
   - Example:
     - `{FULLNAME, DOB}` can uniquely identify students.

### **Additional Points**
- **Entity Integrity:** Enforced using primary keys to ensure no duplicate or NULL values in the primary key column.
- **Referential Integrity:** Enforced using foreign keys to maintain consistency between referenced and referencing tables.
- **Key Constraints:**
  - **Unique Constraint:** Ensures no duplicate values in a column but allows NULL values (once per column in SQL Server).
  - **Not Null Constraint:** Ensures no NULL values in the column.

### **Relationships Between Keys**
- **Primary Key vs. Candidate Key:** A primary key is chosen from candidate keys.
- **Primary Key vs. Foreign Key:** A primary key ensures entity integrity, while a foreign key maintains referential integrity by linking tables.
- **Super Key vs. Candidate Key:** All candidate keys are super keys, but not all super keys are candidate keys.

### **Conclusion**
The effective use of database keys—candidate, primary, alternate, foreign, composite, and super keys—ensures robust database design and data integrity. Proper understanding and implementation of these keys help in achieving efficient querying, enforcing constraints, and maintaining relational consistency across tables.

**GFG Link :** https://www.geeksforgeeks.org/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/?ref=lbp
