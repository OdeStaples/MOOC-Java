# Loops

- A loop consists of an expression that determines whether or not the code within the loop should be repeated, along with a block containing the source code to be repeated. A loop takes the following form.

```java
while (_expression_) {
    // The content of the block wrapped in curly brackets
    // The block can have an unlimited amount of content
}
```

# Ending a Loop

- The loop can be broken out of with command `'break'`. When a computer executes the command `'break'`, the program execution moves onto the next command following the loop block.

- The example below is a program that prints numbers from one to five. Note how the variable that's used within the loop is defined before the loop. This way the variable can be incremented inside the loop and the change sticks between multiple iterations of the loop.

```java
int number = 1;

while (true) {
    System.out.println(number);
    if (number >= 5) {
        break;
    }

    number = number + 1;
}

System.out.println("Ready!");

/*
1
2
3
4
5
Ready!
*/
```

# Returning to the Start of the Loop

- When the execution reaches the end of the loop, the execution starts again from the start of the loop. This means that all the commands in the loop have been executed. You can also return to the beginning from other places besides the end with the command `continue`. When the computer executes the command `continue`, the execution of the program moves to the beginning of the loop.

- The example below demonstrates the use of the `continue` command. The program asks the user to input positive numbers. If the user inputs a negative number or a zero, the program prints the message "Unfit number, try again", after which the execution returns to the beginning of the loop. In the previous example, the program read inputs of type string from the user. Similar programs with different input types are also possible. In the example below, the user is asked for numbers until they input a zero.

```java
Scanner scanner = new Scanner(System.in);

while (true) {
    System.out.println("Insert positive integers");
    int number = Integer.valueOf(scanner.nextLine());

    if (number <= 0) {
        System.out.println("Unfit number! Try again.");
        continue;
    }

    System.out.println("Your input was " + number);
}
```

- The program in the example above is repeated infinitely since the `break` command used for exiting the loop is not used. To exit the loop, the `break` command must be added to it.

- In the example below, the program is modified in such a way that the user is asked to input positive numbers. If the user inputs a negative number, the program informs them that the number was unfit and returns to the beginning of the loop. If the number was zero, the program exits the loop.

```java
Scanner scanner = new Scanner(System.in);

while (true) {
    System.out.println("Input positive numbers.");
    int number = Integer.valueOf(scanner.nextLine());

    if (number == 0) {
        break;
    }

    if (number < 0) {
        System.out.println("Unfit number! Try again.");
        continue;
    }

    System.out.println("Your input was " + number);
}
```

# For Loop

- Above, we learned how a `while` loop with a condition can be used to go through numbers in a certain interval.

- The structure of this kind of loop is the following.

```java
int i = 0;
while (i < 10) {
    System.out.println(i);
    i++;
}
```

- The above loop can be split into three parts. First we introduce the variable `i`, used to count the number of times the loop has been executed so far, and set its value to 0: `int i = 0;`. This is followed by the definition of the loop — the loop's condition is `i < 10` so the loop is executed as long as the value of the variable `i` is less than 10. The loop body contains the functionality to be executed `System.out.println(i);`, which is followed by increasing the value of the variable `i++`. The command `i++` is shorthand for `i = i + 1`.

The same can be achieved with a `for` loop like so.

```java
for (int i = 0; i < 10; i++) {
    System.out.println(i);
}
```

- A for loop contains four parts:
  (1) introducing the variable for counting the number of executions;
  (2) the condition of the loop;
  (3) increasing (or decreasing or changing) the value of the counter variable; and (4) the functionality to be executed.

```java
for (*introducing a variable*; *condition*; *increasing the counter*) {
    // Functionality to be executed
}
```
