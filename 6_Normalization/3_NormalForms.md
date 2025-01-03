**Normal Forms in DBMS**

### Introduction to Normal Forms
Normal forms in database management systems (DBMS) are a series of guidelines to reduce data redundancy and improve data consistency. The primary goal is to organize data into tables in a way that avoids undesirable characteristics like update anomalies, insert anomalies, and delete anomalies.

---

### **1. First Normal Form (1NF)**
- **Definition**: A relation is in 1NF if each attribute contains only atomic (indivisible) values, and there are no repeating groups or arrays.
- **Key Points**:
  - Every attribute must contain a single value (atomicity).
  - Each column must have a unique name.
  - Rows must be uniquely identifiable using a primary key.

**Example (Non-1NF to 1NF Transformation)**:
- **Non-1NF Table**:
  | ID  | Name | Courses  |
  |-----|------|----------|
  | 1   | A    | c1, c2   |
  | 2   | E    | c3       |
  | 3   | M    | c2, c3   |

- **1NF Table**:
  | ID  | Name | Course   |
  |-----|------|----------|
  | 1   | A    | c1       |
  | 1   | A    | c2       |
  | 2   | E    | c3       |
  | 3   | M    | c2       |
  | 3   | M    | c3       |

---

### **2. Second Normal Form (2NF)**
- **Definition**: A relation is in 2NF if it is in 1NF and all non-prime attributes are fully functionally dependent on the primary key. Partial dependency (where a non-prime attribute is dependent on only part of a composite primary key) must be eliminated.
- **Key Points**:
  - Eliminate partial dependencies.
  - Divide the table into smaller tables to ensure all attributes depend fully on the primary key.

**Example (Non-2NF to 2NF Transformation)**:
- **Non-2NF Table**:
  | STUD_NO | COURSE_NO | COURSE_FEE |
  |---------|-----------|------------|
  | 1       | C1        | 1000       |
  | 2       | C2        | 1500       |
  | 1       | C4        | 2000       |

- **2NF Tables**:
  - Table 1: STUD_NO, COURSE_NO
  - Table 2: COURSE_NO, COURSE_FEE

---

### **3. Third Normal Form (3NF)**
- **Definition**: A relation is in 3NF if it is in 2NF and there are no transitive dependencies for non-prime attributes.
- **Key Points**:
  - Eliminate transitive dependencies (non-prime attribute depends indirectly on the primary key).
  - Ensure every non-prime attribute depends only on the primary key.

**Example**:
- **Non-3NF Table**:
  | STUD_NO | STUD_STATE | STUD_COUNTRY |
  |---------|------------|--------------|
  | 1       | CA         | USA          |

- **3NF Tables**:
  - STUDENT(STUD_NO, STUD_STATE)
  - STATE_COUNTRY(STUD_STATE, STUD_COUNTRY)

---

### **4. Boyce-Codd Normal Form (BCNF)**
- **Definition**: A relation is in BCNF if it is in 3NF and for every functional dependency X → Y, X is a superkey.
- **Key Points**:
  - Stricter than 3NF.
  - Eliminate functional dependencies where non-superkey attributes determine other attributes.

**Example**:
- **Non-BCNF Table**:
  | COURSE_NO | INSTRUCTOR | DEPT       |
  |-----------|------------|------------|
  | C1        | John       | Physics    |
  | C2        | Mike       | Chemistry  |

- **BCNF Table**:
  - COURSE(COURSE_NO, DEPT)
  - INSTRUCTOR(COURSE_NO, INSTRUCTOR)

---

### **5. Fourth Normal Form (4NF)**
- **Definition**: A relation is in 4NF if it is in BCNF and contains no multi-valued dependencies.
- **Key Points**:
  - Eliminate multi-valued dependencies.
  - Ensure that a single attribute does not have two or more independent relationships.

**Example**:
- **Non-4NF Table**:
  | STUDENT | COURSE  | HOBBY    |
  |---------|---------|----------|
  | John    | Math    | Chess    |
  | John    | Physics | Football |

- **4NF Tables**:
  - STUDENT_COURSE(STUDENT, COURSE)
  - STUDENT_HOBBY(STUDENT, HOBBY)

---

### **6. Fifth Normal Form (5NF)**
- **Definition**: A relation is in 5NF if it is in 4NF and cannot be decomposed further without losing data.
- **Key Points**:
  - Eliminate join dependencies.
  - Ensure no lossless decomposition.

**Example**:
Decompose tables to eliminate redundant data while maintaining integrity.

---

### **Applications of Normalization**
1. **Data Consistency**: Prevents anomalies and ensures accurate data representation.
2. **Data Redundancy**: Reduces redundant data, saving storage.
3. **Query Performance**: Simplifies queries and improves response times.
4. **Database Maintenance**: Easier updates, deletions, and modifications.
5. **Efficient Design**: Creates flexible, scalable database structures.

---

### **Key Points to Remember**
1. A relational database is always at least in 1NF.
2. Every binary relation (two attributes) is in BCNF.
3. BCNF is stricter than 3NF but might not preserve all functional dependencies.
4. Higher normal forms like 4NF and 5NF are rarely used in practical systems.
5. Always balance normalization with practical performance requirements.

**Conclusion**: Normalization is a critical aspect of database design, ensuring data integrity, consistency, and efficiency. However, excessive normalization can lead to complex queries, so striking a balance between normalization and practicality is essential.

**GFG Link :** https://www.geeksforgeeks.org/normal-forms-in-dbms/?ref=lbp
