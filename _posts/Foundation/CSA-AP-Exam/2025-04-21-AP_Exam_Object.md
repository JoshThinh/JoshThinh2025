---
layout: post
title: Using Objects - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand object usage in Java.
permalink: /CSA/Final/Exam/using-objects
type: collab
comment: true
---

# Using Objects - AP CSA Practice Problems

## Description

Understanding how to use objects in Java is fundamental to object-oriented programming (OOP). In this section, we will focus on creating objects, using constructors, calling methods, and understanding the `String` class and wrapper classes such as `Integer` and `Double`.

---

## Practice Problem 1: String Methods and Object Creation

**Problem:**  
What is the result of the following code? What will the output be?

```java
public class StringMethods {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = new String("World");
        System.out.println(str1.equals(str2));
        System.out.println(str1 == str2);
    }
}
```

**Failed Attempt:**  
I expected both outputs to be `true`, as both strings seem to hold the same value: `"Hello"` and `"World"`.

**Mistake:**  
The first comparison uses the `equals()` method, which compares the values of the strings (i.e., the content of the strings), while the second comparison uses `==`, which compares the reference memory addresses of the two objects. In this case, `str1` and `str2` refer to two different string objects in memory, even though they contain the same string value.

**Correction:**  
The `equals()` method compares the contents of the strings, so it correctly returns `false` because `"Hello"` and `"World"` are different. On the other hand, the `==` operator compares the memory addresses of `str1` and `str2`, which are not the same because `str2` was created using the `new` keyword.

```java
public class StringMethods {
    public static void main(String[] args) {
        String str1 = "Hello";
        String str2 = new String("World");
        System.out.println(str1.equals(str2));  // Output will be false
        System.out.println(str1 == str2);       // Output will be false
    }
}
```

---

## Practice Problem 2: Creating and Using Custom Classes

**Problem:**  
What is the output of the following code when using a custom class with a constructor?

```java
public class Person {
    String name;
    int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Method to display information
    public void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }

    public static void main(String[] args) {
        Person person1 = new Person("Alice", 30);
        person1.displayInfo();
    }
}
```

**Failed Attempt:**  
I expected the code to print the person's name and age correctly. I thought everything would work fine, as I correctly created a `Person` object.

**Mistake:**  
In this case, the code is correct, but I made an assumption that the `name` and `age` properties would automatically be initialized. This is not the case unless you define a constructor that sets the properties.

**Correction:**  
This code works because the constructor correctly initializes the `name` and `age` properties when the `Person` object is created. The `displayInfo()` method prints these properties.

```java
public class Person {
    String name;
    int age;

    // Constructor
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    // Method to display information
    public void displayInfo() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
    }

    public static void main(String[] args) {
        Person person1 = new Person("Alice", 30);  // Create a new Person object
        person1.displayInfo();  // Output: Name: Alice, Age: 30
    }
}
```

---

## Practice Problem 3: Using Wrapper Classes

**Problem:**  
What is the output of the following code when using wrapper classes like `Integer` and `Double`?

```java
public class WrapperClasses {
    public static void main(String[] args) {
        Integer x = 10;
        Double y = 3.14;
        System.out.println(x + y);
        System.out.println(x.equals(y));
    }
}
```

**Failed Attempt:**  
I thought the program would add the values of `x` and `y` correctly, and I thought `x.equals(y)` would return `true` because the values are the same.

**Mistake:**  
In the first output, the `Integer` and `Double` values are automatically unboxed to their respective primitive types (`int` and `double`) for the addition. This works fine, but I incorrectly assumed that `x.equals(y)` would work because both have values. However, the `equals()` method compares objects, and since `x` is an `Integer` and `y` is a `Double`, they are different types and thus not equal.

**Correction:**  
The code will work correctly for addition because Java automatically unboxes wrapper classes to primitives when performing operations like addition. However, `equals()` is checking for object equality, so it returns `false` since the two objects are of different types.

```java
public class WrapperClasses {
    public static void main(String[] args) {
        Integer x = 10;
        Double y = 3.14;
        System.out.println(x + y);  // Output will be 13.14 (unboxing and adding)
        System.out.println(x.equals(y));  // Output will be false (different object types)
    }
}
```

---

## Practice Problem 4: Passing Objects to Methods

**Problem:**  
What happens when an object is passed by reference to a method in Java? What will the output of the following code be?

```java
public class Dog {
    String name;

    public Dog(String name) {
        this.name = name;
    }

    public void changeName(Dog dog) {
        dog.name = "Max";
    }

    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy");
        System.out.println("Before change: " + myDog.name);
        myDog.changeName(myDog);
        System.out.println("After change: " + myDog.name);
    }
}
```

**Failed Attempt:**  
I thought that the method `changeName()` would not modify the original object `myDog` because it was passed by reference, and I expected it to print "Buddy" both times.

**Mistake:**  
In Java, when objects are passed to methods, they are passed by reference, not by value. This means that the `dog` parameter in the `changeName()` method is pointing to the same object as `myDog`. Thus, any changes made to `dog` also affect `myDog`.

**Correction:**  
Because `myDog` is passed by reference, when the `changeName()` method modifies the `name` field of the `dog` object, it also modifies the `name` field of `myDog`.

```java
public class Dog {
    String name;

    public Dog(String name) {
        this.name = name;
    }

    public void changeName(Dog dog) {
        dog.name = "Max";  // The dog's name is changed
    }

    public static void main(String[] args) {
        Dog myDog = new Dog("Buddy");
        System.out.println("Before change: " + myDog.name);  // Output: Buddy
        myDog.changeName(myDog);
        System.out.println("After change: " + myDog.name);  // Output: Max
    }
}
```

---

## Future Topics to Work On

1. **String Methods**:
   - Practice using `substring()`, `indexOf()`, and `toUpperCase()`.
   
2. **Custom Classes**:
   - Work with constructors, `this`, and `super` in inheritance.
   
3. **Wrapper Classes**:
   - Explore `Integer`, `Double`, `Character`, and others, especially when converting between primitive types and objects.

4. **Passing Objects to Methods**:
   - Practice passing objects as parameters and modifying them inside methods.
