---
layout: post
title: Primitive Types - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand primitive types in Java.
permalink: /CSA/Final/Exam/primitive-types/
type: collab
comment: true
---

# Primitive Types - AP CSA Practice Problems

## Description

Understanding primitive types is crucial for Java programming. In this section, we will review the key primitive types in Java: `int`, `double`, `boolean`, and `char`. We will explore how these types work in expressions, and discuss common mistakes and corrections.

The primary Java primitive types include:
- **int**: 32-bit signed integer.
- **double**: 64-bit floating-point number.
- **boolean**: Represents `true` or `false`.
- **char**: A single 16-bit Unicode character.

---

## Practice Problem 1: Integer Division with Large Numbers

**Problem:**  
What is the result of the following code when working with large integers?

```java
public class IntegerDivision {
    public static void main(String[] args) {
        long a = 10000000000L;
        long b = 3;
        System.out.println(a / b);
    }
}
```

**Failed Attempt:**  
I expected the output to be `3333333333.33` because it's dividing a large number by 3, which should result in a decimal.

**Mistake:**  
The result of `a / b` is still a `long` because both `a` and `b` are `long` types. Java performs integer division by default, truncating the result instead of producing a decimal.

**Correction:**  
In order to get a floating-point result, one of the operands needs to be cast to `double` or `float`:

```java
public class IntegerDivision {
    public static void main(String[] args) {
        long a = 10000000000L;
        long b = 3;
        System.out.println((double) a / b);  // Output will be 3333333333.3333335
    }
}
```

Now, the division produces a `double` result, and the output includes the decimal places as expected.

---

## Practice Problem 2: Complex Boolean Expressions

**Problem:**  
What is the result of the following code, and why?

```java
public class BooleanTest {
    public static void main(String[] args) {
        int x = 10;
        int y = 15;
        boolean result = (x < y) && (x % 2 == 0) || (y % 5 == 0);
        System.out.println(result);
    }
}
```

**Failed Attempt:**  
I thought the result would be `true` because both conditions seemed like they should be true.

**Mistake:**  
I didn't correctly evaluate the precedence of the logical operators. The `&&` (AND) operator has higher precedence than `||` (OR), so the expression is evaluated like this:
1. `(x < y)` is `true`
2. `(x % 2 == 0)` is `true`
3. The `&&` operator evaluates both to `true`, so this part is `true`
4. The last part, `(y % 5 == 0)`, is also `true` because `y = 15` and `15 % 5 == 0`
5. The final OR expression is `true || true`, which evaluates to `true`

**Correction:**  
To avoid confusion, you can use parentheses to explicitly specify the order of evaluation:

```java
public class BooleanTest {
    public static void main(String[] args) {
        int x = 10;
        int y = 15;
        boolean result = ((x < y) && (x % 2 == 0)) || (y % 5 == 0);
        System.out.println(result);  // Output will be true
    }
}
```

This ensures clarity in your boolean expression and helps you avoid logical mistakes in future code.

---

## Practice Problem 3: Char Manipulation with Arithmetic

**Problem:**  
What is the result of the following code, and what happens when arithmetic is applied to `char` values?

```java
public class CharArithmetic {
    public static void main(String[] args) {
        char ch = 'A';
        int result = ch + 3;
        System.out.println("Character: " + ch);
        System.out.println("Result after adding 3: " + result);
        System.out.println("Result as char: " + (char) result);
    }
}
```

**Failed Attempt:**  
I expected the result after adding `3` to `A` to be `D`, because I thought the `char` value would simply shift to the next character.

**Mistake:**  
In Java, `char` values are represented as their Unicode values. The value of `'A'` is `65` in Unicode. When you add `3` to `ch`, you're actually adding to its numeric value, not its character representation. This means the result is a number, not a `char`.

**Correction:**  
The code works correctly, but the result is an integer. To display the character that corresponds to the result, you need to cast the result back to `char`:

```java
public class CharArithmetic {
    public static void main(String[] args) {
        char ch = 'A';
        int result = ch + 3;  // Adding 3 to the Unicode value of 'A'
        System.out.println("Character: " + ch);  // Output: A
        System.out.println("Result after adding 3: " + result);  // Output: 68 (Numeric result)
        System.out.println("Result as char: " + (char) result);  // Output: D
    }
}
```

In this corrected code, we see that the result is `68` in numeric form, which corresponds to the character `'D'`.

---

## Future Topics to Work On

1. **Integer Division**:
   - Practice dividing integers and using type casting for floating-point results.
   
2. **Boolean Expressions**:
   - Work with `&&`, `||`, and `!` operators and understand short-circuiting.
   
3. **Character Handling**:
   - Practice working with `char` and converting between characters and their numeric Unicode values.
