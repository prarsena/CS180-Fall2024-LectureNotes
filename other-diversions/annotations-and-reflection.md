## Java Annotations
[Annotations in Java Lang Specification.](https://docs.oracle.com/javase/specs/jls/se23/html/jls-9.html#jls-9.6)

```java

```
## Java Reflect
Reflection is a feature in the Java programming language. It allows an executing Java program to examine or "introspect" upon itself, and manipulate internal properties of the program. For example, it's possible for a Java class to obtain the names of all its members and display them.

The ability to examine and manipulate a Java class from within itself may not sound like very much, but in other programming languages this feature simply doesn't exist. For example, there is no way in a Pascal, C, or C++ program to obtain information about the functions defined within that program.

Reflect objects are in the [java/lang/reflect](https://github.com/openjdk/jdk/tree/master/src/java.base/share/classes/java/lang/reflect)  package.

```java
import java.lang.reflect.*;  
  
public class PrintClassMethods {  
	public static void main(String args[]){  
		try {  
			//Class c = Class.forName(args[0]);  
			Class c = Class.forName("java.lang.String");  
			Method m[] = c.getDeclaredMethods();  
			for (int i = 0; i < m.length; i++)  
			System.out.println(m[i].toString());  
		}  
		catch (Throwable e) {  
			System.err.println(e);  
		}  
	}  
}
```

Here's a prettier printed class:
```java
import java.lang.reflect.*;

public class method1 {
  private int f1(Object p, int x) throws NullPointerException{
	 if (p == null)
		throw new NullPointerException();
	 return x;
  }
	
  public static void main(String args[]){
	 try {
	   Class cls = Class.forName("method1");
	
		Method methlist[] 
		  = cls.getDeclaredMethods();
		for (int i = 0; i < methlist.length; i++) {  
		   Method m = methlist[i];
		   System.out.println("name = " + m.getName());
		   System.out.println("decl class = " + m.getDeclaringClass());
		   
		   Class pvec[] = m.getParameterTypes();
		   for (int j = 0; j < pvec.length; j++)
			  System.out.println("param #" + j + " " + pvec[j]);
			  
		   Class evec[] = m.getExceptionTypes();
		   for (int j = 0; j < evec.length; j++)
			  System.out.println("exc #" + j + " " + evec[j]);
		   System.out.println("return type = " + m.getReturnType());
		   System.out.println("-----");
		}
	 }
	 catch (Throwable e) {
		System.err.println(e);
	 }
  }
}
```

## Accessing annotations via Reflection

Accessing annotations in a Java program typically involves using Java Reflection. 

1. **Define the Annotation**: First, you need to define the annotation. For example:
    
    ```java
    import java.lang.annotation.*;
    
    @Retention(RetentionPolicy.RUNTIME)
    @Target(ElementType.METHOD)
    public @interface MyAnnotation {
        String value();
    }
    ```
    
2. **Apply the Annotation**: Next, apply the annotation to a method, class, or field:
    
    ```java
    public class MyAnnotatedClass {
        @MyAnnotation(value = "Hello, World!")
        public void myMethod() {
            System.out.println("This is my method.");
        }
    }
    ```
    
3. **Access the Annotation**: Use Java Reflection to access the annotation at runtime:
    
    ```java
    import java.lang.reflect.Method;
    
    public class Main {
        public static void main(String[] args) {
            try {
                // Get the method that has the annotation
                Method method = MyAnnotatedClass.class.getMethod("myMethod");
    
                // Check if the annotation is present
                if (method.isAnnotationPresent(MyAnnotation.class)) {
                    // Get the annotation
                    MyAnnotation annotation = method.getAnnotation(MyAnnotation.class);
    
                    // Access the annotation value
                    System.out.println("Annotation value: " + annotation.value());
                }
            } catch (NoSuchMethodException e) {
                e.printStackTrace();
            }
        }
    }
    ```
    

In this example, the `MyAnnotation` annotation is defined with a `value` element. It is applied to the `myMethod` method in the `MyClass` class. The `Main` class uses reflection to check if `myMethod` has the `MyAnnotation` annotation and then retrieves and prints its value.

Key points:

- **Retention Policy**: The `@Retention(RetentionPolicy.RUNTIME)` annotation ensures that the annotation is available at runtime.
- **Target**: The `@Target(ElementType.METHOD)` annotation specifies that this annotation can be applied to methods.
- **Reflection**: The `Method` class from the `java.lang.reflect` package is used to access the annotation.

This approach allows you to dynamically inspect and use annotations in your Java programs.