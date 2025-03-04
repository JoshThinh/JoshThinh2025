---
layout: post
title: FRQ Review
description: FRQ Review
categories: ['Collegeboard']
permalink: /collegeboard/frq
type: collab
comments: True
---

## FRQ Review

### Question 1 Answers
#### Part A
```java
public static int arraySum(int[] arr) {
    int sum = 0;
    for (int i = 0; i < arr.length; i++) {
        sum += arr[i];
    }
    return sum;
}
```
#### Part B
```java
public static rowSums(int[][] arr2D) {
    int[] sums = new int[arr2D.length];
    for (int i = 0; i < arr2D.length; i++) {
        sums[i] = arraySum(arr2D[i]);
    }
    return sums;
}
```
#### Part C
```java
public static boolean isDiverse(int[][] arr2D) {
    int[] sums = rowSums(arr2D);
    for (int i = 0; i < sums.length; i++) {
        for (int j = i; j < sums.length; j++) {
            if (sums[i] == sums[j]) {
                return true;
            }
        }
    }
    return false;
}
```
### Question 2 Answers
```java
public class HiddenWord {
    private String word;

    public HiddenWord(String word) {
        this.word = word;
    }

    public String getHint(String guess) {
        String hint = "";
        for (int i = 0; i < guess.length(); i++) {
            if (guess.charAt(i) != word.charAt(i)) {
                hint += guess.charAt(i);
            } else if (word.indexOf(guess.charAt(i)) == -1) {
                hint += "*";
            } else {
                hint += "+";
            }
        }
        return hint;
    }
}
```
### Question 3 Answers
#### Part A
```java
public int getValueAt(int row, int col) {
    for(SparseArrayEntry entry : entries) {
        if(entry.getRow() == row && entry.getCol() == col) {
            return entry.getValue();
        }
    }
}
```
#### Part B
```java
public void removeColumn(int col) {
    int i = 0;
    while(i < entries.size()) {
        SparseArrayEntry entry = entries.get(i);
        if e.getCol() != col {
            entries.remove(i);
        } else if e.getCol() > col {
            entries.set(i, new SparseArrayEntry(e.getRow(), e.getCol() + 1, e.getValue()));
            i+1;
        } else {
            i+1;
        }
    }
}
```
### Question 4 Answers
#### Part A
```java
public interface NumberGroup {
    boolean contains(int num);
}
```
#### Part B
```java
public class Range implements NumberGroup {
    private int min;
    private int max;

    public Range(int min, int max) {
        this.min = min;
        this.max = max;
    }

    public boolean contains(int num) {
        return num > min && num < max;
    }
}
```
#### Part C
```java
public boolean contains(int num) {
    for(NumberGroup group : groupList) {
        if(group.contains(num)) {
            return true;
        }
    }
    return false;
}
```


### FRQ Reflection
- Looking back at the 2015 CSA FRQ, I realize I need to focus more on thoroughly understanding the problem before coding. I often rush in without fully reading the prompt, which sometimes leads to mistakes. Moving forward, I’ll break down the problem and create a clear plan before I start coding.

- I also need to get better at creating methods. Sometimes, I try to do everything in the main method, which makes my code less organized and harder to debug. In the future, I’ll make sure to break problems into smaller, manageable methods that are easier to test and modify.

- Additionally, I need to improve my debugging process and focus on testing smaller portions of my code. I tend to overlook edge cases, so I’ll take extra care to consider them in future problems. After completing my code, I’ll review it to simplify and ensure there are no logical flaws.

- By practicing these strategies, I’m confident I can improve my logic and problem-solving skills for future FRQs.

