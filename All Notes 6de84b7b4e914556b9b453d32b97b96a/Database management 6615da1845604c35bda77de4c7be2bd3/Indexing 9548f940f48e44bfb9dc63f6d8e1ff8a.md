# Indexing

In DBMS (Database Management Systems), indexing is the process of creating data structures that enable faster data retrieval from a database table. Indexes are used to optimize query performance by providing a quick lookup mechanism for specific columns, allowing the database to locate and access data more efficiently. Indexing works like the index of a book, enabling you to quickly find the page numbers of specific topics instead of searching through the entire book.

**Example: Employee Database**

Consider an "Employee" table with the following columns:

| Employee ID | Name | Department | Age | Salary |
| --- | --- | --- | --- | --- |
| 101 | John | HR | 30 | 50000 |
| 102 | Alice | Sales | 28 | 45000 |
| 103 | Bob | Marketing | 32 | 52000 |
| 104 | Mary | HR | 35 | 55000 |
| 105 | David | Finance | 31 | 58000 |

Without any indexes, the database would perform a full table scan to find specific data. For example, if you want to retrieve the salary of the employee with Employee ID 103, the database would have to go through each row in the table to find the matching record.

**Creating an Index:**

To speed up the retrieval of data based on specific columns, you can create an index on those columns. In this case, let's create an index on the "Employee ID" column:

```sql
sqlCopy code
CREATE INDEX idx_employee_id ON Employee(Employee ID);

```

**Indexed Retrieval:**

With the index in place, data retrieval becomes more efficient. Now, when you search for the salary of the employee with Employee ID 103, the database can use the index to directly locate the corresponding row without scanning the entire table.

```sql
sqlCopy code
SELECT Salary FROM Employee WHERE Employee ID = 103;

```

The database looks up the index entry for Employee ID 103, which points to the exact location of the corresponding row, and quickly retrieves the salary value without needing to examine other rows.

**Benefits of Indexing:**

- Faster Data Retrieval: Indexes allow the database to avoid full table scans and directly access specific rows, resulting in faster query execution.
- Query Optimization: By creating indexes on frequently accessed columns, you can significantly improve the performance of common queries.
- Data Integrity: Indexes can enforce uniqueness and data integrity constraints on indexed columns, ensuring that duplicate or null values are not allowed (for unique indexes).
- Efficient Joins: Indexes on join columns can speed up the process of joining tables together.

**Considerations:**

While indexing offers significant performance benefits, it's essential to use indexing judiciously. Indexes consume additional storage space and can impact the performance of data modification operations (e.g., inserts, updates, deletes). Therefore, indexes should be carefully chosen based on the data access patterns and query requirements of the application. Only columns that are frequently used for searching, filtering, or sorting should be indexed to achieve the best balance between improved query performance and efficient data maintenance.

[Bitmap indexing](Indexing%209548f940f48e44bfb9dc63f6d8e1ff8a/Bitmap%20indexing%2068bb81258c4141e89fc15d6f8d612649.md)

[Key and Non-Key Column](Indexing%209548f940f48e44bfb9dc63f6d8e1ff8a/Key%20and%20Non-Key%20Column%2016b3db1b5594440d819085ce8e68b225.md)

[Index Scan vs Index Only Scan](Indexing%209548f940f48e44bfb9dc63f6d8e1ff8a/Index%20Scan%20vs%20Index%20Only%20Scan%208bd66dbebc384072a2282076aed1bc6f.md)