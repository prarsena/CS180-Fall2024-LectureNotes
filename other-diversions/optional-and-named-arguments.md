### Java
Java doesn't support optional or named arguments for methods by default. When I'm elected president of Java, I will correct this. 

This is annoying because when using overloaded Methods and Class Constructors, you must write each supported constructor individually and you must provide the arguments in the correct order! Plus, the Java compiler may get confused if you have multiple methods with the same signature (same data types). Here's an example of how verbose creating a Person could be:

```java
public class Person {
    private String firstName;
    private String lastName;
    private int age;
    private String address;

    // Constructor with all parameters
    public Person(String firstName, String lastName, int age, String address) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
        this.address = address;
    }

    // Constructor with three parameters (no address)
    public Person(String firstName, String lastName, int age) {
        this(firstName, lastName, age, "Unknown");
    }

    // Constructor with three parameters (no age)
    public Person(String firstName, String lastName, String address) {
        this(firstName, lastName, 0, address);
    }

    // Constructor with three parameters (no last name)
    public Person(String firstName, int age, String address) {
        this(firstName, "Unknown", age, address);
    }

    // Constructor with two parameters (firstName and lastName)
    public Person(String firstName, String lastName) {
        this(firstName, lastName, 0, "Unknown");
    }

    // Constructor with two parameters (firstName and age)
    public Person(String firstName, int age) {
        this(firstName, "Unknown", age, "Unknown");
    }

    // Constructor with two parameters (firstName and address)
    public Person(String firstName, String address) {
        this(firstName, "Unknown", 0, address);
    }

    // Constructor with one parameter (firstName)
    public Person(String firstName) {
        this(firstName, "Unknown", 0, "Unknown");
    }

    // Default constructor (no parameters)
    public Person() {
        this("Unknown", "Unknown", 0, "Unknown");
    }

    // Getters and setters...
}
```

Below are examples of how other languages support optional or named arguments for methods:
### Python

**Optional Arguments:** You can provide default values for parameters.

```python
def greet(name, message="Hello"):
    print(f"{message}, {name}!")

greet("Alice")  # Output: Hello, Alice!
greet("Bob", "Hi")  # Output: Hi, Bob!
```

**Named Arguments:** You can call functions using keyword arguments.

```python
def greet(name, message="Hello"):
    print(f"{message}, {name}!")

greet(name="Alice", message="Hi")  # Output: Hi, Alice!
greet(message="Hey", name="Bob")  # Output: Hey, Bob!
```

### Scala

**Optional Arguments:** You can define default values for parameters.

```scala
def greet(name: String, message: String = "Hello"): Unit = {
  println(s"$message, $name!")
}

greet("Alice")  // Output: Hello, Alice!
greet("Bob", "Hi")  // Output: Hi, Bob!
```

**Named Arguments:** You can call functions using named parameters.

```scala
greet(name = "Alice", message = "Hi")  // Output: Hi, Alice!
greet(message = "Hey", name = "Bob")  // Output: Hey, Bob!
```

### Swift

**Optional Arguments:** You can provide default values for parameters.

```swift
func greet(name: String, message: String = "Hello") {
    print("\(message), \(name)!")
}

greet(name: "Alice")  // Output: Hello, Alice!
greet(name: "Bob", message: "Hi")  // Output: Hi, Bob!
```

**Named Arguments:** You can call functions using named parameters.

```swift
greet(name: "Alice", message: "Hi")  // Output: Hi, Alice!
greet(message: "Hey", name: "Bob")  // Output: Hey, Bob!
```

### R

**Optional Arguments:** You can provide default values for parameters.

```r
greet <- function(name, message = "Hello") {
  cat(message, name, "!\n")
}

greet("Alice")  # Output: Hello Alice !
greet("Bob", "Hi")  # Output: Hi Bob !
```

**Named Arguments:** You can call functions using named parameters.

```r
greet(name = "Alice", message = "Hi")  # Output: Hi Alice !
greet(message = "Hey", name = "Bob")  # Output: Hey Bob !
```

### Kotlin

**Optional Arguments:** You can provide default values for parameters.

```kotlin
fun greet(name: String, message: String = "Hello") {
    println("$message, $name!")
}

greet("Alice")  // Output: Hello, Alice!
greet("Bob", "Hi")  // Output: Hi, Bob!
```

**Named Arguments:** You can call functions using named parameters.

```kotlin
greet(name = "Alice", message = "Hi")  // Output: Hi, Alice!
greet(message = "Hey", name = "Bob")  // Output: Hey, Bob!
```


### Java workaround for Optional Input Parameters
There is a class introduced to the Java API in Java 8 called Optional. 
