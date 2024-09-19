In class: Gaddis 2B slides.

- Primitive Data Types 
	- https://www.w3schools.com/java/java_data_types.asp
	- We will focus mostly on int, double, char, and Boolean.  
	  
- Non-Primitive Data Types are called Java Objects or Java Classes. 
	- String, Scanner, etc. are non-primitive data types (objects). 
		- The Java API gives us these objects (for free!).  
	- In Java, you make your own data types using **classes**. 
	- Java is known as an Object Oriented Programming (OOP) language.
		- Objects are a big deal in Java! 
		  
- Float/double - Both are decimal-based primitive data types.
	- Mostly you should use **double**. 
	- Float uses less memory (half) than double so it can be (slightly) faster.
	- Using Double, you can represent scientific notation with e or E: 
	  `double sci = 4.728197e4;` equals `47281.97`
	  
- Char
	- enclosed with Single Quote. 
	- For example, 'A' for A.
	- Supports Unicode (extended characters, every language) with "\\u". 
		- So If you type ' \\u4F60', you get this char 你. 
		- However [Google's Java style guide](https://google.github.io/styleguide/javaguide.html) says, just type the character. You don't need to type the \\u code. 
	- Slide 9: Char also supports Hexadecimal. For example, 0x6e (no quotes). 
		- 0x07 is kind of fun: it says BEL.
		- 0x20 can be used for explicit spacing.
		  
- Variable Assignment and Initialization
	- You can assign variables without initializing with data up top, but you can also just doing it in one line.
	- Tip on Assignment 2a:  
		- For the seven days and total, initialize variables without assigning data. 
		- For the three more (halfDay, etc.), initialize them WITH their value. How much should a halfDay be worth? How much should a fullDay be worth?
	  
- Arithmetic operators
	- Binary operators (+, -, etc.) - BI because they require two operands. With these operators, you combine two numbers. 
	- Operand is the value on which the operator acts: 
		- 2 and 2 are operands in 2 + 2.  
	- Be very careful with Integer division! 
	  It rounds down, so you'll end up with non-precise answers:
	  `jshell> 6 / 3`
	  `2`
	  `jshell> 7/3
	  `2`
	  
- Order of operations: 6/2*(1+2) 
	- Generally follows PEMDAS.
	- JShell helps to test equations!
	
- Casting 
	- Be sure to read and understand Section 2.7: Conversion between primitive data types.
	  
	- Casting can be done implicitly from Smaller to Larger (Widening) data types: 
	  `byte → short → char → int → long → float → double`
	  
	  So you can convert an int to a double with no problems: 
	  `int num = 100; 
	  `doublt result = num`
	  `result = 100.0` 
	  
	- Explicit Casting (Narrowing Conversing) must be done when converting a larger data type to a smaller because there is a risk of losing information or precision. 
	  You must manually specify the target type in parentheses before the value. 
	  `double decimal = 100.99`
	  `int decCast = (int) decimal;`
	  `decCast = 100`
	  
- JShell demo - super easy and useful Java console within Terminal (mac), PowerShell (Windows), or Command Prompt (Windows). 
	- Comes with Java!
	- Run calculations, declare and use variables, etc.
	- [Helpful video about JShell]([https://www.youtube.com/watch?v=mMnWwlIXLIY](https://www.youtube.com/watch?v=mMnWwlIXLIY)).
	  
- Combined Assignment Operators
	- `+=` and `-=` are used frequently in Loops. 
	  
- `final` keyword creates an unmodifiable variable. 
	- Used for constants that will never change. Example: `PI`.
	- You should write in all caps with underscores between words.
	  
- `String` is a non-primitive data type. Java gives us this object, it's not native to the machine code of the computer. Briefly: 
	- We create Variables. (`int x = 25; print x;`)
	- The computer stores those somewhere in memory (example, memory address `0x001`)
	- For Primitive data types, the value itself is stored in that memory location. 
	- For non-primitive data type, that memory location is a reference to other locations which store the primitive data types. 
		- Let's say `String S = "Sarah"` is stored in computer memory at `0x002`. If you looked inside that memory space, you'd see a reference to another place in memory (`0x116`) along with a length. 
		- A String is made out (primitive type) Chars. So if I look in `0x116` location, I see `S`. Then `0x117`, I see `A`. Etc..
		- When I tell Java, `print S`, it looks in `0x002` drawer, gets the length of Chars and prints the chars in order. 
		  
- I said String is non-primitive and that Java **gives** us this. 
	- Java has objects that are written in Java that you can use. It's a major benefit over coding directly on the machine in Assembly or C. 
	- Thousands of [objects](https://docs.oracle.com/javase/8/docs/api/index.html?java/lang/Object.html) given to us by the Java API. 
		- Examples: Scanner, Array, Web Request, Server, Image Handler. 
	- You write your own using classes. 
	- There are many benefits to non-primitive data types. Like Methods!
	  
- But first, Strings are special non-prim types because they can be assigned as a String literal.
	- `String value = "Hello"`
- All other java non-prim types must be created using the `new` keyword.
	- `String value = new String("Hello");`
	  
- Methods
	- Perform an action on a java object/ class. 
	- Specified by dot notation after an instance of the class, followed by parentheses with parameters (if required) or empty parentheses. 
	- Example: String objects have a length() method. 
	  
	  `String s = "Sarah"
	  `String newString = s.length()`
	  (length doesn't require any parameters)
	`
	- Scanner objects have a nextLine() method 
	  `Scanner keyboard = new Scanner(System.in)`
	  `String input = keyboard.nextLine()` 

- `var` keyword was introduced to Java in 2018 (JDK10). 
	- I don't encourage it because Java is **Strongly (Data) Typed**.
	- Remember: Java wants to always know what Type of data you're using (int, String, char, etc.).  
	  
- `Scanner` class -   
	- Our first non-primitive data type that behaves like other non-primitive data types!
	- We know `System.out`  is used to print to console, Scanner is `System.in` is used to type to console. 
	- Must be imported at top of file: `import java.util.Scanner;`
	- Must be initialized using the `new` keyword: 
	  `Scanner keyboard = new Scanner (System.in);`
	- Accepts user input using `keyboard.nextLine()`, `keyboard.nextInt()`, `keyboard.nextDouble()` .. depending on the type of expected input.
		- **Important!** If the Scanner is expecting an Int, and you type a letter, your program will crash. 
	  
- `Parse` methods 
	
`parseInt` and `parseDouble` are useful for extracting numbers out of strings!

```java
int number;
String str;  
double dbl;

str = “100.25”;
number = Integer.parseInt(str);
dbl = Double.parseDouble(str);
```

You can also convert a integer or double into a String using the `String.valueOf()` method.
```java
int num = 100; 
String str = String.valueOf(num); // "100" 
```

