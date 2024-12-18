### Relational Algebra: 

Relational Algebra is a **procedural query language** that provides a theoretical foundation for relational databases and SQL. It defines operators that transform one or more input relations into an output relation. As it operates purely on mathematical principles, it uses symbols rather than English keywords to represent operators.

### Key Features
1. **Foundation for Relational Databases**: Relational Algebra is the basis for database query languages like SQL.
2. **Operator-based**: It provides a collection of operations to transform input relations into output relations, allowing complex queries.
3. **Mathematical Notation**: It avoids English keywords, relying on symbols to represent operations.

### Fundamental Operators
Relational Algebra consists of the following fundamental operators to manipulate data efficiently:

#### 1. **Selection (σ)**
- **Description**: Filters rows from a relation based on a specified condition.
- **Purpose**: Retrieve tuples that satisfy a condition.
- **Syntax**: σ(condition)R
- **Example**:
  - Relation R:
    | A | B | C |
    |---|---|---|
    | 1 | 2 | 4 |
    | 2 | 2 | 3 |
    | 3 | 2 | 3 |
    | 4 | 3 | 4 |
  - Query: σ(C > 3)R
  - Result:
    | A | B | C |
    |---|---|---|
    | 1 | 2 | 4 |
    | 4 | 3 | 4 |

#### 2. **Projection (π)**
- **Description**: Filters specific columns from a relation.
- **Purpose**: Retrieve required attributes while ignoring others.
- **Syntax**: π(attributes)R
- **Example**:
  - Relation R:
    | A | B | C |
    |---|---|---|
    | 1 | 2 | 4 |
    | 2 | 2 | 3 |
    | 3 | 2 | 3 |
    | 4 | 3 | 4 |
  - Query: π(B, C)R
  - Result:
    | B | C |
    |---|---|
    | 2 | 4 |
    | 2 | 3 |
    | 3 | 4 |
- **Note**: Projection eliminates duplicate rows by default.

#### 3. **Union (U)**
- **Description**: Combines results from two relations.
- **Constraint**: Relations must have the same attributes.
- **Syntax**: R1 U R2
- **Example**:
  - Relation FRENCH:
    | Student_Name | Roll_Number |
    |--------------|-------------|
    | Ram          | 01          |
    | Mohan        | 02          |
    | Vivek        | 13          |
    | Geeta        | 17          |
  - Relation GERMAN:
    | Student_Name | Roll_Number |
    |--------------|-------------|
    | Vivek        | 13          |
    | Geeta        | 17          |
    | Shyam        | 21          |
    | Rohan        | 25          |
  - Query: π(Student_Name)FRENCH U π(Student_Name)GERMAN
  - Result:
    | Student_Name |
    |--------------|
    | Ram          |
    | Mohan        |
    | Vivek        |
    | Geeta        |
    | Shyam        |
    | Rohan        |

#### 4. **Set Difference (-)**
- **Description**: Retrieves tuples from one relation that are not in another.
- **Constraint**: Relations must have the same attributes.
- **Syntax**: R1 - R2
- **Example**:
  - Query: π(Student_Name)FRENCH - π(Student_Name)GERMAN
  - Result:
    | Student_Name |
    |--------------|
    | Ram          |
    | Mohan        |

#### 5. **Set Intersection (∩)**
- **Description**: Retrieves tuples common to both relations.
- **Constraint**: Relations must have the same attributes.
- **Syntax**: R1 ∩ R2
- **Example**:
  - Query: π(Student_Name)FRENCH ∩ π(Student_Name)GERMAN
  - Result:
    | Student_Name |
    |--------------|
    | Vivek        |
    | Geeta        |

#### 6. **Rename (ρ)**
- **Description**: Renames a relation or its attributes.
- **Purpose**: Avoid ambiguity in complex queries.
- **Syntax**: ρ(new_name/old_name)R

#### 7. **Cartesian Product (×)**
- **Description**: Combines each tuple of one relation with every tuple of another.
- **Purpose**: Basis for more complex operations like joins.
- **Syntax**: R1 × R2
- **Example**:
  - Relation A:
    | Name | Age | Sex |
    |------|-----|-----|
    | Ram  | 14  | M   |
    | Sona | 15  | F   |
    | Kim  | 20  | M   |
  - Relation B:
    | ID | Course |
    |----|--------|
    | 1  | DS     |
    | 2  | DBMS   |
  - Query: A × B
  - Result:
    | Name | Age | Sex | ID | Course |
    |------|-----|-----|----|--------|
    | Ram  | 14  | M   | 1  | DS     |
    | Ram  | 14  | M   | 2  | DBMS   |
    | Sona | 15  | F   | 1  | DS     |
    | Sona | 15  | F   | 2  | DBMS   |
    | Kim  | 20  | M   | 1  | DS     |
    | Kim  | 20  | M   | 2  | DBMS   |

### Derived Operators

#### 1. **Natural Join (⋈)**
- **Description**: Combines tuples from two relations based on common attributes.
- **Example**:
  - EMP:
    | Name | ID  | Dept_Name |
    |------|-----|-----------|
    | A    | 120 | IT        |
    | B    | 125 | HR        |
    | C    | 110 | Sales     |
    | D    | 111 | IT        |
  - DEPT:
    | Dept_Name | Manager |
    |-----------|---------|
    | Sales     | Y       |
    | Production| Z       |
    | IT        | A       |
  - Query: EMP ⋈ DEPT (condition: EMP.Dept_Name = DEPT.Dept_Name)
  - Result:
    | Name | ID  | Dept_Name | Manager |
    |------|-----|-----------|---------|
    | A    | 120 | IT        | A       |
    | C    | 110 | Sales     | Y       |
    | D    | 111 | IT        | A       |

#### 2. **Conditional Join**
- **Description**: Similar to Natural Join but allows specifying conditions other than equality.
- **Example**:
  - Relation R:
    | ID | Sex | Marks |
    |----|-----|-------|
    | 1  | F   | 45    |
    | 2  | F   | 55    |
    | 3  | F   | 60    |
  - Relation S:
    | ID | Sex | Marks |
    |----|-----|-------|
    | 10 | M   | 20    |
    | 11 | M   | 22    |
    | 12 | M   | 59    |
  - Query: R ⋈ S (condition: R.Marks >= S.Marks)
  - Result:
    | R.ID | R.Sex | R.Marks | S.ID | S.Sex | S.Marks |
    |------|-------|---------|------|-------|---------|
    | 1    | F     | 45      | 10   | M     | 20      |
    | 1    | F     | 45      | 11   | M     | 22      |
    | 2    | F     | 55      | 10   | M     | 20      |
    | 2    | F     | 55      | 11   | M     | 22      |
    | 3    | F     | 60      | 10   | M     | 20      |
    | 3    | F     | 60      | 11   | M     | 22      |
    | 3    | F     | 60      | 12   | M     | 59      |

### Relational Calculus
Relational Calculus is a **non-procedural query language** focused on specifying the desired result without detailing how to achieve it. It comes in two types:
1. **Tuple Relational Calculus (TRC)**
2. **Domain Relational Calculus (DRC)**

### Conclusion
Relational Algebra, while theoretical, is a powerful tool for understanding database operations. It allows us to break down complex queries into simpler, manageable parts and serves as the foundation for practical query languages like SQL.

**GFG Link :** https://www.geeksforgeeks.org/introduction-of-relational-algebra-in-dbms/?ref=lbp
