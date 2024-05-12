# Key and Non-Key Column

**Key Column:**

- A key column is a column or set of columns in a database table that uniquely identifies each row or record in that table. It serves as a unique identifier for each record, ensuring that there are no duplicate or identical rows in the table.
- There are different types of key columns:
    - **Primary Key:** The primary key is a special key column that uniquely identifies each record in the table. It must have unique and non-null values for each row, and there can be only one primary key in a table.
    - **Composite Key:** A composite key consists of two or more columns combined to form a unique identifier for each row in the table. Together, these columns ensure the uniqueness of each record.
    - **Foreign Key:** A foreign key is a column or set of columns in one table that refers to the primary key of another table, establishing a relationship between the two tables.
- Key columns are essential for maintaining data integrity, enforcing uniqueness, and establishing relationships between tables in a relational database.

**Non-Key Column:**

- A non-key column is any column in a database table that is not part of the primary key, composite key, or foreign key. It does not serve as a unique identifier for rows in the table.
- Non-key columns contain additional data or attributes about each record, providing details or information associated with the primary key.
- Non-key columns are used to store various types of data that describe the characteristics or properties of the entities represented by the table.

**Differences between Key and Non-Key Columns:**

1. **Uniqueness:** Key columns have unique values for each row in the table, ensuring that no two records are identical. Non-key columns may contain duplicate values, as they do not serve as unique identifiers.
2. **Data Integrity:** Key columns enforce data integrity by preventing duplicate records and maintaining the uniqueness of each row. Non-key columns do not enforce data integrity in the same way.
3. **Relationships:** Key columns are used to establish relationships between tables in the database, while non-key columns provide additional information about the entities represented by the table.
4. **Identification:** Key columns are essential for identifying and retrieving specific records from the table efficiently. Non-key columns are used to provide supplementary information about those records.
5. **Constraints:** Key columns can have specific constraints, such as uniqueness and non-nullability. Non-key columns may also have constraints, but they are not required to have unique values.

In summary, key columns are critical for uniquely identifying each record and enforcing data integrity and relationships in a database table. Non-key columns, on the other hand, contain additional descriptive data that provides details about the identified entities without serving as unique identifiers. Both types of columns work together to represent and manage data effectively in a database.