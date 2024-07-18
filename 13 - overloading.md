# Constructor Overloading

- We would also like to be able to create persons so that the constructor is provided both the age as well as the name as parameters. This is possible since a class may have multiple constructors.

```java
public Person(String name) {
        this.name = name;
        this.age = 0;
        this.weight = 0;
        this.height = 0;
    }

public Person(String name, int age) {
    this.name = name;
    this.age = age;
    this.weight = 0;
    this.height = 0;
}
```

- We now have two alternative ways to create objects:

```java
public static void main(String[] args) {
    Person paul = new Person("Paul", 24);
    Person ada = new Person("Ada");

    System.out.println(paul);
    System.out.println(ada);
}
/*OUTPUT
Paul is 24 years old.
Ada is 0 years old.
*/
```

- The technique of having two (or more) constructors in a class is known as _constructor overloading_. A class can have multiple constructors that differ in the number and/or type of their parameters. It's not, however, possible to have two constructors with the exact same parameters.

- We cannot, for example, add a `public Person(String name, int weight)` constructor since it would be impossible for Java to differentiate between this and the one that has two parameters where int parameter is used for age.

# Calling Your Constructor

- In the example above, the first constructor - the one that receives a name as a parameter - is in fact a special case of the second constructor - the one that's given both name and age. What if the first constructor could call the second constructor?

- This is possible. A constructor can be called from another constructor using the `this` keyword, which refers to this object in question!

```java
public Person(String name) {
    this(name, 0);
    //here the code of the second constructor is run, and the age is set to 0
}

public Person(String name, int age) {
    this.name = name;
    this.age = age;
    this.weight = 0;
    this.height = 0;
}
```

- The constructor call `this(name, 0);` might seem a bit weird. A way to think about it is to imagine that the call is automatically replaced with "copy-paste" of the second constructor in such a way that the age parameter is set to 0.

### NB! If a constructor calls another constructor, the constructor call must be the first command in the constructor.

- New objects can be created just as before:

```java
public static void main(String[] args) {
    Person paul = new Person("Paul", 24);
    Person eve = new Person("Eve");

    System.out.println(paul);
    System.out.println(eve);
}
/*OUTPUT
Paul is 24 years old.
Eve is 0 years old.
*/
```

# Method Overloading

- Methods can be overloaded in the same way as constructors, i.e., multiple versions of a given method can be created. Once again, the parameters of the different versions must be different. Let's make another version of the `growOlder` method that ages the person by the amount of years given to it as a parameter.

```java
public void growOlder() {
    this.age = this.age + 1;
}

public void growOlder(int years) {
    this.age = this.age + years;
}
```

- In the example below, "Paul" is born 24 years old, ages by a year and then by 10 years:

```java
public static void main(String[] args) {
    Person paul = new Person("Paul", 24);
    System.out.println(paul);

    paul.growOlder();
    System.out.println(paul);

    paul.growOlder(10);
    System.out.println(paul);
}
/*OUTPUT
Paul is 24 years old.
Paul is 25 years old.
Paul is 35 years old.
*/
```

- A Person now has two methods, both called `growOlder`. The one that gets executed depends on the number of parameters provided. We may also modify the program so that the parameterless method is implemented using the method `growOlder(int years)`:

```java
public void growOlder() {
    this.growOlder(1);
}

public void growOlder(int years) {
    this.age = this.age + years;
}
```
