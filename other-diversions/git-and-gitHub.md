[work in progress]
Someone once said: **Java is to JavaScript as Car is to Carpet**. Meaning they are in no way directly connected. Yes, they both have the word "Java" in their names, however, each language has its own syntax, plugins, frameworks, etc. Git and GitHub have a much closer relationship than **Car** and **Carpet**.
### Git
- **Type**: Version Control System (VCS)
- **Purpose**: Manages and tracks changes to source code during software development.
- **Functionality**: Allows multiple developers to work on the same project without conflicts, keeps a history of changes, and supports branching and merging.
- **Installation**: Installed locally on your computer.
- **Usage**: Command-line tool, though there are graphical user interfaces (GUIs) available.

### GitHub
- **Type**: Web-based platform
- **Purpose**: Hosts Git repositories online, providing a collaborative environment for developers.
- **Functionality**: Offers additional features like issue tracking, project management, code review, and integration with other tools.
- **Installation**: No installation required; accessed via a web browser.
- **Usage**: Provides a user-friendly interface for managing Git repositories, along with social coding features like pull requests and discussions.

In summary, **Git** is the tool that handles version control, while **GitHub** is a platform that leverages Git to facilitate collaboration and project management.

## Java (OpenJDK) source code is available on GitHub
Java classes are [written in Java and hosted on GitHub](https://github.com/openjdk/jdk/tree/master/src/java.base/share/classes/java).

Here are some examples of the actual source code of Java object classes that we may want to be familiar with: 

`java.io` package classes:
- [File](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/io/File.java)
- [FileWriter](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/io/FileWriter.java)
- [PrintWriter](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/io/PrintWriter.java)

`java.lang` package classes:
(**note**: these class **do not** need to be imported):
- [Math](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/Math.java)
- [Object](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/Object.java) - The root of the class hierarchy. Every class has Object as a superclass. All objects, including arrays, implement the methods of this class.
- [String](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/String.java)
- [System](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/lang/System.java) 

`java.net` package classes:
- [HttpURLConnection](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/net/HttpURLConnection.java)
- [InetAddress](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/net/InetAddress.java)
- [ServerSocket](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/net/ServerSocket.java)
- [Socket](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/net/Socket.java)

`java.util` package classes:
- [ArrayList](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/ArrayList.java)
- [List](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/List.java)
- [Optional](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/Optional.java)
- [Random](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/Random.java)
- [Scanner](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/Scanner.java)
- [Timer](https://github.com/openjdk/jdk/blob/master/src/java.base/share/classes/java/util/Timer.java)
- 
In fact, all our friends are there [classes/java]().  Math.round, etc.