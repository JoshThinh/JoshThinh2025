---
layout: post
title: Recursion - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand recursion in Java.
permalink: /CSA/Final/Exam/recursion
type: collab
comment: true
---

# Recursion - AP CSA Practice Problems

## Description

Recursion is a method in programming where a function calls itself to solve a problem. Recursion is especially useful for problems that have a repetitive or nested structure. In this section, we will explore how recursion works, examine common mistakes, and go over the corrections.

---

## Practice Problem 1: Factorial Calculation

**Problem:**  
Write a recursive method to calculate the factorial of a number.

```java
public class RecursionExample {
    public static void main(String[] args) {
        int number = 5;
        System.out.println("Factorial of " + number + " is: " + factorial(number));
    }

    public static int factorial(int n) {
        if (n == 0) {
            return 1;
        } else {
            return n * factorial(n - 1);
        }
    }
}
```

**Failed Attempt:**  
I thought the factorial calculation would be simple and worked as expected, but it returned an incorrect result when I tried to input negative numbers.

**Mistake:**  
The factorial function works fine for positive numbers, but there's no handling for negative numbers. Factorial is undefined for negative numbers, so an additional condition is necessary to handle invalid input.

**Correction:**  
Add a check to ensure that the input is non-negative:

```java
public class RecursionExample {
    public static void main(String[] args) {
        int number = -5;
        if (number < 0) {
            System.out.println("Factorial is undefined for negative numbers.");
        } else {
            System.out.println("Factorial of " + number + " is: " + factorial(number));
        }
    }

    public static int factorial(int n) {
        if (n == 0) {
            return 1;
        } else {
            return n * factorial(n - 1);
        }
    }
}
```

Now, the program correctly handles negative numbers by displaying an error message.

---

## Practice Problem 2: Fibonacci Sequence

**Problem:**  
Write a recursive method to find the nth number in the Fibonacci sequence.

```java
public class RecursionExample {
    public static void main(String[] args) {
        int n = 6;
        System.out.println("The " + n + "th Fibonacci number is: " + fibonacci(n));
    }

    public static int fibonacci(int n) {
        if (n == 0) {
            return 0;
        } else if (n == 1) {
            return 1;
        } else {
            return fibonacci(n - 1) + fibonacci(n - 2);
        }
    }
}
```

**Failed Attempt:**  
I expected the program to work for any number, but it was very slow when calculating large Fibonacci numbers.

**Mistake:**  
The recursive method has exponential time complexity due to redundant calculations, which makes it inefficient for larger values of `n`.

**Correction:**  
Use memoization to store already calculated Fibonacci numbers and avoid redundant calculations. Here's how:

```java
public class RecursionExample {
    public static void main(String[] args) {
        int n = 50;
        int[] memo = new int[n + 1];
        System.out.println("The " + n + "th Fibonacci number is: " + fibonacci(n, memo));
    }

    public static int fibonacci(int n, int[] memo) {
        if (n == 0) {
            return 0;
        } else if (n == 1) {
            return 1;
        }
        if (memo[n] != 0) {
            return memo[n];
        }
        memo[n] = fibonacci(n - 1, memo) + fibonacci(n - 2, memo);
        return memo[n];
    }
}
```

Now, the Fibonacci function runs efficiently by storing previously calculated results in an array, reducing redundant calls.

---

## Practice Problem 3: Sum of Array Elements Using Recursion

**Problem:**  
Write a recursive method to calculate the sum of elements in an array.

```java
public class RecursionExample {
    public static void main(String[] args) {
        int[] arr = {1, 2, 3, 4, 5};
        System.out.println("Sum of array elements is: " + sumArray(arr, 0));
    }

    public static int sumArray(int[] arr, int index) {
        if (index == arr.length) {
            return 0;
        } else {
            return arr[index] + sumArray(arr, index + 1);
        }
    }
}
```

**Failed Attempt:**  
I thought the program would work without any issue, but when I passed in an empty array, the result was incorrect.

**Mistake:**  
The base case works for a non-empty array, but when the array is empty, the method returns `0`, which is fine. However, I didn't consider a situation where the array could be `null`, leading to a `NullPointerException`.

**Correction:**  
Add a null check to ensure that the array is not `null`:

```java
public class RecursionExample {
    public static void main(String[] args) {
        int[] arr = null;
        if (arr == null) {
            System.out.println("Array is null.");
        } else {
            System.out.println("Sum of array elements is: " + sumArray(arr, 0));
        }
    }

    public static int sumArray(int[] arr, int index) {
        if (arr == null) {
            return 0;
        }
        if (index == arr.length) {
            return 0;
        } else {
            return arr[index] + sumArray(arr, index + 1);
        }
    }
}
```

This version includes a check for `null` and ensures that the array is valid before proceeding with the sum calculation.

---

## Future Topics to Work On

1. **Factorial Recursion**:
   - Practice base cases and recursive calls to solve problems like factorial.
   
2. **Fibonacci Recursion**:
   - Work with memoization and recursion optimization techniques for better performance.

3. **Array Summing**:
   - Practice recursion for array operations, such as summing, reversing, and searching.

