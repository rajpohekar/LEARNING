Commonly repeated questions : 

1. What are the different types of databases?
2. What is the difference between `DBMS` and `RDBMS`?
3. Explain the concept of normalization and its types.
4. What is a primary key, and why is it important?
5. What are foreign keys and their role in relational databases?
6. Explain the difference between `DELETE`, `TRUNCATE`, and `DROP` commands.
7. What are the different types of joins in SQL?
8. What is the difference between clustered and non-clustered indexes?
9. How does ACID properties ensure database integrity?
10. Explain the concept of a transaction in a database.
11. What is a stored procedure, and when would you use it?
12. How do triggers work in a database?
13. What is the difference between `HAVING` and `WHERE` clauses in SQL?
14. What are the advantages of using views in a database?
15. What is the difference between `INNER JOIN` and `OUTER JOIN`?
16. Explain the concept of referential integrity.
17. What are the various constraints in a relational database?
18. How do you implement a many-to-many relationship in a database?
19. What is an `ER` (Entity-Relationship) diagram, and how is it used?
20. What is the difference between `UNION` and `UNION ALL`?
21. Explain indexing and its types.
22. What are the differences between `OLTP` and `OLAP` systems?
23. How does the `GROUP BY` clause work in SQL?
24. What is a deadlock in DBMS, and how can it be avoided?
25. Explain the concept of database sharding and its benefits.

1.) Explain order of execution of SQL.
2.) What is difference between where and having?
3.) What is the use of group by?
4.) Explain all types of joins in SQL?
5.) What are triggers in SQL?
6.) What is stored procedure in SQL
7.) Explain all types of window functions?
(Mainly rank, row_num, dense_rank, lead & lag)
8.) What is difference between Delete and Truncate?
9.) What is difference between DML, DDL and DCL?
10.) What are aggregate function and when do we use them? explain with few example.
11.) Which is faster between CTE and Subquery?
12.) What are constraints and types of Constraints?
13.) Types of Keys?
14.) Different types of Operators ?
15.) Difference between Group By and Where?
16.) What are Views?
17.) What are different types of constraints?
18.) What is difference between varchar and nvarchar?
19.) Similar for char and nchar?
20.) What are index and their types?
21.) What is an index? Explain its different types.
22.) List the different types of relationships in SQL.
23.) Differentiate between UNION and UNION ALL.
24.) How many types of clauses in SQL?
25.) What is the difference between UNION and UNION ALL in SQL?
26.) What are the various types of relationships in SQL?
27.) Difference between Primary Key and Secondary Key?
28.) What is the difference between where and having?
29.) Find the second highest salary of an employee?
30.) Write retention query in SQL?
31.) Write year-on-year growth in SQL?
32.) Write a query for cummulative sum in SQL?
33.) Difference between Function and Store procedure ?
34.) Do we use variable in views?
35.) What are the limitations of views?

Answers update
# DBMS & SQL Interview Answers (Concise + Interview Ready)

---

## 1. Types of Databases
There are several types:
- Relational (MySQL, PostgreSQL)
- NoSQL (MongoDB, Cassandra)
- Distributed databases
- Data warehouses (Snowflake, Redshift)
- Graph databases (Neo4j)
- In-memory databases (Redis)

---

## 2. DBMS vs RDBMS
DBMS stores data in files, while RDBMS stores data in tables with relationships.
RDBMS supports constraints, normalization, and ACID properties.

---

## 3. Normalization
Normalization removes redundancy and improves data integrity.
Types:
- 1NF: Atomic values
- 2NF: No partial dependency
- 3NF: No transitive dependency
- BCNF: Stronger version of 3NF

---

## 4. Primary Key
A unique identifier for each record.
Cannot be NULL or duplicate.

---

## 5. Foreign Key
Used to maintain relationships between tables.
Ensures referential integrity.

---

