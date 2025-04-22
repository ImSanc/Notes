# Factory Method
A factory method in Java is a design pattern used to create objects without specifying the exact class of the object that will be created. Instead of using the new keyword directly in the client code, the object creation logic is encapsulated in a method — the factory method.


## 🔧 Definition
A factory method is a method that returns an instance of a class. It can:
 - Be part of a factory class, or
 - Be  a static method in the class itself.


# 🧠 Why use a factory method?
- Encapsulation of object creation: Hide complex creation logic from the user.
- Loose coupling: The client code depends on an interface or abstract class, not a specific implementation.
- Object reuse / Singleton / caching: Control instance creation (e.g., returning the same instance).
- Polymorphism at runtime: Return different subclasses depending on inputs.


# Example : 

    
    // Product interface
    interface Shape {
    void draw();
    }
    
    // Concrete implementations
    class Circle implements Shape {
    public void draw() {
    System.out.println("Drawing Circle");
    }
    }
    
    class Rectangle implements Shape {
    public void draw() {
    System.out.println("Drawing Rectangle");
    }
    }
    
    // Factory class
    class ShapeFactory {
    public static Shape getShape(String type) {
    if (type.equalsIgnoreCase("circle")) {
    return new Circle();
    } else if (type.equalsIgnoreCase("rectangle")) {
    return new Rectangle();
    }
    return null;
    }
    }
    
    // Client code
    public class Main {
    public static void main(String[] args) {
    Shape shape1 = ShapeFactory.getShape("circle");
    shape1.draw();  // Output: Drawing Circle
    
            Shape shape2 = ShapeFactory.getShape("rectangle");
            shape2.draw();  // Output: Drawing Rectangle
        }
    }


## Summary
Pattern name: Factory Method Pattern
Used for: Delegating object creation to a method
Benefits: Flexibility, encapsulation, and loose coupling