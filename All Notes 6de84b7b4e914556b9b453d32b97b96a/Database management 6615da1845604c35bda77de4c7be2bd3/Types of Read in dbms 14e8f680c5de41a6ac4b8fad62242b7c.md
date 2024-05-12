# Types of Read in dbms

**Read Level →**

1. **Dirty Read:** A dirty read occurs when a transaction reads data that has been modified but not yet committed by another transaction. This can lead to unexpected results.
    
    **Example:** Transaction A updates the price of a product from $10 to $15, but it has not yet committed the changes. Transaction B reads the product's price and sees the updated value of $15. If Transaction A rolls back, Transaction B had a "dirty read" of the uncommitted price change.
    
2. **Non-Repeatable Read:** Non-repeatable reads happen when a transaction reads the same row multiple times, but each time it gets different data because other transactions have made changes in between.
    
    **Example:** Transaction A reads a customer's address and then Transaction B updates the address. If Transaction A reads the customer's address again, it will get a different value due to the change made by Transaction B.
    
3. **Phantom Read:** Phantom reads occur when a transaction reads a set of rows based on a condition, and another transaction inserts new rows that also satisfy the condition. This causes the first transaction to see additional "phantom" rows in the result set.
    
    **Example:** Transaction A retrieves all products with a price greater than $20. While Transaction A is running, Transaction B inserts a new product with a price of $25. When Transaction A fetches the data again, it will see the newly inserted product as a "phantom" read.
    
4. **Lost Updates:** Lost updates happen when two transactions try to update the same row concurrently. One transaction's changes overwrite the changes made by the other, resulting in data loss.
    
    **Example:** Transaction A and Transaction B both attempt to update the quantity of a product in stock. If they run concurrently, one transaction may overwrite the other's update, leading to the loss of one of the updates.