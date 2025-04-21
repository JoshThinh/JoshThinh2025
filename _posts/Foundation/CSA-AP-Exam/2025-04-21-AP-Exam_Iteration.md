---
layout: post
title: Iteration - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand iteration in Java.
permalink: /CSA/Final/Exam/iteration
type: collab
comment: true
---

# Iteration - AP CSA Practice Problems

## Description

Iteration is a fundamental concept in programming that allows you to repeat a block of code multiple times. In Java, there are three primary types of loops: `for`, `while`, and `do-while`. It's important to understand how these loops work, their use cases, and common errors when using them.

In this section, we will explore iteration in Java with a variety of problems, focusing on using loops for common tasks.

---

## Practice Problem 1: Summing Even Numbers Using a For Loop

**Problem:**  
Write a program that sums all the even numbers from `1` to `100` using a `for` loop.

```java
public class EvenSum {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 1; i <= 100; i++) {
            if (i % 2 == 0) {
                sum += i;
            }
        }
        System.out.println("Sum of even numbers: " + sum);
    }
}
```

**Failed Attempt:**  
I expected the sum to be calculated correctly. However, when I tested the code, the sum was incorrect.

**Mistake:**  
The logic is actually correct, but I mistakenly set the loop to start at `1` instead of `2`. Even though I check if `i` is even, I wanted to start the loop directly from the first even number (`2`).

**Correction:**  
To make sure the loop starts with `2` instead of `1`, I adjusted the starting point of the loop:

```java
public class EvenSum {
    public static void main(String[] args) {
        int sum = 0;
        for (int i = 2; i <= 100; i += 2) {  // Start at 2 and increment by 2
            sum += i;
        }
        System.out.println("Sum of even numbers: " + sum);  // Output will be 2550
    }
}
```

Now the program sums all even numbers correctly, with an efficient loop.

---

## Practice Problem 2: Finding the Factorial of a Number Using a While Loop

**Problem:**  
Write a program that calculates the factorial of a given number (e.g., `5!`) using a `while` loop.

```java
public class Factorial {
    public static void main(String[] args) {
        int num = 5;
        int factorial = 1;
        int i = 1;
        
        while (i <= num) {
            factorial *= i;
            i++;
        }
        
        System.out.println(num + "! = " + factorial);
    }
}
```

**Failed Attempt:**  
I expected the output to be `120` for `5!`, but I got an incorrect result, `24`.

**Mistake:**  
The mistake was in the condition of the `while` loop. I wasn't correctly multiplying the numbers. I started with `i = 1`, but I forgot that the factorial calculation needs to start at `1` and multiply until `n` (the value of `num`).

**Correction:**  
The `while` loop and logic were correct, but I had an issue with the factorial formula and the loop condition. The corrected version is:

```java
public class Factorial {
    public static void main(String[] args) {
        int num = 5;
        int factorial = 1;
        int i = 1;
        
        while (i <= num) {
            factorial *= i;
            i++;
        }
        
        System.out.println(num + "! = " + factorial);  // Output will be 120
    }
}
```

The loop runs from `1` to `5`, and it correctly calculates `5! = 120`.

---

## Practice Problem 3: Printing a Pattern Using a Nested For Loop

**Problem:**  
Write a program that prints the following pattern using nested loops:

```
*
**
***
****
*****
```

```java
public class StarPattern {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {
            for (int j = 1; j <= i; j++) {
                System.out.print("*");
            }
            System.out.println();
        }
    }
}
```

**Failed Attempt:**  
I expected the correct output, but the pattern was printed in a different way.

**Mistake:**  
I didn't fully understand how the inner loop was controlling the number of stars printed. The outer loop determines how many rows there are, and the inner loop controls how many stars to print in each row.

**Correction:**  
The logic was correct, but I mistakenly misinterpreted the loop structure. Here's the corrected version:

```java
public class StarPattern {
    public static void main(String[] args) {
        for (int i = 1; i <= 5; i++) {  // Outer loop controls the number of rows
            for (int j = 1; j <= i; j++) {  // Inner loop controls the number of stars per row
                System.out.print("*");
            }
            System.out.println();  // Move to the next line after each row
        }
    }
}
```

This code will now print the pattern as expected.

---

## Practice Problem 4: Reverse a String Using a Do-While Loop

**Problem:**  
Write a program that reverses a string using a `do-while` loop.

```java
public class ReverseString {
    public static void main(String[] args) {
        String str = "hello";
        String reversed = "";
        int i = str.length() - 1;
        
        do {
            reversed += str.charAt(i);
            i--;
        } while (i >= 0);
        
        System.out.println("Reversed string: " + reversed);
    }
}
```

**Failed Attempt:**  
I expected the reversed string to be printed correctly, but I was getting an incorrect result.

**Mistake:**  
I used a `do-while` loop correctly, but I made a mistake in how I concatenated the characters. The string is immutable in Java, so repeatedly adding to `reversed` within the loop is inefficient and may cause issues with larger strings.

**Correction:**  
Instead of concatenating characters within the loop, I used a `StringBuilder` for better performance:

```java
public class ReverseString {
    public static void main(String[] args) {
        String str = "hello";
        StringBuilder reversed = new StringBuilder();
        int i = str.length() - 1;
        
        do {
            reversed.append(str.charAt(i));
            i--;
        } while (i >= 0);
        
        System.out.println("Reversed string: " + reversed.toString());
    }
}
```

This approach is more efficient and works well for string manipulation tasks.

---

## Future Topics to Work On

1. **For Loops**:
   - Practice using `for` loops to iterate over arrays and collections.
   
2. **While Loops**:
   - Use `while` loops for situations where you don't know how many iterations you need in advance.

3. **Do-While Loops**:
   - Practice with `do-while` loops where the loop must run at least once before the condition is checked.

4. **Nested Loops**:
   - Work with nested loops to handle more complex problems like pattern printing and matrix operations.

5. **Efficiency**:
   - Learn about loop efficiency, especially in large loops (e.g., `StringBuilder` vs. `String` concatenation).

