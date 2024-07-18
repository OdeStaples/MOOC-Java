# Objects in a list

- The type parameter used in creating a list defines the type of the variables that are added to the list. For instance, `ArrayList<String>` includes strings, `ArrayList<Integer>` integers, and `ArrayList<Double>` floating point numbers.

- In the example below we first add strings to a list, after which the strings in the list are printed one by one.

```java
ArrayList<String> names = new ArrayList<>();

// string can first be stored in a variable
String name = "Betty Jennings";
// then add it to the list
names.add(name);

// strings can also be directly added to the list:
names.add("Betty Snyder");
names.add("Frances Spence");
names.add("Kay McNulty");
names.add("Marlyn Wescoff");
names.add("Ruth Lichterman");

// several different repeat statements can be
// used to go through the list elements

// 1. while loop
int index = 0;
while (index < names.size()) {
    System.out.println(names.get(index));
    index = index + 1;
}

// 2. for loop with index
for (int i = 0; i < names.size(); i++) {
    System.out.println(names.get(i));
}

System.out.println();
// 3. for each loop (no index)
for (String name: names) {
    System.out.println(name);
}
/*OUTPUT
Betty Jennings
Betty Snyder
Frances Spence
Kay McNulty
Marlyn Wescoff
Ruth Lichterman

Betty Jennings
Betty Snyder
Frances Spence
Kay McNulty
Marlyn Wescoff
Ruth Lichterman

Betty Jennings
Betty Snyder
Frances Spence
Kay McNulty
Marlyn Wescoff
Ruth Lichterman
*/
```

# Adding object to a list

- Strings are objects, so it should come as no surprise that other kinds of objects can also be found in lists. Next, let's examine the cooperation of lists and objects in more detail.

```java
public class Person {

    private String name;
    private int age;
    private int weight;
    private int height;

    public Person(String name) {
        this.name = name;
        this.age = 0;
        this.weight = 0;
        this.height = 0;
    }

    public String getName() {
        return this.name;
    }

    public int getAge() {
        return this.age;
    }

    public void growOlder() {
        this.age = this.age + 1;
    }

    public void setHeight(int newHeight) {
        this.height = newHeight;
    }

    public void setWeight(int newWeight) {
        this.weight = newWeight;
    }

    public double bodyMassIndex() {
        double heightDivByHundred = this.height / 100.0;
        return this.weight / (heightDivByHundred * heightDivByHundred);
    }

    @Override
    public String toString() {
        return this.name + ", age " + this.age + " years";
    }
}
```

- Handling objects in a list is not really different in any way from the previous experience we have with lists. The essential difference is only to define the type for the stored elements when you create the list.

- In the example below we first create a list meant for storing Person type object, after which we add persons to it. Finally the person objects are printed one by one.

```java
ArrayList<Person> persons = new ArrayList<>();

// a person object can be created first
Person john = new Person("John");
// and then added to the list
persons.add(john);

// person objects can also be created "in the same sentence" that they are added to the list
persons.add(new Person("Matthew"));
persons.add(new Person("Martin"));

for (Person person: persons) {
    System.out.println(person);
}

/*OUTPUT
John, age 0 years
Matthew, age 0 years
Martin, age 0 years
*/
```

# Adding user-inputted objects to a list

```java
Scanner scanner = new Scanner(System.in);
ArrayList<Person> persons = new ArrayList<>();

// Read the names of persons from the user
while (true) {
    System.out.print("Enter a name, empty will stop: ");
    String name = scanner.nextLine();
    if (name.isEmpty()) {
        break;
    }


    // Add to the list a new person
    // whose name is the previous user input
    persons.add(new Person(name));
}

// Print the number of the entered persons, and their individual information
System.out.println();
System.out.println("Persons in total: " + persons.size());
System.out.println("Persons: ");

for (Person person: persons) {
    System.out.println(person);
}

/*OUTPUT
Enter a name, empty will stop: -> Alan Kay
Enter a name, empty will stop: -> Ivan Sutherland
Enter a name, empty will stop: -> Kristen Nygaard

Persons in total: 3
Persons:
Alan Kay, age 0 years
Ivan Sutherland, age 0 years
Kristen Nygaard, age 0 years
*/
```

# Multiple constructor parameters

- If the constructor demands more than one parameter, you can query the user for more information. Let's assume we have the following constructor for the class `Person`.

```java
public class Person {

    private String name;
    private int age;
    private int weight;
    private int height;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
        this.weight = 0;
        this.height = 0;
    }

    // methods
}
```
