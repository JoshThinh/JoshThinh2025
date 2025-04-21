---
layout: post
title: ArrayList - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand ArrayLists in Java.
permalink: /CSA/Final/Exam/arraylist
type: collab
comment: true
---

# ArrayList - AP CSA Practice Problems

## Description

The `ArrayList` class is part of Java's `java.util` package and is a flexible, dynamic array implementation that can grow and shrink in size. It allows you to store objects in a collection, and provides useful methods for adding, removing, and accessing elements.

Key concepts of `ArrayList` include:
- **Add elements**: You can add elements to an `ArrayList` dynamically.
- **Access elements**: Elements can be accessed by index.
- **Remove elements**: You can remove elements by index or by object reference.
- **Resize dynamically**: The `ArrayList` grows and shrinks automatically as needed.

---

## Practice Problem 1: Adding and Removing Elements in ArrayList

**Problem:**  
What is the result of the following code? How does the `ArrayList` behave when elements are added and removed?

```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(5);
        numbers.add(10);
        numbers.add(15);
        numbers.remove(1);  // Remove element at index 1
        System.out.println(numbers);
    }
}
```

**Failed Attempt:**  
I thought the output would be `[5, 15]` because I removed the element at index 1, which should be `10`.

**Mistake:**  
In this case, the code behaves as expected. The `ArrayList` removes the element at index `1`, which is `10`, so the result should be `[5, 15]`. However, the mistake in my thinking was that I wasn't sure how `ArrayList` automatically adjusts its size and shifts remaining elements when an element is removed.

**Correction:**  
The `ArrayList` automatically resizes when you add or remove elements. When you remove an element at index `1`, the `ArrayList` shifts the remaining elements to fill the gap.

```java
import java.util.ArrayList;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<Integer> numbers = new ArrayList<>();
        numbers.add(5);
        numbers.add(10);
        numbers.add(15);
        numbers.remove(1);  // Remove element at index 1 (which is 10)
        System.out.println(numbers);  // Output will be: [5, 15]
    }
}
```

This is how `ArrayList` behaves by default when elements are removed.

---

## Practice Problem 2: Accessing ArrayList with `get()` and Index

**Problem:**  
What is the result of the following code?

```java
import java.util.ArrayList;

public class ArrayListAccess {
    public static void main(String[] args) {
        ArrayList<String> words = new ArrayList<>();
        words.add("Hello");
        words.add("World");
        words.add("Java");
        String firstWord = words.get(0);
        String lastWord = words.get(2);
        System.out.println(firstWord + " " + lastWord);
    }
}
```

**Failed Attempt:**  
I expected the output to be `"Hello Java"` because I accessed the first and third elements in the list.

**Mistake:**  
I did not consider that the list is zero-indexed. So, `words.get(0)` retrieves the first element (`"Hello"`) and `words.get(2)` retrieves the third element (`"Java"`), which is correct.

**Correction:**  
The code is correct. The output will indeed be `"Hello Java"`.

```java
import java.util.ArrayList;

public class ArrayListAccess {
    public static void main(String[] args) {
        ArrayList<String> words = new ArrayList<>();
        words.add("Hello");
        words.add("World");
        words.add("Java");
        String firstWord = words.get(0);
        String lastWord = words.get(2);
        System.out.println(firstWord + " " + lastWord);  // Output will be: Hello Java
    }
}
```

Make sure to remember that indexing in Java `ArrayList` is zero-based!

---

## Practice Problem 3: ArrayList with Loops and Iteration

**Problem:**  
What will the following code print, and why?

```java
import java.util.ArrayList;

public class ArrayListIteration {
    public static void main(String[] args) {
        ArrayList<Double> numbers = new ArrayList<>();
        numbers.add(3.14);
        numbers.add(2.71);
        numbers.add(1.61);
        double sum = 0;
        for (int i = 0; i < numbers.size(); i++) {
            sum += numbers.get(i);
        }
        System.out.println("Sum: " + sum);
    }
}
```

**Failed Attempt:**  
I expected the sum to be `7.46` because I added `3.14`, `2.71`, and `1.61`.

**Mistake:**  
My calculation was correct. The mistake was assuming that the sum would be printed with more decimals than expected.

**Correction:**  
The code correctly sums the elements of the `ArrayList` and prints the result. However, the result is `7.46`, as expected:

```java
import java.util.ArrayList;

public class ArrayListIteration {
    public static void main(String[] args) {
        ArrayList<Double> numbers = new ArrayList<>();
        numbers.add(3.14);
        numbers.add(2.71);
        numbers.add(1.61);
        double sum = 0;
        for (int i = 0; i < numbers.size(); i++) {
            sum += numbers.get(i);
        }
        System.out.println("Sum: " + sum);  // Output will be: Sum: 7.46
    }
}
```

This is a simple example of how to iterate through an `ArrayList` using a `for` loop.

---

## Future Topics to Work On

1. **ArrayList Resizing**:
   - Understand how `ArrayList` automatically resizes when adding or removing elements.
   
2. **Looping Through ArrayList**:
   - Practice using both traditional `for` loops and enhanced `for` loops (`for-each`).
   
3. **ArrayList Methods**:
   - Explore `add()`, `remove()`, `get()`, `set()`, and other methods of `ArrayList`.
   
4. **Handling Edge Cases**:
   - Practice handling empty `ArrayList` or accessing an index that doesn't exist (e.g., `IndexOutOfBoundsException`).
