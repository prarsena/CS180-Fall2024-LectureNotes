
## Bonus: Data Hiding: Why are Object fields private?
In Java, object class fields are typically made private to adhere to the principle of **encapsulation**, which is a fundamental concept in object-oriented programming. Here are a few reasons why this is important:

1. **Data Hiding**: By making fields private, you prevent direct access to them from outside the class. This helps protect the internal state of the object from unintended or harmful modifications.
    
2. **Controlled Access**: Private fields can only be accessed and modified through public methods (getters and setters). This allows you to control how the data is accessed and modified, ensuring that any necessary validation or processing is performed.
    
3. **Maintainability**: Encapsulation makes it easier to change the internal implementation of a class without affecting other parts of the code that rely on it. You can modify the private fields and the methods that access them without worrying about breaking external code.
    
4. **Improved Debugging**: When fields are private, you can more easily track and control how and when they are accessed or modified, which can simplify debugging and troubleshooting.
    
5. **Enhanced Security**: By restricting access to the fields, you reduce the risk of accidental or malicious interference with the object's state.

The difference between directly accessing a private field value and getting a private field using a method (like a getter) lies in the principles of encapsulation and control over the data. Here's a breakdown:

### Direct Access (Not Recommended)

Directly accessing a private field value is generally not allowed in Java because private fields are not accessible outside their class. This is by design to enforce encapsulation. If you try to access a private field directly from outside the class, you'll get a compilation error.

### Using a Getter Method (Recommended)

A getter method is a public method that provides controlled access to a private field. Here's why using a getter is beneficial:

1. **Encapsulation**: It maintains the principle of encapsulation by hiding the internal representation of the object.
2. **Control**: It allows you to control how the field is accessed. For example, you can add logic to the getter method to return a computed value or to log access.
3. **Validation**: You can include validation logic within the getter to ensure the field's value is appropriate before returning it.
### Example: Direct access vs. using a Getter method

Here's a simple example to illustrate the difference:

```java
public class Person {
    // Private field
    private String name;

    // Getter method
    public String getName() {
        return name;
    }

    // Setter method
    public void setName(String name) {
        this.name = name;
    }
}

public class Main {
    public static void main(String[] args) {
        Person person = new Person();
        person.setName("Alice");

        // Direct access (not allowed)
        // System.out.println(person.name); // This will cause a compilation error

        // Access via getter method (allowed)
        System.out.println(person.getName()); // This will print "Alice"
    }
}
```

In this example, the `name` field is private and cannot be accessed directly from outside the `Person` class. Instead, you use the `getName()` method to access the value of `name`.