## Java Feature
-  [x] Simple
-  [x] Object Oriented
-  [x] Platform Independent
-  [x] Arch Neutral
-  [x] Portable
-  [x] Robust
-  [x] Secure
-  [x] Dynamic
-  [x] Distributed
-  [x] Multi Threaded
-  [x] Interpretive 
-  [x] High Performance

 
### `Java Versions`


| XML based tech       | Annotation based tech(XML Optional) |
| ----------- | ----------- |
| JDK- 1.4      | JDK-5.0 or above       |
| JDBC-3.0   | JDBC 4.0     |
| Servlet-2.5| Servlet-3.0  |
| Struts-1.x | Struts-2.x   |
| JSF-1.x    | JSF-2.x      |
| EJBs-2.x   | EJBs-3.x     |
| Spring-2.x | Spring-3.x   |


Why it is not possible to define multiple package statement in a single java file?
Ans- Because package declaration statement must be the first statement

````java
package p1; // vallid -  must be first statement
package p2; // error -   invalid - second statement 
package p3; // error -   invalid - third statement

````

Is it possible to use classes and interfaces without importing that package?
Ans- Yes , but we need to provide Fully Qualified Name.
eg- `java.util.ArrayList`

````java
java.io.BufferedReader br = new java.io.BufferedReader(new java.io.InputStreamReader(System.in))
`````



<br/>

In Windows - if we  want to use 3 different version of java then create three file_Name.bat file
````sh
C:\java8\java8.bat  set path=C:\java8\bin;
C:\java11\java11.bat  set path=C:\java11\bin;
C:\java21\java21.bat  set path=C:\java21\bin;
````


Is it possible to provide more than one public class within a single java file?
Ans- No, Because if provide more than one public class then we must save the file with more than one name ,it is not possible in any operating system. 

``abc.java
```java
class FirstApp{
public static void main(String[] args){
System.println("Hello JAVA");
  }
}
```
> Status - No Compilation Error but not suggestible

``FirstApp.java
```java
class FirstApp{
public static void main(String[] args){
System.println("Hello JAVA");
  }
}
```
> Status - No Compilation Error, it is suggestible


``FirstApp.java
```java
public class A{ }
class FirstApp{
public static void main(String[] args){
System.println("Hello JAVA");
   }
 }
```
>> Status -  Compilation Error 



### Operator
