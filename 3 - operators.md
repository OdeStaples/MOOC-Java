# Comparision Operators

- `>` greater than
- `>=` greater than or equal to
- `<` less than
- `<=` less than or equal to
- `==` equal to
- `!=` not equal to

# If-Else

- If the expression inside the parentheses of the conditional statement evaluates to false, then the execution of the code moves to the statement following the closing curly bracket of the current conditional statement. This is not always desired, and usually we want to create an alternative option for when the conditional expression evaluates to false.

This can be done with the help of the `else` command, which is used together with the `if` command.

```java
int number = 4;

if (number > 5) {
    System.out.println("Your number is greater than five!");
} else {
    System.out.println("Your number is five or less!");
}
/* OUTPUT
Your number is five or less!
*/
```

- If an `else` branch has been specified for a conditional statement, the block defined by the else branch is run in the case that the condition of the conditional statement is false. The `else`-command is placed on the same line as the closing bracket of the block defined by the `if`-command.

# More Conditionals: else if

- In the case of multiple conditionals, we use the `else if`-command. The command `else if` is like `else`, but with an additional condition. `else if` follows the `if`-condition, and they may be multiple.

```java
int number = 3;

if (number == 1) {
    System.out.println("The number is one");
} else if (number == 2) {
    System.out.println("The given number is two");
} else if (number == 3) {
    System.out.println("The number must be three!");
} else {
    System.out.println("Something else!");
}

// OUTPUT
// The number must be three!
```

# Conditional Statement Expression and the Boolean Variable

- The value that goes between the parentheses of the conditional statement should be of type boolean after the evaluation. `boolean` type variables are either true or false.

```java
boolean isItTrue = true;
System.out.println("The value of the boolean variable is " + isItTrue); // The value of the boolean variable is true
```

# Conditional Statements and Comparing Strings

- Even though we can compare integers, floating point numbers, and boolean values using two equals signs (`variable1 == variable2`), we cannot compare the equality of strings using two equals signs.

```java
Scanner reader = new Scanner(System.in);

System.out.println("Enter the first string");
String first = reader.nextLine();
System.out.println("Enter the second string");
String second = reader.nextLine();

if (first == second) {
    System.out.println("The strings were the same!");
} else {
    System.out.println("The strings were different!");
}
/*OUTPUT
Enter the first string
->same
Enter the second string
->same
The strings were different!
*/
```

- This has to do with the internal workings of strings as well as how variable comparison is implemented in Java. In practice, the comparison is affected by how much information a variable can hold — strings can hold a limitless amount of characters, whereas integers, floating-point numbers, and boolean values always contain a single number or value only. Variables that always contain only one number or value can be compared using an equals sign, whereas this doesn't work for variables containing more information. We will return to this topic later in this course.

- When comparing strings we use the `equals`-command, which is related to string variables. The command works in the following way:

```java
Scanner reader = new Scanner(System.in);

System.out.println("Enter a string");
String input = reader.nextLine();

if (input.equals("a string")) {
    System.out.println("Great! You read the instructions correctly.");
} else {
    System.out.println("Missed the mark!");
}

/*OUTPUT
Enter a string
-> ok!
Missed the mark!

Enter a string
->a string
Great! You read the instructions correctly.
*/
```

- The equals command is written after a string by attaching it to the string to be compared with a dot. The command is given a parameter, which is the string that the variable will be compared against. If the string variable is being directly compared with a string, then the string can be placed inside the parentheses of the equals-command within quotation marks. Otherwise, the name of the string variable that holds the string to be compared is placed inside the parentheses.

- In the example below the user is prompted for two strings. We first check to see if the provided strings are the same, after which we'll check if the value of either one of the two strings is "two strings".

```java
Scanner reader = new Scanner(System.in);

System.out.println("Input two strings");
String first = reader.nextLine();
String second = reader.nextLine();

if (first.equals(second)) {
    System.out.println("The strings were the same!");
} else {
    System.out.println("The strings were different!");
}

if (first.equals("two strings")) {
    System.out.println("Clever!");
}

if (second.equals("two strings")) {
    System.out.println("Sneaky!");
}

/*OUTPUT
Input two strings
->hello
->world
The strings were different!

Input two strings
->two strings
->world
The strings were different!
Clever!
*/
```

# Logical Operators

- The expression of a conditional statement may consist of multiple parts, in which the logical operators and `&&`, or `||`, and not `!` are used.

- In the next example we combine two individual conditions using `&&,` i.e., the and-operator. The code is used to check if the number in the variable is greater than or equal to 5 and less than or equal to 10. In other words, whether it's within the range of 5-10:

```java
System.out.println("Is the number within the range 5-10: ");
int number = 7;

if (number >= 5 && number <= 10) {
    System.out.println("It is! :)");
} else {
    System.out.println("It is not :(")
}

/* OUTPUT
Is the number within the range 5-10:
It is! :)
*/
```

- In the next one we provide two conditions using `||`, i.e., the or-operator: is the number less than zero or greater than 100. The condition is fulfilled if the number fulfills either one of the two conditions:

```java
System.out.println("Is the number less than 0 or greater than 100");
int number = 145;

if (number < 0 || number > 100) {
    System.out.println("It is! :)");
} else {
    System.out.println("It is not :(")
}
/* OUTPUT
Is the number less than 0 or greater than 100
It is! :)
*/
```

- In this example we flip the result of the expression `number > 4` using `!`, i.e., the not-operator. The not-operator is written in such a way that the expression to be flipped is wrapped in parentheses, and the not-operator is placed before the parentheses.

```java
int number = 7;

if (!(number > 4)) {
    System.out.println("The number is not greater than 4.");
} else {
    System.out.println("The number is greater than 4.")
}

// OUTPUT
// The number is greater than 4.
```
