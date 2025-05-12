### **Chapter 1: C++ Questions**

1. **Syntax Question (Fix the programming errors):**
    
    ```C++
    int main() {
        int* ptr = nullptr;
        *ptr = 5;
        return 0;
    }
    
    ```
    
    - **Task**: Identify and correct the error in the code.
    
    - answer
        
        ```C++
        int main() {
            int* ptr = nullptr;
            // Error: dereferencing a nullptr causes a segmentation fault.
            // Fix: allocate memory for ptr before dereferencing.
            ptr = new int(5)
            delete ptr;  // Always free dynamically allocated memory
            return 0;
        }
        ```
        
2. **Count the number of times a destructor will be called**:
    
    ```C++
    class Test {
    public:
        ~Test() { std::cout << "Destructor called"; }
    };
    
    void createTest() {
        Test t1;
        Test* t2 = new Test();
        delete t2;
    }
    
    int main() {
        createTest();
    }
    
    ```
    
    - **Task**: How many times will the destructor be called in this program?
    
    - answer
        
        ```C++
        cpp
        Copy code
        class Test {
        public:
            ~Test() { std::cout << "Destructor called"; }
        };
        
        void createTest() {
            Test t1;          // Destructor called once (when t1 goes out of scope)
            Test* t2 = new Test();  // No destructor call here (manual deallocation needed)
            delete t2;        // Destructor called once (when t2 is deleted)
        }
        
        int main() {
            createTest();  // Destructor is called 2 times: once for t1, once for t2
        }
        
        ```
        
        **Answer**: The destructor is called **2 times**.
        
3. **Count the number of times a copy constructor will be called**:
    
    ```C++
    class Point {
    public:
        Point(const Point& p) { std::cout << "Copy Constructor called"; }
    };
    
    Point createPoint(Point p) {
        return p;
    }
    
    int main() {
        Point p1;
        Point p2 = createPoint(p1);
    }
    
    ```
    
    - **Task**: How many times is the copy constructor called in this program?
    
    - answer
        
        ```C++
        cpp
        Copy code
        class Point {
        public:
            Point(const Point& p) { std::cout << "Copy Constructor called"; }
        };
        
        Point createPoint(Point p) {  // Copy constructor called when passing by value
            return p;                 // Copy constructor called for returning by value
        }
        
        int main() {
            Point p1;                 // No copy constructor call here
            Point p2 = createPoint(p1); // Copy constructor called once for function a g, once for return
        }
        
        ```
        
        **Answer**: The copy constructor is called **2 times**.
        
4. **What is the output of the following program segment?**:
    
    ```C++
    class A {
    public:
        A() { std::cout << "A created\n"; }
        ~A() { std::cout << "A destroyed\n"; }
    };
    
    int main() {
        A obj1;
        {
            A obj2;
        }
    }
    ```
    
    - **Task**: What will be the output of this code?
    
    - answer
        
        ```CSS
        A created
        A created
        A destroyed
        A destroyed
        ```
        
5. **Write the copy constructor for the following class**:
    
    ```C++
    class MyClass {
    private:
        int* data;
    public:
        MyClass(int val) { data = new int(val); }
        // Write the copy constructor here
    }
    ```
    
    - answer
        
        ```C++
        // Copy constructor (deep copy)
        MyClass(const MyClass& other) {
            data = new int(*other.data);  // Deep copy of the value pointed to by other.data
        }
        
        ~MyClass() { delete data; }  // Destructor to free memory
        ```
        

---

  

### **Chapter 2: Algorithms and Recursion**

1. **Find the Big-O of the following function**:
    
    ```C++
    void func(int n) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                std::cout << i * j;
            }
        }
    }
    
    ```
    
    - **Task**: What is the time complexity of this function?
    
    - answer
        
        The time complexity is **O(n²)**, because there are two nested loops, each iterating `n` times.
        
2. **Count the number of primitive operations**:
    
    ```C++
    int sum(int n) {
        int total = 0;
        for (int i = 1; i <= n; i++) {
            total += i;
        }
        return total;
    }
    
    ```
    
    - **Task**: Count the number of primitive operations in the function `sum`.
    
    - answer
        
        There are 5n+6 primitive operations
        
3. **Write a recursive function to calculate the factorial of a number**:
    
    ```C++
    int factorial(int n) {
        // Write the recursive function here
    }
    ```
    
    - answer
        
        ```C++
        int factorial(int n) {
            if (n == 0) return 1;       // Base case: factorial of 0 is 1
            else return n * factorial(n - 1); // Recursive case
        }
        ```
        

---

### **Chapter 3: Arrays, Vectors, and Matrices**

