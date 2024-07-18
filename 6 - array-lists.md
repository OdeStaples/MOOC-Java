# ArrayLists

- ArrayList is a pre-made tool in Java that helps dealing with lists. It offers various methods, including ones for adding values to the list, removing values from it, and also for the retrieval of a value from a specific place in the list. The concrete implementations — i.e., how the list is actually programmed — has been abstracted behind the methods, so that a programmer making use of a list doesn't need to concern themselves with its inner workings.

- From the point of view of the programmer, the size of the ArrayList is unlimited. In reality there are no magic tricks in the ArrayList — they have been programmed like any other programs or tools offered by the programming language. When you create a list, a limited space is reserved in the memory of the computer. When the ArrayList runs out of space, a larger space is reserved and the data from the previous space is copied to the new one.

# Using and Creating Lists

- For an ArrayList to be used, it first needs be imported into the program. This is achieved by including the command `import java.util.ArrayList;` at the top of the program.

- Creating a new list is done with the command `ArrayList<Type> list = new ArrayList<>()`, where Type is the type of the values to be stored in the list (e.g. `String`). We create a list for storing strings in the example below.

```java
// import the list so the program can use it
import java.util.ArrayList;

public class Program {

    public static void main(String[] args) {
        // create a list
        ArrayList<String> list = new ArrayList<>();

        // the list isn't used yet
    }
}
```

- The type of the ArrayList variable is `ArrayList`. When a list variable is initialized, the type of the values to be stored is also defined in addition to the variable type — all the variables stored in a given list are of the same type. As such, the type of an ArrayList that stores strings is `ArrayList<String>`. A new list is created with the command `new ArrayList<>();`.

# Defining the Type of Values That a List Can Contain

- When defining the type of values that a list can include, the first letter of the element type has to be capitalized. A list that includes int-type variables has to be defined in the form `ArrayList<Integer>;` and a list that includes double-type variables is defined in the form `ArrayList<Double>`.

- The reason for this has to do with how the ArrayList is implemented. Variables in Java can be divided into two categories: `value type (primitive) and reference type (reference type)` variables. **Value-type** variables such as `int` or `double` hold their actual values. **Reference-type** variables such as `ArrayList`, in contrast, contain a reference to the location that contains the value(s) relating to that variable.

- Value-type variables can hold a very limited amount of information, whereas references can store a near limitless amount of it.

- You'll find examples below of creating lists that contain different types of values.

```java
ArrayList<Integer> list = new ArrayList<>();
list.add(1);

ArrayList<Double> list = new ArrayList<>();
list.add(4.2);

ArrayList<Boolean> list = new ArrayList<>();
list.add(true);

ArrayList<String> list = new ArrayList<>();
list.add("String is a reference-type variable");
```

- Once a list has been created, ArrayList assumes that all the variables contained in it are reference types. Java automatically converts an `int` variable into `Integer` when one is added to a list, and the same occurs when a variable is retrieved from a list. The same conversion occurs for `double`-type variables, which are converted to `Double`. This means that even though a list is defined to contain `Integer`-type variables, variables of type `int` can also be added to it.

```java
ArrayList<Integer> integers = new ArrayList<>();
int integer = 1;
integers.add(integer); // autoboxing

ArrayList<Double> doubles = new ArrayList<>();
double d = 4.2;
doubles.add(d); // autoboxing
```

# Adding to a List and Retrieving a Value from a Specific Place

- The next example demonstrates the addition of a few strings into an ArrayList containing strings. Addition is done with the list method `add`, which takes the value to be added as a parameter. We then print the value at position zero. To retrieve a value from a certain position, you use the list method `get`, which is given the place of retrieval as a parameter.

- To call a list method you first write the name of the variable describing the list, followed by a dot and the name of the method.

```java
// import list so that the program can use it
import java.util.ArrayList;

public class WordListExample {

    public static void main(String[] args) {
        // create the word list for storing strings
        ArrayList<String> wordList = new ArrayList<>();

        // add two values to the word list
        wordList.add("First");
        wordList.add("Second");

        // retrieve the value from position 0 of the word list, and print it
        System.out.println(wordList.get(0));
        System.out.println(wordList.get(1));
    }
}
// OUTPUT
// First
// Second
```

- As can be seen, the `get` method retrieves the first value from the list when it is given the parameter `0`. This is because **list positions are counted starting from zero**. The first value is found by `wordList.get(0)`, the second by `wordList.get(1)`, and so on.

# Retrieving Information from a "Non-Existent" Place

- If you try to retrieve information from a place that does not exist on the list, the program will print a `IndexOutOfBoundsException` error. In the example below, two values are added to a list, after which there is an attempt to print the value at place two on the list.

