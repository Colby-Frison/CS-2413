Main topics 
- Encapsulation
- Inheritance
## Goals of OOP
- **Isolate sections of code**, this allows errors and bugs to be easily tracked down
	- By having numerous methods errors will mostly stay in that given section
- **Errors and bugs** in one section **will not propagate** to others
	- Not entirely true as if methods are called in other methods it will carry errors, then the error will have to be tracked down
	- But none the less the root of the error is easier to track down
- To allow and encourage **reuse of code**
	- by having sub methods instead of just one function that does everything it not only makes the file smaller (less lines) but it also greatly improves the readability of the code
- To **simplify the programmer's task** and **reduce the memory load**
	- by creating methods the programmer doesn't need to write as much and there are less lines which decreases memory usage as said earlier
- Another goal not mentioned in the source material is **to create modular code**
	- In other words by OOP the code can easily be expanded on or simplified based on the task. This is very useful when new features needed to be added or removed, as it is simply adding a few methods instead of rewriting the whole file
## Encapsulation 
- **Encapsulation** refers to the bundling of data with the mechanisms or methods that operate on the data. 
	- In other words data is kept private (or hidden) within the given object, with the only way to access said data is through certain methods put in place to ensure the data is accessed or modified properly.
	- In other words: If all accesses to certain data must pass through a specified interface, **improper accesses can be prevented.**
- It may also refer to the limiting of direct access to some of that data, such as an object's components. 
	- This ensures crucial components of the object remain intact
	- This is especially useful in certain data structures where the data is modified in very specific ways
- Essentially, encapsulation prevents external code from being concerned with the internal workings of an object.
	- In other words the class can radically change its implementation without having to worry about disrupting the inner workings of the object
- Encapsulation also encourages programmers to put all the code that is concerned with a certain set of data in the same class, which organizes it for easy comprehension by other programmers. 
	- Encapsulation is a technique that encourages [decoupling](https://en.wikipedia.org/wiki/Coupling_(computer_programming) "Coupling (computer programming)").
	- Coupling is basically how interconnected things are, by using encapsulation decoupling is encouraged, which is restricting errors from spreading through the entire program.

Note:
- All [object-oriented programming](https://en.wikipedia.org/wiki/Object-oriented_programming "Object-oriented programming") (OOP) systems support encapsulation, but encapsulation is not unique to OOP. Implementations of [abstract data types](https://en.wikipedia.org/wiki/Abstract_data_types "Abstract data types"), [modules](https://en.wikipedia.org/wiki/Module_(programming) "Module (programming)"), and [libraries](https://en.wikipedia.org/wiki/Library_(computing) "Library (computing)") also offer encapsulation. The similarity has been explained by programming language theorists in terms of [existential types](https://en.wikipedia.org/wiki/Existential_types "Existential types").
### Encapsulation in Real Life
- One (kinda vague) example of  encapsulation in real life is with cars, as for the most part they have a specified and unchanging interface
- So basically the interface to interact with a car is always the same, as it allows everyone to interact with the car without having to work with the underlying mechanics of the car
	- There are always an accelerator and brake, and they always have the same function
- Even in vehicles that have slightly different underlying mechanics the interfaces do the same thing
	- Electric and combustion
	- Rear engine and front/mid engine
	- steering column and drive by wire
### Encapsulation in C++
- The language **C++ provides several flexible schemes** to implement information hiding
- Class members  (fields and methods) can be defined to be **public , private, or protected.**
	- Members defined as **public** <u>are visible</u> (that can be accessed) <u>to everyone</u> that operates the object.
	- Members declared **private** are <u>truly encapsulated</u> and hence <u>not visible</u> to the outside
	- Members declared **protected** are <u>visible only to methods defined in the class</u> and to methods in its subclass
## Inheritance
- Inheritance is a mechanism for **allowing code reuse in a controlled and efficient manner.**
	- This once again increases readability of code whilst also increasing efficiency for the programmer as they won't have to rewrite the same thing multiple times
- The main way this is done is by **allowing the extension of classes**; a class can be written to solve a generic problem, then this class can be extended by a subclass to handle the smaller quirks of a particular problems without changing the original code.
	- Along with that a subclass can have more than one parent class to achieve a more niche inheritance
- A subclass (aka. descendant class, derived class, or child class) inherits all behavior of the class (aka base class, parent class, or superclass of the subclass), except those parts that it must modify to handle its particular problem.
- Along with that each subclass can form its own subclass creating a deep hierarchy for any particular reason
- Additionally a subclass can have multiple parent classes in order to
### Inheritance in Real Life
- Using the car example again automobiles would be the class, and the different types of cars as the subclasses (station wagons, sports cars, pickup trucks, sedan, and so on)
	- In all of these examples of cars they all have steering wheels, accelerators, and brakes
	- On the other hand all of the cars are different shapes, have different kinds of engine, maybe different transitions, and other smaller changes

- For the case of **multiple inheritance**, an example is something like Teslas
	- They inherit the features from a car such as the pedals and the steering wheel, but they also inherit the self driving features
	- This isn't a great example, but you get the idea
### Inheritance in C++
- subclasses are defined as follows
``` c++
class ColorPoint:public Point
```
- To declare that a class is a subclass of some class, we simply follow the class identifier with a colon, the word “public” and the identifier for the superclass/parent class
### Overriding
- Another important concept  of inheritance is that a subclass cannot merely inherit, but also override, its superclass' methods
	- This is important as certain methods may have slightly different implementations so changing them slightly is important 
- To override the superclass' method, the subclass must declare a method with the exact same identifier, parameter, and return type, while also giving a different method body. Moreover, the method must be flagged as **virtual** in the superclass
	- So the method cannot be overridden unless its marked as "overridable", which is done through the virtual tag on the parent method

- When the subclass doesn't want to override the superclass' method it can simply call it by doing the following operation
```c++
void SubClass::exampleMethod() {
	SuperClass::exampleMethod();
}
```
- In this example subclass and superclass are just placeholder names, but its literally just making making a method to call a method
### Changing Access Restrictions
- When overriding a method, the subclass can also change its access restriction, but only in the **direction of increasing visibility.**
	- For example: if the superclass declared MethodA() to be protected, the subclass can declare MethodA() to be public, but cannot declare it to be private
### constructor for subclasses
- constructor syntax:
```c++
subClass::subClass(parameters):superClass(superclass parameters) {
constructor bosy
}
```
- The constructor body then only contains the assignment for the parameters passed in the subclass parameters. The superclass parameter's are handled by the superclass

Not complete yet I got lazy