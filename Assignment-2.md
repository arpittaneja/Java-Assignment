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

### Answer
```java
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

### Answer
```java
Class A
Class B
Class C
```


