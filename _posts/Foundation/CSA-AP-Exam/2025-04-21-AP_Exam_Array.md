---
layout: post
title: Arrays - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand arrays in Java.
permalink: /CSA/Final/Exam/array/
type: collab
comment: true
---

# Arrays - AP CSA Practice Problems

## Description

Arrays are a fundamental data structure in Java that allow you to store multiple elements of the same type in a single variable. In this section, we will work through common mistakes related to arrays, including array initialization, indexing, and common errors in array algorithms.

### Key Concepts:
- **Array Declaration**: You define an array with a type and size.
- **Array Indexing**: Arrays are zero-indexed, meaning the first element is at index `0`.
- **Array Initialization**: You can initialize an array in various ways, including using loops or specific values.
- **Array Length**: Use `array.length` to determine the size of an array.

---

## Practice Problem 1: Array Initialization and Looping

**Problem:**  
What is the output of the following code?

```java
public class ArrayInitialization {
    public static void main(String[] args) {
        int[] nums = new int[5];
        for (int i = 0; i <= nums.length; i++) {
            nums[i] = i * 2;
        }
        for (int num : nums) {
            System.out.print(num + " ");
        }
    }
}
```

**Failed Attempt:**  
I expected the program to output the elements of the array `nums`, with each value being `0, 2, 4, 6, 8`.

**Mistake:**  
The loop in the first part of the code runs from `i = 0` to `i = 5` (because of `i <= nums.length`), but the array `nums` has indices from `0` to `4`. This causes an `ArrayIndexOutOfBoundsException` when `i = 5`.

**Correction:**  
To fix the issue, the loop condition should be `i < nums.length` so that it stops at index `4`:

```java
public class ArrayInitialization {
    public static void main(String[] args) {
        int[] nums = new int[5];
        for (int i = 0; i < nums.length; i++) {  // Fix: use < instead of <=
            nums[i] = i * 2;
        }
        for (int num : nums) {
            System.out.print(num + " ");  // Output: 0 2 4 6 8
        }
    }
}
```

This will correctly initialize the array and print `0 2 4 6 8` as expected.

---

## Practice Problem 2: Summing Array Elements

**Problem:**  
Write a program that sums all elements of an integer array and prints the result.

```java
public class ArraySum {
    public static void main(String[] args) {
        int[] arr = {5, 7, 2, 8, 3};
        int sum = 0;
        for (int i = 0; i <= arr.length; i++) {
            sum += arr[i];
        }
        System.out.println("Sum of array elements: " + sum);
    }
}
```

**Failed Attempt:**  
I expected the program to print the sum of the array elements, which is `25` (`5 + 7 + 2 + 8 + 3`).

**Mistake:**  
The loop condition is incorrect. The loop runs from `i = 0` to `i = 5` (because of `i <= arr.length`), but the array `arr` has indices from `0` to `4`. This causes an `ArrayIndexOutOfBoundsException`.

**Correction:**  
To fix this, the loop condition should be `i < arr.length` so that the index stays within bounds:

```java
public class ArraySum {
    public static void main(String[] args) {
        int[] arr = {5, 7, 2, 8, 3};
        int sum = 0;
        for (int i = 0; i < arr.length; i++) {  // Fix: use < instead of <=
            sum += arr[i];
        }
        System.out.println("Sum of array elements: " + sum);  // Output: 25
    }
}
```

Now, the code correctly sums the array elements and prints `25`.

---

## Practice Problem 3: Finding the Maximum Value in an Array

**Problem:**  
Write a program that finds the maximum value in an integer array.

```java
public class MaxArrayValue {
    public static void main(String[] args) {
        int[] arr = {5, 7, 2, 8, 3};
        int max = Integer.MIN_VALUE;
        for (int i = 0; i <= arr.length; i++) {
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("Maximum value: " + max);
    }
}
```

**Failed Attempt:**  
I expected the program to output `8`, as it is the largest value in the array.

**Mistake:**  
The loop condition is again incorrect. The loop runs from `i = 0` to `i = 5` (because of `i <= arr.length`), causing an `ArrayIndexOutOfBoundsException` when `i = 5`.

**Correction:**  
The loop condition should be `i < arr.length` to ensure that the index is within bounds:

```java
public class MaxArrayValue {
    public static void main(String[] args) {
        int[] arr = {5, 7, 2, 8, 3};
        int max = Integer.MIN_VALUE;
        for (int i = 0; i < arr.length; i++) {  // Fix: use < instead of <=
            if (arr[i] > max) {
                max = arr[i];
            }
        }
        System.out.println("Maximum value: " + max);  // Output: 8
    }
}
```

This will correctly find and print the maximum value in the array, which is `8`.

---

## Future Topics to Work On

1. **Array Indexing**:
   - Practice with correctly accessing and manipulating array elements.

2. **Multi-dimensional Arrays**:
   - Work with 2D arrays and nested loops to process multi-dimensional data.

3. **Array Sorting**:
   - Learn how to sort arrays using built-in methods and implement simple sorting algorithms.

4. **Common Array Algorithms**:
   - Study algorithms like searching, reversing, and finding duplicates within arrays.

---

This markdown file contains detailed explanations, code snippets, and solutions to common array-related problems. You can copy this entire content into your markdown file for use in your study plan.

Let me know if you need further refinements!
