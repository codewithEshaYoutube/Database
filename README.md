# Database Interview Questions & Answers for Software Engineers

## Basic SQL & Relational Databases

1. **What is the difference between `INNER JOIN` and `LEFT JOIN`?**
   - **Answer**: 
     - An `INNER JOIN` returns rows when there is a match in both tables.
     - A `LEFT JOIN` returns all rows from the left table, and matched rows from the right table. If no match exists, the result is `NULL` from the right table.

2. **Explain the difference between `UNION` and `UNION ALL`.**
   - **Answer**: 
     - `UNION` combines the results of two queries and removes duplicate rows.
     - `UNION ALL` combines the results but does **not** remove duplicates.

3. **What are the different types of indexing in SQL? How do they work?**
   - **Answer**: 
     - **B-tree indexes**: Default type of index in most databases, used for searching sorted data.
     - **Bitmap indexes**: Efficient for columns with a low cardinality.
     - **Hash indexes**: Used for exact-match queries, not range queries.
     - **Full-text indexes**: Used for searching large text fields.
     - **Spatial indexes**: Used for geographic data.

4. **What is normalization? Can you explain the different normal forms (1NF, 2NF, 3NF)?**
   - **Answer**:
     - **Normalization** is the process of organizing data to avoid redundancy and dependency issues.
     - **1NF** (First Normal Form): Ensures that each column contains atomic (indivisible) values.
     - **2NF** (Second Normal Form): Ensures 1NF and removes partial dependencies (all non-key attributes must depend on the entire primary key).
     - **3NF** (Third Normal Form): Ensures 2NF and removes transitive dependencies (non-key attributes must be directly dependent on the primary key).

5. **What is denormalization? In what scenarios might it be used?**
   - **Answer**: 
     - **Denormalization** involves combining tables or adding redundant data to improve read performance. It is useful in situations where read performance is critical and the overhead of maintaining normalized data is too high (e.g., in OLAP systems or data warehousing).

6. **How does a `GROUP BY` clause work in SQL? Can you give an example?**
   - **Answer**:
     - The `GROUP BY` clause is used to group rows that have the same values in specified columns into summary rows. For example:
       ```sql
       SELECT department, COUNT(*) FROM employees GROUP BY department;
       ```
     - This query will return the number of employees per department.

7. **What is a foreign key, and what role does it play in database design?**
   - **Answer**: 
     - A **foreign key** is a field in a table that uniquely identifies a row of another table. It is used to enforce referential integrity between the two tables, ensuring that relationships between tables are consistent.

8. **What is the difference between `CHAR` and `VARCHAR` data types in SQL?**
   - **Answer**: 
     - `CHAR` is a fixed-length data type, meaning it always occupies the defined number of characters.
     - `VARCHAR` is a variable-length data type, meaning it only uses as much space as needed for the actual data.

9. **Explain ACID properties in database transactions.**
   - **Answer**:
     - **Atomicity**: The transaction is all or nothing; it either completes entirely or not at all.
     - **Consistency**: The database remains in a valid state before and after the transaction.
     - **Isolation**: Transactions are isolated from each other, preventing interference.
     - **Durability**: Once a transaction is committed, its changes are permanent, even if the system crashes.

10. **What are stored procedures and triggers? Can you provide use cases for each?**
    - **Answer**: 
      - **Stored Procedures**: Precompiled SQL code that can be executed on demand. Use cases include batch processing or encapsulating complex logic.
      - **Triggers**: Automatically executed in response to certain events on a table (INSERT, UPDATE, DELETE). Use cases include auditing changes or enforcing business rules.

## Advanced SQL & Performance

1. **What is query optimization, and what steps can be taken to optimize SQL queries?**
   - **Answer**: 
     - **Query optimization** involves improving the performance of SQL queries by reducing resource consumption (e.g., CPU, memory, disk IO). Common techniques include:
       - Using proper indexes.
       - Avoiding subqueries when joins will do.
       - Using `EXPLAIN` to analyze query execution plans.
       - Reducing the number of nested queries.

2. **Explain the concept of database locking and deadlocks. How can they be prevented?**
   - **Answer**: 
     - **Database locking** ensures that only one transaction can access a resource at a time. **Deadlocks** occur when two transactions are waiting for each other to release resources. To prevent deadlocks:
       - Use consistent locking orders.
       - Implement timeout strategies.
       - Break large transactions into smaller ones.

3. **What are `Indexes` and how do they affect the performance of SQL queries?**
   - **Answer**: 
     - **Indexes** are structures that improve query performance by allowing fast data retrieval. They reduce the need for full table scans. However, they can slow down `INSERT`, `UPDATE`, and `DELETE` operations due to the need for index updates.

4. **How does a `JOIN` operation affect query performance compared to using `WHERE` clauses?**
   - **Answer**:
     - `JOIN` operations are typically more efficient than using `WHERE` clauses to combine tables, as `JOIN` can leverage indexes. Using `WHERE` to filter joined tables can result in unnecessary computations, leading to slower performance.

5. **What is an execution plan, and how can you use it to optimize queries?**
   - **Answer**:
     - An **execution plan** is a detailed report that shows how the SQL query will be executed, including the order of operations, use of indexes, and data retrieval strategies. By analyzing the execution plan, you can identify inefficiencies like missing indexes or suboptimal join strategies.

6. **What is a composite index? Can you provide an example of when it would be useful?**
   - **Answer**: 
     - A **composite index** is an index that includes multiple columns. It is useful when queries filter on multiple columns, improving query performance. For example:
       ```sql
       CREATE INDEX idx_customer_date ON orders(customer_id, order_date);
       ```

7. **How would you design a scalable, highly available database system?**
   - **Answer**:
     - To design a scalable, highly available database system:
       - Use **replication** for high availability (e.g., master-slave or multi-master).
       - Implement **sharding** for horizontal scaling.
       - Use **load balancing** to distribute traffic.
       - Implement **automatic failover** mechanisms.

## NoSQL & Non-Relational Databases

1. **What are the differences between SQL and NoSQL databases?**
   - **Answer**: 
     - **SQL databases** are relational, schema-based, and use structured query language. They are typically used for applications that require strong consistency and complex queries.
     - **NoSQL databases** are non-relational, schema-less, and can handle unstructured data. They are typically used for large-scale, distributed applications and flexible data models.

2. **Explain the CAP theorem. How does it apply to NoSQL databases?**
   - **Answer**:
     - **CAP Theorem** states that a distributed system can provide only two of the following three guarantees at the same time:
       - **Consistency**: All nodes have the same data.
       - **Availability**: Every request receives a response.
       - **Partition tolerance**: The system continues to operate even if network partitions occur.
     - NoSQL databases are often designed with a trade-off between these guarantees, depending on the specific use case (e.g., **Cassandra** focuses on availability and partition tolerance, while **MongoDB** focuses on consistency and partition tolerance).

---

This set of questions and answers covers a broad range of topics in database systems, from basic SQL to advanced concepts and NoSQL systems. Let me know if you'd like more details on any specific area!
