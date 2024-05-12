# Index Scan vs Index Only Scan

**Index Scan:**

1. An "Index Scan" is a method used by the database engine to access data from a table using an index.
2. When a query involves filtering or searching on a column with an existing index, the database engine can use the index to quickly find the relevant rows, instead of scanning the entire table.
3. The index is traversed to locate the rows that match the specified condition, and then the database engine performs a lookup in the main table to retrieve the remaining columns needed to satisfy the query.
4. While an index scan can speed up the search process, it may still require additional table lookups to fetch columns not covered by the index. These lookups are known as "bookmark lookups" or "key lookups."
5. Index scans are useful for selective queries that return a small percentage of the total rows. If the query is non-selective and returns a large portion of the table, a full table scan might be more efficient.

**Example Query:**

Suppose we have created an index on the **`Category`** column:

```sql
sqlCopy code
CREATE INDEX idx_category ON Products (Category);
```

Now, consider the following query:

```sql
sqlCopy code
SELECT ProductID, ProductName FROM Products WHERE Category = 'Electronics';
```

Explanation:

- In this query, the database engine will use the index **`idx_category`** to perform an "Index Scan."
- The index helps to quickly locate all the rows with **`Category = 'Electronics'`**.
- However, the index only contains the **`ProductID`** (Primary Key) and **`Category`** columns.
- To fulfill the **`SELECT ProductID, ProductName`** projection, the database engine will have to perform a "bookmark lookup" or "key lookup" in the main table to retrieve the **`ProductName`**.
- The lookup operation adds some overhead, as it requires additional I/O operations to access the main table.

**Index-Only Scan (Covering Index):**

1. An "Index-Only Scan" or "Covering Index" is a specialized type of index that includes all the columns required to satisfy a particular query.
2. In an index-only scan, the database engine can perform the entire query directly from the covering index without the need to access the main table.
3. Covering indexes store all the necessary data for the query, including the columns specified in the SELECT and WHERE clauses, so there's no need for additional table lookups.
4. Index-only scans are particularly beneficial for queries that involve columns fully covered by the index. They significantly reduce I/O operations and improve query performance.
5. However, covering indexes require more storage space since they store additional columns in the index structure. Careful consideration of the included columns is essential to strike a balance between query performance and storage requirements.

**Example Query:**

Now, let's consider a different query with an additional index that covers the necessary columns:

```sql
sqlCopy code
CREATE INDEX idx_category_covering ON Products (Category) INCLUDE (ProductID, ProductName);
```

Query:

```sql
sqlCopy code
SELECT ProductID, ProductName FROM Products WHERE Category = 'Electronics';
```

Explanation:

- In this query, the database engine will use the index **`idx_category_covering`** to perform an "Index-Only Scan" or "Covering Index" scan.
- The covering index includes both **`ProductID`** and **`ProductName`** along with the indexed **`Category`** column.
- As a result, the database engine can satisfy the entire query directly from the index, without needing to access the main table.
- The covering index contains all the data required for the query, so there's no need for additional "bookmark lookups."

**Summary:**

- In the first query with a regular index, the database performs an "Index Scan" using the index on **`Category`**, but additional table lookups are required to fetch the **`ProductName`**.
- In the second query with a covering index, the database performs an "Index-Only Scan" using the index on **`Category`**, and all the required data for the query (**`ProductID`** and **`ProductName`**) is available in the covering index, avoiding the need for extra table lookups.
- The covering index results in improved performance by reducing I/O operations and providing an "index-only scan" for the query.
- The choice between regular indexes and covering indexes depends on the query's selectivity and the columns involved in the query. Careful index design is crucial to optimize database performance for various types of queries.