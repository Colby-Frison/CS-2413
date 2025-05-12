# 2 - 3 Tree

L = left node ; M = middle node ; R = right node

- 2 -nodes
    - 1 value and 2 children
        - Left 2 middle
        - right child is NULL
    - values is the left tree are less than the single value v
    - Value …
- 3-node
    - If anode is a leaf node the n
        - L, M, R are all NULL
- If a node is a non lead node
    - if 2-node
        - L and M are not empty
    - if 3-node
        - L, M, R, are not empty
- ==All lead nodes have to be at the same level==

  

- If every node is a 2 node
    - Complexity is log_2 (n)
- If every node is a 3 node
    - complexity is log_3 (n)

## Project 4

### M-arr Tree

  

# B-tree

- b^t - tree → records are stored at leaf nodes

  

Find min and max = 0(logn) (or 0(1) with additional pointers)

remove min and max = O(logn)

insert = O(logn)

- Above operations can be done on an AVL tree or Red Black tree since the worst case height is O(logn)

  

- Data structure that returns the operations
    - Find min, find max, remove min, remove max

# representations of binary trees

(Not binary search tree)

- left pointer right pointer
- parent array
- left index number right index number
- generalized list
- complete binary tree
- InOrder and preorder transversal

  

# Min/max heap

- Find min O(1)
- Delete min O(logn)
    - Height of the main heap is O(logn)
        - Because the maximum height of a complete BT which a node is O(logn)
- insert O(logn)
- find x ⇒ cannot do this unless we perform a delete x
    - ==note possible,== sequential search

  

# min/max tree

- complete BT
    - Can do:
        - find min O(1)
        - find max O(1)
        - delete min O(logn)
        - delete max O(logn)
        - insert O(logn)

  

# Deaps

- CBT
- Dummy root
    - Left side is a min heap right side is a max heap