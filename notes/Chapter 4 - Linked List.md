- A data structure that can grow /shrink in size.
- You can insert or remove without having to move other elements (data)
- The number ‘q’ of elements in a linked list is linked by the capacity ‘q’ memory
- When you grow you don’t need to copy the elements into the new data structure

  

==**def: A linked list points to another linked list**==

![[Untitled.png]]

when incrementing a linked list the null box tells us the list is complete

**size() method**

```c++
template <class DT>

int LinkedList<DT>::size(){
	if(_info == null) return 0;
	else return (1 + (*_next).size());
}
```


Destructor

```C++
template <class DT> 
LinkedList<DT>::~LinkedList() {
	if(_info != null){
		delete _info;
		delete _next;
	}
	
}
```

  

int at method

```C++
(*N).intAt(0)

template <calss DT>

DTR LinkedList<DT>::intAT(int position){
	if(position < 0 || position >= (*this).size()){
		throw LinkedList out of bounds exception(); // unusable index
	}
	if( position == 0) {
		return *_info; // index is 0
	}
	else {
		return (*_next).infoAt(position-1); // returns a linked list that begins at position
	}
}
```

  

[ ] operator

```C++
DTR LinkedList<DT>::operator[](int i){
	if(i < 0 || i >= size()){
		throw LinkedList out of bounds exception(); // unusable index
	}
	if( i == 0) {
		return *_info; // index is 0
	}
	else {
		return (*_next)[i - 1]; // returns a linked list that begins at position
	}
}
```

  

Skip list : a different type of linked list that uses more pointers so it more easier to created operations like binary search. Its not covered in this class, but is utilized in the real world frequently

  

find method

```C++
bool LinekdList <DT>::find(DTR n){
	if(_info != null){
		
	}
```

  

delete method

```C++
template<DT> 

void LinkedList<DT>::removeAt(int position){
	if(position < 0 || position >= (*this).size()){ //make sure call is within bounds
		throw LinkedList out of bounds exception();
	}
	if (position > 0) {
		(*_next).removeAt(position-1);
	}
	if (position == 0){
		LinkedList<DT>* temp = _next;
		delete _info;
		(*_info) = (*_new)._info;
		_next = (*_next)._next;
		(*temp)._next = null;
		(*temp)._info = null;
		delete temp;
	}
```

  

add method

![[image 12.png|image 12.png]]

```C++
//add to begining of a linked list

```