1. **ArrayClass Practice**:
    
    - **Task**: Write a C++ class definition for `ArrayClass`
    
    - answer
        
        This also includes proper implementation of each public method which is not nessesary
        
        ```C++
        template <class DT>
        class ArrayClass : AbstractArray <DT> {
        	protected :
        		DT * _myArray ;
        		int _size ;
        	public :
        		Arrayclass () ;
        		Arrayclass ( int n);
        		Arrayclass ( Arrayclass <DT>& A);
        		
        		DT & operator [] (int i);
        		Arrayclass <DT>& operator = ( Arrayclass <DT>& B);
        		~ Arrayclass ();
        };
        ```
        
2. **Simple Bucket Sort**:
    
    - **Task**: Write the algorithm for Bucket Sort and describe its time complexity.
    
    - answer
        
        ```C++
        void bucketSort(float arr[], int n) {
            std::vector<float> buckets[n];
        
            for (int i = 0; i < n; i++) {
                int bucketIndex = n * arr[i];  // Finding the appropriate bucket
                buckets[bucketIndex].push_back(arr[i]);
            }
        
            for (int i = 0; i < n; i++) {
                std::sort(buckets[i].begin(), buckets[i].end());  // Sorting individual buckets
            }
        
            int index = 0;
            for (int i = 0; i < n; i++) {
                for (int j = 0; j < buckets[i].size(); j++) {
                    arr[index++] = buckets[i][j];
                }
            }
        }
        ```
        
        Time complexity : **O(n + k)**, where k is the number of buckets.
        
3. **Merging Algorithm**:
    
    - **Task**: Given two sorted arrays, write an algorithm to merge them into a single sorted array.
    
    - answer
        
        ```C++
        void merge(int arr1[], int size1, int arr2[], int size2, int merged[]) {
            int i = 0, j = 0, k = 0;
            while (i < size1 && j < size2) {
                if (arr1[i] < arr2[j]) {
                    merged[k++] = arr1[i++];
                } else {
                    merged[k++] = arr2[j++];
                }
            }
        
            while (i < size1) {
                merged[k++] = arr1[i++];
            }
        
            while (j < size2) {
                merged[k++] = arr2[j++];
            }
        }
        ```
        
4. **Binary Search Algorithm**:
    
    ```C++
    int binarySearch(int arr[], int size, int key) {
        // Write the binary search algorithm here
    }
    ```
    
    - **Task**: Implement the binary search algorithm.
    
    - answer
        
        ```C++
        int binarySearch(int arr[], int size, int key) {
            int low = 0, high = size - 1;
            while (low <= high) {
                int mid = low + (high - low) / 2;
                if (arr[mid] == key) return mid;
                else if (arr[mid] < key) low = mid + 1;
                else high = mid - 1;
            }
            return -1;  // Not found
        }
        ```
        
5. **Matrix Storage Methods**:
    
    - **Task**: List the different ways a matrix can be stored, and provide an example of Row Major and Column Major ordering.
    
    - answer
        
        - **Row Major Ordering**: Stores matrix data row by row in memory.
        
        ```C++
        int matrix[3][3] = {1, 2, 3, 4, 5, 6, 7, 8, 9};
        
        { 1 , 2 , 3 ,
          4 , 5 , 6 , 
          7 , 8 , 9 } 
        ```
        
        - **Column Major Ordering**: Stores matrix data column by column in memory.
        
        ```C++
        int matrix[3][3] = {1, 4, 7, 2, 5, 8, 3, 6, 9};
        
        { 1 , 2 , 3 ,
          4 , 5 , 6 , 
          7 , 8 , 9 } 
        ```
        
        - **C++ Matrix**: Represents a matrix using a two-dimensional array in C++.
        - **ArrayClass of ArrayClass Objects**: A matrix where each row is represented as an instance of `ArrayClass`.
        - **Sparse Matrix Representation**: A matrix where most elements are zero, stored efficiently by only keeping track of non-zero elements.
        - Compressed sparse row

---

### **Chapter 4: Linked Lists**

1. **C++ class definition of a LinkedList**:
    
    ```C++
    class LinkedList {
    private:
        struct Node {
            int data;
            Node* next;
        };
        Node* head;
    public:
        LinkedList() : head(nullptr) {}
        ~LinkedList();
        void add(int value);   // implement
        void remove(int value);// implement
        int infoAt(int index); // implement
    };
    
    ```
    
    - **Task**: Complete the `LinkedList` class by implementing the destructor, `add`, `remove`, and `infoAt` functions.
    
    - answer
        
        ```C++
             void add(int value) {
                Node* newNode = new Node(value);
                newNode->next = head;
                head = newNode;
            }
        
            void remove(int value) {
                Node* current = head;
                Node* prev = nullptr;
                while (current != nullptr && current->data != value) {
                    prev = current;
                    current = current->next;
                }
                if (current != nullptr) {
                    if (prev == nullptr) {
                        head = current->next;
                    } else {
                        prev->next = current->next;
                    }
                    delete current;
                }
            }
        
            int infoAt(int index) {
                Node* current = head;
                int count = 0;
                while (current != nullptr) {
                    if (count == index) return current->data;
                    count++;
                    current = current->next;
                }
                throw std::out_of_range("Index out of range");
            }
        ```
        
