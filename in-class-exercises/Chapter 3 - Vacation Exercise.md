This in-class exercise will allow our program to have FOUR specific paths depending on user input. We ask the user to tell us how many cities they're visiting on their vacation and then print a different message depending on how many cities they're travelling to (or NOT travelling to). 

### Part 1
1. Initialize a Scanner object 
2. Print: "How many cities are you visiting on your vacation?"
3. Create an `int numberOfCities` variable assigned to an integer from the keyboard.
5. Write an `if/else` statement. 
	- If the user will visit 1 city: 
		- Print: "What is one city you are visiting?"
		- Create a `String cityName` variable assigned to a String from the keyboard (use `next()`).
		- print "Have fun in *cityName*"
	- else: 
		- print "Have fun on your adventures!"




### Part 2
1. Turn this `if/else` statement into an `if/else if/else` statement and add a else condition. 
2. Change the "Have fun on your adventures" part to an `else if` statement by adding a condition to run if the user enters a number of cities greater than 1. 
   
   This means that our `else` condition (evaluated only if number of cities is not 1 or greater than 1) indicates the user will NOT be travelling. 
   
4. Within the else condition, print:  "Do you want to travel?" 
5. Create a String variable called `wantsToTravelString` and assign it input of the keyboard (use `next()`).
6. Below `wantsToTravelString`, create a Char variable called `wantsToTravelChar`, and assign it to the upper-cased first Char of `wantsToTravelString`. 
7. Within the `0` condition, write a nested if statement:
	- If `wantsToTravelChar` is `Y`, print "Maybe next year!"
	- If `wantsToTravelChar` is `N`, print "Enjoy your staycation!"

### Part 3
Use a block comment to comment-out your entire if/else if/else block.
Re-write this logic using a `Switch` statement (classic or modern) expressing the same conditions! 


### Example outputs:
```java
How many cities are you visiting on your vacation?
1
What is one city you are visiting?
Berlin
Have fun in Berlin

How many cities are you visiting on your vacation?
2
Have fun on your adventures

How many cities are you visiting on your vacation?
0
Do you want to travel?
no
Enjoy your staycation!

How many cities are you visiting on your vacation?
0
Do you want to travel?
y
Maybe next year!
```