```java
import java.util.ArrayList;

public class Example {

    public static void main(String[] args) {
        ArrayList<String> wordList = new ArrayList<>();

        wordList.add("First");
        wordList.add("Second");

        System.out.println(wordList.get(2));
    }
}
/* OUTPUT
Exception in thread "main" java.lang.IndexOutOfBoundsException: Index: 2, Size: 2
at java.util.ArrayList.rangeCheck(ArrayList.java:653)
at java.util.ArrayList.get(ArrayList.java:429)
at Example.main(Example.java:(line))
Java Result: 1
*/
```

- Since the numbering (i.e., **indexing**) of the list elements starts with zero, the program isn't able to find anything at place two and its execution ends with an error.

- The error message provides hints of the internal implementation of an ArrayList object. It lists all the methods that were called leading up to the error. First, the program called the `main` method, whereupon ArrayList's `get` method was called. Subsequently, the get method of ArrayList called the `rangeCheck` method, in which the error occurred. This also acts as a good illustration of proper method naming. Even if we'd never heard of the `rangeCheck` method, we'd have good reason to guess that it checks if a searched place is contained within a given desired range. The error likely occurred because this was not the case.

# Iterating Over a List

- We'll next be examining methods that can be used to go through the values on a list. Let's start with a simple example where we print a list containing four values.

```java
ArrayList<String> teachers = new ArrayList<>();

teachers.add("Simon");
teachers.add("Samuel");
teachers.add("Ann");
teachers.add("Anna");

for(int i = 0;i<teachers.size();i++){
    System.out.println(teachers[i])
}
```

- The number of values on a list is provided by the list's **size** method which returns the number of elements the list contains. The number is an integer (`int`), and it can be used as a part of an expression or stored in an integer variable for later use.

# Iterating Over a List with a For-Each Loop

- If you don't need to keep track of the index as you're going through a list's values, you can make use of the **for-each** loop. It differs from the previous loops in that it has no separate condition for repeating or incrementing.

```java
ArrayList<String> teachers = new ArrayList<>();


teachers.add("Simon");
teachers.add("Samuel");
teachers.add("Ann");
teachers.add("Anna");

for (String teacher: teachers) {
    System.out.println(teacher);
}
```

- In practice, the for-each loop examines the values of the list in order one at a time. The expression is defined in the following format: `for (TypeOfVariable nameOfVariable: nameOfList)`, where `TypeOfVariable` is the list's element type, and `nameOfVariable` is the variable that is used to store each value in the list as we go through it.

# Removing from a List and Checking the Existence of a Value

- The list's **remove** method removes the value that is located at the index that's given as the parameter. The parameter is an integer.

```java
ArrayList<String> list = new ArrayList<>();

list.add("First");
list.add("Second");
list.add("Third");

list.remove(1);

System.out.println("Index 0 so the first value: " + list.get(0));
System.out.println("Index 1 so the second value: " + list.get(1));

/*OUTPUT
Index 0 so the first value: First
Index 1 so the second value: Third
*/
```

- If the parameter given to `remove` is the same type as the values in the list, but not an integer, (integers are used to remove from a given index), it can be used to remove a value directly from the list.

```java
ArrayList<String> list = new ArrayList<>();

list.add("First");
list.add("Second");
list.add("Third");

list.remove("First");

System.out.println("Index 0 so the first value: " + list.get(0));
System.out.println("Index 1 so the second value: " + list.get(1));

/*
Index 0 so the first value: Second
Index 1 so the second value: Third
*/
```

- If the list contains integers, you cannot remove a number value by giving an int type parameter to the remove method. This would remove the number from the index that the parameter indicates, instead of an element on the list that has the same value as the parameter. To remove an integer type value you can convert the parameter to Integer type; this is achieved by the `valueOf` method of the Integer class or `indexOf` method of ArrayList.

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(15);
list.add(18);
list.add(21);
list.add(24);
list.add(28);

list.remove(2);
list.remove(Integer.valueOf(15));
list.remove(list.indexOf(28));

for(int num:list){
    System.out.println(num);
}
// OUTPUT
// 18
// 24
```

- The list method **contains** can be used to check the existence of a value in the list. The method receives the value to be searched as its parameter, and it returns a boolean type value (`true` or `false`) that indicates whether or not that value is stored in the list.

```java
ArrayList<String> list = new ArrayList<>();

list.add("First");
list.add("Second");
list.add("Third");

System.out.println("Is the first found? " + list.contains("First"));

boolean found = list.contains("Second");
if (found) {
    System.out.println("Second was found");
}

