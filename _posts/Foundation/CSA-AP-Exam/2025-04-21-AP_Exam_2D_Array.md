---
layout: post
title: 2D Arrays - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand 2D arrays in Java.
permalink: /CSA/Final/Exam/2d-array
type: collab
comment: true
---

# 2D Arrays - AP CSA Practice Problems

## Description

A 2D array is an array of arrays, and it can be used to represent tables, grids, or matrices. Understanding how to work with 2D arrays is an important part of the AP CSA exam. In this section, we will solve some practice problems involving 2D arrays, highlighting common mistakes and corrections.

---

## Practice Problem 1: Accessing Elements in a 2D Array

**Problem:**  
What is the value printed by the following code?

```java
public class TwoDArrayAccess {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        System.out.println(matrix[1][2]);
    }
}
```

**Failed Attempt:**  
I expected the output to be `6`, because I thought `matrix[1][2]` would access the second row and third column of the matrix.

**Mistake:**  
Actually, the matrix indices are zero-based. Therefore, `matrix[1][2]` correctly accesses the element at the second row (index `1`) and the third column (index `2`), which is indeed `6`.

**Correction:**  
The initial code is correct. The output is `6`, because we are accessing the second row and third column of the 2D array.

```java
public class TwoDArrayAccess {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        System.out.println(matrix[1][2]);  // Output will be 6
    }
}
```

---

## Practice Problem 2: Iterating Through a 2D Array with Nested Loops

**Problem:**  
What is the output of the following code?

```java
public class TwoDArrayIteration {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

**Failed Attempt:**  
I thought the output would be a single line of numbers. I did not account for the new line after each row of the matrix.

**Mistake:**  
In the inner loop, `System.out.print(matrix[i][j] + " ")` prints each element of a row on the same line. However, the `System.out.println()` after the inner loop creates a new line after each row is printed.

**Correction:**  
The code works correctly, and the output will be a matrix printed row by row. Here's the output:

```java
public class TwoDArrayIteration {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();  // Moves to the next line after each row
        }
    }
}
```

**Output:**

```
1 2 3 
4 5 6 
7 8 9 
```

---

## Practice Problem 3: Summing All Elements of a 2D Array

**Problem:**  
What is the sum of all the elements in the following 2D array?

```java
public class TwoDSum {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        int sum = 0;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                sum += matrix[i][j];
            }
        }
        System.out.println("Sum of all elements: " + sum);
    }
}
```

**Failed Attempt:**  
I expected the sum to be `45` because I added the numbers in my head, but I missed a calculation mistake in the first iteration.

**Mistake:**  
The logic for summing the elements is correct, but it's important to verify each number being added. The correct sum of the elements in the 2D array should be `45` (1+2+3+4+5+6+7+8+9).

**Correction:**  
The code works correctly, and the sum of all the elements is calculated as expected:

```java
public class TwoDSum {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        int sum = 0;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                sum += matrix[i][j];
            }
        }
        System.out.println("Sum of all elements: " + sum);  // Output will be 45
    }
}
```

**Output:**

```
Sum of all elements: 45
```

---

## Practice Problem 4: Searching for a Specific Element in a 2D Array

**Problem:**  
What is the result of the following code, and how do we search for a specific element in a 2D array?

```java
public class TwoDSearch {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        int target = 5;
        boolean found = false;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                if (matrix[i][j] == target) {
                    found = true;
                    break;
                }
            }
            if (found) break;
        }
        System.out.println("Element " + target + " found: " + found);
    }
}
```

**Failed Attempt:**  
I expected the result to be `true` because `5` is in the matrix, but I didn't consider the break statement and thought the code would loop forever.

**Mistake:**  
The `break` statement inside the inner loop ensures that the search stops once the target is found. This prevents unnecessary iterations and ensures efficiency.

**Correction:**  
The code is correct, and it works as expected. The output will be `true` because the element `5` is present in the matrix.

```java
public class TwoDSearch {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };
        int target = 5;
        boolean found = false;
        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                if (matrix[i][j] == target) {
                    found = true;
                    break;
                }
            }
            if (found) break;
        }
        System.out.println("Element " + target + " found: " + found);  // Output will be true
    }
}
```

**Output:**

```
Element 5 found: true
```

---

## Future Topics to Work On

1. **Advanced 2D Array Manipulation**:
   - Try rotating matrices or flipping them.
   
2. **Efficient Searching**:
   - Practice searching for elements in large 2D arrays.
   
3. **Matrix Operations**:
   - Try performing matrix addition, subtraction, or multiplication.
