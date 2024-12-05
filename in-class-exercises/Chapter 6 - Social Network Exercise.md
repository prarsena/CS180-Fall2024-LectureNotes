Last updated: Tuesday, November 26, 2025
## LET'S BUILD A SOCIAL NETWORK

1. Add a new package to Chapter 06 called `FriendBook`. 
2. Create a `User` object class with these fields:

```java
private int id = generateID();
private String username;
private String password;
private String school;
private String quote;
private List<User> friends
```

3. Write getter methods for all fields.
4. Write setter methods for quote.
5. Write a four-arg constructor to set the username, password, school, and quote. 
6. Write a generateID() method that returns a Random int between 9999 and 99999.
7. Make a file in the same package called `TestFriendBook`. Run the file:  

```java
// TestFriendbook.java
package FriendBook;  
  
public class TestFriendBook {  
	public static void main(String[] args) {  
		User john = new User("John Doe", "password", "Springfield High", "I finally learned how to write without a pencil.");  
		User jane = new User("Jane Smith", "password", "Riverview Academy", "I’m outta here! See you all at the 10-year reunion.");  
		User alex = new User("Alex Johnson", "password", "Mountainview High", "I’m not a complete idiot. Some parts are missing.");  
		User emily = new User("Emily Brown", "password", "Lakeside School", "I’m not late; I’m just early for tomorrow.");  
		User michael = new User("Michael Davis", "password","Greenwood High", "I didn’t choose the school life; the school life chose me.");  
		User sarah = new User("Sarah Wilson", "password", "Sunnydale High", "I’m 100% certain that I am 0% sure of what I’m doing.");  
		User david = new User("David Martinez", "password","Riverside High", "I’m not arguing; I’m just explaining why I’m right.");  
		User laura = new User("Laura Garcia", "password","Hilltop Academy", "I’m not lazy; I’m on energy-saving mode.");  
		User james = new User("James Lee", "password","Westside High", "I’m not a procrastinator; I’m just extremely productive at unimportant things.");  
		User sophia = new User("Sophia Kim", "password","Eastwood High", "I’m not weird; I’m limited edition.");  
		
		System.out.println("ID: " + james.getId());  
		System.out.println("Username: " + james.getUsername());  
		System.out.println("School: " + james.getSchool());  
		System.out.println("Quote: " + james.getQuote());
		//User.printUserProfile(sophia);  
		//System.out.println(sophia.toString());  
	}  
}
```

8. Move the print statements into the `User` class as a static void method called `printUserProfile` that takes `User u` as an input parameter. Uncomment the relevant line in `TestFriendbook` and see if it runs. 
9. Change the `printUserProfile` method to a custom toString method. Add a print statement for a User object in `TestFriendbook`.