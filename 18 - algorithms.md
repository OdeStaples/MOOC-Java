# Static Keyword

- Methods in Java can be divided into two groups, based on whether they have the `static` modifier or not. Methods without the static modifier are **instance methods**. Methods with the `static` modifier are **class methods**.

- Instance methods are methods that are associated with an object, can process the objects variables and can call the object's other methods. Instance methods specifically CAN use the `this` modifier, which refers to the variables associated with the specific object, that is calling the instance method. Class methods can't use the `this` modifier, meaning that they can only access the variables they are given as parameters or that they create themselves.

# Built-in sorting algorithms in Java

- Arrays can be sorted (into their natural order) using the class method `sort` of the `Arrays`-class. Lists can be sorted (into their natural order) using the class method sort of the `Collections` class.

  ```java
  int[] numbers = {8, 3, 7, 9, 1, 2, 4};
  System.out.println(Arrays.toString(numbers)); // [8, 3, 7, 9, 1, 2, 4]
  Arrays.sort(numbers);
  System.out.println(Arrays.toString(numbers)); // [1, 2, 3, 4, 7, 8, 9]

  ArrayList<Integer> numbers = new ArrayList<>();
  numbers.add(8);
  numbers.add(3);
  numbers.add(7);
  System.out.println(numbers); // [8, 3, 7]
  Collections.sort(numbers);
  System.out.println(numbers); // [3, 7, 8]
  ```

# Linear Search

- Linear search is a search algorithm that searches for information in an array by going through every value in the array one by one. When the value that was searched for is found, its index is immediately returned. If the requested value cannot be found, linear search returns the information that the value was not found — typically this means returning `-1` instead of a valid index.

  ```java
  public class Algorithms {

    public static int linearSearch(int[] array, int searched) {
        for (int i = 0; i < array.length; i++) {
            if (array[i] == searched) {
                return i;
            }
        }

        return -1;
    }
  }
  ```

- In the worst case scenario, i.e when the value searched for isn't found, the algorithm has to do as many comparisons as there are values in the array. In an array containing, say, 10 million values, this means 10 million comparisons. If we are doing more than one search, it makes sense to try and improve efficiency.

# Binary Search (aka half-interval search or logarithmic search)

### Check binary_search.pdf on how binary search works
