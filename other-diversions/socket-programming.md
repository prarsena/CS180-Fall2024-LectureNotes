server
```java
import java.io.*;  
import java.net.*;  
  
public class SimpleSocketServer {  
	public static void main(String[] args) {  
		try (ServerSocket serverSocket = new ServerSocket(12345)) {  
			System.out.println("Server is listening on port 12345");  
			while (true) {  
				Socket socket = serverSocket.accept();  
				System.out.println("New client connected");  
				new ServerThread(socket).start();  
			}  
		} catch (IOException ex) {  
			ex.printStackTrace();  
		}  
	}  
}  
  
class ServerThread extends Thread {  
	private Socket socket;  
	  
	public ServerThread(Socket socket) {  
		this.socket = socket;  
	}  
	  
	public void run() {  
		try (InputStream input = socket.getInputStream();  
			BufferedReader reader = new BufferedReader(new InputStreamReader(input));  
			OutputStream output = socket.getOutputStream();  
			PrintWriter writer = new PrintWriter(output, true)) {  
			  
			String text;  
			while ((text = reader.readLine()) != null) {  
			System.out.println("Received: " + text);  
			writer.println("Echo: " + text);  
			}  
		} catch (IOException ex) {  
			ex.printStackTrace();  
		}  
	}
}
```

client
```java
import java.io.*;  
import java.net.*;  
  
public class SocketClient {  
	public static void main(String[] args) {  
		// IP ADDRESS OF SERVER
		String hostname = "10.100.175.55";  
		int port = 12345;  
		  
		try (Socket socket = new Socket(hostname, port)) {  
			OutputStream output = socket.getOutputStream();  
			PrintWriter writer = new PrintWriter(output, true);  
			  
			InputStream input = socket.getInputStream();  
			BufferedReader reader = new BufferedReader(new InputStreamReader(input));  
			String dataToSend = InetAddress.getLocalHost().getHostName() 
			+ "\n" + InetAddress.getLocalHost().getHostAddress()  
			+ "\n" + System.getenv().toString();  
			writer.println("Hello, Server\n" + dataToSend);  
			  
			String response = reader.readLine();  
			System.out.println("Server response: " + response);  
		} catch (UnknownHostException ex) {  
			System.out.println("Server not found: " + ex.getMessage());  
		} catch (IOException ex) {  
			System.out.println("I/O error: " + ex.getMessage());  
		}  
	}  
}
```

Compiling and running the client on cli:
```bash
javac .\SocketClient.java
java SocketClient
```