// or more simply
if (list.contains("Second")) {
    System.out.println("Second can still be found");
}
/*OUTPUT
Is the first found? true
Second was found
Second can still be found
*/
```

# List as a Method Parameter

- Like other variables, a list can be used as a parameter to a method too. When the method is defined to take a list as a parameter, the type of the parameter is defined as the type of the list and the type of the values contained in that list. Below, the method `print` prints the values in the list one by one.

```java
ArrayList<String> strings = new ArrayList<>();

strings.add("First");
strings.add("Second");
strings.add("Third");

print(strings);

public static void print(ArrayList<String> list) {
    for (String value: list) {
        System.out.println(value);
    }
}
/*OUTPUT
First
Second
Third
*/
```

- The chosen parameter in the method definition is not dependent on the list that is passed as parameter in the method call. In the program that calls `print`, the name of the list variable is `strings`, but inside the method `print` the variable is called `list` — the name of the variable that stores the list could also be `printables`, for instance.

- It's also possible to define multiple variables for a method. In the example the method receives two parameters: a list of numbers and a threshold value. It then prints all the numbers in the list that are smaller than the second parameter.

```java
ArrayList<Integer> list = new ArrayList<>();

list.add(1);
list.add(2);
list.add(3);
list.add(2);
list.add(1);

printSmallerThan(list, 3);

public static void printSmallerThan(ArrayList<Integer> numbers, int threshold) {
    for (int number: numbers) {
        if (number < threshold) {
            System.out.println(number);
        }
    }
}

/*OUTPUT
1
2
2
1
*/
```

- As before, a method can also return a value. The methods that return values have the type of the return value in place of the `void` keyword, and the actual returning of the value is done by the `return` command. The method below returns the size of the list.

```java
public static int size(ArrayList<String> list) {
    return list.size();
}

public static double average(ArrayList<Integer> numbers) {
    if (numbers.size() == 0) {
        return -1.0;
    }

    int sum = 0;
    for (int number: numbers) {
        sum = sum + number;
    }

    return 1.0 * sum / numbers.size();
}
```

# On Copying the List to a Method Parameter

- Earlier we have used integers, floating point numbers, etc. as method parameters. When variables such as `int` are used as method parameters, the value of the variable is copied for the method's use. The same occurs in the case that the parameter is a list.

- Lists, among practically all the variables that can store large amounts of information, are reference-type variables. This means that the value of the variable is a reference that points to the location that contains the information.

- When a list (or any reference-type variable) is copied for a method's use, the method receives the value of the list variable, i.e., a reference. In such a case the **method receives a reference to the real value of a reference-type variable**, and the method is able to modify the value of the original reference type variable, such as a list. In practice, the list that the method receives as a parameter is the same list that is used in the program that calls the method.

Let's look at this briefly with the following method.

```java
public static void removeFirst(ArrayList<Integer> numbers) {
    if (numbers.size() == 0) {
        return;
    }

    numbers.remove(0);
}

ArrayList<Integer> numbers = new ArrayList<>();
numbers.add(3);
numbers.add(2);
numbers.add(6);
numbers.add(-1);

System.out.println(numbers);

removeFirst(numbers);

System.out.println(numbers);

removeFirst(numbers);
removeFirst(numbers);
removeFirst(numbers);

System.out.println(numbers);

/*OUTPUT
[3, 2, 6, -1]
[2, 6, -1]
[]
*/
```

# A Summary of List Methods

- The ArrayList contains a bunch of useful methods. The method always operates on the list object that is connected to the method call — this connection is established with a dot. The example below illustrates that a program can contain multiple lists, which also holds true for other variables. Two separate lists are created below.

- Adding to a list is done with the method `add` that receives the value to be added as a parameter.

```java
ArrayList<String> list = new ArrayList<>();
list.add("hello world!");
```

- The number of elements in a list can be discovered with the non-parameterized method `size`; it returns an integer.

```java
ArrayList<String> list = new ArrayList<>();
int size = list.size();
System.out.println(size);
```

- You can retrieve a value from a certain index with the method `get` that is given the index at which the value resides as a parameter.

```java
ArrayList<String> list = new ArrayList<>();
list.add("hello world!");
String string = list.get(0);
System.out.println(string);
```

- Removing elements from a list is done with the help of `remove`. It receives as a parameter either the value that is to be removed, or the index of the value to be removed.

```java
ArrayList<String> list = new ArrayList<>();
// remove the string "hello world!"
list.remove("hello world!");
 // remove the value at index 3
list.remove(3);
```

- Checking for the existence of a value is done with the method `contains`. It's provided the value being searched for as a parameter, and it returns a boolean value.

```java
ArrayList<String> list = new ArrayList<>();
boolean found = list.contains("hello world!");
```
