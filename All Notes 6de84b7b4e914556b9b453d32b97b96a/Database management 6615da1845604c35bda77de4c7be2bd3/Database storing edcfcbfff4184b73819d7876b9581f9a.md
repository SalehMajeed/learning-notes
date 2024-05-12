# Database storing

- Pages: Imagine a database table that stores information about users. Each user's data, such as name, age, and email, is stored as a row in the table. To efficiently access the data, the database organizes the rows into pages. For instance, if each page can hold 100 rows, and there are 500 users in total, the data will be spread across five pages (500 rows / 100 rows per page).
- Index: Suppose we have a table containing product information, including product names, prices, and stock levels. To speed up the retrieval of products by their unique IDs (primary key), the database creates an index on the ID column. This index acts as a reference to the specific pages where each product's data is stored, making it quicker to access products by their IDs.

**Types of database →** 

1. **Row-Oriented Database:** Consider a transactional database used by an e-commerce platform. The orders placed by customers are stored as rows in the database, with each row containing information about a specific order, such as the customer's name, the ordered products, and the total amount. When querying for a particular order, the database retrieves the entire row containing all the order details.
2. **Column-Oriented Database:** Imagine a large dataset containing sales information, including the date, product name, quantity sold, and revenue generated. In a column-oriented database, each column of data is stored separately. When performing analytical queries, such as calculating total revenue for a specific date range, the database can efficiently access only the columns needed for the calculation, resulting in faster data retrieval.

**use of index:** 

Suppose we have a database table for employees, and it contains information such as employee IDs, names, departments, and hire dates. In this scenario, the primary key might be the employee ID. The database automatically creates an index for the employee ID column, allowing for quick retrieval of an employee's information based on their unique ID.

**Example:**

Now, let's consider a scenario where we want to retrieve all employees with a specific department name, such as "Marketing." Without an index on the department name column, the database would need to scan through all the pages to find employees with the "Marketing" department, which could be time-consuming for large datasets.

To improve the search performance for the "Marketing" department, we can create an index on the department name column. This index acts like a quick reference guide, pointing to the pages containing all the employees in the "Marketing" department. Consequently, the database can efficiently fetch all relevant employees with just a few I/O operations.

However, suppose we need to search for employees whose names contain a specific pattern using the "LIKE" operator, such as "John%". In this case, creating an index on the name column may not be as effective, as "LIKE" searches often involve non-predictable patterns. The database would still need to scan multiple pages, even with an index, to find all matching rows, which could result in slower performance.

Adding examples provides concrete scenarios where these concepts are applied, making it easier to understand their practical use and benefits. If you have any further questions or need more examples, feel free to ask!