2. **Implement a Linked List using an array.**
    
    - **Task**: Write a C++ class to support operations like adding and removing elements.
    
    - **Solution**:
        
        ```C++
        class ArrayLinkedList {
        private:
            int* data;
            int* next;
            int head;
            int size;
            int capacity;
        
        public:
            ArrayLinkedList(int cap) : head(-1), size(0), capacity(cap) {
                data = new int[capacity];
                next = new int[capacity];
                for (int i = 0; i < capacity; i++) {
                    next[i] = -1;  // Initialize all nodes as unlinked
                }
            }
        
            void add(int value) {
                if (size == capacity) throw std::overflow_error("List is full");
                data[size] = value;
                next[size] = head;
                head = size;
                size++;
            }
        
            void remove(int value) {
                int prev = -1, current = head;
                while (current != -1 && data[current] != value) {
                    prev = current;
                    current = next[current];
                }
                if (current != -1) {  // Found the value
                    if (prev == -1) {  // Deleting head
                        head = next[current];
                    } else {
                        next[prev] = next[current];
                    }
                    size--;
                }
            }
        
            ~ArrayLinkedList() {
                delete[] data;
                delete[] next;
            }
        };
        
        ```
        

  

1. **Explain the advantages and disadvantages of using an array implementation for a linked list.**
    
    - **Task**: Discuss how array size affects performance and memory usage.
    
    - **Solution**:
        - **Advantages**:
            - **Contiguous Memory Allocation**: Can lead to better cache performance.
            - **Simplicity**: Easier to implement for small, fixed-size lists.
        - **Disadvantages**:
            - **Fixed Size**: Once created, the size cannot be changed, leading to wasted space if not fully utilized or overflow if exceeded.
            - **Inefficient Deletions**: Requires shifting elements to maintain order when deleting, which can be costly.
2. **Write a C++ class to implement a Circular Linked List.**
    
    - **Task**: The class should allow adding elements in a circular manner.
    
    - **Solution**:
        
        ```C++
        cpp
        Copy code
        class CircularLinkedList {
        private:
            struct Node {
                int data;
                Node* next;
                Node(int value) : data(value), next(nullptr) {}
            };
            Node* head;
        public:
            CircularLinkedList() : head(nullptr) {}
        
            void add(int value) {
                Node* newNode = new Node(value);
                if (!head) {
                    head = newNode;
                    head->next = head;
                } else {
                    Node* temp = head;
                    while (temp->next != head) {
                        temp = temp->next;
                    }
                    temp->next = newNode;
                    newNode->next = head;
                }
            }
        
            ~CircularLinkedList() {
                if (!head) return;
                Node* current = head;
                do {
                    Node* nextNode = current->next;
                    delete current;
                    current = nextNode;
                } while (current != head);
            }
        };
        
        ```
        
3. **Describe the differences between a singly linked list, a doubly linked list, and a circular linked list.**
    
    - **Task**: Compare their structures and typical use cases.
    
    - **Solution**:
        - **Singly Linked List**:
            - **Structure**: Each node contains data and a pointer to the next node.
            - **Use Case**: Simple operations, less memory overhead.
        - **Doubly Linked List**:
            - **Structure**: Each node contains data, a pointer to the next node, and a pointer to the previous node.
            - **Use Case**: Easier to traverse in both directions, useful for complex data structures (e.g., deques).
        - **Circular Linked List**:
            - **Structure**: Similar to a singly or doubly linked list but the last node points back to the head.
            - **Use Case**: Useful for circular buffering and round-robin scheduling.

---

### **Chapter 5: Stacks and Queues**

1. **Write a C++ class to implement a Stack that handles exceptions when the stack is full or empty.**
    
    - **Task**: The class should support `push`, `pop`, and `peek` operations with exception handling.
    
    - **Solution**:
        
        ```C++
        cpp
        Copy code
        template<typename T>
        class Stack {
        private:
            T* arr;
            int top;
            int capacity;
        
        public:
            Stack(int size) : capacity(size), top(-1) {
                arr = new T[size];
            }
        
            void push(T value) {
                if (top == capacity - 1) throw std::overflow_error("Stack overflow");
                arr[++top] = value;
            }
        
            T pop() {
                if (top == -1) throw std::underflow_error("Stack underflow");
                return arr[top--];
            }
        
            T peek() const {
                if (top == -1) throw std::underflow_error("Stack is empty");
                return arr[top];
            }
        
            ~Stack() {
                delete[] arr;
            }
        };
        
        ```
        
