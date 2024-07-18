# Reading From the Keyboard

- We've been using the `Scanner`-class since the beginning of this course to read user input. The block in which data is read has been a while-true loop where the reading ends at a specific input.

```java
Scanner scanner = new Scanner(System.in);

while (true) {
    String line = scanner.nextLine();

    if (line.equals("end")) {
        break;
    }

    // add the read line to a list for later
    // handling or handle the line immediately

}
```

- In the example above, we pass system input (`System.in`) as a parameter to the constructor of the Scanner-class. In text-based user interfaces, the input of the user is directed into the input stream one line at a time, which means that the information is sent to be handled every time the user enters a new line.

# Reading From a File

- Reading a file is done using the Scanner-class.

- When we want to read a file using the Scanner-class, we give the path for the file we want to read as a parameter to the constructor of the class.

- The path to the file can be acquired using Java's `Paths.get` command, which is given the file's name in string format as a parameter: `Paths.get("filename.extension")`.

- When the `Scanner`-object that reads the file has been created, the file can be read using a while-loop.

- The reading proceeds until all the lines of the file have been read, i.e., until the scanner finds no more lines to read. Reading a file may result in an error, and it's for this reason that the process requires separate blocks - one for the `try`, and another to `catch` potential errors.

```java
// first
import java.util.Scanner;
import java.nio.file.Paths;

// in the program:

// we create a scanner for reading the file
try (Scanner scanner = new Scanner(Paths.get("file.txt"))) {

    // we read the file until all lines have been read
    while (scanner.hasNextLine()) {
        // we read one line
        String row = scanner.nextLine();
        // we print the line that we read
        System.out.println(row);
    }
} catch (Exception e) {
    System.out.println("Error: " + e.getMessage());
}
```

- A file is read from the project root by default ( when `new Scanner(Paths.get("file.txt"))` is called), i.e., the folder that contains the folder `src` and the file `pom.xml` (and possibly other files as well). The contents of this folder can the inspected using the `Files`-tab in NetBeans.

# An Empty Line In a File

- Sometimes an empty line finds it way into a file. Skipping an empty line can be done using the command `continue` and the `isEmpty`-method of the string.

```java
// we create a scanner for reading the file
try (Scanner scanner = new Scanner(Paths.get("henkilot.csv"))) {

    // we read all the lines of the file
    while (scanner.hasNextLine()) {
        String line = scanner.nextLine();

        // if the line is blank we do nothing
        if (line.isEmpty()) {
            continue;
        }

        // do something with the data

    }
} catch (Exception e) {
    System.out.println("Error: " + e.getMessage());
}
```

# Reading Data of a Specific Format From a File

- Data is often stored in files using a specific format. One such format that's already familiar to us is comma-separated values (CSV) format, i.e., data separated by commas.

```java
Scanner scanner = new Scanner(System.in);

while (true) {
    System.out.print("Enter name and age separated by a comma: ");
    String line = scanner.nextLine();

    if (line.equals("")) {
        break;
    }

    String[] parts = line.split(",");
    String name = parts[0];
    int age = Integer.valueOf(parts[1]);

    System.out.println("Name: " + name);
    System.out.println("Age: " + age);
}
/*OUTPUT
Enter name and age separated by a comma:
-> virpi,19
Name: virpi
Age: 19
Enter name and age separated by a comma:
-> jenna,21
Name: jenna
Age: 21
Enter name and age separated by a comma:
-> ada,20
Name: ada
Age: 20
*/
```

# Reading Objects From a File

- Creating objects from data that is read from a file is straightforward. Let's assume that we have a class called `Person`, as well as the data from before.

```java
ArrayList<Person> people = new ArrayList<>();

try (Scanner scanner = new Scanner(Paths.get("records.txt"))) {

    while (scanner.hasNextLine()) {
        String line = scanner.nextLine();

        String[] parts = line.split(",");
        String name = parts[0];
        int age = Integer.valueOf(parts[1]);

        people.add(new Person(name, age));
    }
}

System.out.println("Total amount of people read: " + people.size());

```
