Binary Search: Decrease and Conquer
Data needs to be sorted first

# Simple sorting algorithms
Rearranging a set of data items in asscending or descending order based on a key

Stability means when we sort a set more than once, the second key does not destory the order of the first sort
any algo can be made stable

![[Pasted image 20231212003505.png]]

# Hashing
array is called the hash table
index is hash-code or hash-index

Overwrite the hashCode() method in the Object class
If equals() is overridden, then hashCode() should also be overridden
hash code is generated

# Tree Traversal
pre-order: parent -> left -> right, visit root before subtrees
in order: left -> parent -> right
post order: left -> right -> parent, visit root after subtrees