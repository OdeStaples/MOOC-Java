# Stack Trace

- When an error occurs in a program, the program typically prints something called a stack trace, i.e., the list of method calls that resulted in the error. For example, a stack trace might look like this:

  > Exception in thread "main" ...
  > at Program.main(Program.java:15)

- The type of error is stated at the beginning of the list, and the following line tells us where the error occurred. The line "at Program.main(Program.java:15)" says that the error occurred at line number 15 in the Program.java file.

# Checklist for Troubleshooting

1. Indent your code properly and find out if there are any missing parentheses.
   Verify that the variables used are correctly named.

2. Test the program flow with different inputs and find out the sort of input that causes the program to not work as desired. If you received an error in the tests, the tests may also indicate the input used.

3. Add print commands to the program in which you print out the values of the variables used at various stages of the program's execution.

4. Verify that all variables you are using are initialized. If they aren't, a NullPointerException error will occur.

5. If your program causes an exception, you should definitely pay attention to the stack trace associated with the exception, which is the list of method calls that resulted in the situation that caused the exception.

6. Learn how to use the debugger. The earlier video will get you started.

# Passing Test Input to Scanner

- Manually testing the program is often laborious. It's possible to automate the passing of input by, for example, passing the string to be read into a Scanner object.

- The test input can be given as a string to the Scanner object in the constructor. Each line break in the test feed is marked on the string with a combination of a backslash and an n character "\n".

```java
String input = "one\n" + "two\n"  +
                "three\n" + "four\n" +
                "five\n" + "one\n"  +
                "six\n";

Scanner reader = new Scanner(input);

ArrayList<String> read = new ArrayList<>();

while (true) {
    System.out.println("Enter an input: ");
    String line = reader.nextLine();
    if (read.contains(line)) {
        break;
    }

    read.add(line);
}

System.out.println("Thank you!");

if (read.contains("six")) {
    System.out.println("A value that should not have been added to the group was added to it.");
}

/*OUTPUT
Enter an input:
Enter an input:
Enter an input:
Enter an input:
Enter an input:
Enter an input:
Thank you!
*/
```

- Passing a string to the constructor of the Scanner class replaces input read from the keyboard. As such, the content of the string variable `input` 'simulates' user input.

- A line break in the input is marked with `\n`. Therefore, each part ending in an newline character in a given string input corresponds to one input given to the `nextLine()` command.

# Creating a unit testing file in TMCBeans

- Click open the folder Project Files, and double click the `‘pom.xml’` file.

- Paste the contents after <properties></properties>

  ```
  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.12</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
  ```

- Once the contents above are copied into the pom.xml file (before the line `</project>`), save the file.

- This gives the project access to the JUnit library and enables us to write unit tests.

- Let’s create the first unit test. You can create unit tests by `right-clicking the project and choosing new -> Other`.

- Then press `“Next”`.

- Set the class name as ‘`<fileName>Test`’ and choose not to generate code in the class.

- Press Finish when ready.

### NB! Ensure that the class name ends with “Test”. The string `Test` at the end of the name tells the programming environment that this is a test class. Without the string Test, the tests in the class will not be executed.

# Unit Testing

- Let's take a look at writing unit tests with the help of an example. Let's assume that we have the following Calculator class and want to write automated tests for it.

```java
public class Calculator {

    private int value;

    public Calculator() {
        this.value = 0;
    }

    public void add(int number) {
        this.value = this.value + number;
    }

    public void subtract(int number) {
        this.value = this.value + number;
    }

    public int getValue() {
        return this.value;
    }
}
```
