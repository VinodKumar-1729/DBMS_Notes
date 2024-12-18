**Schema: External, Conceptual, Physical**

1. **External Schema**:
   - **Definition**: Represents the user's view of the database, showing how specific users or user groups interact with the database.
   - **Purpose**: To provide a tailored view for different user groups to ensure data relevance and security.
   - **Key Points**:
     - Each user or group can have a unique external schema.
     - It includes only the data elements and operations relevant to the user group.
     - Security mechanisms can restrict access to sensitive data at this level.

2. **Conceptual Schema**:
   - **Definition**: A unified, logical view of the entire database as defined by the database administrator.
   - **Purpose**: To describe what data is stored and the relationships among those data elements.
   - **Key Points**:
     - Independent of physical storage details.
     - Includes the data entities, attributes, constraints, and relationships.
     - Provides a high-level abstraction of the database.

3. **Physical Schema**:
   - **Definition**: Represents the internal, physical representation of the database, detailing how data is stored in the hardware.
   - **Purpose**: To optimize data storage, retrieval, and performance.
   - **Key Points**:
     - Includes file structures, indexing, and storage details.
     - Closest to the hardware and system software.
     - Affects performance and scalability of the database system.

**Instance vs. Schema**:

1. **Schema**:
   - **Definition**: The overall design or blueprint of a database structure, defining how data is organized and related.
   - **Types**:
     - **External Schema**: User-level view.
     - **Conceptual Schema**: Logical structure.
     - **Physical Schema**: Physical storage details.
   - **Characteristics**:
     - Remains relatively stable over time.
     - Acts as a framework for the database.
     - Defines entities, relationships, and constraints.

2. **Instance**:
   - **Definition**: The actual content of the database at a particular moment in time.
   - **Characteristics**:
     - Changes frequently as data is updated, inserted, or deleted.
     - Reflects the state of the database.
     - Also known as a database snapshot.

3. **Key Differences**:
   - Schema is static and defines the structure, whereas an instance is dynamic and reflects the data at any point in time.
   - Schema is used for design; the instance is used for operations.

**Codd’s Rules for Relational DBMS**:

Dr. Edgar F. Codd proposed 12 rules (plus Rule 0) to define a fully relational database system. These rules serve as a benchmark for relational database management systems (RDBMS).

1. **Rule 0: Foundation Rule**
   - A system must qualify as relational, as a database, and as a management system to be an RDBMS.
   - It should use relational capabilities exclusively.

2. **Rule 1: Information Rule**
   - All data is represented as stored relations (tables) with column values.
   - Data is in a tabular format, with each column as an attribute and each row as a tuple.

3. **Rule 2: Guaranteed Access Rule**
   - Each data element is uniquely identifiable by a combination of the table name, primary key, and column name.
   - Ensures precise access to any data item.

4. **Rule 3: Systematic Treatment of Null Values**
   - Null values must be uniformly supported for representing missing, unknown, or inapplicable information.
   - Nulls must be distinct from zeros or empty strings.

5. **Rule 4: Active Online Catalog**
   - Metadata (data about data) should be stored within the database itself and accessible through standard SQL.
   - Catalogs should be relational.

6. **Rule 5: Comprehensive Data Sublanguage Rule**
   - The system must support a relational language with capabilities for data definition, manipulation, and control.
   - The language should include operations like SELECT, INSERT, UPDATE, and DELETE.

7. **Rule 6: View Updating Rule**
   - Any view that is theoretically updatable must also be updatable in the system.
   - Ensures consistency when interacting with virtual tables (views).

8. **Rule 7: High-Level Insert, Update, and Delete**
   - Data manipulation must be possible at a set level rather than a single record level.
   - SQL should support set operations for efficiency.

9. **Rule 8: Physical Data Independence**
   - Changes to the physical storage structure should not affect how data is accessed.
   - Ensures flexibility and scalability.

10. **Rule 9: Logical Data Independence**
    - Changes to the logical structure (schema) should not affect user views or applications.
    - Ensures adaptability to changing requirements.

11. **Rule 10: Integrity Independence**
    - Integrity constraints (e.g., primary key, foreign key) must be stored within the database catalog and not in application programs.
    - This rule promotes consistency.

12. **Rule 11: Distribution Independence**
    - A distributed database system must allow data distribution across multiple locations without affecting its relational nature.

13. **Rule 12: Non-Subversion Rule**
    - Operations performed using lower-level access methods must not bypass integrity constraints or security measures.

**Summary**:
- Codd’s rules emphasize standardization, integrity, and data independence.
- Not all modern RDBMS strictly follow all of Codd’s rules, but they serve as a guiding framework.

