  

# **Chapter 1: C++ Questions**

1. **Syntax questions: Fix programming errors**:
    - These questions provide C++ code with mistakes, such as missing semicolons, incorrect variable types, improper use of pointers, or other syntax issues. You are required to debug the segment by identifying and correcting the errors.
2. **Count the number of times a destructor will be called**:
    - You need to understand the lifecycle of objects in C++. Destructors are called when an object goes out of scope or is explicitly deleted. This question requires you to analyze the code and count how many objects are being destroyed.
3. **Count the number of times a copy constructor will be called**:
    - Similar to the destructor count, but for copy constructors. The copy constructor is invoked when an object is copied, either through direct assignment or when passed by value to a function.
4. **What is the output of the following program segment?**:
    - These types of questions test your understanding of C++ semantics. Given a code snippet, you have to predict the output by tracing the program flow.
5. **Given a class, write the destructor or the copy constructor**:
    - These tasks require you to implement the destructor (which releases resources like dynamic memory) or the copy constructor (which makes a deep copy of an object). The goal is to manage memory correctly, especially when dealing with dynamic allocations.

---

# **Chapter 2: Algorithms and Recursion**

1. **Given a function, find Big-Oh**:
    - You need to analyze the time complexity of a function. Big-O notation describes the worst-case growth rate of the function. Look for nested loops, recursive calls, and the size of input to determine the complexity (e.g., O(n), O(n²), O(log n)).
2. **Given a program segment, count the number of primitive operations**:
    - Count the basic operations (like assignments, comparisons, and arithmetic operations) performed by the program. This helps in understanding the computational cost of algorithms.
3. **Given a function, write a recursive algorithm to implement the function**:
    - You must be able to convert a function to its recursive form. A recursive function calls itself with a reduced problem size until a base case is reached.

---

# **Chapter 3: Arrays, Vectors, and Matrices**

1. **Know the ArrayClass well**:
    - You are expected to understand how the `ArrayClass` is implemented, including dynamic memory management, resizing, and basic array operations. You should also be comfortable with accessing and modifying elements and how to handle bounds checking.
2. **Simple Bucket Sort**:
    - This is a sorting algorithm where elements are distributed into buckets, sorted within each bucket (often using another algorithm like insertion sort), and then concatenated. It is typically efficient for uniformly distributed data.
3. **Merging Algorithm; Merge Sort Algorithm**:
    - The merging algorithm combines two sorted arrays into one sorted array.
    - Merge Sort is a divide-and-conquer algorithm that recursively splits the array into halves, sorts each half, and then merges the sorted halves. Its time complexity is O(n log n).
4. **Binary Search Algorithm and Execution**:
    - Binary Search is an efficient algorithm for finding an element in a sorted array. It repeatedly divides the search space in half, reducing the size of the array until the element is found or determined to be absent. Time complexity is O(log n).
5. **Binary Search and Insertion**:
    - This technique combines binary search with insertion into a sorted array. First, find the correct position using binary search, then shift the elements to insert the new item while maintaining the sorted order.
6. **Matrices**:
    - **Row Major Ordering**: Stores matrix data row by row in memory.
    - **Column Major Ordering**: Stores matrix data column by column in memory.
    - **C++ Matrix**: Represents a matrix using a two-dimensional array in C++.
    - **ArrayClass of ArrayClass Objects**: A matrix where each row is represented as an instance of `ArrayClass`.
    - **Sparse Matrix Representation**: A matrix where most elements are zero, stored efficiently by only keeping track of non-zero elements.
    - **C++ Definitions**: Involves creating C++ classes or functions for each of these matrix representations.

---

# Chapter 4: Linked Lists

1. **C++ Class Definition of LinkedList**:
    - Designing a `LinkedList` class with necessary attributes (like head/tail pointers) and methods.
2. **LinkedList Operations**:
    - Implementing constructors, destructors, and methods for adding (`Add`) and removing (`Remove`) elements, and accessing information (`InfoAT`).
3. **Array Implementation of Linked List**:
    - Representing a linked list using an array, which involves managing node indices instead of pointers.
4. **Other Forms of Linked Lists**:
    - **Circular Linked Lists**: Last node points back to the first node, allowing traversal in a circular manner.
    - **Doubly Linked Lists**: Nodes have pointers to both the next and previous nodes, allowing bidirectional traversal.
    - **Generalized Lists**: Can store different data types or other lists as elements.

---

# Chapter 5: Stacks and Queues

1. **C++ Class Definition for Stack**:
    - Implementing a `Stack` class, managing the collection of elements with LIFO behavior, and handling exceptions.
2. **LinkedList and Array Implementation of a Stack**:
    - Two approaches to implement a stack: using a linked list or using an array, each with its advantages and drawbacks.
3. **Infix to Postfix Conversion Algorithm**:
    - An algorithm to convert expressions written in infix notation (e.g., `A + B`) to postfix notation (e.g., `AB+`), often using a stack for operator precedence.
4. **Postfix Evaluation Algorithm**:
    - Evaluating expressions written in postfix notation using a stack to compute values based on operands and operators.
5. **Queue Data Structure**:
    - Understanding the implementation of a circular queue, which overcomes the limitations of a regular queue by reusing vacant spaces.
6. **C++ Class Definition for Queue**:
    - Implementing a `Queue` class, which manages a collection of elements with FIFO behavior.

---

  

[[Practice problems]]