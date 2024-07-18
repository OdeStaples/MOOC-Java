# Introduction to object-oriented programming (oop)

- Object-oriented programming is concerned with isolating concepts of a problem domain into separate entities and then using those entities to solve problems. Concepts related to a problem can only be considered once they've been identified. In other words, we can form abstractions from problems that make those problems easier to approach.

# Classes and Objects

- A class defines the attributes of objects, i.e., the information related to them (instance variables), and their commands, i.e., their methods. The values of instance (i.e., object) variables define the internal state of an individual object, whereas methods define the functionality it offers.

- A Method is a piece of source code written inside a class that's been named and has the ability to be called. A method is always part of some class and is often used to modify the internal state of an object instantiated from a class.

- As an example, `ArrayList` is a class offered by Java, and we've made use of objects instantiated from it in our programs. Below, an `ArrayList` object named `integers` is created and some integers are added to it.

- An object is a data type that has instance variables and methods that operate on those instance variables. (More about objects: https://www.reddit.com/r/javahelp/comments/1uh6np/eli5_objects_in_java/)

- In ELI5 terms,

  > Class: A class in Java is like the instructions for building the castle. It tells you what kind of bricks you need, how many of each, and how to put them together. But it's just a blueprint, not the actual castle yet.

  > Object: An object in Java is like the actual castle you built using the instructions. It's a real-world thing that exists and can interact with other objects.

  > Class: Imagine a class called "Animal." This class would define what makes an animal, like having fur, claws, and the ability to move.

  > Object: A dog is an object of the "Animal" class. It has all the features of an animal, but it's also a specific type of animal with its own unique characteristics, like wagging its tail.

> Note: `this` keyword for instance variables is (preferably) used when there are conflicting names, for eg. if an instance variable has name "test" and in constructor, there's also a parameter named "test", in such case `this` keyword is used to avoid conflict.

```java
// we create an object from the ArrayList class named integers
ArrayList<Integer> integers = new ArrayList<>();

// let's add the values 15, 34, 65, 111 to the integers object
integers.add(15);
integers.add(34);
integers.add(65);
integers.add(111);

// we print the size of the integers object
System.out.println(integers.size());
```

- In the above example, the `integers` object has helper methods like `add()`,`size()`,`remove()`,`indexOf()`,`get()` etc.

- An object is always instantiated by calling a method that created an object, i.e., a **constructor** by using the `new` keyword.

# Creating Classes

- A class specifies what the objects instantiated from it are like.

  > The object's variables (instance variables) specify the internal state of the object
  > The object's methods specify what the object does

- Let's create a class named "Person"

```java
public class Person{

}
```

- Let's decide that each person object has a name and an age. It's natural to represent the name as a string, and the age as an integer. We'll go ahead and add these to our blueprint:

```java
public class Person{
  private String name;
  private int age;
}
```

- We specify above that each object created from the `Person` class has a `name` and an `age`. Variables defined inside a class are called **instance variables**, or object fields or object attributes. Other names also seem to exist.

- Each variable is preceded by the keyword **private**. The keyword private means that the variables are "hidden" inside the object. This is known as **encapsulation**.

- We have now defined a blueprint — a class — for the person object. Each new person object has the variables `name` and `age`, which are able to hold object-specific values. The "state" of a person consists of the values assigned to their name and age.

# Defining a Constructor

- We want to set an initial state for an object that's created. Custom objects are created the same way as objects from pre-made Java classes, such as `ArrayList`, using the `new` keyword. It'd be convenient to pass values ​​to the variables of that object as it's being created. For example, when creating a new person object, it's useful to be able to provide it with a name:

```java
public static void main(String[] args) {
    Person ada = new Person("Prabhu");
    // ...
}
```

- This is achieved by defining the method that creates the object, i.e., its constructor. **The constructor is defined after the instance variables**. In the following example, a constructor is defined for the Person class, which can be used to create a new Person object. The constructor sets the age of the object being created to 0, and the string passed to the constructor as a parameter as its name:

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }
}
```

- The constructor's name is always the same as the class name. The class in the example above is named Person, so the constructor will also have to be named Person.

- The constructor is also provided, as a parameter, the name of the person object to be created. The parameter is enclosed in parentheses and follows the constructor's name. The parentheses that contain optional parameters are followed by curly brackets. In between these brackets is the source code that the program executes when the constructor is called (e.g., `new Person ("Ada")`).

- **Objects are always created using a constructor.**

- A few things to note: the constructor contains the expression `this.age = 0`. The expression sets the instance variable `age` of the newly created object (i.e., "this" object's age) to 0. The second expression `this.name = initialName` likewise assigns the string passed as a parameter to the instance variable `name` of the object created.

# Default Constructor

- If the programmer does not define a constructor for a class, Java automatically creates a default one for it. A default constructor is a constructor that doesn't do anything apart from creating the object. The object's variables remain uninitialized (generally, the value of any object references will be `null`, meaning that they do not point to anything, and the values of primitives will be `0`)

- If a constructor has been defined for a class, no default constructor exists, you have to manually create one. For the class below, calling `new Person` would cause an error, as Java cannot find a constructor in the class that has no parameters.

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
      this.age = 0;
      this.name = initialName;
    }
}

public class Main{
  public static void main(String[] args){
    Person person = new Person(); // error:constructor Person in class Person cannot be applied to given types;
  }
}
```

```java
public class Person {
    private String name;
    private int age;

    //defining default constructor manually
    public Person(){
      this.age = 28;
      this.name = "Prabhu";
    }

    public Person(String initialName) {
      this.age = 0;
      this.name = initialName;
    }
}

public class Main{
  public static void main(String[] args){
    Person person = new Person();
  }
}
```

# Defining Methods For an Object

