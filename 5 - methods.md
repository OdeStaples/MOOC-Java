# Methods

- A method is a named set of statements. It's a piece of a program that can be called from elsewhere in the code by the name given to the method. For instance `System.out.println("I am a parameter given to the method!")` calls a methods that performs printing to the screen. The internal implementation of the method — meaning the set of statements to be executed — is hidden, and the programmer does not need to concern themselves with it when using the method.

# Custom Methods

- A method means a named set consisting of statements that can be called from elsewhere in the program code by its name. Programming languages offer pre-made methods, but programmers can also write their own ones. It would, in fact, be quite exceptional if a program used no methods written by the programmer, because methods help in structuring the program. From this point onward nearly every program on the course will therefore contain custom-created methods.

```java
import java.util.Scanner;

public class Example {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        // program code
    }

    // your own methods here
    public static void greet() {
        System.out.println("Greetings from the method world!");
    }
}
```

- The definition of the method consists of two parts. The first line of the definition includes the name of the method, i.e. `greet`. On the left side of the name are the keywords `public static void`. Beneath the line containing the name of the method is a code block surrounded by curly brackets, inside of which is the code of the method — the commands that are executed when the method is called. The only thing our method `greet` does is write a line of text on the screen.

- Calling a custom method is simple: write the name of the methods followed by a set of parentheses and the semicolon. In the following snippet the main program (main) calls the greet method four times in total.

```java
import java.util.Scanner;

public class ProgramStructure {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // program code
        System.out.println("Let's try if we can travel to the method world:");
        greet();

        System.out.println("Looks like we can, let's try again:");
        greet();
        greet();
        greet();
    }

    // own methods
    public static void greet() {
        System.out.println("Greetings from the method world!");
    }
}
/* OUTPUT
Let's try if we can travel to the method world:
Greetings from the method world!
Looks like we can, let's try again:
Greetings from the method world!
Greetings from the method world!
Greetings from the method world!
*/
```

- The order of execution is worth noticing. The execution of the program happens by executing the lines of the main method (`main`) in order from top to bottom, one at a time. When the encountered statement is a method call, the execution of the program moves inside the method in question. The statements of the method are executed one at a time from top to bottom. After this the execution returns to the place where the method call occured, and then proceeds to the next statement in the program.

- Strictly speaking, the main program (`main`) itself is a method. When the program starts, the operating system calls `main`. The main method is the starting point for the program, since the execution begins from its first line. The execution of a program ends at the end of the main method.

# Method Parameters

- **Parameters** are values given to a method that can be used in its execution. The parameters of a method are defined on the uppermost line of the method within the parentheses following its name. The values of the parameters that the method can use are copied from the values given to the method when it is executed.

- In the following example a parameterized method `greet` is defined. It has an `int` type parameter called `numOfTimes`.

```java
public static void main(String[] args) {
    greet(1);
    System.out.println("");
    greet(1+2);
}

public static void greet(int numOfTimes) {
    int i = 0;
    while (i < numOfTimes) {
        System.out.println("Greetings!");
        i++;
    }
}

/* OUTPUT
Greetings!

Greetings!
Greetings!
Greetings!
*/
```

# Parameter Values Are Copied in a Method Call

- As a method is called the **values of its parameters are copied**. In practice, this means that both the main method and the method to be called can use variables with the same name. However, changing the value of the variables inside the method does not affect the value of the variable in the main method that has the same name. Let's examine this behavior with the following program. We define a variable called `number` in the main method. That variable is passed as a parameter to the method `incrementByThree`.

```java
// main program
public static void main(String[] args) {
    int number = 1;
    System.out.println("The value of the variable 'number' in the main program: " + number);
    incrementByThree(number);
    System.out.println("The value of the variable 'number' in the main program: " + number);
}

// method
public static void incrementByThree(int number) {
    System.out.println("The value of the method parameter 'number': " + number);
    number = number + 3;
    System.out.println("The value of the method parameter 'number': " + number);
}

/* OUTPUT
The value of the variable 'number' in the main program: 1
The value of the method parameter 'number': 1
The value of the method parameter 'number': 4
The value of the variable 'number' in the main program: 1
*/
```

- When the variable `number` is incremented inside the method, there's no issue. This, however, is not reflected in the `number` variable of the main program. The `number` variable living in the main program is different from the `number` variable of the method.

# Methods Can Return Values

- The definition of a method tells whether that method returns a value or not. If it does, the method definition has to include the type of the returned value. Otherwise the keyword `void` is used in the definition. The methods we've created so far have been defined with the keyword `void`, meaning that they have not returned values.

- The keyword `void` means that the method returns nothing. If we want the method to return a value, the keyword must be replaced with the type of the return variable. In the following example, there is a method called `alwaysReturnsTen` which returns an integer-type (`int`) variable (in this case the value 10). To actually return a value, we use the command `return` followed by the value to be returned (or the name of the variable whose value is to be returned).

```java
public static int alwaysReturnsTen() {
    return 10;
}
```

- The method defined above returns an `int`-type value of `10` when called. For the return value to be used, it must be stored in a variable. This is done the same way as regular value assignment to a variable, by using an equals sign.

- The lines of source code following the command `return` are never executed. If a programmer adds source code after the return to a place which can never be reached during the method's execution, the IDE will produce an error message.

# Defining Variables Inside Methods

- Defining variables inside methods is done in the same manner as in the "main program". The following method calculates the average of the numbers it receives as parameters. Variables `sum` and `avg` are used to help in the calculation.

# Execution of Method Calls and the Call Stack

- The environment that executes Java source code keeps track of the method being executed in the call stack. The **call stack** contains frames, each of which includes information about a specific method's internal variables and their values. When a method is called, a new frame containing its variables is created in the call stack. When the execution of a method ends, the frame relating to a method is removed from the call stack, which leads to execution resuming at the previous method of the stack.

- When a method is called, the execution of the calling method is left waiting for the execution of the called method to end. This can be visualized with the help of a call stack. The call stack refers to the stack formed by the method calls — the method currently being executed is always on the top of the stack, and when that method has finished executing the execution moves on to the method that is next on the stack. Let's examine the following program:

```java
public static void main(String[] args) {
    System.out.println("Hello world!");
    printNumber();
    System.out.println("Bye bye world!");
}

public static void printNumber() {
    System.out.println("Number");
}
```

- The execution begins from the first line of the `main` method when the program is run. The command on this line prints the text `"Hello world!"`. The call stack of the program looks as follows:

  > main

- Once the print command has been executed, we move on to the next command, which calls the method `printNumber`. Calling this method moves the execution of the program to the beginning of the method `printNumber`. Meanwhile, the `main` method will await for the execution of the method `printNumber` to end. While inside the method printNumber, the call stack looks like this:

  > printNumber
  > main

- Once the method `printNumber` completes, we return to the method that is immediately below the method `printNumber` in the call stack — which in this case is the method main. `printNumber` is removed from the call stack, and the execution continues from the line after the `printNumber` method call in the `main` method. The state of the call stack is now the following:

  > main
