# Assignment-2 (Classes & Inheritance)
Dated - 14 June, 2021

#### Q1. Write a program in Java (using try-with-resources functionality) to do the following:
####i) open two files "exam1.txt" and "exam2.txt". Accept file names through command-line arguments.
#### ii) exit the program if any of the two files is unable to open.
#### iii) append contents of "exam1.txt" to "exam2.txt".
#### iv) re-write contents of "exam2.txt" after removing all white spaces from the updated content (without using built-in methods).
### i)

```java
import java.io.*;

class AppendFiles
{
	public static void main(String args[])
	{
		if(args.length != 2)
		{
			System.out.println("Usage: java AppendFiles <file1> <file2>");
			return;
		}

		int i;

		try(FileInputStream fin = new FileInputStream(args[0]);
		FileOutputStream fout = new FileOutputStream(args[1], true))
		{
			
			do
			{
				i = fin.read();
				if(i != -1)
				{
					fout.write(i);
				}
			}while(i != -1);

			System.out.println("Program Runned successfully");
		}
		catch(FileNotFoundException e)
		{
			System.out.println("File Not Found");
			return;
		}
		catch(IOException e)
		{
			System.out.println("An I/O error occurred");
		}

		removespaces();
		return;
	}

	public static void removespaces()
	{
		try{
		FileInputStream fin = new FileInputStream("exam2.txt");
		FileOutputStream fout = new FileOutputStream("abc.txt");
		int i;

		do
		{
			i = fin.read();
			if(i!=-1 && i != 32)
			{
				fout.write(i);
			}
		}while(i!=-1);
		System.out.println("Removed Spaces Successfully");
		}
		catch(FileNotFoundException e)
		{
			System.out.println("File Not Found");
			return;
		}
		catch(IOException e)
		{
			System.out.println("An I/O error occurred");
		}
		return;
	}
}
```


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------


#### Q2. Write a program in Java to do the following:
#### i) define a class Person having three private instance variables: name, age and emailid; a private class variable count (that keeps count of total number of instances), all having appropriate data types.
#### ii) define a parameterized constructor; and two methods- displayCount() and toString().
#### iii) define a custom exception class InvalidEmailIdException having a toString()method that prints appropriate exception details. The exception object is thrown when an emailid of a person is invalid.
#### iv) define a custom exception class ExcessMembersException having a toString()method that prints appropriate exception details. The exception object is thrown when the variable count (count of instances of class Person) is greater than 5.
#### v) define a class Demo having main method with appropriate code to show working of the above classes.
### Ans.
```java
import java.util.Scanner;
import java.util.regex.Matcher;
import java.util.regex.Pattern;

class InvalidEmailIdException extends Exception
{
	String msg;
	InvalidEmailIdException()
	{
		msg = "Invalid E-mail Id";
	}

	public String toString()
	{
		return msg;
	}
}

class ExcessMemberException extends Exception
{
	String msg;
	ExcessMemberException()
	{
		msg = "Excess member(s) found";
	}

	public String toString()
	{
		return msg;
	}
}

class Person
{
	private String name;
	private int age;
	private String email;
	private static int count = 0;

	Person(String name, int age,String email)
	 {
		try{
		if(count<5){
		String emailRegex = "^[a-zA-Z0-9_+&*-]+(?:\\."+
		"[a-zA-Z0-9_+&-]+)@" +
		"(?:[a-zA-Z0-9-]+\\.)+[a-z" +
		"A-Z]{2,7}$";
		Pattern pat = Pattern.compile(emailRegex);
		try {
		if(!pat.matcher(email).matches()) {
		throw new InvalidEmailIdException();
		}
		}catch(InvalidEmailIdException e) {
		System.out.println(e);
		return;
		}
		this.name=name;
		this.email=email;
		this.age=age;
		count++;
		}
		else if(count>5)
		{
			throw new ExcessMemberException();
		}
		}catch(ExcessMemberException e)
		{
			System.out.println(e);
			return;
		}
	}

	public void displayCount()
	{
		System.out.println("Number of instances = " + count);
	}

	public int getCount()
	{
		return count;
	}

	public String toString()
	{
		return "Name:  " + this.name + "\nAge:  " + this.age + "\nE-mail:  " + this.email;
	}
}

public class Demo
{
	public static void main(String args[])
	{
		Person P;
		Person P1 = new Person("Arpit", 19, "Arpit219@gmail.com");
		P = P1;
		P.displayCount();
		System.out.println(P);
		Person P2 = new Person("Goku", 18, "Goku219@gmail.com");
		P = P2;
		P.displayCount();
		System.out.println(P);
		Person P3 = new Person("Light", 20, "Light219@gmail.com");
		P = P3;
		P.displayCount();
		System.out.println(P);
		Person P4 = new Person("Armin", 24, "Armin219@gmail.com");
		P = P4;
		P.displayCount();
		System.out.println(P);
		Person P5 = new Person("Jonas", 25, "Jonas219@gmail.com");
		P = P5;
		P.displayCount();
		System.out.println(P);
		Person P6 = new Person("Mikasa", 21, "Mikasa219@gmail.com");
		P = P6;
		P.displayCount();
		System.out.println(P);
		Person P7 = new Person("Levi", 21, "Levi219@gmail.com");
		P = P7;
		P.displayCount();
		System.out.println(P);
		
	}
}
```
