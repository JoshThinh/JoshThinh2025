---
layout: post
title: Insertion and Selection Sort - Practice Problems and Performance Comparison
description: Learn about Selection and Insertion sort with Big O analysis and real Java implementations to sort arrays and compare performance.
permalink: /CSA/Final/Exam/insertion-selection-frq/
type: collab
comment: true
---

# Insertion and Selection Sort - AP CSA Practice Problems

## Description

Big O is a mathematical notation used to describe the performance of an algorithm in terms of time and space. It provides an upper bound on the growth rate of a function, allowing us to compare the efficiency of different algorithms.

### Selection Sort
- Sorts arrays by repeatedly finding the minimum element from the unsorted part and putting it at the beginning.
- Time Complexity:  
  - **Best:** O(n²)  
  - **Average:** O(n²)  
  - **Worst:** O(n²)

### Insertion Sort
- Sorts arrays by taking an element from the unsorted part and inserting it into the correct position in the sorted part.
- Time Complexity:  
  - **Best:** O(n) (already sorted)  
  - **Average/Worst:** O(n²)

---

## Homework Problems

```java
import java.util.Arrays;

public class SortingHomework {

    // Selection Sort in DESCENDING order
    public static void selectionSortDescending(int[] arr) {
        int n = arr.length;
        for (int i = 0; i < n - 1; i++) {
            int maxIdx = i;
            for (int j = i + 1; j < n; j++) {
                if (arr[j] > arr[maxIdx]) {
                    maxIdx = j;
                }
            }
            int temp = arr[i];
            arr[i] = arr[maxIdx];
            arr[maxIdx] = temp;
        }
    }

    // Insertion Sort in ASCENDING order
    public static void insertionSortAscending(int[] arr) {
        int n = arr.length;
        for (int i = 1; i < n; i++) {
            int key = arr[i];
            int j = i - 1;
            while (j >= 0 && arr[j] > key) {
                arr[j + 1] = arr[j];
                j--;
            }
            arr[j + 1] = key;
        }
    }

    // Time Complexity Comparison
    public static void compareSorts() {
        int[] arrayA = {29, 10, 14, 37, 13};
        int[] arrayB = {1, 2, 5, 4, 3, 6, 7, 8, 9, 10};

        // Clone arrays for fair comparison
        int[] a1 = arrayA.clone();
        int[] a2 = arrayA.clone();
        int[] b1 = arrayB.clone();
        int[] b2 = arrayB.clone();

        long start, end;

        // Selection Sort on arrayA
        start = System.nanoTime();
        selectionSortDescending(a1);
        end = System.nanoTime();
        System.out.println("Selection Sort (Descending) - Array A: " + Arrays.toString(a1));
        System.out.println("Time: " + (end - start) + " ns");

        // Insertion Sort on arrayA
        start = System.nanoTime();
        insertionSortAscending(a2);
        end = System.nanoTime();
        System.out.println("Insertion Sort (Ascending) - Array A: " + Arrays.toString(a2));
        System.out.println("Time: " + (end - start) + " ns");

        // Selection Sort on arrayB
        start = System.nanoTime();
        selectionSortDescending(b1);
        end = System.nanoTime();
        System.out.println("Selection Sort (Descending) - Array B: " + Arrays.toString(b1));
        System.out.println("Time: " + (end - start) + " ns");

        // Insertion Sort on arrayB
        start = System.nanoTime();
        insertionSortAscending(b2);
        end = System.nanoTime();
        System.out.println("Insertion Sort (Ascending) - Array B: " + Arrays.toString(b2));
        System.out.println("Time: " + (end - start) + " ns");
    }

    public static void main(String[] args) {
        compareSorts();
    }
}
```

---

## Questions to Answer

- **Which algorithm performed better for Array A? Why?**  
  _Depends on timing output, but generally Insertion Sort may perform better if elements are nearly sorted._

- **Which algorithm performed better for Array B? Why?**  
  _Insertion Sort should perform better here because Array B is almost sorted and Insertion Sort handles nearly sorted data very efficiently._

- **When is it best to use each sorting algorithm?**  
  - **Selection Sort:** When you want a simple, predictable algorithm regardless of data arrangement.
  - **Insertion Sort:** When data is already or nearly sorted or when working with small data sets.

---
