### Database Normalization: 

Database normalization is a critical process in database design aimed at improving efficiency, consistency, and accuracy. By organizing data to reduce redundancy and dependency, normalization simplifies management, ensures adaptability to business changes, and improves database integrity.

---

### **What is Database Normalization?**
Database normalization organizes the attributes of a database to reduce or eliminate data redundancy and inconsistency. Reducing redundancy minimizes database size and avoids anomalies during insert, delete, and update operations.

---

### **What is Functional Dependency and its Types?**
**Functional Dependency** is a relationship between two sets of attributes in a database. It ensures that for a specific value of attribute A, there exists a corresponding value of attribute B. For instance:

| A | B |
|---|---|
| 1 | 3 |
| 2 | 3 |
| 4 | 0 |
| 1 | 3 |
| 4 | 0 |

Here, A -> B is true, but B -> A is not true as B=3 maps to multiple values of A.

#### **Types of Functional Dependencies:**
1. **Trivial Functional Dependency:**
   X -> Y is trivial if Y is a subset of X.
   - Examples:
     - ABC -> AB
     - ABC -> A
     - ABC -> ABC

2. **Non-Trivial Functional Dependency:**
   X -> Y is non-trivial if Y is not a subset of X.
   - Example:
     - Id -> Name
     - Name -> DOB

3. **Semi Non-Trivial Functional Dependency:**
   X -> Y is semi non-trivial if X intersect Y is not NULL.
   - Examples:
     - AB -> BC
     - AD -> DC

#### **Advantages of Functional Dependencies:**
- Maintains data quality.
- Precisely defines database constraints.
- Helps identify potential keys.
- Essential for database normalization.

---

### **Why Do We Need Normalization?**
Normalization addresses anomalies:
1. **Insertion Anomalies:** Occur when incomplete data prevents insertion.
   - Example: Missing primary key value.
2. **Deletion Anomalies:** Occur when deleting a record unintentionally removes related data.
   - Example: Deleting a customer also deletes their orders.
3. **Update Anomalies:** Occur when changes in one record lead to inconsistencies in others.
   - Example: Updating an employee's salary in one table but not in others.

---

### **Features of Normalization**
- **Elimination of Data Redundancy:** Reduces repetitive data, improving efficiency.
- **Data Consistency:** Ensures accuracy by avoiding contradictions.
- **Simplified Data Management:** Breaks complex data into manageable tables.
- **Improved Database Design:** Enhances flexibility and adaptability.
- **Avoidance of Anomalies:** Minimizes insertion, deletion, and update anomalies.
- **Standardization:** Ensures uniform data organization.

---

### **Normal Forms in DBMS**
Normalization is achieved through a series of normal forms:

1. **First Normal Form (1NF):**
   - Attributes must be atomic (single-valued).

2. **Second Normal Form (2NF):**
   - In 1NF and all non-primary-key attributes are fully functionally dependent on the primary key.

3. **Third Normal Form (3NF):**
   - In 2NF and no transitive dependency exists for non-prime attributes.
   - Conditions:
     - X is a superkey.
     - Y is a prime attribute.

4. **Boyce-Codd Normal Form (BCNF):**
   - In 3NF and every functional dependency X -> Y, X must be a superkey.

5. **Fourth Normal Form (4NF):**
   - In BCNF and no multi-valued dependencies exist.

6. **Fifth Normal Form (5NF):**
   - In 4NF and no lossless decomposition occurs (join dependency).

---


### **Advantages of Normalization**
- Eliminates data redundancy.
- Ensures data accuracy and consistency.
- Simplifies data updates.
- Enhances query flexibility.
- Scales databases for future requirements.
- Supports consistent integration across applications.

### **Disadvantages of Normalization**
- **Performance Overhead:** Increased joins may slow query execution.
- **Loss of Context:** Data split across tables requires joins for retrieval.
- **Complexity:** Requires expert knowledge for proper implementation.
- **Design Challenges:** Poorly understood data models can complicate normalization.

---

**Conclusion:**
Database normalization is indispensable for efficient database design. Understanding its forms, functional dependencies, and the role of keys is essential for creating scalable, maintainable, and reliable databases.

**GFG Link :** https://www.geeksforgeeks.org/introduction-of-database-normalization/?ref=lbp
