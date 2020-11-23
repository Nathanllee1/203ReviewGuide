# 202 Final Review

Made with ❤️ by Nathan Lee

[toc]



# Week 1

## Java Language 

Java is compiled while python is interpreted

Java runs on top of a virtual machine

Creates a ```.class``` file when compiled

Variables are type checked

Primitive types are checked with ```=``` while reference types are checked with ``.equal()``



## Switch

```java
int month = 8;
String monthString;switch (month) {
    case 1:  monthString= "January";
        break;
    case 2:  monthString= "February";
        break;
    case 3:  monthString= "March";
        break;
    case 4:  monthString= "April";
        break;
    case 5:  monthString= "May";
        break;
    case 6:  monthString= "June";
        break;
    default:  monthString= “Invalid month";
        break;
}
```

And: ``&&``

Or: ``||``

Not: ``!	``



## Arrays

Initialize Array:

```java
double[] values = new double[10];
double[] initValues = { 32, 54, 32, 4};
```

Access Array:

```java
initValues[32];
```

Number of Values:

```java
initValues.length
```



## Array List

Initialize ArrayList:

```java
ArrayList<String> friends = new ArrayList<String>();
ArrayList<String> friendsInit = new ArrayList<String>(Arrays.asList("Bella", "Elijah"));
```

Access Array:

```Java
friendsInit.get(4);
```

Number of Values:

```java
friendsInit.size()
```



## HashMap

Initialize HashMap:

```java
Map <String, Integer> vehichles = new HashMap<>();
vehicles.put("BMW", 6);
```

Access HashMap:

```java
vehicles.get(searchKey); // Returns Value
vehicles.contains(searchKey); // Returns Boolean
```



## Casting

ex: ```(int) (balance *100)```

# Week 2

## UML Diagrams

![image-20201122193929487](/home/nathanlee/.config/Typora/typora-user-images/image-20201122193929487.png)

| Rectangle                                 |
| ----------------------------------------- |
| -length: double<br />-width: double       |
| +setLength(): void<br />+setWidth(): void |

"+" represents public and "-" represents private



## Constructors

+ Called when an object is created
+ Usually initializes instance fields
+ Have no return type
+ A default constructor is used by java when no constructor is provided, setting all numeric fields to ``0``, booleans to ``false``, and reference variables to ``null``



## Overloading Methods

When two methods have the same name

+ Can have different inputs and functionality

```java
public int add(int num1, int num2){
    int sum = num1 + num2;return sum;
}

public String add (String str1, String str2){
    String combined = str1 + str2;
    return combined;
}
```



## Static Methods and Fields

+ Do not belong to a single instance of a class
+ Use the class name to use the method

```java
double val = Math.sqrt(25.0);
```



## "This"

```java
public Student(String name, String major, intyear, doublegpa)   {
    //Explicitly	   //Implicitly
    this.name = name;  //name = name;
    this.major= major; //major = major;
    this.years= year;  //years = year;
    this.gpa= gpa;     //gpa= gpa; 
}
```

```java
Student st = new Student ("Joe", "CSC", 3.75, 3);
```



## Packages and Import Statements

Explicit

```java
import java.util.Scanner;
```

Wildcard

```java
import java.util.*;
```



## Garbage Collection

+ When objects aren't used, they're deleted to free up memory
+ The finalize method is a method that you can override that gets run when the garbage collector gets rid of the class



## Casting

ex: ```(int) (balance *100)```



## Equals Method

```java
@Override
public boolean equals(Object o) {
    // If the object is compared with itself then return true   
    if (o == this) { 
        return true; 
    } 

    /* Check if o is an instance of Complex or not 
      "null instanceof [type]" also returns false */
    if (!(o instanceof Complex)) { 
        return false; 
    } 

    // typecast o to Complex so that we can compare data members  
    Complex c = (Complex) o; 

    // Compare the data members and return accordingly  
    return Double.compare(re, c.re) == 0 && Double.compare(im, c.im) == 0; 
}
```

# Week 3

## Refactoring

+ Restructuring code
+ The code has to **not** have removed or added any functionality
+ Eliminates duplicates, makes design logic clear

## Random

https://www.geeksforgeeks.org/generating-random-numbers-in-java/ 

### Generate Random Number

```java
import java.util.Random; 
Random rand = new Random(); 

int rand_int1 = rand.nextInt(1000); // Random ints from 0 to 1000
double rand_dub1 = rand.nextDouble(); // Double version
```



## File I/O

### Read from a file

