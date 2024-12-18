**Anomalies in the Relational Model**

### **Introduction**
Anomalies in the relational model refer to inconsistencies or errors that can arise when working with relational databases, particularly during data insertion, deletion, and modification. These anomalies can disrupt the integrity and consistency of the database and are categorized as follows:

1. **Insertion Anomalies**
2. **Deletion Anomalies**
3. **Update Anomalies**

### **Causes of Anomalies in DBMS**
Database anomalies are often caused by poorly designed database structures where all data is stored in a single table or "flat" database. These issues arise due to data redundancy and weak relational designs.

**Solution:**
Normalization, the process of restructuring a database into smaller, well-organized tables, is the primary method to reduce anomalies. Normalization minimizes data redundancy and ensures referential integrity.

### **Examples of Anomalies**

#### **Example Tables**:

**STUDENT Table**
| STUD_NO | STUD_NAME | STUD_PHONE  | STUD_STATE | STUD_COUNTRY | STUD_AGE |
|---------|-----------|-------------|------------|--------------|----------|
| 1       | RAM       | 9716271721  | Haryana    | India        | 20       |
| 2       | RAM       | 9898291281  | Punjab     | India        | 19       |
| 3       | SUJIT     | 7898291981  | Rajasthan  | India        | 18       |
| 4       | SURESH    |             | Punjab     | India        | 21       |

**STUDENT_COURSE Table**
| STUD_NO | COURSE_NO | COURSE_NAME        |
|---------|-----------|--------------------|
| 1       | C1        | DBMS               |
| 2       | C2        | Computer Networks  |
| 1       | C2        | Computer Networks  |

#### **Insertion Anomalies**:
An insertion anomaly occurs when a record cannot be added to a referencing table due to the absence of a corresponding referenced value.

**Example:** Attempting to insert `STUD_NO = 7` in the `STUDENT_COURSE` table will fail because `STUD_NO = 7` does not exist in the `STUDENT` table.

#### **Deletion Anomalies**:
A deletion anomaly occurs when deleting a record unintentionally removes important information.

**Example:** Deleting `STUD_NO = 1` from the `STUDENT` table will also result in the loss of course details for that student in the `STUDENT_COURSE` table.

#### **Update Anomalies**:
An update anomaly occurs when inconsistent or incomplete updates are made across a database.

**Example:** Updating the `COURSE_NAME` for `COURSE_NO = C2` in one row but not in all rows of the `STUDENT_COURSE` table can lead to data inconsistencies.

### **Avoiding Anomalies**
To address these issues, referential integrity constraints and normalization techniques are used:

1. **ON DELETE/UPDATE SET NULL:**
   - If a tuple is deleted or updated in the referenced table, the corresponding foreign key value in the referencing table is set to `NULL`.

2. **ON DELETE/UPDATE CASCADE:**
   - If a tuple is deleted or updated in the referenced table, the corresponding rows in the referencing table are also deleted or updated.

### **How These Anomalies Occur**

- **Insertion Anomalies:** Occur due to missing mandatory fields or incomplete data.
  - Example: Attempting to insert a record without a primary key value.

- **Deletion Anomalies:** Occur when deleting a record removes additional unintended data.
  - Example: Deleting a customer record removes all associated order details.

- **Update Anomalies:** Occur due to partial updates across multiple records.
  - Example: Changing an employee's salary in one record but not in others.

### **Removing Anomalies with Normalization**
Normalization ensures that data is organized efficiently by splitting large tables into smaller, related ones while maintaining data integrity. This process adheres to rules such as the following:

- **Eliminating Repeated Data:** Ensures each piece of information is stored only once.
- **Avoiding Undesirable Anomalies:** Prevents issues during insertion, deletion, and updating.
- **Establishing Proper Relationships:** Creates well-defined relationships between tables.

### **Advantages of Normalization**
1. **Data Integrity:** Maintains accuracy and consistency using primary keys, foreign keys, and constraints.
2. **Scalability:** Easily handles growing datasets.
3. **Flexibility:** Allows complex querying and reporting.
4. **Security:** Protects data through robust access controls.

### **Disadvantages of Normalization**
1. **Data Redundancy:** Can still exist if normalization is not done properly.
2. **Complexity:** Requires expertise to design and maintain.
3. **Performance Overhead:** Joins across multiple tables can degrade performance for large datasets.
4. **Limited for Unstructured Data:** Relational models struggle with unstructured data like text and videos.

### **Conclusion**
Relational model anomalies can disrupt data integrity and consistency. By applying normalization techniques and enforcing referential integrity constraints, these anomalies can be minimized or eliminated, ensuring a reliable and efficient database structure. Adhering to principles like those defined by E.F. Codd improves data organization and ensures the overall dependability of relational databases.

**GFG Link :** https://www.geeksforgeeks.org/anomalies-in-relational-model/?ref=lbp
