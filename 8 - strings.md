# Splitting a String

- You can split a string to multiple pieces with the `split`-method of the String class. The method takes as a parameter a string denoting the place around which the string should be split. The `split` method returns an array of the resulting sub-parts. In the example below, the string has been split around a space.

```java
String text = "first second third fourth";
String[] pieces = text.split(" ");
System.out.println(pieces[0]);
System.out.println(pieces[1]);
System.out.println(pieces[2]);
System.out.println(pieces[3]);

System.out.println();

for (int i = 0; i < pieces.length; i++) {
    System.out.println(pieces[i]);
}
/*OUTPUT
first
second
third
fourth

first
second
third
fourth
*/
```

# Length of string

- The length of a string is calculated by `length()` method

```java
String word = "equisterian";
int length = word.length();
System.out.println("The length of the word" + word + " is " + length); // The length of the word equisterian is 11
```

# Data of Fixed Format

- Splitting strings is used particularly when the data is of a fixed format. This refers to data that adheres to some predefined format. An example of this of this is the comma-separated values (`csv`) format, where commas are used to separate values. Below you'll find an example of data in csv form containing names and ages. The first column contains names and the second one ages. The columns are separated by a comma.

-> sebastian,2
-> lucas,2
-> lily,1

```java
Scanner reader = new Scanner(System.in);

while (true) {
    String input = reader.nextLine();
    if (input.equals("")) {
        break;
    }

    String[] pieces = input.split(",");
    System.out.println("Name: " + pieces[0] + ", age: " + pieces[1]);
}
/*OUTPUT
->sebastian,2
Name: sebastian, age: 2
->lucas,2
Name: lucas, age: 2
->lily,1
Name: lily, age: 1
*/
```

- You can get a character at a specified index of a string with the `charAt` method.

```java
String text = "Hello world!";
char character = text.charAt(0);
System.out.println(character);

// OUTPUT
// H
```
