# B+ Tree

A B+ tree is another type of self-balancing search tree data structure, similar to a B-tree. It is commonly used in databases and file systems to efficiently store and retrieve large amounts of data. The B+ tree is an extension of the B-tree with some additional properties.

Here are the key characteristics of a B+ tree:

1. **Balancing**: Similar to a B-tree, a B+ tree is designed to maintain balance. All leaf nodes in a B+ tree are at the same level, creating a sorted linked list. This allows for efficient range queries.
2. **Degree**: Like a B-tree, a B+ tree has a defined degree. Each internal node can have between ceil(d/2) and d children, where d is the degree of the tree. Leaf nodes store the actual data values.
3. **Leaf nodes**: Leaf nodes in a B+ tree contain the actual data values and are linked together to form a sorted linked list. These nodes do not contain any pointers to other nodes. This structure makes range queries efficient, as all the data within a specific range can be easily accessed by traversing the linked list.
4. **Internal nodes**: Internal nodes in a B+ tree contain the keys that serve as separators or guides for searching and retrieving data. Each key in the internal node corresponds to the smallest key value in its right child.
5. **Search operation**: The search operation in a B+ tree works similar to a B-tree. It starts at the root node and recursively traverses down the tree to find the desired key. Once it reaches a leaf node, it performs a linear search within the node to find the exact key or the range of keys. The time complexity of a search operation is also O(log n), where n is the number of elements in the tree.
6. **Insertion operation**: When inserting a new element into a B+ tree, the tree is traversed to find the appropriate leaf node, and the element is inserted in sorted order. If the insertion causes a leaf node to overflow, it is split into two, and the split key is pushed up to the parent node. This splitting process may cascade up the tree if necessary.
7. **Deletion operation**: Similar to insertion, the deletion operation in a B+ tree involves finding the leaf node containing the element to be deleted. Once located, the element is removed from the leaf node. If the delete operation causes a leaf node to have fewer keys than the minimum required, it can be merged with a neighboring node or redistribute keys among sibling nodes to maintain balance.

B+ trees are efficient for storing and retrieving large sets of data. They are commonly used in scenarios that require fast search, insertion, deletion, and range queries. The B+ tree's structure, with its sorted linked list of leaf nodes, helps optimize range query operations by allowing efficient traversal of data within a specified range.

In database internal nodes only contain keys while leaf node contains all the values.