# Assignment-2 (Packages and Interfaces)
Dated - 14 June, 2021

### Q1. What will be the output of the below program?
### a)

```java
package AssignmentPractise;

interface A
{
    void myMethod();
}
class B
{
    public void myMethod()
    {
        System.out.println("My Method");
    }
}
class C extends B implements A
{
}
public class MainClass
{
    public static void main(String[] args)
    {
        A a = new C();
        a.myMethod();
    }
}
```

### Output:
```
My Method
```


### b)

```java
interface P
{
    String p = "PPPP";
    String methodP();
}
interface Q extends P
{
    String q = "QQQQ";
    String methodQ();
}
class R implements P, Q

{
    public String methodP()
    {
        return q+p;
    }
    public String methodQ()
    {
        return p+q;
    }
}
public classMainClass
{
    public static void main(String[] args)
    {
        R r = new R();
        System.out.println(r.methodP());
        System.out.println(r.methodQ());
    }
}
```

### Output:
```java
QQQQPPPP
PPPPQQQQ
```


### Q2. Create a class TwoDim which contains private members as x and y coordinates in package P1. Define the default constructor, a parameterized constructor and override toString() method to display the co-ordinates. Now reuse this class and in package P2 create another class ThreeDim, adding a new dimension as z as its private member. Define the constructors for the subclass and override toString() method in the subclass also. Write appropriate methods to show dynamic method dispatch. The main() function should be in a package P. (Try on machine also, if possible)
### Ans.
```java
//PACKAGE P1
package P1;

public class TwoDim {
    private int x;
    private int y;

    public TwoDim(){
        this.x = 0;
        this.y = 0;
    }

    public TwoDim(int x, int y){
        this.x = x;
        this.y = y;
    }

    public String toString(){
        return "The coordinates are \nx: " + this.x + "\ny: " + this.y;
    }
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

//PACKAGE P2
package P2;

import P1.TwoDim;
public class ThreeDim extends TwoDim {
    private int z;

    public ThreeDim(){
        super();
        this.z = 0;
    }

    public ThreeDim(int x, int y, int z){
        super(x, y);
        this.z = z;
    }

    public String toString(){
        return super.toString() + "\nz: " + this.z;
    }
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

//PACKAGE P
package P;

import P1.TwoDim;
import P2.ThreeDim;
public class MainClass {
    public static void main(String[] args) {

//        TwoDim td0 = new TwoDim();
//        System.out.println(td0.toString());
//
//        TwoDim td1 = new TwoDim(4, 10);
//        System.out.println(td1.toString());
//
//        ThreeDim td2 = new ThreeDim();
//        System.out.println(td2.toString());
//
//        ThreeDim td3 = new ThreeDim(3, 5, 7);
//        System.out.println(td3.toString());

        //Example of Dynamic Method Dispatch
        //Reference variable of superclass(TwoDim) referring to an object off subclass(ThreeDim)
        TwoDim ob = new ThreeDim(5, 3, 9);
        System.out.println(ob.toString());
    }
}

```
### Output:
```java
x: 5
y: 3
z: 9
```

### Q3. Define an abstract class Shape in package P1. Inherit two more classes: Rectangle in package P2 and Circle in package P3. Write a program to ask the user for the type of shape and then using the concept of dynamic method dispatch, display the area of the appropriate subclass. Also write appropriate methods to read the data. The main() function should not be in any package. (Try on machine also, if possible)

