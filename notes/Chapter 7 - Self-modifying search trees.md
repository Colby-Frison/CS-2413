  

# Binary search tree

- Binary tree stores ==**comparable**== elements (numbers) that can be compared:
    
    ⇒ Integers or real you can do comparison
    
    ⇒ Fruits apple → Jack Fruit
    
    Color red → blue
    
- ==**BST**==
    - Empty tree is a BST
        - For a non empty tree
            - The values stored at a node is greater than or equal to all values stores in its left subtree
            - As it is less than vales stored in its right subtree
        - Every node in a BST is also a BST
    - ==**The InOrder traversal of a binary tree is a sorted set of elements**==
        - PreOrder is not
    - ==**worst case**== time complexity is height of tree O(n)
    - ==**best case**== time complexity with n node is O(log(n))
        - minimum height of binary tree with n nodes is log(n)
- Worst case insertion is O(n^2)

## class definition

```C++
template <class DT>
class BST:public BinaryTree<DT> {
	protected:
		DT* _info;
		BT<DT>* _L;
		BT<DT>* _R;
	public:
		//constructors
		constructors
			default
			copy
		//creating reading destructor
		operators
			==
			<<
			destructor
		//methods inportant for traversal
		height method
		size method
		traversals
			inorder
			preorder
			postorder
		Find remove insert
};
```

## find method (and insert)

```C++
//find method is very similar to a binary search algo
//in binary search you find the mid point of the remainer array
//but in binary tree the mid is the root, so when oyu call _L or _R
//it goes to the node of the subtree, which is the center

template <class DT>
BST<DT>& BST<DT>::Find(DT& x){
	if(_info == null) throw notfoundException;
	if(*_info == x) return *this;
	if(*_info < x)
		return (*_R).find(x);
	else
		return (*_L).find(x);
		
//this method can then be used to insert nodes aswell, as it will locate the
//empty node where the element should be then instead of throwing a not found error
//it creates a new node of that element
```

### comparing objects

- it is important when comparing two object elements, the comparison operators are adjusted in the objects class, so it is faster than trying to compare the arbitrary object in the find/insert.

## BST sorting

- sorting using binary search tree is very simple.
    - The first element in the list is the root for the tree
    - Then the find method is used to insert the remaining elements
        - This can result in a severely unbalanced tree, which in turn causes search to be O(n)

  

- Prof says this method of sorting is better than merge sort as there are less operations taking place.
    - In merge sort elements continue to be moved around
    - But in BST its just inserted then left alone
    - So even though the time complexity is slightly worse, it is slightly better, due to the simplicity of the algorithm

## Remove

```C++
i dunno
```

- if leaf node easy to delete
- if it has only one child copy it over
- if two …

  

## Globally balancing binary search tree

- Basically just binary search, but instead of returning when found the mid is made the root, then let then right
    
    - For example 5,11,20,28,42
    - 20 is the root 5 if is the left child then 22 is its right child, 28 is the right child of 20 and 42 is its right child
    
    ```C++
           20
          /  \
         5    28
          \     \
    	     11	   42
    
    //Globalling Balancing a BST
    GB(L,R) {
    	_if(l < R) {
    		mid = (L + R)/2;
    		node = A[mid];
    		node-> 
    		
    		//bro went so fast
    ```
    

  

## Optimal binary search tree construction

i dunno

# Self adjusting BST

watch lecture videos (8 videos - 15 mins each)

- The goal of self adjusting BST is to keep the height of the tree at a minimum upon each insertion and deletion
- The minimum height of a BST is O(logn)
    - AVL trees, red black trees, 2-3 trees
        - Height of the trees is O(logn)
        - insertion sort is O(logn)
        - deletion sort is O(logn)
    - Splay tree [move to the front heuristics]
        
        - BST
        - The height of the tree is not O(logn)
        
        ```C++
                     100
                    /   \
                   50    200
                           \ 
                            300
        ```
        

## Rotations

- Zig [clockwise rotation]
- zag [counter clockwise rotation

## double rotations

- zig-zig rotation
    
- zag-zag rotation
    
- zig-zag rotation
    
- zag-zig rotation

  

# Splay tree data structure

- It is a BST
- Find (x)
    - if x is found then bring x to the root of the tree with rotations
    - if x is not fund then bring y the parent of the node leaf where x could be
- 3
- Remove (x)
    - Remove x and bring parent of x to the root of the tree with rotations
- the operation to bring the root of the tree is called splaying

## two kinds of splay

- Bottom up splay
- top down splay
    - better way

  

## definition of a splay tree

- class definition of a splay tree
    - BST class definition
        - BT class definition
    - In other words its literally just an extension of a BST with special traversal methods (splaying)
- BST [splay tree}
    - insert (bottom up or top down)
        - Show after each rotation

# AVL tree

- BST
- Balance factor of each node in the BST
    - Height of left subtree(x) - height of right subtree(x)
        - can be -1, 0, 1
- Right-Right violation
    - A node has a value of -2 having 2 more nodes on the left subtree than thre right
    - This breaks the rule of only havjing -1 1 or 0
    - Solve with single zag rotation
- Left-left violation
    - same thing as right right but reversed
    - Solve with single Zig rotation
- Right-Left violation
    - Zag zig rotation
- Left-right violation
    - Zig zag rotation

  

- O(n * logn) for sorting time complexity

  

## Class definition of AVL tree

- BST
    - Store the balance factor
        - 00 → 0
        - 01 → -1
        - 10 → 1
        - 11 → idk/err
- rotation

  

  

# Red black tree

- BST
- nodes are colored red or black
- A node colored red does not have any children colored red
- The number of black nodes form he root to any leaf node is the same

  

# Project 4

- array tree