- We know how to create an object and initialize its variables. However, an object also needs methods to be able to do anything. As we've learned, a **method** is a named section of source code inside a class which can be invoked.

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public void printPerson() {
        System.out.println(this.name + ", age " + this.age + " years");
    }
}
```

# Objects and the Static Modifier

- The `static` modifier indicates that the method in question does not belong to an object and thus cannot be used to access any variables that belong to objects.

- Going forward, our methods will not include the `static` keyword if they're used to process information about objects created from a given class. If a method receives as parameters all the variables whose values ​​it uses, it can have a `static` modifier.

- non-static variables(including `this` keyword) cannot be referenced from a static context/methods.

```java
public class Person {
    private String name;
    private int age;

    public Person(){
      this.age = 28;
      this.name = "Prabhu";
    }

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public static int getAge(){
      return age + 2; // error: non-static variable age cannot be referenced from a static context

      // To fix the issue, add static keyword to age instance variable
    }
}
```

# Changing an Instance Variable's Value in a Method

```java
public class Person {
    private String name;
    private int age;

    public Person(String initialName) {
        this.age = 0;
        this.name = initialName;
    }

    public void printPerson() {
        System.out.println(this.name + ", age " + this.age + " years");
    }

    // growOlder() method has been added
    public void growOlder() {
        this.age = this.age + 1;
    }
}

public class Main {

    public static void main(String[] args) {
        Person ada = new Person("Ada");
        Person antti = new Person("Antti");

        ada.printPerson();
        antti.printPerson();
        System.out.println("");

        ada.growOlder();
        ada.growOlder();

        ada.printPerson();
        antti.printPerson();
    }
}
/*OUTPUT
Ada, age 0 years
Antti, age 0 years

Ada, age 2 years
Antti, age 0 years
*/
```

- The `ada` object's `growOlder` method is called twice. As the print output demonstrates, the age of Ada is 2 years after growing older. Calling the method on an object corresponding to Ada has no impact on the age of the other person object since each object instantiated from a class has its own instance variables.

# Returning a Value From a Method

- A method that returns nothing has the `void` modifier as the type of variable to be returned.

- A method that returns an integer variable has the `int` modifier as the type of variable to be returned.

- A method that returns a string has the `String` modifier as the type of the variable to be returned.

- A method that returns a double-precision number has the `double` modifier as the type of the variable to be returned.

# A string representation of an object and the toString-method

- We are guilty of programming in a somewhat poor style by creating a method for printing the object, i.e., the `printPerson` method. A preferred way is to define a method for the object that returns a "string representation" of the object. The method returning the string representation is always `toString` in Java. Let's define this method for the person in the following example:

```java
public class Person {
    // ...

    public String toString() {
        return this.name + ", age " + this.age + " years";
    }
}

public static void main(String[] args) {
    Person pekka = new Person("Pekka");
    Person antti = new Person("Antti");

    int i = 0;
    while (i < 30) {
        pekka.growOlder();
        i = i + 1;
    }

    antti.growOlder();

    System.out.println(antti); // same as System.out.println(antti.toString());
    System.out.println(pekka); // same as System.out.println(pekka.toString());
}
```

- In principle, the `System.out.println` method requests the object's string representation and prints it. The call to the `toString` method returning the string representation does not have to be written explicitly, as Java adds it automatically. When a programmer writes:

```java
System.out.println(antti);
```

- Java extends the call at run time to the following form:

```java
System.out.println(antti.toString());
```

# Method parameters

- Let's continue with the `Person` class once more. We've decided that we want to calculate people's body mass indexes. To do this, we write methods for the person to set both the height and the weight, and also a method to calculate the body mass index. The new and changed parts of the Person object are as follows:

```java
public class Person {
    private String name;
    private int age;
    private int weight;
    private int height;

    public Person(String initialName) {
        this.age = 0;
        this.weight = 0;
        this.height = 0;
        this.name = initialName;
    }

    public void setHeight(int newHeight) {
        this.height = newHeight;
    }

    public void setWeight(int newWeight) {
        this.weight = newWeight;
    }

    public double bodyMassIndex() {
        double heigthPerHundred = this.height / 100.0;
        return this.weight / (heigthPerHundred * heigthPerHundred);
    }

    // ...
}
```

- The instance variables `height` and `weight` were added to the person. Values for these can be set using the `setHeight` and `setWeight` methods. Java's standard naming convention is used once again, that is, if the method's only purpose is to set a value to an instance variable, then it's named as `setVariableName`. Value-setting methods are often called "setters". The new methods are put to use in the following case:

```java
public static void main(String[] args) {
    Person matti = new Person("Matti");
    Person juhana = new Person("Juhana");

    matti.setHeight(180);
    matti.setWeight(86);

    juhana.setHeight(175);
    juhana.setWeight(64);

    System.out.println(matti.getName() + ", body mass index is " + matti.bodyMassIndex());
    System.out.println(juhana.getName() + ", body mass index is " + juhana.bodyMassIndex());
}
/*OUTPUT
Matti, body mass index is 26.54320987654321
Juhana, body mass index is 20.897959183673468
*/
```

# Calling an internal method

- The object may also call its methods. For example, if we wanted the string representation returned by toString to also tell of a person's body mass index, the object's own `bodyMassIndex` method should be called in the `toString` method:

```java
public String toString() {
    return this.name + ", age " + this.age + " years, my body mass index is " + this.bodyMassIndex();
}
```

- So, when an object calls an internal method, the name of the method and this prefix suffice. An alternative way is to call the object's own method in the form `bodyMassIndex()`, whereby no emphasis is placed on the fact that the object's own bodyMassIndex method is being called:

```java
public String toString() {
    return this.name + ", age " + this.age + " years, my body mass index is " + bodyMassIndex();
}
```
