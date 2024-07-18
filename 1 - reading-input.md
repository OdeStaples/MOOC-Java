# Reading Input

- For reading input, we use the `Scanner` tool that comes with Java. The tool can be imported for use in a program by adding the command `import java.util.Scanner;` before the beginning of the main program's frame (`public class` ...). The tool itself is created with `Scanner scanner = new Scanner(System.in);`.

  ```java
  import java.util.Scanner;

  public class Program {

      public static void main(String[] args) {
          Scanner scanner = new Scanner(System.in);

          // We can now use the scanner tool.
          // This tool is used to read input.
      }
  }
  ```

- Below is an example of a program which asks for user input, reads the string entered by the user, and then prints it.

  ```java
  // Introduce the scanner tool used for reading user input
  import java.util.Scanner;

  public class Program {

      public static void main(String[] args) {
          // Create a tool for reading user input and name it scanner
          Scanner scanner = new Scanner(System.in);

          // Print "Write a message: "
          System.out.println("Write a message: ");

          // Read the string written by the user, and assign it
          // to program memory "String message = (string that was given as input)"
          String message = scanner.nextLine();

          // Print the message written by the user
          System.out.println(message);
      }
  }

  // OUTPUT:
  // Write a message:
  // -> Hello world
  // Hello world
  ```

- More precisely, input is read with the `scanner` tool's `nextLine()` method. The call `scanner.nextLine()` is left waiting for the user to write something. When user writes something and presses enter, the provided string is assigned to a **string variable** (in this instance `message`). The program is then able to reference the variable `message` later on — in the example above, the variable `message` is referenced in the print command.

# Reading Strings

- The `reader.nextLine();` command reads the user's input and returns a string. If we then want to use the string in the program, it must be saved to a string variable — `String message = scanner.nextLine();`. A value saved to a variable can be used repeatedly. In the example below, the user input is printed twice.

  ```java
  //Introduce the Scanner tool used for reading
  import java.util.Scanner;

  public class Program {

      public static void main(String[] args) {

          //Create the tool for reading, assign it to variable caller "scanner
          Scanner scanner = new Scanner(System.in);

          //Print user a message "Write a message: "
          System.out.println("Write a message: ");

          //Read the user's string input, save it to program memory
          //"String message = (user input)"
          String message = scanner.nextLine();

          // Print the user input twice
          System.out.println(message);
          System.out.println(message);
      }
  }
  // OUTPUT
  // Write a message:
  // -> This will be printed twice...
  // This will be printed twice...
  // This will be printed twice...
  ```

# Program Execution Waits for Input

- When the program's execution comes a statement that attempts to read input from the user (the command `reader.nextLine()`), the execution stops and waits. The execution continues only after the user has written some input and pressed enter.

- In the example below, the program prompts the user for three strings. First, the program prints `Write the first string: `, and then waits for user input. When the user writes some text, the program prints `Write the second string: `, and then waits for user input again. This continues for a third time, after which the program prints all three strings.

  ```java
  import java.util.Scanner;

  public class Program {

      public static void main(String[] args) {
          Scanner scanner = new Scanner(System.in);

          System.out.println("Write the first string:");
          String first = scanner.nextLine();
          System.out.println("Write the second string:");
          String second = scanner.nextLine();
          System.out.println("Write the third string:");
          String third = scanner.nextLine();

          System.out.println("You wrote:");
          System.out.println(first);
          System.out.println(second);
          System.out.println(third);
      }
  }
  // OUTPUT
  // Write the first string:
  // ->The first
  // Write the second string:
  // ->second
  // Write the third string:
  // third
  // You wrote:
  // The first
  // second
  // third
  ```

### Note: Java is lexically/static scoped

    ```java
    public class MyClass {
    public static void main(String[] args) {
        int x = 10;
        int y = 20;

        // This is a block of code.
        {
        int z = 30;

        // This code can access the variables x, y, and z.
        System.out.println(x + y + z); // 60
        }

        // This code can only access the variables x and y.
        System.out.println(x + y); // 30
    }
    }
    ```