### Code:
```java

//PACKAGE P1
package P1;

import java.io.IOException;

abstract public  class Shape{
    abstract public void enterDimensions() throws IOException;
    abstract public double setArea() throws IOException;
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

//PACKAGE P2
package P2;

import P1.*;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Rectangle extends Shape{

    private double length;
    private double breadth;
    public void enterDimensions() throws IOException {
        BufferedReader br0 = new BufferedReader(new InputStreamReader(System.in));
        length = Double.parseDouble(br0.readLine());
        br0.close();

        BufferedReader br1 = new BufferedReader(new InputStreamReader(System.in));
        length = Double.parseDouble(br1.readLine());
        br1.close();
    }

    @Override
    public double setArea() throws IOException{
        return length*breadth;
    }
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

//PACKAGE P3
package P3;

import P1.*;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;

public class Circle extends Shape {
    private double radius;
    public void enterDimensions() throws IOException {
        BufferedReader br0 = new BufferedReader(new InputStreamReader(System.in));
        radius = Double.parseDouble(br0.readLine());
        br0.close();
    }

    @Override
    public double setArea() throws IOException {
        return Math.PI * this.radius * this.radius;
    }
}

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

//PACKAGE P
package P;

import P1.*;
import P2.*;
import P3.Circle;

import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.Scanner;

public class MainClass {
    public static void main(String[] args) throws IOException {
        boolean flag = true;
        Shape ref;

        while (flag){
            Scanner obj0 = new Scanner(System.in);
            System.out.println("Select a shape!");
            System.out.println(" (1) Rectangle\n (2) Circle");
            System.out.print("Enter Choice: ");
            int choice = obj0.nextInt();
            if (choice ==1) {
                ref = new Rectangle();
                ref.enterDimensions();
                System.out.println("Area: " + ref.setArea() + " sq units");
                flag = false;
            }
            else if (choice == 2) {
                ref = new Circle();
                ref.enterDimensions();
                System.out.println("Area: " + ref.setArea() + " sq units");
                flag = false;
            }
            else {
                flag = true;
                System.err.println("Invalid Option\nTry Again");
            }
        }
    }
}

```
### Output:
```java
Select a shape!
 (1) Rectangle
 (2) Circle
Enter Choice: 3
Select a shape!
Invalid Option
Try Again
 (1) Rectangle
 (2) Circle
Enter Choice: 1
4
3
Area: 12.0 sq units

```


### Q4. Define an interface shape which contains a function area(). Write the implementation of the interface for circle, rectangle and square. Also write the main() to test the interface. Can we declare variable in an Interface?
### Code:
```java
import java.util.Scanner;

interface Shape{
    public double area();
}

class Circle implements Shape{
    private double radius;
    public void enterDimensions(){
        System.out.print("Enter the radius of circle: ");
        Scanner sc = new Scanner(System.in);
        this.radius = sc.nextDouble();
    }

    public double area(){
        return Math.PI*this.radius*this.radius;
    }
}

class Rectangle implements Shape{
    private double length;
    private double breadth;
    public void enterDimensions(){
        System.out.print("Enter the dimensions of the rectangle: ");
        Scanner sc0 = new Scanner(System.in);
        this.length = sc0.nextDouble();

        Scanner sc1 = new Scanner(System.in);
        this.breadth = sc1.nextDouble();

    }

    public double area(){
        return this.breadth*this.breadth;
    }
}

class Square implements Shape{
    private double side;
    public void enterDimensions(){
        System.out.print("Enter the side of the square: ");
        Scanner sc = new Scanner(System.in);
        this.side = sc.nextDouble();
    }

    public double area(){
        return this.side*this.side;
    }
}

public class MainClass {
    public static void main(String[] args) {
        Circle myCircle = new Circle();
        myCircle.enterDimensions();
        System.out.println("The area of the circle is " + myCircle.area() + " sq. units");

        Rectangle myRect = new Rectangle();
        myRect.enterDimensions();
        System.out.println("The area of the rectangle is " + myRect.area() + " sq. units");

        Square mySquare = new Square();
        mySquare.enterDimensions();
        System.out.println("The area of the square is " + mySquare.area() + " sq. units");
    }
}

```
### Output:
```java
Enter the radius of circle: 5
The area of the circle is 78.53981633974483 sq. units

Enter the dimensions of the rectangle: 
6
8
The area of the rectangle is 64.0 sq. units

Enter the side of the square: 9
The area of the square is 81.0 sq. units

Process finished with exit code 0
```
```java
No, a variable cannot be declared in interfaces in java.
```


### Q5.Can interfaces have constructors?
### Ans.
```java
No, interfaces cannot have constructors in java.
```
