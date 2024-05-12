# Isolation levels

**Levels of ISOLATION →**

1. **Read Uncommitted:** This is the lowest level of isolation. It allows a transaction to read data that has been modified but not yet committed by other transactions.
    
    **Example:** Transaction A reads data from a table while Transaction B is in progress, modifying the same data. If Transaction B rolls back, Transaction A might have read inconsistent and uncommitted data.
    
2. **Read Committed:** This level ensures that a transaction will only read committed changes made by other transactions. It prevents dirty reads.
    
    **Example:** Transaction A reads data from a table after Transaction B has made changes and committed them. Transaction A will not see any uncommitted changes made by Transaction B.
    
3. **Repeatable Read:** This level prevents other transactions from applying changes to any rows used by a transaction. It avoids non-repeatable reads.
    
    **Example:** Transaction A reads a set of rows that meet a condition. Even if Transaction B inserts, updates, or deletes rows that also meet the same condition, Transaction A's result set remains unaffected until it completes.
    
4. **Snapshot Isolation:** Snapshot isolation provides a consistent view for the ongoing transaction, showing data as it existed at the beginning of the transaction.
    
    **Example:** Transaction A begins, and at that point, the database creates a snapshot of the data. Even if other transactions make changes during Transaction A's execution, it will continue to see the data as it was at the beginning.
    
5. **Serializable:** This is the highest level of isolation. It ensures that transactions appear to execute in a serial order, one after the other, even if they are executed concurrently. This guarantees the same outcome as if the transactions were executed serially.
    
    **Example:** Transactions A and B execute concurrently. Serializable isolation ensures that the outcome of executing both transactions concurrently is the same as if they were executed sequentially, maintaining consistency.