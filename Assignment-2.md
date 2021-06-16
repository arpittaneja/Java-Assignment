# Assignment-2 (Classes & Inheritance)
Dated - 14 June, 2021

### Q1. What will be the output of the below program?
### a)

```java
class A
{
    public A()
    {
        System.out.println("Class A Constructor");
    }
}
class B extends A
{
    public B()
    {
        System.out.println("Class B Constructor");
    }
}
class C extends B
{
    public C()
    {
        System.out.println("Class C Constructor");
    }
}
public class MainClass
{
    public static void main(String[] args)
    {
    C c = new C();
    }
}
```

### Output
```
Class A Constructor
Class B Constructor
Class C Constructor
```


### b)

```java
class A
{
    String s = "Class A";
}
class B extends A
{

    String s = "Class B";
    {
        System.out.println(super.s);
    }
}
class C extends B
{
    String s = "Class C";
    {
        System.out.println(super.s);
    }
}
public class MainClass
{
    public static void main(String[] args)
    {
        C c = new C();
        System.out.println(c.s);
    }
}
```

### Output
```java
Class A
Class B
Class C
```

### c)
```java
public class classCommLine {
    public static void main(String args[]) {
        for(int i=0; i<args.length; i++)
            System.out.println("args[" + i + "]: " + args[i]);
    }
}
```

### Output
```
C:\Users\Arpit\Desktop>javac classCommLine.java

C:\Users\Arpit\Desktop>java classCommLine 10 20 30 40 50 60
args[0]: 10
args[1]: 20
args[2]: 30
args[3]: 40
args[4]: 50
args[5]: 60
```

### Q2. Can abstract class have constructors in Java?
### Ans
```java
Yes, in Java, abstract classes do have constructors. They can be called by using the super() keyword.
```

### Q3. Create an abstract class 'Parent' with a method 'message'. It has two subclasses each having a method with the same name 'message' that prints "This is first subclass" and "This is second subclass" respectively. Call the methods 'message' by creating an object for each subclass.

### Code
```java
abstract class Parent{
    abstract void message();

}

class SubClassOne extends Parent{
    void message(){
        System.out.println("This is first subclass");
    }
}

class SubClassTwo{
    void message(){
        System.out.println("This is second subclass");
    }
}

public class Main{
    public static void main(String[] args) {
        SubClassOne one = new SubClassOne();
        SubClassTwo  two = new SubClassTwo();

        one.message();
        two.message();
    }
}
```
### Output
```java
This is first subclass
This is second subclass
```

### Q4. An abstract class has a construtor which prints "This is constructor of abstract class", an abstract method named 'a_method' and a non-abstract method which prints "This is a normal method of abstract class". A class 'SubClass' inherits the abstract class and has a method named 'a_method' which prints "This is abstract method". Now create an object of 'SubClass' and call the abstract method and the non-abstract method. (Analyse the result)
### Code
```java
abstract class Abstract
{
    public Abstract() {
        System.out.println("This is constructor of abstract class");
    }
    abstract void a_method();
    public void nonAbstractMethod()
    {
        System.out.println("This is a normal method of abstract class");
    }
}
class Subclass extends Abstract
{
    @Override
    void a_method() {
        System.out.println("This is abstract method");
    }
}
public class program2 {
    public static void main(String[] args) {
        Subclass sc = new Subclass();
        sc.a_method();
        sc.nonAbstractMethod();
    }
}
```

### Output:
```java
This is constructor of abstract class
This is abstract method
This is a normal method of abstract class
```

### Q5. Write a java code to find whether a number is prime or not where number is accepted from command line.
### Code 
```java

public class Prime{
    public static void main(String[] args) {
        int num = Integer.parseInt(args[0]);
        
        boolean prime = true;
        for (int i = 2; i < num; i++){
            if ((num%i) == 0){
                prime = false;
            }
        }
        if(prime == false){
                System.out.println(num + " is not a prime number!");
        }
        else{
            System.out.println(num + " is a prime number!");
        }
    }
}

```
### Output

```
C:\Users\Arpit\Desktop>javac Prime.java

C:\Users\Arpit\Desktop>java Prime 13
13 is a prime number!

C:\Users\Arpit\Desktop>java Prime 10
10 is not a prime number!
```
