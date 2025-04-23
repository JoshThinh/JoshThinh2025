---
layout: post
title: Merge Sort - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand Merge Sort in Java.
permalink: /CSA/Final/Exam/FRQ-Overview/
type: collab
comment: true
---

### There are four main types of FRQ questions commonly seen in the AP Computer Science A exam.
1. Methods and Control Structures
- These questions ask you to write a method that uses loops, conditionals, and basic logic. You’ll often be asked to iterate over arrays or process input conditionally. Example:
```
public int countPositives(int[] arr) {
    int count = 0;
    for (int num : arr) {
        if (num > 0) count++;
    }
    return count;
}
```
## Tips:

Pay close attention to loop boundaries and conditional logic.

Ensure you return the expected value.

Use enhanced for-loops for clarity and simplicity when possible.

## Common Mistakes:

- Off-by-one errors in loops.

- Incorrect logic in conditionals.

- Forgetting to initialize variables properly.

- Make sure to test edge cases, like empty arrays or arrays with only negative numbers.

2. Classes
- These questions focus on writing or completing a class with fields, constructors, and methods. The main concepts are object-oriented design principles like encapsulation, constructor use, and method behaviors. Example:
```
public class Book {
    private String title;
    private int pages;

    public Book(String t, int p) {
        title = t;
        pages = p;
    }

    public int getPages() {
        return pages;
    }

    public void addPages(int morePages) {
        pages += morePages;
    }
}
```
## Tips:

- Use private for fields and provide public getters and setters to maintain encapsulation.

- Follow the constructor signature exactly as given in the prompt.

- Avoid hardcoding values in methods unless explicitly required.

## Common Mistakes:

- Forgetting to initialize fields properly in the constructor.

- Failing to use this. when necessary to differentiate between instance variables and method parameters.

- Incorrect return types or missing return statements in methods.

3. Array / ArrayList
- These questions require you to work with one-dimensional arrays, two-dimensional arrays, or ArrayList objects. Tasks typically include traversing, inserting, deleting, or searching elements. Example:
```
public int countLongWords(ArrayList<String> words) {
    int count = 0;
    for (String word : words) {
        if (word.length() > 5) {
            count++;
        }
    }
    return count;
}
```
## Tips:

- Use enhanced for-loops for easier and clearer iteration over arrays and ArrayLists.

- Use .get(i) for accessing ArrayList elements and array[i] for arrays.

- Make sure to understand the structure of 2D arrays: they are typically accessed by array[row][col].

## Common Mistakes:

- Index out-of-bounds errors, especially when using indices incorrectly.

- Confusing the methods for ArrayLists (.get(i)) and arrays (array[i]).

- Forgetting to properly update the list or array during iteration.

4. 2D Array
- These questions focus on working with nested loops to process 2D arrays. You need to be comfortable with the row and column logic and element access within a 2D structure. Example:
```
public int sumEvenValues(int[][] matrix) {
    int sum = 0;
    for (int row = 0; row < matrix.length; row++) {
        for (int col = 0; col < matrix[row].length; col++) {
            if (matrix[row][col] % 2 == 0) {
                sum += matrix[row][col];
            }
        }
    }
    return sum;
}
```
## Tips:

- Use a nested loop to iterate over both rows and columns of a 2D array.

- Always use matrix[row].length to access the column length, rather than assuming the dimensions.

- Drawing out a matrix helps visualize the iteration process.

## Common Mistakes:

- Mixing up the row and column order in nested loops.

- Hardcoding dimensions of arrays, like using [3][3] when you should be using dynamic lengths.

- Forgetting to return the result or initialize the accumulator variable.