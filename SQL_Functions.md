

### SQL Functions Overview
SQL functions allow data manipulation directly within SQL queries. These functions simplify calculations, text manipulation, and data conversion, enabling efficient data analysis and reporting.

### 1. Aggregate Functions
Aggregate functions operate on a set of values and return a single summarizing result. These are essential in reporting and analytics, often used with the `GROUP BY` clause.

#### a. **SUM()** 
   - **Usage**: Calculates the total of numeric values.
   - **Syntax**: `SELECT SUM(column_name) FROM table_name;`
   - **Example**: `SELECT SUM(salary) FROM employees;` returns the total salaries.
   - **Edge Concept**: Can use `SUM(DISTINCT column_name)` to sum only unique values.

#### b. **COUNT()**
   - **Usage**: Counts the number of rows or unique values in a specified column.
   - **Syntax**: `SELECT COUNT(column_name) FROM table_name;`
   - **Example**: `SELECT COUNT(employee_id) FROM employees;` returns the number of employees.
   - **Variations**:
     - `COUNT(*)`: Counts all rows, including those with `NULL` values.
     - `COUNT(DISTINCT column_name)`: Counts unique values, ignoring duplicates.

#### c. **AVG()**
   - **Usage**: Calculates the average of numeric values.
   - **Syntax**: `SELECT AVG(column_name) FROM table_name;`
   - **Example**: `SELECT AVG(salary) FROM employees;`
   - **Edge Concept**: Handles `NULL` values by default (i.e., `NULL` values are ignored).

#### d. **MAX()**
   - **Usage**: Finds the maximum value in a column.
   - **Syntax**: `SELECT MAX(column_name) FROM table_name;`
   - **Example**: `SELECT MAX(salary) FROM employees;`
   - **Exam Insight**: Can be combined with `GROUP BY` to find the maximum per group (e.g., `SELECT department, MAX(salary) FROM employees GROUP BY department;`).

#### e. **MIN()**
   - **Usage**: Finds the minimum value in a column.
   - **Syntax**: `SELECT MIN(column_name) FROM table_name;`
   - **Example**: `SELECT MIN(salary) FROM employees;`
   - **Edge Concept**: Like `MAX()`, it can be grouped for finer data granularity.

---

### 2. String Functions
String functions manipulate and format text data. These functions are especially useful for formatting reports and cleaning data.

#### a. **CONCAT()**
   - **Usage**: Joins two or more strings together.
   - **Syntax**: `SELECT CONCAT(string1, string2, ...) FROM table_name;`
   - **Example**: `SELECT CONCAT(first_name, ' ', last_name) AS full_name FROM employees;`
   - **Additional Note**: In some databases like MySQL, `CONCAT_WS(separator, string1, string2, ...)` adds a separator between strings, e.g., `CONCAT_WS('-', '2024', '11', '03')` outputs `'2024-11-03'`.

#### b. **SUBSTRING()**
   - **Usage**: Extracts a portion of a string.
   - **Syntax**: `SELECT SUBSTRING(column_name, start, length) FROM table_name;`
   - **Example**: `SELECT SUBSTRING(phone_number, 1, 3) AS area_code FROM contacts;`
   - **Advanced Tip**: Use negative `start` values to count backward in databases like MySQL, e.g., `SUBSTRING(string, -3)` returns the last three characters.

#### c. **UPPER()**
   - **Usage**: Converts all characters in a string to uppercase.
   - **Syntax**: `SELECT UPPER(column_name) FROM table_name;`
   - **Example**: `SELECT UPPER(name) FROM employees;`
   - **Unique Detail**: Useful for case-insensitive comparisons, e.g., `WHERE UPPER(name) = 'JOHN'`.

#### d. **LOWER()**
   - **Usage**: Converts all characters in a string to lowercase.
   - **Syntax**: `SELECT LOWER(column_name) FROM table_name;`
   - **Example**: `SELECT LOWER(email) FROM customers;`
   - **Exam Insight**: Often paired with `UPPER()` for case normalization in case-insensitive queries.

---

### 3. Additional Important Functions (Out-of-the-Box)
While the above are common, these additional functions are also important in exams and are sometimes less obvious.

#### a. **ROUND()**
   - **Usage**: Rounds a numeric value to a specified decimal place.
   - **Syntax**: `SELECT ROUND(column_name, decimal_places) FROM table_name;`
   - **Example**: `SELECT ROUND(price, 2) FROM products;`
   - **Advanced Use**: Useful in financial data reporting to ensure uniform decimal precision.

#### b. **IFNULL() / COALESCE()**
   - **Usage**: Replaces `NULL` values with a specified replacement value.
   - **Syntax**: `SELECT IFNULL(column_name, replacement) FROM table_name;` or `SELECT COALESCE(column_name1, column_name2, ...) FROM table_name;`
   - **Example**: `SELECT IFNULL(salary, 0) FROM employees;`
   - **Edge Detail**: `COALESCE()` can handle multiple columns, returning the first non-`NULL` value, often useful for hierarchical data (e.g., `SELECT COALESCE(manager_id, supervisor_id) FROM employees;`).

#### c. **TRIM()**
   - **Usage**: Removes leading and trailing spaces from a string.
   - **Syntax**: `SELECT TRIM(column_name) FROM table_name;`
   - **Example**: `SELECT TRIM(name) FROM customers;`
   - **Unique Detail**: Also supports removing specific characters in some databases (e.g., `TRIM('x' FROM 'xxxJohnxxx')` outputs `'John'`).

#### d. **LEN() or LENGTH()**
   - **Usage**: Returns the number of characters in a string.
   - **Syntax**: `SELECT LENGTH(column_name) FROM table_name;`
   - **Example**: `SELECT LENGTH(description) FROM products;`
   - **Exam Tip**: Useful in finding records with specific text lengths, e.g., `WHERE LENGTH(username) > 8`.

---

### Summary and Exam Tips
- **Combining Functions**: Often, multiple functions can be combined for powerful transformations, e.g., `SELECT UPPER(SUBSTRING(name, 1, 1)) || LOWER(SUBSTRING(name, 2)) FROM employees;` capitalizes the first letter and lowercases the rest.
- **NULL Handling**: Many functions ignore `NULL` values (e.g., `SUM()`), but for functions like `COUNT()`, knowing how they handle `NULL` is crucial.
- **CASE Expressions**: Often useful for conditional calculations within aggregate functions. E.g., `SELECT SUM(CASE WHEN gender = 'M' THEN 1 ELSE 0 END) FROM employees;` counts male employees.
