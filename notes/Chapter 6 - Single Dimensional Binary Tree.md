  

# Basic definitions of Binary tree

- Most definitions define the root to be 0, but in Shridhar’s definition the root is 0.
    - This causes a lot of algorithms to be simpler, but it also causes a lot of confusion when referencing other sources

  

- **Root** : A node with nothing pointing to it
    - Can also be a leaf node, but it its self is never a child node
- **Leaf Node** : A node that has no children
    - It is pointing to a null box on the left and right
- **Child node** : will be declared as either right or left child
    - has at least one child, otherwise it would just be a leaf node

  

## Pointer implementation of Binary Tree

```C++
template <class DT>
class BinaryTree { // pointer implementation
	Protected: 
		DT* _info;
		BinaryTree<DT>* _LC;
		BinartTree<DT>* _RC;
	Public:
		//default constructors
		.
		.
		.
		.
		.
};
```

  

### Declaration of binary tree

```C++
BinaryTree<int>* myT = new BinaryTree<int>*(100);
```

  

## Traversal of a binary Tree

“Visiting nodes of a binary Tree”

![[27ce6dd8-2304-4484-be3d-95811d924876.png]]

![[bb1c0548-c9d5-4de7-ba5a-8c22ed335e34.png]]

### ==PreOrder Traversal==

- Print the value in the root ==⇒ visit the root==
- Proceed to left subtree in preorder ==⇒ Preorder(LC)==
- Proceed to right subtree in preorder ==⇒ preorder(RC)==

![[image 14.png|image 14.png]]

![[image 1 8.png|image 1 8.png]]

### ==InOrder Traversal==

- Process Left subtree
- Print the value in the root ==⇒ visit root==
- Process right subtree

![[image 14.png|image 14.png]]

![[image 2 5.png|image 2 5.png]]

### ==PostOrder Traversal==

- ⇒ process Left subtree
- ⇒ process right subtree
- ⇒ visit the root

![[image 3 4.png|image 3 4.png]]

![[image 4 4.png|image 4 4.png]]

```C++
template<class DT> 
void BT<DT>::PreOrder(){
	if(_info != null){
		cout << *_info << ' ';
		(*LC).PreOrder();
		(*RC).PreOrder()
	}

/*	
This is basically the same for all three types of traversal, but the 
order of which it calls reccursion and print info will all be different
*/
```

==**Know how to construct a tree based on two traversal printouts**==

  

```C++
//size method
int BT<DT>::size(){
if(_info == null) return 0;
return (*LC).size() + (*RC).size();

/height
int BT<DT>::size(){
if(_info == null) return 0;
return (max.((*LC).height(), (*RC).height()) + 1);

...
```

  

  

  

  

```C++
//destructor

temoplate <class DT>
BT<DT>::~BT(){
	if(_info != null){
		delete _info;
		delete _LC; //recursive
		delete _RC; //recursive
	}
}
```

  

## Array implementation of a binary tree

- He has a tree diagram and picture of the array implementation, I’m too lazy to draw it all, just copy once he posts slide

  

1. Pointer implementation
2. Array implementation
3. InOrder / PreOrder Traversal
4. ==generalized list==(GL) ⇒ with a bit indicating LC and RC

  

```C++
class node {
	Protected:
		DT* _info;
		int _LC;
		int _RC;
		
}

class ARrayBT{
	Proteceted:
		ArrayClass<Node<DT>> T;
		int root;
		LinkedList<node<DT>> empty;
}

```

  

### ==Parent Array==

- Honestly no clue what this guy is talking about try to find some video on this made up topic, if it doesn't exist copy notes and try to make since of it

  

### Non-recursive PreOrder Traversal using stack

```C++
//traversal of tree without recursion
s.Push(root);
while(!s.empty()){
	x= s.pop();
	cout << x;
	if(!x->right() == empty)
		s.push(x->right());
	if(!x->left() == empty)
		s.push(x->left());
}
```

## push to _btm _left

i dunno but he said it was important

### Non-recursive InOrder Traversal using stack

```C++
//traversal of a tree without recursion
```