---
layout: post
title: Boolean Expressions and If Statements - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand Boolean expressions and if statements in Java.
permalink: /CSA/Final/Exam/boolean-expressions
type: collab
comment: true
---

# Boolean Expressions and If Statements - AP CSA Practice Problems

## Description

Boolean expressions and `if` statements are fundamental concepts in Java that allow the program to make decisions based on certain conditions. This section will cover various types of boolean operations and logical expressions, as well as the structure and usage of `if`, `else`, and `else-if` statements.

### Key Concepts:
- **Boolean Operators**: `&&` (AND), `||` (OR), `!` (NOT)
- **if, else, and else-if statements**: Used for conditional branching in Java.
- **Comparisons**: Understanding how to compare values (e.g., `==`, `>`, `<`, `!=`).

---

## Practice Problem 1: Complex Logical Expressions

**Problem:**  
What is the result of the following code?

```java
public class LogicalTest {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        int c = 30;
        boolean result = (a < b && b < c) || !(a == b);
        System.out.println(result);
    }
}
```

**Failed Attempt:**  
I thought the result would be `false` because I didn't properly account for the precedence of the operators.

**Mistake:**  
In Java, the `&&` operator has higher precedence than `||`, and `!` has higher precedence than both `&&` and `||`. Here's the breakdown of the evaluation:
1. `(a < b)` evaluates to `true`.
2. `(b < c)` evaluates to `true`.
3. `(a < b && b < c)` evaluates to `true && true`, which is `true`.
4. `(a == b)` evaluates to `false`, so `!(a == b)` becomes `true`.
5. The overall expression `(true) || (true)` evaluates to `true`.

**Correction:**  
You can explicitly use parentheses to ensure the correct evaluation order:

```java
public class LogicalTest {
    public static void main(String[] args) {
        int a = 10;
        int b = 20;
        int c = 30;
        boolean result = ((a < b && b < c) || !(a == b));
        System.out.println(result);  // Output will be true
    }
}
```

Now the result will be `true`, as expected.

---

## Practice Problem 2: Nested If Statements

**Problem:**  
What is the output of the following code?

```java
public class NestedIfTest {
    public static void main(String[] args) {
        int x = 10;
        int y = 5;
        if (x > y) {
            if (x % 2 == 0) {
                System.out.println("x is even");
            } else {
                System.out.println("x is odd");
            }
        } else {
            System.out.println("x is not greater than y");
        }
    }
}
```

**Failed Attempt:**  
I expected the output to be `"x is even"` because I thought the outer `if` statement was always true.

**Mistake:**  
The mistake was in assuming that the second condition for the inner `if` statement was irrelevant. The outer `if` statement is indeed true, but the inner check for whether `x % 2 == 0` will evaluate `x` for evenness. Since `x = 10`, it is even.

**Correction:**  
Here’s the correct explanation and code:

```java
public class NestedIfTest {
    public static void main(String[] args) {
        int x = 10;
        int y = 5;
        if (x > y) {
            if (x % 2 == 0) {
                System.out.println("x is even");  // Output will be "x is even"
            } else {
                System.out.println("x is odd");
            }
        } else {
            System.out.println("x is not greater than y");
        }
    }
}
```

Now, the output will correctly be `"x is even"` because `10 % 2 == 0`.

---

## Practice Problem 3: Using Else-If Ladder

**Problem:**  
What is the output of the following code?

```java
public class ElseIfTest {
    public static void main(String[] args) {
        int score = 85;
        String grade;

        if (score >= 90) {
            grade = "A";
        } else if (score >= 80) {
            grade = "B";
        } else if (score >= 70) {
            grade = "C";
        } else if (score >= 60) {
            grade = "D";
        } else {
            grade = "F";
        }

        System.out.println("Grade: " + grade);
    }
}
```

**Failed Attempt:**  
I expected the output to be `"Grade: A"` because `85` is greater than `80`.

**Mistake:**  
The mistake was not properly understanding how `else-if` works. Since `score = 85`, the condition `score >= 80` evaluates to `true`, so the program will output `"B"`. It doesn’t check the next conditions because the first condition is met.

**Correction:**  
Here’s the code with the correct understanding of how `else-if` works:

```java
public class ElseIfTest {
    public static void main(String[] args) {
        int score = 85;
        String grade;

        if (score >= 90) {
            grade = "A";
        } else if (score >= 80) {
            grade = "B";  // Output will be "B"
        } else if (score >= 70) {
            grade = "C";
        } else if (score >= 60) {
            grade = "D";
        } else {
            grade = "F";
        }

        System.out.println("Grade: " + grade);  // Output will be "Grade: B"
    }
}
```

The output will be `"Grade: B"` because the `score = 85` satisfies the condition `score >= 80`.

---

## Practice Problem 4: Combining Boolean Operators

**Problem:**  
What will be the output of the following code?

```java
public class ComplexBooleanTest {
    public static void main(String[] args) {
        int x = 15;
        int y = 5;
        boolean result = !(x % 2 == 0) && (y > 3 || y == 5);
        System.out.println(result);
    }
}
```

**Failed Attempt:**  
I thought the result would be `true` because both conditions seemed to work together.

**Mistake:**  
The mistake is misunderstanding how the negation (`!`) operator works. Here's how the expression is evaluated:
1. `x % 2 == 0` is `false` because `x = 15` is odd.
2. `!(x % 2 == 0)` becomes `true`.
3. `(y > 3 || y == 5)` is `true` because `y = 5`, so the second part of the condition is `true`.
4. The final expression is `true && true`, which evaluates to `true`.

**Correction:**  
Here’s the corrected code with the proper logical evaluation:

```java
public class ComplexBooleanTest {
    public static void main(String[] args) {
        int x = 15;
        int y = 5;
        boolean result = !(x % 2 == 0) && (y > 3 || y == 5);
        System.out.println(result);  // Output will be true
    }
}
```

Now, the result will be `true` as expected.

---

## Future Topics to Work On

1. **Boolean Expressions**:
   - Practice using logical operators like `&&`, `||`, and `!`.
   
2. **If/Else Statements**:
   - Work with multiple `if` statements, `else if` ladders, and nested conditions.

3. **Comparisons**:
   - Master comparisons using `==`, `!=`, `>`, `<`, and `>=`.
