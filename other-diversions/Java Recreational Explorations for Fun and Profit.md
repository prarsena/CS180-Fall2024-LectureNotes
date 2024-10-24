
### Poetry in the OpenJDK Source Code
The OpenJDK Source code is sometimes well-worth a read for the poetic examples they give for the methods.

For example, the documentation for the [String.replace()](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/String.java#L3022) method (which we all know well), contains these comments:
```java
     * Examples:
     * "mesquite in your cellar".replace('e', 'o')
     *         returns "mosquito in your collar"
     * "the war of baronets".replace('r', 'y')
     *         returns "the way of bayonets"
     * "sparring with a purple porpoise".replace('p', 't')
     *         returns "starring with a turtle tortoise"
     * "JonL".replace('q', 'x') returns "JonL" (no change)
```

The comments for the [String.substring()](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/String.java#L2897) method:

```java
     * "unhappy".substring(2) returns "happy"
     * "Harbison".substring(3) returns "bison"
     * "emptiness".substring(9) returns "" (an empty string)

     * "hamburger".substring(4, 8) returns "urge"
     * "smiles".substring(1, 5) returns "mile"
```

And the comments for the [String.concat()](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/String.java#L2986) method:
```java
     * "cares".concat("s") returns "caress"
     * "to".concat("get").concat("her") returns "together"
```

### For loops - Initializing multiple variables. 

```java
for (int i = 0, j = 10; i < j; i++, j--) {  
    System.out.println("i: " + i + ", j: " + j);  
}
```

Could be useful for calculating 2 to the power of n:
```java
System.out.println("Calculate 2 to the power of N");  
for (int i = 0, j = 1; i < 16; i++, j*=2) {  
    System.out.println("n: " + i + ", 2^n: " + j);  
}
n: 0, 2^n: 1
n: 1, 2^n: 2
n: 2, 2^n: 4
n: 3, 2^n: 8
n: 4, 2^n: 16
n: 5, 2^n: 32
n: 6, 2^n: 64
n: 7, 2^n: 128
n: 8, 2^n: 256
n: 9, 2^n: 512
n: 10, 2^n: 1024
n: 11, 2^n: 2048
n: 12, 2^n: 4096
n: 13, 2^n: 8192
n: 14, 2^n: 16384
n: 15, 2^n: 32768
```
### For loops can be written as while loops
The difference is that you manage the initialization outside the loop and the count inside the loop. Both of which could have side effects.
```java
//for
for (int i=0; i<5; i++){  
    System.out.println(i);  
}

//while
int i=0;  
while (i<5) {  
    System.out.println(i);  
    i++;  
}

//do-while
int i=0;
do {  
    System.out.println(i);  
    i++;  
} while (i<5);
```
For example, since `i` is a common variable name used in counters, if you use it multiple times in a program, it can be changed when you don't want it to be. 

You can also forget to increment the counter within the while loop body -- leading to an infinite loop. This is not usually possible in For Loops because the three elements (initialization value, test condition, and update values) are defined all together in the for-loop header. The only time you would have an infinite loop is if you set the update condition the wrong way (decrementing to below infinity when you wanted to increment to a given value).
### For loops - initialization and update are optional. 
Curiously, Java also lets you mess around with for loops. It's not required to have all three parameters in the for loop header. 

It's valid Java to write a for loop like this: 
```java
int i = 1;  
for (;i < 5;){  
    i++;
}
```
It looks very similar to a while loop acting like a For loop. While loops are best used for input validation. 

Finally, you don't even need the test condition. For some reason the following evaluates to true and gives you an infinite for loop:

```java
for (;;){  
    System.out.println("hi");  
}
```

This means the condition in the middle is evaluated as `(;true;)`. Not exactly sure why. 

### Printf Variable Widths: Strings in Motion?
How do you use a variable for a width signal? 
%20s, how do I pass 20 as a variable? and maybe use a For Loop to increment the spacing? 

We know that by default, the string is right-aligned to the width in printf. So if we continue to increase the width, the string will drift to the right for each increment. 

```java
String format;  
for (int i=1; i < 50; i++){  
    format = "%" + i + "s";  
    System.out.printf(format + "%n", "Sarah");  
}

Sarah
Sarah
Sarah
Sarah
Sarah
 Sarah
  Sarah
   Sarah
    Sarah
     Sarah
      Sarah
       Sarah
        Sarah
         Sarah
          Sarah
           Sarah
            Sarah
             Sarah
              Sarah
               Sarah
                Sarah
                 Sarah
                  Sarah
                   Sarah
                    Sarah
                     Sarah
                      Sarah
                       Sarah
                        Sarah
                         Sarah
                          Sarah
                           Sarah
                            Sarah
                             Sarah
                              Sarah
                               Sarah
                                Sarah
                                 Sarah
                                  Sarah
                                   Sarah
                                    Sarah
                                     Sarah
                                      Sarah
                                       Sarah
                                        Sarah
                                         Sarah
                                          Sarah
                                           Sarah
                                            Sarah
```


```java
String format;  
int i=1;  
for (; i < 100; i++){  
    format = "%" + i + "s";  
    System.out.printf(format + "%n", "Sarah");  
}  
for (int p=1; p<10;p++){  
    System.out.printf("%" + (i-1) + "s %n", "Sarah");  
}

Sarah
Sarah
Sarah
Sarah
Sarah
 Sarah
  Sarah
   Sarah
    Sarah
     Sarah
      Sarah
       Sarah
        Sarah
         Sarah
          Sarah
           Sarah
            Sarah
             Sarah
              Sarah
              Sarah 
              Sarah 
              Sarah 
              Sarah 
              Sarah 
              Sarah 
              Sarah 
              Sarah 
              Sarah 
```

### Nested For Loops for Art

## Java http server exploits

web server HTTP headers should use the Latin1 encoding of bytes, but sometimes they use UTF8
http-garden repo from Ben

