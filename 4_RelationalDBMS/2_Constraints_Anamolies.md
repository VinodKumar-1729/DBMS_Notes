**Constraints in Relational Model**

### **Introduction**
Constraints in the Relational Model are conditions that must hold for the data in the database. These constraints ensure the integrity, consistency, and accuracy of the data and are validated before performing any operations such as insertion, deletion, or update. If any constraint is violated, the operation fails.

---

### **Types of Constraints**

#### **1. Domain Constraints**
- **Definition**: Attribute-level constraints that restrict attribute values to a specified domain.
- **Example**: For a `STUDENT` relation, if `AGE > 0` is applied, inserting a negative age value will fail.
- **Key Point**: Domain constraints ensure that attribute values remain valid and meaningful.
- **Additional Point**: They can also enforce specific data types, formats, or enumerated values (e.g., email format or gender as 'M' or 'F').

#### **2. Key Integrity**
- **Definition**: Ensures every relation has at least one set of attributes (keys) that uniquely identify each tuple.
- **Properties**:
  - **Uniqueness**: Each tuple in a relation must have a unique value for the key.
  - **Non-NULL**: Keys cannot have NULL values.
- **Example**: `ROLL_NO` in the `STUDENT` relation is a key since it uniquely identifies students.
- **Additional Point**: Composite keys can act as primary keys when no single attribute is sufficient to ensure uniqueness.

#### **3. Referential Integrity**
- **Definition**: Ensures that an attribute in one relation refers to a valid value in another relation.
- **Key Concepts**:
  - **Referencing Relation**: The relation that contains the referencing attribute.
  - **Referenced Relation**: The relation containing the referenced attribute.
- **Example**:
  - Relations:
    - **Student**:
      | ROLL_NO | NAME   | ADDRESS  | PHONE       | AGE | BRANCH_CODE |
      |---------|--------|----------|-------------|-----|-------------|
      | 1       | RAM    | DELHI    | 9455123451  | 18  | CS          |
      | 2       | RAMESH | GURGAON  | 9652431543  | 18  | CS          |
      | 3       | SUJIT  | ROHTAK   | 9156253131  | 20  | ECE         |
      | 4       | SURESH | DELHI    |             | 18  | IT          |
    - **Branch**:
      | BRANCH_CODE | BRANCH_NAME                           |
      |-------------|---------------------------------------|
      | CS          | COMPUTER SCIENCE                     |
      | IT          | INFORMATION TECHNOLOGY               |
      | ECE         | ELECTRONICS AND COMMUNICATION        |
      | CV          | CIVIL ENGINEERING                    |
  - Here, `BRANCH_CODE` in `STUDENT` must match `BRANCH_CODE` in `BRANCH`. If a value like `ME` is inserted in `STUDENT`, it will fail unless `ME` exists in `BRANCH`.
- **Additional Point**: Foreign keys are the implementation of referential integrity, and constraints like `ON DELETE SET NULL` can also be used to handle anomalies.

#### **4. Entity Integrity Constraint**
- **Definition**: Ensures that the primary key of a table cannot have NULL values and is unique for every tuple.
- **Key Point**: Without entity integrity, the relational database cannot differentiate between records.

---

### **Anomalies in the Relational Model**
Anomalies are inconsistencies or irregularities in database operations. There are three primary types:

#### **1. Insertion Anomaly**
- **Definition**: Occurs when a row cannot be inserted into the referencing relation due to a missing value in the referenced relation.
- **Example**: Attempting to insert a student with `BRANCH_CODE = ME` into `STUDENT` will fail if `ME` does not exist in the `BRANCH` table.
- **Additional Point**: It can also occur when excessive data redundancy forces unrelated attributes to be included in the table.

#### **2. Deletion/Updation Anomaly**
- **Definition**: Occurs when deleting or updating a row in the referenced relation affects the referencing relation.
- **Example**:
  - Deleting `BRANCH_CODE = CS` from `BRANCH` will fail if it is referenced in `STUDENT`.
  - Deleting `BRANCH_CODE = CV` is allowed since it is not referenced.
- **Additional Point**: These anomalies are particularly common in poorly normalized databases.

#### **3. Update Anomaly**
- **Definition**: Occurs when multiple rows need to be updated for a single change, leading to data inconsistency.
- **Example**: If a branch name in the `BRANCH` relation is updated, all corresponding rows in `STUDENT` must be updated to reflect the change.
- **Additional Point**: This anomaly highlights the importance of normalization to avoid redundant data.

---

### **Cascade Options**

#### **1. On Delete Cascade**
- Automatically deletes tuples in the referencing relation when the referenced value is deleted.
- **Example**: Deleting `BRANCH_CODE = CS` in `BRANCH` will also delete students with `BRANCH_CODE = CS` from `STUDENT`.

#### **2. On Update Cascade**
- Automatically updates the referencing attribute in the referencing relation when the referenced attribute is updated.
- **Example**: Updating `BRANCH_CODE = CS` to `CSE` in `BRANCH` will update all `CS` entries in `STUDENT` to `CSE`.
- **Additional Point**: Cascading options are crucial for maintaining referential integrity in large-scale databases.

---

**Key Takeaways**:
1. Constraints are essential for maintaining data integrity and consistency.
2. Referential integrity involves maintaining relationships between tables.
3. Cascade operations can simplify handling of referential integrity violations.


**GFG Link :** https://www.geeksforgeeks.org/relational-model-in-dbms/
