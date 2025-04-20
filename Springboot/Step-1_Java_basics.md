
# Java Basic Interview Questions
 ## Q1. What is Java?
Java is a high-level, class-based, object-oriented programming language that is designed to have as
few implementation dependencies as possible. It is a widely used language for developing
applications for web, mobile, and desktop platforms.
Q2. What are the features of Java?
Key features of Java include platform independence, object-orientation, security, robustness,
simplicity, multithreading support, and garbage collection.
Q3. What is JVM and why is it important?
JVM stands for Java Virtual Machine, which is the part of the Java Run-time Environment that
executes Java byte code. It is important because it provides a platform-independent way of executing
Java code.
Q4. What is the difference between JDK, JRE, and JVM?
JDK (Java Development Kit) is the full software development kit required to develop Java
applications, JRE (Java Runtime Environment) is a subset of JDK that is required to run Java
applications, and JVM (Java Virtual Machine) is the component of JRE that executes Java bytecode.
Q5. What is the use of the public static void main(String[] args) method?
This method is the entry point for any Java application. It is the method called by the JVM to run the
program.
Q6. Explain the concept of Object-Oriented Programming in Java.
Object-Oriented Programming (OOP) in Java is a programming paradigm based on the concept of
"objects", which can contain data in the form of fields (attributes) and code in the form of
procedures (methods). Java uses OOP principles including inheritance, encapsulation, polymorphism,
and abstraction.
Q7. What is inheritance in Java?
Inheritance is a fundamental OOP concept where one class can inherit fields and methods from
another class. In Java, inheritance is achieved using the extends keyword.

Q8. What is polymorphism in Java?
Polymorphism in Java is the ability of an object to take on many forms. It is typically achieved
through method overriding and method overloading.
Q9. Explain encapsulation with an example in Java.
Encapsulation in Java is the bundling of data (variables) and methods that operate on the data into a
single unit, or class, and restricting access to some of the object's components. This is usually done
by making fields private and providing public getter and setter methods. For example:
public class Employee {
 private String name;
 public String getName() {
 return name;
 }
 public void setName(String newName) {
 this.name = newName;
 }
}
Q10. What is an interface in Java?
An interface in Java is a reference type, similar to a class, that can contain only constants, method
signatures, default methods, static methods, and nested types. Interfaces cannot contain instance
fields. The methods in interfaces are abstract by default.
Q11. Explain the concept of an abstract class.
An abstract class in Java is a class that cannot be instantiated and may contain abstract methods,
which do not have an implementation and must be implemented in subclasses.
Q12. What are constructors in Java?

Constructors in Java are special methods used to initialize objects. The constructor is called when an
object of a class is created and has the same name as the class.
Q13. What is method overloading?
Method overloading is a feature in Java that allows a class to have more than one method having the
same name, if their parameter lists are different. It is a way of implementing compile-time
polymorphism.
Q14. What is method overriding?
Method overriding, in Java, is a feature that allows a subclass to provide a specific implementation of
a method that is already provided by one of its super-classes or parent classes.
Q15. What is a package in Java?
In Java, a package is a namespace that organizes a set of related classes and interfaces. Conceptually,
packages are similar to different folders on your computer.
Q16. Explain the final keyword in Java.
The final keyword in Java can be used to mark a variable as constant (not changeable), a method as
not overrideable, or a class as not inheritable.
Q17. What are Java Exceptions?
Exceptions in Java are events that disrupt the normal flow of the program. They are objects that wrap
an error event that occurred within a method and are either caught or propagated further up the
calling chain.
Q18. What is the difference between checked and unchecked exceptions?
Checked exceptions are exceptions that are checked at compile-time, meaning that the code must
handle or declare them. Unchecked exceptions are checked at runtime, meaning they can be thrown
without being caught or declared.
Q19. What is the static keyword used for in Java?
The static keyword in Java is used to indicate that a particular field, method, or block of code belongs
to the class, rather than instances of the class. Static members are shared among all instances of a
class.

Q20. What is a thread in Java?
A thread in Java is a lightweight subprocess, the smallest unit of processing. Multithreading is a Java
feature that allows concurrent execution of two or more parts of a program for maximum utilization
of CPU.
Q21. Explain the difference between == and .equals() in Java.
In Java, == operator is used to compare primitive data types and checks if two references point to the
same object in memory. .equals() method is used to compare the contents of two objects.
Q22. What is garbage collection in Java?
Garbage collection in Java is the process by which Java programs perform automatic memory
management. Java programs compile to bytecode that is run on the Java Virtual Machine (JVM).
When objects are no longer in use, the garbage collector attempts to reclaim memory on the JVM for
reuse.
Q23. What is the Collections Framework in Java?
The Collections Framework in Java is a unified architecture for representing and manipulating
collections. All collections frameworks contain interfaces, implementations, and algorithms to help
Java programmers handle data efficiently.
Q24. Explain synchronized keyword in Java.
The synchronized keyword in Java is used to control the access of multiple threads to any shared
resource. It is used to prevent thread interference and consistency problems.
Q25. What are generics in Java?
Generics are a feature that allows you to write and use parameterized types and methods in Java.
Generics provide compile-time type safety that allows programmers to catch invalid types at compile
time.
Q26. What is the use of ‘this’ keyword in Java?
In Java, ‘this’ is a reference variable that refers to the current object. It can be used to refer current
class instance variable, invoke current class method, pass as an argument in the method call, pass as
argument in the constructor call, and return the current class instance.
Q27. What is Enum in Java?

Enum in Java is a data type that consists of a fixed set of constants. Enums are used to create our
own data types (Enumerated Data Types). It is used when we know all possible values at compile
time, such as choices on a menu, rounding modes, command line flags, etc.
Q28. What are threads?
In Java, threads are lightweight processes that allow a program to perform multiple tasks
simultaneously. Each thread runs a separate path of execution within the program. Java provides
built-in support for threads through the Thread class and the Runnable interface.
By using threads, you can improve the performance of applications by handling tasks such as
background operations, parallel processing, and asynchronous tasks more efficiently. Threads share
the same memory space, which makes communication between them easier but also requires
careful synchronization to avoid conflicts.
Q29. What is multithreading?
Multithreading in Java is a process of executing multiple threads simultaneously. Thread is a
lightweight sub-process, a smallest unit of processing. It allows the concurrent execution of two or
more parts of a program to maximize the utilization of CPU time.
Q30. Explain volatile keyword in Java.
The volatile keyword in Java is used to indicate that a variable's value will be modified by different
threads. Declaring a variable volatile ensures that its value is read from the main memory and not
from the thread's cache memory.