2. **Compare the performance of stack implementations using an array versus a linked list.**
    
    - **Task**: Discuss the trade-offs in terms of time complexity and memory usage.
    
    - **Solution**:
        - **Array Implementation**:
            - **Performance**: O(1) for push/pop operations due to direct indexing.
            - **Memory Usage**: Wastes space if the stack isn’t full (fixed size).
        - **Linked List Implementation**:
            - **Performance**: O(1) for push/pop operations due to pointer manipulation.
            - **Memory Usage**: More memory overhead per element due to storing pointers, but no wasted space.
3. **Write the algorithm to convert an infix expression to a postfix expression.**
    
    - **Task**: Implement the conversion algorithm.
    
    - **Solution**:
        
        ```C++
        cpp
        Copy code
        \#include <iostream>#include <stack>#include <string>int precedence(char op) {
            if (op == '+' || op == '-') return 1;
            if (op == '*' || op == '/') return 2;
            return 0;
        }
        
        std::string infixToPostfix(const std::string& infix) {
            std::stack<char> operators;
            std::string postfix;
            for (char ch : infix) {
                if (std::isdigit(ch) || std::isalpha(ch)) {
                    postfix += ch;
                } else if (ch == '(') {
                    operators.push(ch);
                } else if (ch == ')') {
                    while (!operators.empty() && operators.top() != '(') {
                        postfix += operators.top();
                        operators.pop();
                    }
                    operators.pop();
                } else {
                    while (!operators.empty() && precedence(operators.top()) >= precedence(ch)) {
                        postfix += operators.top();
                        operators.pop();
                    }
                    operators.push(ch);
                }
            }
        
            while (!operators.empty()) {
                postfix += operators.top();
                operators.pop();
            }
        
            return postfix;
        }
        
        ```
        
4. **Write an algorithm to evaluate a postfix expression.**
    
    - **Task**: Implement the evaluation algorithm.
    
    - **Solution**:
        
        ```C++
        cpp
        Copy code
        \#include <iostream>#include <stack>#include <string>int evaluatePostfix(const std::string& postfix) {
            std::stack<int> s;
            for (char ch : postfix) {
                if (std::isdigit(ch)) {
                    s.push(ch - '0');
                } else {
                    int val2 = s.top(); s.pop();
                    int val1 = s.top(); s.pop();
                    switch (ch) {
                        case '+': s.push(val1 + val2); break;
                        case '-': s.push(val1 - val2); break;
                        case '*': s.push(val1 * val2); break;
                        case '/': s.push(val1 / val2); break;
                    }
                }
            }
            return s.top();
        }
        
        ```
        
5. **Implement a Circular Queue in C++.**
    
    - **Task**: The class should support `enqueue`, `dequeue`, and exception handling.
    
    - **Solution**:
        
        ```C++
        cpp
        Copy code
        template<typename T>
        class CircularQueue {
        private:
            T* arr;
            int front;
            int rear;
            int size;
            int capacity;
        
        public:
            CircularQueue(int cap) : capacity(cap), front(-1), rear(-1), size(0) {
                arr = new T[capacity];
            }
        
            void enqueue(T value) {
                if (size == capacity) throw std::overflow_error("Queue is full");
                if (front == -1) front = 0;
                rear = (rear + 1) % capacity;
                arr[rear] = value;
                size++;
            }
        
            T dequeue() {
                if (size == 0) throw std::underflow_error("Queue is empty");
                T value = arr[front];
                front = (front + 1) % capacity;
                size--;
                return value;
            }
        
            ~CircularQueue() {
                delete[] arr;
            }
        };
        
        ```
        
6. **Explain the advantages and disadvantages of using a circular queue.**
    
    - **Task**: Discuss how it efficiently utilizes space compared to a linear queue.
    
    - **Solution**:
        - **Advantages**:
            - **Efficient Space Utilization**: Utilizes all available space by wrapping around when the end of the array is reached.
            - **No Wasted Space**: Unlike linear queues, which may waste space when elements are dequeued.
        - **Disadvantages**:
            - **Complexity**: More complex to implement due to the need for managing wraparounds.
            - **Fixed Size**: Still has a fixed capacity, leading to potential overflows if not managed correctly.