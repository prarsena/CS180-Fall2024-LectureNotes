Using Java, you can access information about the system running your program

```java
public class Main {
  public static void main(String[] args) {
	System.getProperties().list(System.out);
    System.out.println(System.getenv());
    System.out.println(System.getenv("ONEDRIVE"));
    System.out.println(System.getenv("PATH"));
  }
}
```