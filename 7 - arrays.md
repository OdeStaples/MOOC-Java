# Arrays

- An Array contains a limited amount of numbered spots (indices) for values. The length (or size) of an Array is the amount of these spots, i.e. how many values can you place in the Array. The values in an Array are called **elements**.

# Creating an Array

- There are two ways to create an Array. In the first one you have to explicitly define the size upon the creating. This is how you create an Array to hold three integers:

```java
int[] numbers = new int[3];
```

- An array is declared by adding square brackets after the type of the elements it contains (typeofelements[]). A new Array is created by calling `new` followed by the type of the elements, square brackets and the number of the elements in the square brackets.

- An Array to hold 5 Strings can be created like this:

```java
String[] strings = new String[5];
```

# Assigning and accessing elements

- An element of an Array is referred to by its index. In the example below we create an Array to hold 3 integers, and then assign values to indices 0 and 2. After that we print the values.

```java
int[] numbers = new int[3];
numbers[0] = 2;
numbers[2] = 5;

System.out.println(numbers[0]);
System.out.println(numbers[2]);
```

- Assigning a value to a specific spot of an Array works much like assigning a value in a normal variable, but in the Array you must specify the index, i.e. to which spot you want to assign the value. The index is specified in square brackets. The ArrayList `get`-method works very similarly to accessing an element of an Array. Just the syntax, i.e. the way things are written, is different.

- The index is an integer, and its value is between [0, length of the Array - 1]. For example an Array to hold 5 elements has indices 0, 1, 2, 3, and 4.

```java
Scanner reader = new Scanner(System.in);

int[] numbers = new int[5];
numbers[0] = 42;
numbers[1] = 13;
numbers[2] = 12;
numbers[3] = 7;
numbers[4] = 1;

System.out.println("Which index should we access? ");
int index = Integer.valueOf(reader.nextLine());

System.out.println(numbers[index]);
```

# Size of an array and iterating

- You can find the size of the array through the associated variable `length`. You can access this associated variable by writing name of the array dot name of the variable, i.e. `numbers.length`. Note, that this is not a method call, so `numbers.length()` doesn't work.

```java
int[] numbers = new int[4];
numbers[0] = 42;
numbers[1] = 13;
numbers[2] = 12;
numbers[3] = 7;

System.out.println("The array has " + numbers.length + " elements.");

int index = 0;
while (index < numbers.length) {
    System.out.println(numbers[index]);
    index = index + 1;
}

/*OUTPUT
The array has 4 elements.
42
13
12
7
*/
```

- The example above iterates over indices 0, 1, 2 and 3, and at each index prints the value held in the index. So first it prints `numbers[0]`, then `numbers[1]` etc. The iteration stops, once the condition of the loop `index < number.length` is false, i.e. once the index variable is greater or equal to the length of the array. NB! The iteration doesn't stop the moment the index variable grows too big; the condition is evaluated only in the beginning of the while loop.

- If the index is pointing outside the Array, i.e. the element doesn't exist, we get an `ArrayIndexOutOfBoundsException`. This error tells, that the Array doesn't contain the given index. You cannot access outside of the Array, i.e. index that's less than 0 or greater or equal to the size of the Array.

# Type of the elements

- You can create an array stating the type of the elements of the array followed by square brackets (typeofelements[]). Therefore the elements of the array can be of any type. Here's a few examples:

```java
String[] months = new String[12];
double[] approximations = new double[100];

months[0] = "January";
approximations[0] = 3.14;
```

# Array as a parameter of a method

- You can use arrays as a parameter of a method just like any other variable. As an array is a reference type, the value of the array is a reference to the information contained in the array. When you use array as a parameter of a method, the method receives a copy of the reference to the array.

```java
public static void listElements(int[] integerArray) {
    System.out.println("the elements of the array are: ");
    int index = 0;
    while (index < integerArray.length) {
        int number = integerArray[index];
        System.out.print(number + " ");
        index = index + 1;
    }

    System.out.println("");
}

int[] numbers = new int[3];
numbers[0] = 1;
numbers[1] = 2;
numbers[2] = 3;

listElements(numbers);

// OUTPUT
// the elements of the array are: 1 2 3
```

- As noticed earlier, you can freely choose the name of the parameter inside the method, the name doesn't have to be the same as the name of the variable when you call the method. In the example above, we call the array `integerArray`, meanwhile the caller of the method has named the same array `numbers`.

- Array is an object, so when you change the array inside the method, the changes persist after the execution of the method.

# The shorter way to create an array

- Just like for Strings, there's also a shortcut to create an array. Here we create an array to hold 3 integers, and initiate it with values 100, 1 and 42 in it:

```java
int[] numbers = {100, 1, 42};
String[] arrayOfStrings = {"Matti L.", "Matti P.", "Matti V."};
double[] arrayOfFloatingpoints = {1.20, 3.14, 100.0, 0.6666666667};
```
