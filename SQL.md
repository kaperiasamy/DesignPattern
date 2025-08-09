### SQL conceptual questions that are often asked in data analyst interviews

1. **What is the difference between SQL and NoSQL?**

- SQL (Structured Query Language) is a relational database management system, meaning it uses tables (rows and columns) to store data. 
- NoSQL databases, on the other hand, handle unstructured data and don’t rely on a schema, making them more flexible in terms of data storage and retrieval.  
- Interview Tip: Don't just memorize definitions. Be prepared to explain scenarios where you’d use SQL over NoSQL, and vice versa.

2. **What is the difference between INNER JOIN and OUTER JOIN?**

- An INNER JOIN returns records that have matching values in both tables.
- An OUTER JOIN returns all records from one table and the matched records from the second table. If there's no match, NULL values are returned.

3. **How do you optimize a SQL query for better performance?**

- Indexing: Create indexes on columns used frequently in WHERE, JOIN, or GROUP BY clauses.
- Query optimization: Use appropriate WHERE clauses to reduce the data set and avoid unnecessary calculations.
- Avoid SELECT *: Always specify the columns you need to reduce the amount of data retrieved.
- Limit results: If you only need a subset of the data, use the LIMIT clause.

4. **What are the different types of SQL constraints?**

Constraints are used to enforce rules on data in a table. They ensure the accuracy and reliability of the data. The most common types are:

- _PRIMARY KEY_: Ensures each record is unique and not null.
- _FOREIGN KEY_: Enforces a relationship between two tables.
- _UNIQUE_: Ensures all values in a column are unique.
- _NOT NULL_: Prevents NULL values from being entered into a column.
- _CHECK_: Ensures a column's values meet a specific condition.

5. **What is normalization? What are the different normal forms?**

Normalization is the process of organizing data to reduce redundancy and improve data integrity. Here’s a quick overview of normal forms:

- _1NF_ (First Normal Form): Ensures that all values in a table are atomic (indivisible).
- _2NF_ (Second Normal Form): Ensures that the table is in 1NF and that all non-key columns are fully dependent on the primary key.
- _3NF_ (Third Normal Form): Ensures that the table is in 2NF and all columns are independent of each other except for the primary key.

6. **What is a subquery?**

A subquery is a query within another query. It's used to perform operations that need intermediate results before generating the final query. 

Example:
```SQL
SELECT employee_id, name
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);
```
In this case, the subquery calculates the average salary, and the outer query selects employees whose salary is greater than the average.

7. **What is the difference between a UNION and a UNION ALL?**

- UNION combines the result sets of two SELECT statements and removes duplicates.
- UNION ALL combines the result sets and includes duplicates.

8. **What is the difference between WHERE and HAVING clause?**

- _WHERE_ filters rows before any groupings are made. It’s used with SELECT, INSERT, UPDATE, or DELETE statements.
- _HAVING_ filters groups after the GROUP BY clause.

9. **How would you handle NULL values in SQL?**

NULL values can represent missing or unknown data. Here’s how to manage them:

- Use IS NULL or IS NOT NULL in WHERE clauses to filter null values.
- Use COALESCE() or IFNULL() to replace NULL values with default ones.

Example:
```SQL
SELECT name, COALESCE(age, 0) AS age
FROM employees;
```
10. **What is the purpose of the GROUP BY clause?**

The GROUP BY clause groups rows with the same values into summary rows. It’s often used with aggregate functions like COUNT, SUM, AVG, etc.

Example:
```SQL
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```
