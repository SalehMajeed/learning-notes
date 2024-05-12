# Transaction

- A transaction is a collection of queries served as a single logical unit.
- It has three states:
    1. Begin: The transaction begins with the "BEGIN" keyword and executes all the queries inside it.
    2. Commit: The "COMMIT" phase is when the transaction's changes are permanently saved to the database.
    3. Rollback: If any failure occurs during the transaction, all the steps in the transaction logic will revert to their initial state. For example, if we have 100 queries in a transaction, and 99 of them are successfully executed, but we encounter a failure, all 99 queries will revert to their original state.