## 6. DELETE vs TRUNCATE vs DROP
- DELETE: Removes rows (can rollback)
- TRUNCATE: Removes all rows (faster, no rollback)
- DROP: Deletes entire table

---

## 7. Types of Joins
- INNER JOIN: Matching records
- LEFT JOIN: All left + matching right
- RIGHT JOIN: All right + matching left
- FULL JOIN: All records
- CROSS JOIN: Cartesian product

---

## 8. Clustered vs Non-Clustered Index
- Clustered: Data physically stored in order (one per table)
- Non-clustered: Separate structure pointing to data

---

## 9. ACID Properties
- Atomicity: All or nothing
- Consistency: Valid state
- Isolation: No interference
- Durability: Permanent changes

---

## 10. Transaction
A set of operations executed as a single unit following ACID.

---

## 11. Stored Procedure
Precompiled SQL code stored in DB.
Used for reusability and performance.

---

## 12. Triggers
Automatically executed on events like INSERT/UPDATE/DELETE.

---

## 13. WHERE vs HAVING
- WHERE: Filters before grouping
- HAVING: Filters after GROUP BY

---

## 14. Views
Virtual tables based on queries.
Used for abstraction and security.

---

## 15. INNER vs OUTER JOIN
INNER returns matching rows only.
OUTER includes non-matching rows.

---

## 16. Referential Integrity
Ensures valid relationships between tables using foreign keys.

---

## 17. Constraints
- PRIMARY KEY
- FOREIGN KEY
- UNIQUE
- NOT NULL
- CHECK
- DEFAULT

---

## 18. Many-to-Many Relationship
Implemented using a junction table with foreign keys.

---

## 19. ER Diagram
Visual representation of entities and relationships.

---

## 20. UNION vs UNION ALL
- UNION: Removes duplicates
- UNION ALL: Keeps duplicates (faster)

---

## 21. Indexing
Improves query performance.
Types: Clustered, Non-clustered, Composite, Unique

---

## 22. OLTP vs OLAP
- OLTP: Transactional systems
- OLAP: Analytical systems

---

## 23. GROUP BY
Groups rows for aggregation functions.

---

## 24. Deadlock
When transactions wait on each other.
Avoid using proper locking and ordering.

---

## 25. Sharding
Splitting database horizontally.
Improves scalability and performance.

---

# SQL-Specific Questions

---

## 26. Order of Execution
FROM → JOIN → WHERE → GROUP BY → HAVING → SELECT → DISTINCT→WINDOW FUNCTIONS →ORDER BY → LIMIT

---

## 27. Aggregate Functions
Functions like COUNT(), SUM(), AVG(), MAX(), MIN().
Used with GROUP BY.

---

## 28. CTE vs Subquery
CTE is more readable and reusable.
Performance depends on DB engine.

---

## 29. DML vs DDL vs DCL
- DML: INSERT, UPDATE, DELETE
- DDL: CREATE, ALTER, DROP
- DCL: GRANT, REVOKE

---

## 30. Types of Keys
- Primary Key
- Foreign Key
- Candidate Key
- Super Key
- Composite Key

---

## 31. Operators
- Arithmetic (+, -)
- Comparison (=, >)
- Logical (AND, OR)
- Special (LIKE, IN, BETWEEN)

---

## 32. VARCHAR vs NVARCHAR
NVARCHAR supports Unicode.
VARCHAR does not.

---

## 33. CHAR vs NCHAR
Same as above but fixed length.

---

## 34. Relationships
- One-to-One
- One-to-Many
- Many-to-Many

---

## 35. Clauses in SQL
SELECT, FROM, WHERE, GROUP BY, HAVING, ORDER BY, LIMIT

---

## 36. Primary Key vs Secondary Key
Primary: Unique identifier
Secondary: Used for searching, not unique

---

## 37. Second Highest Salary
```sql
SELECT MAX(salary) 
FROM employees 
WHERE salary < (SELECT MAX(salary) FROM employees);
```

