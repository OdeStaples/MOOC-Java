# Primitive Data Types

**Data Type -> Size -> Description**

- byte -> 8 bits -> Signed integer
- short -> 16 bits (2 bytes) -> Signed integer
- int -> 32 bits (4 bytes) -> Signed integer
- long -> 64 bits (8 bytes) -> Signed integer
- float -> 32 bits (4 bytes) -> Single-precision floating-point number
- double -> 64 bits (8 bytes) -> Double-precision floating-point number
- char -> 16 bits (2 bytes) -> Unicode character
- boolean -> 1 bit -> Logical value (true or false)

# Variables

- A variable can be thought of as a container in which information of a given type can be stored. Examples of these different types include text (`String`), whole numbers (`int`), floating-point numbers (`double`), and whether something is true or false (`boolean`). A value is assigned to a variable using the equals sign (=).

```java
String text = "contains text";
int wholeNumber = 123;
double floatingPoint = 3.141592653;
boolean trueOrFalse = true;

System.out.println("Text variable: " + text);
System.out.println("Integer variable: " + wholeNumber);
System.out.println("Floating-point variable: " + floatingPoint);
System.out.println("Boolean: " + trueOrFalse);

/* OUTPUT
Text variable: contains text
Integer variable: 123
Floating-point variable: 3.141592653
Booolean: true
*/
```

- The variable type is stated when the variable is first declared. When a new value is assigned to the variable, the type is no longer declared.

```java
int value = 10;
System.out.println(value);
value = 4;
System.out.println(value);
```

# Variable's Type Persists

- Once a variable's type has been declared, it can no longer be changed. For example, a boolean value cannot be assigned to a variable of the integer type, nor can an integer be assigned to a variable of the boolean type.

```java
boolean integerAssignmentWillWork = false;
integerAssignmentWillWork = 42; // Does not work

int value = 10;
integerAssignmentWillWork = value; // Neither does this
```

- However, exceptions do exist: an integer can be assigned to a variable of the double type, since Java knows how to convert an integer to a double during assignment.

```java
double floatingPoint = 0.42;
floatingPoint = 1; // Works

int value = 10;
floatingPoint = value; // Also works
```

- A floating-point value cannot, however, be assigned to an integer variable. The reason for this is that those who develop the language aim to prevent developers from making errors that lead to a loss of information.

```java
int value = 4.2; // Does not work

double floatingPoint = 0.42;
value = floatingPoint; // Neither does this
```

# The Type of the Variable Informs of Possible Values

**Type -> Example -> Accepted Values**

- Whole number, i.e., `int` -> `int value = 4;` -> An integer can contain whole numbers whose values lie between -2147483648 and 2147483647.

- Floating-point number, i.e., `double` -> `double value = 4.2;` -> Floating-point numbers contain decimal numbers, with the greatest possible value being approximately 2^1023. When a decimal number is represented with a floating-point number, the value can be inaccurate as floating-points are incapable of representing all decimal numbers. The reasons behind this are explored in the Computer organization course.

- `String` -> `String text = "Hi!";` -> A string can contain text. Strings are enclosed in quotation marks.

- True or false value, i.e., `boolean` -> `boolean right = true;` -> A boolean contains either the value `true` or `false`.

# Reading Integers

- The `Integer.valueOf` command converts a string to an integer. It takes the string containing the value to be converted as a parameter.

- On the contrary, you can use `nextInt()` to read an integer input from the user (it doesn't convert string to int type as `Integer.valueOf` does).

```java
String valueAsString = "42";
int value = Integer.valueOf(valueAsString);

Scanner scanner = new Scanner(System.in);
int anotherValue = scanner.nextInt();

System.out.println(value); // 42
System.out.println(anotherValue); // 40
```

# Reading Doubles

- The `Double.valueOf` command converts a string to a double. It takes the string containing the value to be converted as a parameter.

- On the contrary, you can use `nextDouble()` to read an decimal input from the user (it doesn't convert string to int type as `Double.valueOf` does)..

```java
String valueAsString = "42.42";
double value = Double.valueOf(valueAsString);

Scanner sc = new Scanner(System.in);
double decimal = sc.nextDouble();

System.out.println(value); // 42.42
```

# Reading Booleans

- The `Integer.valueOf` command converts a string to an integer and the `Double.valueOf` converts it to a floating-point. The `valueOf` command also appears when converting a string to a boolean — this is done with the command `Boolean.valueOf`.

- Boolean variables can either have the value `true` or `false`. When converting a string to a boolean, the string must be "true" if we want the boolean value to be `true`. The case is insensitive here: both "true" and "TRue" turn into the boolean value of `true`. All other strings turn into the boolean `false`.

- On the contrary, you can use `nextBoolean()` to read an integer input from the user (it doesn't convert string to int type as `Boolean.valueOf` does).

```java
import java.util.Scanner;

public class program {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Write a boolean ");
        boolean value = Boolean.valueOf(scanner.nextLine());
        System.out.println("You wrote " + value);

        System.out.println("Write a boolean ");
        boolean anotherValue = scanner.nextBoolean();
        System.out.println("You wrote " + value);

        System.out.println("Write a boolean ");
        boolean val = Boolean.valueOf(scanner.nextLine());
        System.out.println("You wrote " + value);
    }
}
/* OUTPUT
Write a boolean
-> I wont'!
You wrote false

Write a boolean
-> TRUE
You wrote true

Write a boolean
-> true
You wrote true
*/
```

# Wrapper Classes

- A wrapper class in Java is a class that provides a way to use primitive data types as objects. Each primitive data type has a corresponding wrapper class, which encapsulates the primitive value and provides additional functionality.

- For example, the Integer wrapper class encapsulates the int primitive data type. It provides methods such as intValue(), which returns the primitive int value, and toString(), which returns a string representation of the integer.

- Wrapper classes are often used in collections, such as ArrayList and HashMap, which can only store objects. They are also used when passing primitive data types to methods that expect objects.

```java
Integer myInt = new Integer(10);
int myPrimitiveInt = myInt.intValue(); // The intValue() method converts the Integer object to a primitive int. This was especially necessary before Java 5, when automatic conversion (autoboxing/unboxing) was not available.
```

- In this example, we create an Integer object wrapper around the primitive int value 10. We then use the intValue() method to get the primitive int value back.

# Autoboxing and Unboxing

- Autoboxing and unboxing are two features of the Java programming language that automatically convert primitive data types to their corresponding object wrapper classes and vice versa. This eliminates the need to explicitly box and unbox primitive values, which can make code more concise and readable.

- Here is a table of the primitive types and their corresponding wrapper classes:
  Primitive Type |Wrapper Class
  ---|---
  byte |Byte
  short |Short
  int |Integer
  long |Long
  float |Float
  double |Double
  char |Character
  boolean |Boolean

- For example, the following code will automatically box the primitive value 10 into an Integer object:

```java
int i = 10;
Integer myInteger = i; // Autoboxing
```

- Similarly, the following code will automatically unbox the Integer object myInteger into a primitive int value:

```java
Integer myInteger = 10;
int i = myInteger; // Unboxing
```

- Autoboxing and unboxing can be used in a variety of situations, such as:
  > When passing primitive values to methods that expect object parameters
  > When storing primitive values in collections
  > When performing arithmetic operations on primitive values
