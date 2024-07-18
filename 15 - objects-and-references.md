# Objects and references

```java
public class Person {

    private String name;
    private int age;
    private int weight;
    private int height;

    public Person(String name) {
        this(name, 0, 0, 0);
    }

    public Person(String name, int age, int height, int weight) {
        this.name = name;
        this.age = age;
        this.weight = weight;
        this.height = height;
    }

    // other constructors and methods

    public String getName() {
        return this.name;
    }

    public int getAge() {
        return this.age;
    }

    public int getHeight() {
        return this.height;
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
        double heightPerHundred = this.height / 100.0;
        return this.weight / (heightPerHundred * heightPerHundred);
    }

    @Override
    public String toString() {
        return this.name + ", age " + this.age + " years";
    }
}
```

- Precisely what happens when a new object is created?

  > `Person joan = new Person("Joan Ball");`

- Calling a constructor with the command `new` causes several things to happen. First, space is reserved in the computer memory for storing object variables. Then default or initial values are set to object variables (e.g. an `int` type variable receives an initial value of 0). Lastly, the source code in the constructor is executed.

- A constructor call returns a reference to an object. A **reference** is information about the location of object data.

  ![](https://java-programming.mooc.fi/static/4305b4aa2098287afc1ddda0ff254040/e9131/olio-joan.png)

# Assigning a reference type variable copies the reference

- Let's add a `Person` type variable called `ball` into the program, and assign `joan` as its initial value. What happens then?

  ```java
  Person joan = new Person("Joan Ball");
  System.out.println(joan);

  Person ball = joan;
  ```

- The statement `Person ball = joan;` creates a new Person variable `ball`, and copies the value of the variable `joan` as its value. As a result, `ball` refers to the same object as `joan`.

  ![](https://java-programming.mooc.fi/static/2922372f4ac941766a0a7b5ce115e155/e9131/olio-joan-ja-ball.png)

- Let's inspect the same example a little more thoroughly.

  ```java
  Person joan = new Person("Joan Ball");
  System.out.println(joan);

  Person ball = joan;
  ball.growOlder();
  ball.growOlder();

  System.out.println(joan);

  /*OUTPUT
  Joan Ball, age 0 years
  Joan Ball, age 2 years
  */
  ```

- Joan Ball — i.e. the Person object that the reference in the `joan` variable points at — starts as 0 years old. After this the value of the `joan` variable is assigned (so copied) to the `ball` variable. The Person object `ball` is aged by two years, and Joan Ball ages as a consequence!

- An object's internal state is not copied when a variable's value is assigned. A new object is not being created in the statement `Person ball = joan;` — the value of the variable ball is assigned to be the copy of joan's value, i.e. a reference to an object.

  ![](https://java-programming.mooc.fi/static/f63dfc37e73911b8ee3529f10611d37c/7cb89/olio-joan-ja-ball-2.png)

- Next, the example is continued so that a new object is created for the `joan` variable, and a reference to it is assigned as the value of the variable. The variable `ball` still refers to the object that we created earlier.

  ```java
  Person joan = new Person("Joan Ball");
  System.out.println(joan);

  Person ball = joan;
  ball.growOlder();
  ball.growOlder();

  System.out.println(joan);

  joan = new Person("Joan B.");
  System.out.println(joan);

  /*OUTPUT
  Joan Ball, age 0 years
  Joan Ball, age 2 years
  Joan B., age 0 years
  */
  ```

- So in the beginning the variable `joan` contains a reference to one object, but in the end a reference to another object has been copied as its value. Here is a picture of the situation after the last line of code.

  ![](https://java-programming.mooc.fi/static/d8a908095f7fbd15977399d9577bfbbd/7cb89/olio-joan-ja-ball-3.png)

# `null` value of a reference variable

- Let's extend the example further by setting the value of the reference variable `ball` to `null`, i.e. a reference "to nothing". The `null` reference can be set as the value of any reference type variable.

  ```java
  Person joan = new Person("Joan Ball");
  System.out.println(joan);

  Person ball = joan;
  ball.growOlder();
  ball.growOlder();

  System.out.println(joan);

  joan = new Person("Joan B.");
  System.out.println(joan);

  ball = null;
  System.out.println(ball);
  /*OUTPUT
  Joan Ball, age 0 years
  Joan Ball, age 2 years
  Joan B., age 0 years
  null
  */
  ```

- The situation of the program after the last line is depicted below.

  ![](https://java-programming.mooc.fi/static/2127e1a4c68fe520c142f4c7875caae4/7cb89/olio-joan-ja-ball-null.png)

- The object whose name is Joan Ball is referred to by nobody. In other words, the object has become "garbage". In the Java programming language the programmer need not worry about the program's memory use. From time to time, the automatic garbage collector of the Java language cleans up the objects that have become garbage. If the garbage collection did not happen, the garbage objects would reserve a memory location until the end of the program execution.

- Printing a `null` reference prints "null". How about if we were to try and call a method, say `growOlder`, on an object that refers to nothing:

  ```java
  Person joan = new Person("Joan Ball");
  System.out.println(joan);

  joan = null;
  joan.growOlder();

  /*Java
  Joan Ball, age 0 years
  Exception in thread "main" java.lang.NullPointerException
  at Main.main(Main.java:(row))
  Java Result: 1
  */
  ```

# Object as a method parameter

```java
public class AmusementParkRide {
  private String name;
  private int lowestHeight;

  public AmusementParkRide(String name, int lowestHeight) {
      this.name = name;
      this.lowestHeight = lowestHeight;
  }

  public boolean allowedToRide(Person person) {
      if (person.getHeight() < this.lowestHeight) {
          return false;
      }

      return true;
  }

  public String toString() {
      return this.name + ", minimum height: " + this.lowestHeight;
  }
}
```

- So the method `allowedToRide` of an AmusementParkRide object is given a `Person` object as a parameter. Like earlier, the value of the variable — in this case, a reference — is copied for the method to use. The method handles a copied reference, and it calls the `getHeight` method of the person passed as a parameter.

- Below is an example main program where the amusement park ride method is called twice: first the supplied parameter is a person object `matt`, and then a person object `jasper`:

```java
Person matt = new Person("Matt");
matt.setWeight(86);
matt.setHeight(180);

Person jasper = new Person("Jasper");
jasper.setWeight(34);
jasper.setHeight(132);

AmusementParkRide waterTrack = new AmusementParkRide("Water track", 140);

if (waterTrack.allowedToRide(matt)) {
    System.out.println(matt.getName() + " may enter the ride");
} else {
    System.out.println(matt.getName() + " may not enter the ride");
}

if (waterTrack.allowedToRide(jasper)) {
    System.out.println(jasper.getName() + " may enter the ride");
} else {
    System.out.println(jasper.getName() + " may not enter the ride");
}

System.out.println(waterTrack)

/*OUTPUT
Matt may enter the ride
Jasper may not enter the ride
Water track, minimum height: 140
*/
```

# Object as object variable

- Objects may contain references to objects.

# Date in Java programs

- In the section above, we use our own class SimpleDate to represent date, because it is suitable for illustrating and practising the operation of objects. If you want to handle dates in your own programs, it's worth reading about the premade Java class LocalDate. It contains a significant amount of functionality that can be used to handle dates.

- For example, the current date can be used with the existing LocalDate class in the following manner:

```java
import java.time.LocalDate;

public class Example {

    public static void main(String[] args) {

        LocalDate now = LocalDate.now();
        int year = now.getYear();
        int month = now.getMonthValue();
        int day = now.getDayOfMonth();

        System.out.println("today is  " + day + "." + month + "." + year);

    }
}
```

# Comparing the equality of objects (equals)

- With primitive variables such as int, comparing two variables can be done with `two equality signs (==)`. This is because the value of a primitive variable is stored directly in the "variable's box".

- The value of reference variables, in contrast, is an address of the object that is referenced; so the "box" contains a reference to the memory location.

- Using two equality signs compares the equality of the values stored in the "boxes of the variables" — with reference variables, such comparisons would examine the equality of the memory references.

- The method `equals` is similar to the method `toString` in the respect that it is available for use even if it has not been defined in the class. The default implementation of this method compares the equality of the references. Let's observe this with the help of the previously written `SimpleDate` class.

```java
SimpleDate first = new SimpleDate(1, 1, 2000);
SimpleDate second = new SimpleDate(1, 1, 2000);
SimpleDate third = new SimpleDate(12, 12, 2012);
SimpleDate fourth = first;

if (first.equals(first)) {
    System.out.println("Variables first and first are equal");
} else {
    System.out.println("Variables first and first are not equal");
}

if (first.equals(second)) {
    System.out.println("Variables first and second are equal");
} else {
    System.out.println("Variables first and second are not equal");
}

if (first.equals(third)) {
    System.out.println("Variables first and third are equal");
} else {
    System.out.println("Variables first and third are not equal");
}

if (first.equals(fourth)) {
    System.out.println("Variables first and fourth are equal");
} else {
    System.out.println("Variables first and fourth are not equal");
}

/*OUTPUT
Variables first and first are equal
Variables first and second are not equal
Variables first and third are not equal
Variables first and fourth are equal
*/
```

- There is a problem with the program above. Even though two dates (first and second) have exactly the same values for object variables, they are different from each other from the point of view of the default `equals` method.

- If we want to be able to compare two objects of our own design with the `equals` method, that method must be defined in the class (just like `toString()`).

- The method `equals` is defined as a method that returns a boolean type value — the return value indicates whether the objects are equal. The `equals` method is implemented in such a way that it can be used to compare the current object with any other object.

- The method receives an `Object`-type object as its single parameter — all objects are `Object`-type, in addition to their own type.

  - The `equals` method first compares if the addresses are equal: if so, the objects are equal.
  - After this, we examine if the types of the objects are the same: if not, the objects are not equal.
  - Next, the `Object`-type object passed as the parameter is converted to the type of the object that is being examined by using a type cast, so that the values of the object variables can be compared.

  ```java
  public class SimpleDate {
    private int day;
    private int month;
    private int year;

    public SimpleDate(int day, int month, int year) {
        this.day = day;
        this.month = month;
        this.year = year;
    }

    public int getDay() {
        return this.day;
    }

    public int getMonth() {
        return this.month;
    }

    public int getYear() {
        return this.year;
    }

    public boolean equals(Object compared) {
        // if the variables are located in the same position, they are equal
        if (this == compared) {
            return true;
        }

        // if the type of the compared object is not SimpleDate, the objects are not equal
        if (!(compared instanceof SimpleDate)) {
            return false;
        }

        // convert the Object type compared object
        // into a SimpleDate type object called comparedSimpleDate
        SimpleDate comparedSimpleDate = (SimpleDate) compared;

        // if the values of the object variables are the same, the objects are equal
        if (this.day == comparedSimpleDate.day &&
            this.month == comparedSimpleDate.month &&
            this.year == comparedSimpleDate.year) {
            return true;
        }

        // otherwise the objects are not equal
        return false;
    }

    @Override
    public String toString() {
        return this.day + "." + this.month + "." + this.year;
    }
  }
  ```

# What is Object?

- Every class we create (and every ready-made Java class) inherits the class Object, even though it is not specially visible in the program code. This is why an instance of any class can be passed as a parameter to a method that receives an Object type variable as its parameter. Inheriting the Object can be seen elsewhere, too: for instance, the `toString` method exists even if you have not implemented it yourself, just as the `equals` method does.

- To illustrate, the following source code compiles successfully: `equals` method can be found in the Object class inherited by all classes.

  ```java
  public class Bird {
    private String name;

    public Bird(String name) {
        this.name = name;
    }
  }

  Bird red = new Bird("Red");
  System.out.println(red);

  Bird chuck = new Bird("Chuck");
  System.out.println(chuck);

  if (red.equals(chuck)) {
      System.out.println(red + " equals " + chuck);
  }
  ```

# Object equality and lists

- Let's examine how the `equals` method is used with lists. Let's assume we have the previously described class `Bird` without any `equals` method.

  ```java
  public class Bird {
    private String name;

    public Bird(String name) {
        this.name = name;
    }
  }
  ```

- Let's create a list and add a bird to it. After this we'll check if that bird is contained in it.

  ```java
  ArrayList<Bird> birds = new ArrayList<>()
  Bird red = new Bird("Red");

  if (birds.contains(red)) {
      System.out.println("Red is on the list.");
  } else {
      System.out.println("Red is not on the list.");
  }

  birds.add(red);
  if (birds.contains(red)) {
      System.out.println("Red is on the list.");
  } else {
      System.out.println("Red is not on the list.");
  }


  System.out.println("However!");

  red = new Bird("Red");
  if (birds.contains(red)) {
      System.out.println("Red is on the list.");
  } else {
      System.out.println("Red is not on the list.");
  }

  /*OUTPUT
  Red is not on the list.
  Red is on the list.
  However!
  Red is not on the list.
  */
  ```

  - First, when the bird had not been added to the list, it is not found — and after adding it is found. When the program switches the `red` object into a new object, with exactly the same contents as before, it is no longer equal to the object on the list, and therefore cannot be found on the list.

  - The `contains` method of a list uses the `equals` method that is defined for the objects in its search for objects. In the example above, the `Bird` class has no definition for that method, so a bird with exactly the same contents — but a different reference — cannot be found on the list.

  - Let's implement the `equals` method for the class `Bird`. The method examines if the names of the objects are equal — if the names match, the birds are thought to be equal.

  ```java
  public class Bird {
    private String name;

    public Bird(String name) {
        this.name = name;
    }

    public boolean equals(Object compared) {
        // if the variables are located in the same position, they are equal
        if (this == compared) {
            return true;
        }

        // if the compared object is not of type Bird, the objects are not equal
        if (!(compared instanceof Bird)) {
            return false;
        }

        // convert the object to a Bird object
        Bird comparedBird = (Bird) compared;

        // if the values of the object variables are equal, the objects are, too
        return this.name.equals(comparedBird.name);

        /*
        // the comparison of names above is equal to
        // the following code

        if (this.name.equals(comparedBird.name)) {
            return true;
        }

        // otherwise the objects are not equal
        return false;
        */
    }
  }
  ```

  - Now the contains list method recognizes birds with identical contents.

  ```java
  ArrayList<Bird> birds = new ArrayList<>()
  Bird red = new Bird("Red");

  if (birds.contains(red)) {
      System.out.println("Red is on the list.");
  } else {
      System.out.println("Red is not on the list.");
  }

  birds.add(red);
  if (birds.contains(red)) {
      System.out.println("Red is on the list.");
  } else {
      System.out.println("Red is not on the list.");
  }


  System.out.println("However!");

  red = new Bird("Red");
  if (birds.contains(red)) {
      System.out.println("Red is on the list.");
  } else {
      System.out.println("Red is not on the list.");
  }

  /*OUTPUT
  Red is not on the list.
  Red is on the list.
  However!
  Red is on the list.
  */
  ```

# Object as a method's return value

- We have seen methods return boolean values, numbers, and strings. Easy to guess, a method can return an object of any type.

- In the next example we present a simple counter that has the method `clone`. The method can be used to create a clone of the counter; i.e. a new counter object that has the same value at the time of its creation as the counter that is being cloned.

```java
public class Counter {
    private int value;

    // example of using multiple constructors:
    // you can call another constructor from a constructor by calling this
    // notice that the this call must be on the first line of the constructor
    public Counter() {
        this(0);
    }

    public Counter(int initialValue) {
        this.value = initialValue;
    }

    public void increase() {
        this.value = this.value + 1;
    }

    public String toString() {
        return "value: " + value;
    }

    public Counter clone() {
        // create a new counter object that receives the value of the cloned counter as its initial value
        Counter clone = new Counter(this.value);

        // return the clone to the caller
        return clone;
    }
}

Counter counter = new Counter();
counter.increase();
counter.increase();

System.out.println(counter);         // prints 2

Counter clone = counter.clone();

System.out.println(counter);         // prints 2
System.out.println(clone);          // prints 2

counter.increase();
counter.increase();
counter.increase();
counter.increase();

System.out.println(counter);         // prints 6
System.out.println(clone);          // prints 2

clone.increase();

System.out.println(counter);         // prints 6
System.out.println(clone);           // prints 3
```

- Immediately after the cloning operation, the values contained by the clone and the cloned object are the same. However, they are two different objects, so increasing the value of one counter does not affect the value of the other in any way.

- Similarly, a `Factory` object could also be used to create and return new Car objects. Below is a sketch of the outline of the factory — the factory also knows the makes of the cars that are created.

```java
public class Factory {
    private String make;

    public Factory(String make) {
        this.make = make;
    }

    public Car procuceCar() {
        return new Car(this.make);
    }
}
```