## 38. Retention Query
```sql
SELECT user_id, COUNT(DISTINCT login_date) 
FROM logins 
GROUP BY user_id;
```

UNION removes duplicates
UNION ALL keeps duplicates

49. Constraints
Constraints ensure data integrity in the database.

Retention Query Pattern
-- Find users who were active in Month 1 and returned in Month 2

```sql
SELECT 
    COUNT(DISTINCT a.user_id) as retained_users
FROM activity a
JOIN activity b ON a.user_id = b.user_id
WHERE DATEDIFF(month, a.event_date, b.event_date) = 1;
```

VARCHAR vs NVARCHAR
VARCHAR: Stores non-Unicode characters (1 byte per char). Use for English/standard text.

NVARCHAR: Stores Unicode (2 bytes per char). Essential for multi-language support (Emoji, Chinese, Arabic, etc.).

```sql
WITH first_login AS (
    SELECT user_id, MIN(login_date) AS first_date
    FROM logins
    GROUP BY user_id
),
user_activity AS (
    SELECT l.user_id,
           f.first_date,
           l.login_date,
           DATEDIFF(l.login_date, f.first_date) AS day_diff
    FROM logins l
    JOIN first_login f 
        ON l.user_id = f.user_id
)
SELECT first_date AS cohort_date,
       day_diff,
       COUNT(DISTINCT user_id) AS retained_users
FROM user_activity
GROUP BY first_date, day_diff
ORDER BY first_date, day_diff;
```

39. Year-on-Year Growth
Used to measure growth of a metric (like revenue) compared to previous year.

LAG() fetches previous row value
Difference gives absolute growth
Percentage shows relative growth

```sql
SELECT year, 
       revenue,
       LAG(revenue) OVER (ORDER BY year) AS prev_year_revenue,
       (revenue - LAG(revenue) OVER (ORDER BY year)) AS growth,
       ROUND(
           (revenue - LAG(revenue) OVER (ORDER BY year)) * 100.0 
           / LAG(revenue) OVER (ORDER BY year), 2
       ) AS growth_percentage
FROM sales;
```

---

## 40. Cumulative Sum
Used to calculate running totals over time.

Helps in analytics like revenue trend, balance tracking
Uses window function with ordered rows

```sql
SELECT id, 
       SUM(amount) OVER (
           ORDER BY id 
           ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
       ) AS running_total
FROM transactions;
```

---

## 41. Window Functions
Window functions perform calculations across a set of rows without collapsing them.

ROW_NUMBER(): unique sequence
RANK(): skips ranks on ties
DENSE_RANK(): no gaps in ranking
LAG(): previous row value
LEAD(): next row value

```sql
SELECT 
    employee_id,
    salary,
    ROW_NUMBER() OVER (ORDER BY salary DESC) AS row_num,
    RANK() OVER (ORDER BY salary DESC) AS rank_val,
    DENSE_RANK() OVER (ORDER BY salary DESC) AS dense_rank_val,
    LAG(salary) OVER (ORDER BY salary) AS prev_salary,
    LEAD(salary) OVER (ORDER BY salary) AS next_salary
FROM employees;
```

---

## 42. Function vs Stored Procedure
Function:

Returns a value

Can be used inside SELECT

No side effects (generally)

Stored Procedure:

Performs operations (INSERT/UPDATE)

Can return multiple values or result sets

Used for business logic

```sql
-- Function
CREATE FUNCTION get_bonus(salary INT)
RETURNS INT
RETURN salary * 0.1;

-- Stored Procedure
CREATE PROCEDURE get_employee()
BEGIN
    SELECT * FROM employees;
END;
```

---

## 43. Variables in Views
Views do not support variables.

Reason:

Views are static query definitions

They cannot accept runtime parameters

```sql
-- ❌ Invalid
CREATE VIEW test_view AS
SELECT * FROM employees WHERE salary > @salary;
```

