---
layout: post
title: Merge Sort - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand Merge Sort in Java.
permalink: /CSA/Final/Exam/merge-frq/
type: collab
comment: true
---

# Merge Sort - AP CSA Practice Problems

## Description

Merge Sort is a divide-and-conquer algorithm that efficiently sorts large datasets by recursively dividing a list into smaller sublists, sorting those sublists, and then merging them back together. This approach gives Merge Sort a time complexity of **O(n log n)**, making it highly efficient compared to simpler algorithms like Bubble Sort, which has a worst-case complexity of **O(n²)**. Merge Sort is ideal for sorting large datasets and works well with linked lists, as it does not require random access to elements.

### Time Complexity:
- **Divide Step:** The list is recursively split in half, which takes **O(log n)** time.
- **Merge Step:** Merging two sorted lists takes **O(n)** time.
- **Overall Complexity:** Since we have **O(log n)** levels of recursion and each level takes **O(n)** time to merge, the overall time complexity is **O(n log n)**.

---

## Practice Problem 1: Merge Sort Implementation

**Problem:**  
Here is a standard implementation of Merge Sort in Java. The task is to write the `mergeSort` and `merge` methods, as well as test the sorting functionality.

```java
import java.util.Arrays;

public class MergeSort {

    // Main function to sort an array
    public static void mergeSort(int[] array) {
        if (array.length < 2) {
            return; // Base case: an array of length 0 or 1 is already sorted
        }

        // Find the middle index
        int mid = array.length / 2;

        // Divide the array into two halves
        int[] left = new int[mid];
        int[] right = new int[array.length - mid];

        // Copy data to left and right subarrays
        System.arraycopy(array, 0, left, 0, mid);
        System.arraycopy(array, mid, right, 0, array.length - mid);

        // Recursively sort both halves
        mergeSort(left);
        mergeSort(right);

        // Merge the sorted halves
        merge(array, left, right);
    }

    // Helper function to merge two sorted arrays
    public static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;

        // Merge the two sorted subarrays
        while (i < left.length && j < right.length) {
            if (left[i] <= right[j]) {
                array[k] = left[i];
                i++;
            } else {
                array[k] = right[j];
                j++;
            }
            k++;
        }

        // Copy the remaining elements of left[] if any
        while (i < left.length) {
            array[k] = left[i];
            i++;
            k++;
        }

        // Copy the remaining elements of right[] if any
        while (j < right.length) {
            array[k] = right[j];
            j++;
            k++;
        }
    }

    // Main method to test the merge sort
    public static void main(String[] args) {
        int[] array = { 38, 27, 43, 3, 9, 82, 10 };
        System.out.println("Original array:");
        System.out.println(Arrays.toString(array));

        mergeSort(array);

        System.out.println("Sorted array:");
        System.out.println(Arrays.toString(array));
    }
}
```

---

**Explanation of Homework Task 1:**

**Task 1:**  
**Explain Merge Sort in Your Own Words**

Merge Sort works by recursively splitting the input array into two halves until each sublist contains a single element or is empty. Each of these smaller sublists is then sorted and merged back together in a process known as the **merge step**. During the merge step, two sorted subarrays are combined into a single sorted array by comparing the elements one by one.

Merge Sort has a time complexity of **O(n log n)** due to the divide-and-conquer approach. The **divide step** takes **O(log n)** time because the array is halved at each recursion level, and the **merge step** takes **O(n)** time since each element needs to be compared and merged.

Compared to other algorithms like Bubble Sort, which has a time complexity of **O(n²)**, Merge Sort is far more efficient for large datasets. Unlike Quick Sort, Merge Sort is stable and always runs in **O(n log n)** time, even in the worst case.

---

## Practice Problem 2: Modified Merge Sort - Sorting in Descending Order

**Problem:**  
Modify the mergeSort and merge methods to sort the array in descending order instead of ascending order.

**Solution:**

```java
public class MergeSortDescending {

    // Main function to sort an array
    public static void mergeSort(int[] array) {
        if (array.length < 2) {
            return;
        }

        int mid = array.length / 2;
        int[] left = new int[mid];
        int[] right = new int[array.length - mid];

        System.arraycopy(array, 0, left, 0, mid);
        System.arraycopy(array, mid, right, 0, array.length - mid);

        mergeSort(left);
        mergeSort(right);

        merge(array, left, right);
    }

    // Helper function to merge two sorted arrays in descending order
    public static void merge(int[] array, int[] left, int[] right) {
        int i = 0, j = 0, k = 0;

        while (i < left.length && j < right.length) {
            if (left[i] >= right[j]) {  // Change condition for descending order
                array[k] = left[i];
                i++;
            } else {
                array[k] = right[j];
                j++;
            }
            k++;
        }

        while (i < left.length) {
            array[k] = left[i];
            i++;
            k++;
        }

        while (j < right.length) {
            array[k] = right[j];
            j++;
            k++;
        }
    }

    // Main method to test the merge sort
    public static void main(String[] args) {
        int[] array = { 38, 27, 43, 3, 9, 82, 10 };
        System.out.println("Original array:");
        System.out.println(Arrays.toString(array));

        mergeSort(array);

        System.out.println("Sorted array in descending order:");
        System.out.println(Arrays.toString(array));
    }
}
```

This modification simply changes the comparison in the `merge()` method to ensure that larger numbers are placed first in the array, resulting in a sorted array in descending order.

---

**Explanation of Homework Task 2:**

**Task 2, Option A (Merge Sort Without Recursion):**  
To implement Merge Sort iteratively instead of recursively, we can modify the code to use a bottom-up approach. This approach will gradually merge pairs of subarrays starting with single elements, working up to larger subarrays. The challenge is to manage the merging process without recursive function calls.

```java
public class MergeSortIterative {
    // Main function to sort an array iteratively
    public static void mergeSortIterative(int[] array) {
        int n = array.length;
        for (int size = 1; size < n; size = 2 * size) {
            for (int left = 0; left < n - 1; left += 2 * size) {
                int mid = Math.min(n - 1, left + size - 1);
                int right = Math.min((left + 2 * size - 1), (n - 1));

                merge(array, left, mid, right);
            }
        }
    }

    // Helper function to merge two sorted arrays
    public static void merge(int[] array, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;

        int[] leftArray = new int[n1];
        int[] rightArray = new int[n2];

        for (int i = 0; i < n1; i++)
            leftArray[i] = array[left + i];
        for (int i = 0; i < n2; i++)
            rightArray[i] = array[mid + 1 + i];

        int i = 0, j = 0, k = left;
        while (i < n1 && j < n2) {
            if (leftArray[i] <= rightArray[j]) {
                array[k] = leftArray[i];
                i++;
            } else {
                array[k] = rightArray[j];
                j++;
            }
            k++;
        }

        while (i < n1) {
            array[k] = leftArray[i];
            i++;
            k++;
        }

        while (j < n2) {
            array[k] = rightArray[j];
            j++;
            k++;
        }
    }

    // Main method to test the iterative merge sort
    public static void main(String[] args) {
        int[] array = { 12, 11, 13, 5, 6, 7 };
        mergeSortIterative(array);

        System.out.println("Sorted array:");
        for (int num : array) {
            System.out.print(num + " ");
        }
    }
}
```

---

### Explanation:
- The solution for **Merge Sort Without Recursion** applies a bottom-up iterative approach, sorting subarrays of increasing sizes in a systematic manner.
