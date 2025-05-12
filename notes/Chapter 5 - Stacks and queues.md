# Stacks

- A stack is a data structure where only the first element can be accessed and modified
    - imagine a deck of cards, you can’t really take or put a card in the middle of the deck, only on the top
- ==**_LIFO ←**== ==Last-in; First-out==
    - ==**Push**== : add something to the top of the stack
        - Like add() in a linked list
    - ==**Pop**== : Remove something from the top of the stack
        - like remove() in a linked list
    - ==**Peek**== **:** Find what is at the top of the stack
        - like _info in a linked list
    - ==Size== : number of elements in the stack
    - All of these functions are constant time operations on a stack
- In a stack it isn't adding to the “top” of the stack. In other words it doesn't make the new data index 0. it instead add its to the end
    - So when adding to a stack it grows “down”
    - This strategy also makes it very easy to implement methods
        - for push its just adding to the end
        - for pop its just moving the index by -1
        - for peek its just look at the index at size

## Exceptions

- ==**Stack underflow exception**== **:** When you try to pop from a stack but there is nothing there
- ==Stack overflow exception== : When trying to push to a stack that has already met its limit

  

```C++
template <class DT>
class stackLL:LinkedList<DT> {
public: 
	DTE Pop();
	void Push();
	int size();
	int Peek();
```

  

## Array implementation of a stack

- Top is the first element of the array so top = 0, while the stack is empty of course
- as elements are added to the array the top variable moves down which is how we track the size of the stack
- for an array the top is the bottom so if top = 0 we know the stack is empty, therefore if we pop it would cause a ==StackUnderflowException==
- Similarly if we are trying to push an object but the top is already equals to the size of the array, it would lead to a ==StackOverflowException==
- Activation record : ??

![[image 13.png|image 13.png]]

  

### Maze traversal

- **Backtracking** : A stack stores data in the order it was found so when popping you are backtracking to where you started
- The basic idea is to push to the stack every step you go, then when there are two paths pick one, and continue to push
- Then when a dead end is reached, pop back to the crossroad and continue on the next path

  

## Expression evaluation

- Computers have no sense of PEMDAS so when evaluating equations they will just go left to right, to accommodate this we have infix and postfix expressions
- infix is the standard version we are used to seeing
- postfix is a rearrangement to allow the computer to properly evaluate the equation
- **Infix expression :**
    - x = y * Z + P / q - q * s
    - (((y*z) + (p/q)) - (q * s))
        - Fully parenthesized infix expression
- **Postfix Expression :**
    - x = y z * p q / q s * - +

  

```C++
//algo to evaluate a postfix expression

x <- getnexttoken();

while ( x != endqtoken){
	if(x is an operand)
		s.push
	else {
		x1 = s.pop();
		x2 = s.pop();
		s.push(x1 <x> x2) // <x> is an operator
	}
```

  

# Queue

- ==First-In ⇒ First-out== Data structure
- pretty simple its just a queue

  

## Linked list implementation of a queue

- ==Enqueue== - Add to the queue
- ==Dequeue== - remove from the front of the queue ( O(1) complexity)

  

- Exceptions
    - ==Queue empty (underflow)==
    - ==Queue full (overflow)==

  

- He didn't really talk a whole lot about this one

  

## Array implementation of a queue

- upon initialization there are two variables
    - Top = 0
    - rear = 0
- when top == rear we know the queue is empty
- each time an element is enqueued rear moves down one
    - so in the example rear = 4 (since it starts at 0)
- each time an element is dequeued the front moves down one
    - so in the example it is still at the top so top = 0
- So when we dequeue the entire queue top will == rear so we know its empty

![[image 1 7.png|image 1 7.png]]

  

## Radix sort

- Array of queues
    - Queue<int> [10];
- Take %10 of each element and but it in that index of the array
    - ex. 101 % 10 = 1 so it goes to index 1
    - 134 % 10 = 4 so it goes to index 4
- Then you pop from each element of the array of queues, giving you an array that is sorted by the last integer
- Then this process is repeated by modding at higher values to get the remainder of the second then third then fourth, and so on.
- to know how man ytimes this is repeated the largest value is found and the sort is completed teh amount of ties the largest int has digits