---

## 44. Limitations of Views
No Parameters → cannot pass dynamic values

Performance → query runs every time (no stored data)

No ORDER BY → unless TOP/OFFSET used

DML Restrictions → cannot update if joins/aggregates used

```sql
-- ❌ ORDER BY not allowed
CREATE VIEW sorted_view AS
SELECT * FROM employees ORDER BY salary;

-- ❌ Not updatable
CREATE VIEW complex_view AS
SELECT dept_id, COUNT(*) 
FROM employees 
GROUP BY dept_id;
```

---

## 45. Index Types
Indexes improve query performance by reducing scan time.

Clustered → actual data sorted
Clustered Index
A Clustered Index defines the physical order of rows in a table. When you create a clustered index on a column, SQL Server rearranges the actual data rows to match the index order. This is why a table can have only one clustered index.


Non-clustered → separate pointer structure
A non-clustered index does not change the physical data order. It creates a separate structure with indexed columns and pointers to the actual rows. Multiple non-clustered indexes can be created, improving performance for searches and joins.

Stores index data separately from the table.
Multiple non-clustered indexes can exist on a table.
Contains a copy of the indexed column(s) and a pointer to the actual data row.
Record-Pointer
Example of Non-Clustered Index:
In the Student table, a non-clustered index can be created on the Name column. Since Roll_No is the primary key, it already has a clustered index. A non-clustered index creates a separate structure that stores the Name values and pointers to the actual rows.

Query:

CREATE NONCLUSTERED INDEX NIX_FTE_Name
ON Student (Name ASC);
Output:

Student Table
Creates a non-clustered index named NIX_FTE_Name on the Student table for the Name column.
Stores the index data in ascending order without changing the actual table data.
Improves the speed of searches and queries on the Name column.
Composite → multiple columns

Unique → ensures uniqueness

```sql
CREATE INDEX idx_salary ON employees(salary);
CREATE UNIQUE INDEX idx_email ON employees(email);
```

---

## 46. GROUP BY vs WHERE
WHERE:

Filters rows before grouping

GROUP BY:

Groups rows for aggregation

```sql
-- WHERE
SELECT * FROM employees WHERE salary > 50000;

-- GROUP BY
SELECT dept_id, COUNT(*) 
FROM employees 
GROUP BY dept_id;
```

---

## 47. WHERE vs HAVING
WHERE:

Applied before aggregation

HAVING:

Applied after aggregation

```sql
SELECT dept_id, COUNT(*) 
FROM employees 
GROUP BY dept_id
HAVING COUNT(*) > 5;
```

---

## 48. UNION vs UNION ALL
UNION removes duplicates (slower)

UNION ALL keeps duplicates (faster)

```sql
SELECT name FROM employees
UNION
SELECT name FROM managers;

SELECT name FROM employees
UNION ALL
SELECT name FROM managers;
```

---

## 49. Constraints
Constraints enforce rules on data.

PRIMARY KEY → unique + not null

FOREIGN KEY → relationship

UNIQUE → no duplicates

NOT NULL → mandatory field

CHECK → condition validation

```sql
CREATE TABLE employees (
    id INT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    salary INT CHECK (salary > 0)
);
```

50. NULL Handling (Tri-Valued Logic)
SQL has TRUE, FALSE, UNKNOWN.

Problem:

```sql
SELECT * FROM employees WHERE salary != 50000;
```

This ignores NULL values.

Solution:

```sql
SELECT * FROM employees WHERE salary IS NULL;

SELECT COALESCE(salary, 0) FROM employees;
```

51. SARGability (Performance Optimization)
SARGable queries allow index usage.

Bad:

```sql
SELECT * FROM orders WHERE YEAR(order_date) = 2024;
```

Good:

```sql
SELECT * FROM orders 
WHERE order_date >= '2024-01-01' 
  AND order_date < '2025-01-01';
```
