## Print System Info
Using Java, you can access information about the system running your program. You can also search for environment variables.

```java
public class Main {
  public static void main(String[] args) {
	System.out.println("\n \n PRINTING System Variables: \n" 
						+ System.getenv());  
	System.out.println("\n \n PRINTING ONEDRIVE PATH (IF AVAILABLE): \n" 
						+ System.getenv("ONEDRIVE"));  
	System.out.println("\n \n Printing PATH VARIABLES: \n" 
						+ System.getenv("PATH"));
	}
}
```

Some of the objects we know, such as PrintWriter, throw a `SecurityException` if a Security Manager is present and [`checkWrite(fileName)`](https://docs.oracle.com/javase/7/docs/api/java/lang/SecurityManager.html#checkWrite(java.io.FileDescriptor)) denies write access to the file.

## Security Manager
The Java Security Manager allows you to define a security policy for your application, specifying which actions are allowed or disallowed. Although it was deprecated for removal in Java 17, understanding its usage can still be valuable for legacy systems or specific security needs. 

### Example: Using the Security Manager

1. **Define a Security Policy:** Create a policy file that specifies the permissions for your application. For example, `my.policy`:
    
    ```plaintext
    grant {
        permission java.io.FilePermission "<<ALL FILES>>", "read,write";
        permission java.net.SocketPermission "www.example.com:80", "connect";
    };
    ```
    
2. **Set the Security Manager:** In your Java application, set the Security Manager and specify the policy file.
    
    ```java
    public class SecurityManagerExample {
        public static void main(String[] args) {
            // Set the security policy file
            System.setProperty("java.security.policy", "path/to/my.policy");
    
            // Enable the Security Manager
            System.setSecurityManager(new SecurityManager());
    
            // Example operation that requires permission
            try {
                System.out.println("Attempting to read a file...");
                java.nio.file.Files.readAllLines(java.nio.file.Paths.get("example.txt"));
            } catch (java.security.AccessControlException e) {
                System.out.println("Access denied: " + e.getMessage());
            } catch (java.io.IOException e) {
                e.printStackTrace();
            }
        }
    }
    ```

### Explanation

- **Policy File:** The policy file defines the permissions granted to your application. In this example, it allows reading and writing to all files and connecting to `www.example.com` on port 80.
- **Setting the Security Manager:** The `System.setSecurityManager(new SecurityManager())` line enables the Security Manager, enforcing the specified policy.
- **Handling Permissions:** When the application tries to perform an operation, such as reading a file, the Security Manager checks if the operation is allowed based on the policy. If not, it throws an `AccessControlException`.

### Use Cases

- **Sandboxing:** Restricting the actions of untrusted code, such as plugins or scripts.
- **Legacy Systems:** Maintaining security policies in older applications that still rely on the Security Manager.
- **Custom Security Policies:** Implementing fine-grained security controls for specific application needs.

While the Security Manager is being phased out, understanding its principles can help you transition to modern security practices and tools.

More information is in [this article](https://www.baeldung.com/java-security-manager).