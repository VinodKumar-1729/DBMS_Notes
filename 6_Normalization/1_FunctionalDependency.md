**Functional Dependency and Attribute Closure**

### Functional Dependency (FD)
A **functional dependency (FD)** A → B in a relation holds if two tuples having the same value of attribute A also have the same value for attribute B.

#### Example:
In the **STUDENT** relation (Table 1):
- Functional Dependencies such as STUD_NO → STUD_NAME, STUD_NO → STUD_PHONE hold.
- However, STUD_NAME → STUD_STATE does not hold.

#### Advantages of Functional Dependencies:
1. **Reduces Redundancy**: Helps identify and remove redundant data in databases.
2. **Enhances Data Integrity**: Ensures data correctness and consistency across the database.
3. **Improves Manageability**: Simplifies data addition, modification, and deletion.

#### Disadvantages of Functional Dependencies:
1. **Complexity**: Identifying FDs can be time-consuming and complex, especially in large databases.
2. **Performance Issues**: Over-restrictive FDs can lead to slow query performance or data inconsistencies.
3. **Lack of Semantic Meaning**: FDs may not always reflect the actual relationships between data elements.

#### How to Identify Functional Dependencies:
Functional dependencies in a relation depend on the domain of the relation. For example:
- In the **STUDENT** relation:
  - STUD_NO (unique for each student) determines STUD_NAME, STUD_PHONE, STUD_STATE, STUD_COUNTRY, and STUD_AGE.
  - STUD_STATE → STUD_COUNTRY (same state implies the same country).
- In the **STUDENT_COURSE** relation:
  - COURSE_NO → COURSE_NAME (same course number implies the same course name).

#### Functional Dependency Set:
The **FD set** of a relation is the set of all FDs present in the relation.
For the **STUDENT** relation (Table 1), the FD set is:
```
{ STUD_NO → STUD_NAME, STUD_NO → STUD_PHONE, STUD_NO → STUD_STATE, STUD_NO → STUD_COUNTRY, STUD_NO → STUD_AGE, STUD_STATE → STUD_COUNTRY }
```

---

### Attribute Closure
The **attribute closure** of an attribute set is the set of attributes that can be functionally determined from it.

#### Steps to Find Attribute Closure:
1. Add the elements of the attribute set to the result set.
2. Recursively add elements to the result set that can be functionally determined from the elements of the result set.

#### Examples Using the FD Set of Table 1:
1. (STUD_NO)+ = {STUD_NO, STUD_NAME, STUD_PHONE, STUD_STATE, STUD_COUNTRY, STUD_AGE}
2. (STUD_STATE)+ = {STUD_STATE, STUD_COUNTRY}

#### Advantages of Attribute Closure:
1. **Identifies Derivable Attributes**: Determines all attributes that can be derived from a given set.
2. **Optimizes Design**: Helps establish relationships between attributes and tables to enhance query performance.
3. **Ensures Consistency**: Identifies all valid attribute combinations in the database.

#### Disadvantages of Attribute Closure:
1. **Computational Expense**: Calculating attribute closures can be resource-intensive for large datasets.
2. **Complexity**: Managing closures becomes challenging as attributes and tables grow.
3. **Lack of Semantic Understanding**: Does not account for the true meaning of data relationships.

---

### Candidate Keys and Super Keys Using Attribute Closure
- **Super Key**: If the attribute closure of an attribute set contains all attributes of the relation, it is a super key.
- **Candidate Key**: A super key where no proper subset can determine all attributes of the relation.

#### Example:
Using the FD set of Table 1:
- (STUD_NO, STUD_NAME)+ = {STUD_NO, STUD_NAME, STUD_PHONE, STUD_STATE, STUD_COUNTRY, STUD_AGE}
- (STUD_NO)+ = {STUD_NO, STUD_NAME, STUD_PHONE, STUD_STATE, STUD_COUNTRY, STUD_AGE}
  
Thus, **STUD_NO, STUD_NAME** is a super key but not a candidate key, as its subset (STUD_NO)+ is equal to all attributes of the relation. **STUD_NO** is the candidate key.

---

### Prime and Non-Prime Attributes
- **Prime Attributes**: Attributes that are part of any candidate key.
- **Non-Prime Attributes**: Attributes that are not part of any candidate key.
  
Example: In the **STUDENT** relation, STUD_NO is a prime attribute, while others (e.g., STUD_NAME, STUD_PHONE) are non-prime attributes.

---

### Conclusion
Tools like **functional dependency** and **attribute closure** are critical for designing and optimizing databases. They:
1. Help establish relationships between tables and attributes.
2. Enhance query efficiency.
3. Ensure data consistency and coherence.

**GFG Link :** https://www.geeksforgeeks.org/functional-dependency-and-attribute-closure/