```java
//construct the reading and writingFile 
File inFile= new File(inputFileName);
Scanner in = new Scanner(inFile);
//read from file
while(in.hasNextDouble()) {
    // do something
}//while
in.close();
```

### Write to a file

```java
PrintWriter out = new PrintWriter(fileName);
out.println("Test String");
out.close();
```



## Interfaces

An interface declares methods that classes that implement it **must** include

+ Interfaces **can not** extend another interface

+ A class **can** have multiple interfaces

  

  Uses a dashed line in UML

```java
public interface InterfaceName {
    static final int = 5; // Instance variables must be static and final
    
    void method(int input);
    void method2(double val);
    
    default boolean itworks (int n) { // Can also have "default" variables
        if (n > 5) {
            return true;
        }
    }
}
```

```java
TestClass d = new TestClass(); // Test Class implements above interface
d.itworks(3); // Can be called fairly normally
```

https://www.geeksforgeeks.org/default-methods-java/

# Week 4

## Binding

https://www.geeksforgeeks.org/static-vs-dynamic-binding-in-java/

**Dynamic Binding**: uses the object that's the value to determine how to use that object

```java
Object p1 = new Point(2, 3);
p1.getX();
```



**Static Binding**: uses the type to determine how to use that object

```java
Point p2 = new Point(3, 4);
p2.getX();
```



+ **Static binding** happens during **compile time**
+ **Dynamic binding** happens during **run time**

+ **Static binding** uses **types** to resolve binding
+ **Dynamic binding** uses **objects** to resolve binding

+ **Static binding** is resolved with **overloads**



## Coupling and Cohesion

+ **Cohesion** is how well class members relate to each other
+ **Coupling** is how well classes in a project/application relate to each other
+ Good Object Oriented program has **high cohesion** and **loose coupling**

### High Cohesion

```java
class ObjectInformation {
    public String getObjectClassName(Object o) { return... }
    public String getObjectSuperclassName(Object o) { return... }
    public ArrayList<String> getObjectFields(Object o){ return..}
    public ArrayList<String> getObjectConstructors(Object o) { return... }
}
```

Methods relate to each other

### Loose Coupling

```java
public class Car  {
    public void move() {
        System.out.println("Car is moving");
    }
}

class Traveler {
    Car c = newCar();
    public void startTravel() {
        c.move();
    }
}
```

Classes are loosely connected

# Week 5

## Hash Code Method

+ An integer number associated with each object
+ Used as a more memory efficient identifier

### Overriding a hash code method

```java
@override
public int hashCode() {
   int result;
   for (int i = 0; i<lenthg(); i++ ) {
       hash = 31 * hash + charAt(i);
   }
   return hash;
}
```



## Polymorphism

+ "Many forms"
+ Good example is overriding, you can have something with the same name but different functionality

In overloading, the compiler picks it by 

1. Exact Match
2. Closet is-a relationship
3. Whether it can be converted



## Lambda Expressions

+ Unnamed chunk of code
+ Defines parameters and return value really compact

### Iterating through an array

```java
students.forEach((n) -> {if (n.name().equals("Nathan") {System.out.println(n)}})
```

### Predicate

```java
Predicate<Student> pred= (Student s) -> s.getGpa() > 3.0;
filtered = filterIt(students, pred);
printList(filtered);
```

# Week 6

## Inheritance

Uses ``extends`` keyword 

```java
public class Grasshopper extends Insect {}
```

Forms a **"is-a" relationship**

Subclasses inherit methods and instance variables



### Super

The ``super`` keyword allows variables to be passed to the parent class

```java
class SubClass extends SuperClass {
    two;
    public SubClass(one, two) {
        super(one);
        this.two = two;          
    }
}
```

If you do that, you can call the parent's methods and the variables will be properly filled out

A subclass can also call an overridden super class method

```java
super.setScore(34) // An example method
```

The ``final`` modifier prevents a method from being overridden.

### Protected

The ``protected`` keyword allows methods to be accessed by the subclass and int he same package



### Access Modifier Table

| Access Modifier | Accessible to a subclass inside the same package? | Accessible to all other classes inside the same package |
| --------------- | ------------------------------------------------- | ------------------------------------------------------- |
| default         | Yes                                               | Yes                                                     |
| Public          | Yes                                               | Yes                                                     |
| Protected       | Yes                                               | Yes                                                     |
| Private         | No                                                | No                                                      |

| Access Modifier | Accessible to a subclass outside the package? | Accessible to all other classes outside the package? |
| --------------- | --------------------------------------------- | ---------------------------------------------------- |
| default         | No                                            | No                                                   |
| Pulbic          | Yes                                           | Yes                                                  |
| Protected       | Yes                                           | No                                                   |
| Private         | No                                            | No                                                   |



