
In main, add Scanner to choose between invert and pixelate:

```java
Scanner keyboard = new Scanner(System.in);  
char programMode;

...

System.out.print("Do you want to invert (I) the colors, or pixelate (P) the image? ");  
programMode = keyboard.next().toUpperCase().charAt(0);  
  
if (programMode == 'I') {  
invertColors(imageCopy, filename);  
}  
else if (programMode == 'P') {  
pixelateImage(imageCopy, filename);  
}  
else {  
System.out.println("Invalid choice. Sorry, run again!");  
}
```