## Abstract Classes and Methods

### Abstract Classes

```java
public abstract class ClassName
```

+ Cannot be instantiated, but can be sub classed

### Abstract Methods

```java
public abstract ReturnType method();
```

+ Similar to interface methods, abstract methods have no body and must be implemented by subclasses

# Week 7

## Generic and Bounding Types

Allows a method or class to be able to handle multiple types

### Generic Classes

```java
public class GenericsType<T> {
    privateT t;
    publicT get() {
        returnthis.t;
    }
    public void set(T t1){
        this.t=t1;}
}
```

Generic classes allow you to specify the types of all the methods in a class, makes casting in the class easier

### Generic Methods

```java
public static<E> void method(E[] inArray) {...}

className.method<Int>(intArray);
```

The method above can take multiple types of array as E

### Generic Interfaces

```java
public interface Comparable<T> {
	publicintcompareTo(T o);
}
```



## Sorting

### Natural Ordering / compareTo

Allows you to sort methods according to "natural order"

A - Z, 1 - 10

```java
public class BookInventory  implements Comparable<BookInventory> {

  // code

  public int compareTo(BookInventory other){
    return bookTitle.compareTo(other.bookTitle);
  }
  // Should return < 0 if the current object is before the passed object
  // Should return a 0 if the objects are the same
  // Should return  > 0 if the current object is after the passed object

  //code
}
```



## Comparators

Allows you to sort however specified

```java
Comparator<Type> comp = Comparator.comparing(Type::getMethod);

comp.compare(Obj1, Obj2);
```

Can use the ``compareTo`` method, lambda expressions, and key extractors (shown above)

# Week 8

## Depth First Search

Follow first priority until can't, then second, etc



## A* Algorithm

**G Value**: Distance From Start (via current path)

**H Value**: Distance to End Point. Also known as the heuristic (uses Euclidean distance since real path isn't known)

**F Value**: Sum of G and H

### A* Pseudocode

```java
// A* (star) Pathfinding
// Initialize both open and closed list
let the openList equal empty list of nodes
let the closedList equal empty list of nodes
// Add the start node
put the startNode on the openList (leave its f at zero)
// Loop until you find the end
while the openList is not empty
    // Get the current node
    let the currentNode equal the node with the least f value
    remove the currentNode from the openList
    add the currentNode to the closedList
    // Found the goal
    if currentNode is the goal
        Congratz! Youve found the end! Backtrack to get path
    // Generate children
    let the children of the currentNode equal the adjacent nodes
    
    for each child in the children
        // Child is on the closedList
        if child is in the closedList
            continue to beginning of for loop
        // Create the f, g, and h values
        child.g = currentNode.g + distance between child and current
        child.h = distance from child to end
        child.f = child.g + child.h
        // Child is already in openList
        if child.position is in the openLists nodes positions
            if the child.g is higher than the openList node's g
                continue to beginning of for loop
        // Add the child to the openList
        add the child to the openList
```

# Week 9

## File Streams

### Write a string

```java
String name = "Chloe";
File outputFile = new File(fileName);
outputFile.writeUTF(name);
```

### Read String

```java
String name = inputFile.readUTF();
```

**Note:** Look at your lab 8 for a better implementation of this



## Java Streams (Completely unrelated to file streams!)

### Filter (``.filter``)

```java
List<Shape> shapeStream = shapes.stream()
    .filter(s-> s.area() >= 5.87)
    .collect(Collectors.toList()); // Turns the stream back into a list
```

### Get Attributes (``.map``)

```java
double averagePerim = shapes.stream()
    .map(shapes::perimeter)
    .average();
```

### Sort (``.sorted``)

```java
List<Shape> sortedShape = shapes.stream()
    .sorted(Comparator.comparing(Shape::area))
    .collect(Collectors.toList());
```



## Design Patterns

Completely honestly, I have no idea what or why she went over this so 🤷

# Week 10

## Exception

### Try Catch Statement

```java
try {
	something that could fail
} catch(Exception e) {
    System.out.println(e)
}
```



You can also make your own exception

```java
throw new Exception_Name("Message")
```



You can also catch an exception at method level

```java
public void someMethod() throwsIOException {...}
```

Try not to do this



### Unchecked vs Checked Exception

**Unchecked:** during runtime, such as a file not existing

**Checked:** happens during compile time and has to be handled with a try catch or write ``throws``

All Exceptions are checked, unless they're runtime