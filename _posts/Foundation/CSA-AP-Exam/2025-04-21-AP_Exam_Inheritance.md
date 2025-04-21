---
layout: post
title: Inheritance - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand inheritance in Java.
permalink: /CSA/Final/Exam/inheritance
type: collab
comment: true
---

# Inheritance - AP CSA Practice Problems

## Description

Understanding inheritance is a key concept in Java and object-oriented programming. Inheritance allows one class to inherit the properties and methods of another class. This is a way to establish a relationship between classes where one class (the subclass) inherits from another class (the superclass).

### Key Concepts:
- **Superclass**: The class being inherited from.
- **Subclass**: The class inheriting from the superclass.
- **`extends` keyword**: Used to declare inheritance in Java.
- **Method Overriding**: The ability of a subclass to provide a specific implementation of a method already defined in the superclass.
- **Polymorphism**: The ability of an object to take on many forms, allowing methods to behave differently depending on the object.

---

## Practice Problem 1: Inheritance and Method Overriding

**Problem:**  
Given the following code, what is the output when the `Animal` and `Dog` objects are created and their methods are called?

```java
class Animal {
    public void speak() {
        System.out.println("The animal makes a sound.");
    }
}

class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("The dog barks.");
    }
}

public class TestInheritance {
    public static void main(String[] args) {
        Animal animal = new Animal();
        Dog dog = new Dog();
        animal.speak();
        dog.speak();
    }
}
```

**Failed Attempt:**  
I expected both outputs to be "The animal makes a sound." and "The dog barks.", as I assumed the `speak()` method would always refer to the object type in the main method.

**Mistake:**  
The reason both outputs appear as expected is that the `speak()` method is correctly overridden in the `Dog` subclass. Even though `animal` is of type `Animal`, Java uses dynamic method dispatch (polymorphism) to call the correct `speak()` method based on the actual object type, not the reference type. In the case of `animal.speak()`, it calls the `speak()` method in the `Animal` class, and for `dog.speak()`, it calls the overridden method in the `Dog` class.

**Correction:**  
This code is correct, but if you wanted to ensure it works even when objects are cast or referenced as the superclass type, the subclass version will always be invoked due to polymorphism. This is a demonstration of **method overriding** and **dynamic method dispatch**.

```java
class Animal {
    public void speak() {
        System.out.println("The animal makes a sound.");
    }
}

class Dog extends Animal {
    @Override
    public void speak() {
        System.out.println("The dog barks.");
    }
}

public class TestInheritance {
    public static void main(String[] args) {
        Animal animal = new Animal();
        Animal dog = new Dog();  // Dog object referenced as Animal type
        animal.speak();  // The animal makes a sound.
        dog.speak();  // The dog barks.
    }
}
```

Now, even though `dog` is declared as an `Animal` reference, it still calls the `speak()` method from the `Dog` subclass due to polymorphism.

---

## Practice Problem 2: Constructor Inheritance and `super()`

**Problem:**  
What happens when a subclass tries to call the constructor of its superclass using `super()`? Examine the following code:

```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
        System.out.println("Person constructor called.");
    }
}

class Student extends Person {
    int studentId;

    public Student(String name, int studentId) {
        super(name);  // Calls the Person constructor
        this.studentId = studentId;
        System.out.println("Student constructor called.");
    }
}

public class TestConstructorInheritance {
    public static void main(String[] args) {
        Student student = new Student("John Doe", 12345);
    }
}
```

**Failed Attempt:**  
I expected the `Student` constructor to automatically call the `Person` constructor without using `super()` explicitly.

**Mistake:**  
In Java, if the subclass does not explicitly call the superclass constructor, the compiler automatically inserts a call to the no-argument constructor (`super()`). Since the `Person` class does not have a no-argument constructor, you need to explicitly call the `Person` constructor using `super(name)` in the `Student` constructor.

**Correction:**  
The `super(name)` correctly calls the `Person` constructor and passes the `name` parameter. This ensures that the `Person` part of the `Student` object is properly initialized before executing the code in the `Student` constructor.

```java
class Person {
    String name;

    public Person(String name) {
        this.name = name;
        System.out.println("Person constructor called.");
    }
}

class Student extends Person {
    int studentId;

    public Student(String name, int studentId) {
        super(name);  // Calls the Person constructor with the name
        this.studentId = studentId;
        System.out.println("Student constructor called.");
    }
}

public class TestConstructorInheritance {
    public static void main(String[] args) {
        Student student = new Student("John Doe", 12345);
    }
}
```

This code will output:
```
Person constructor called.
Student constructor called.
```

---

## Practice Problem 3: Inheritance with Fields and `super`

**Problem:**  
What will be the result of the following code, and why is the `super` keyword used?

```java
class Animal {
    String name = "Animal";

    public void speak() {
        System.out.println("The " + name + " makes a sound.");
    }
}

class Dog extends Animal {
    String name = "Dog";

    public void speak() {
        System.out.println("The " + name + " barks.");
    }

    public void callSuperSpeak() {
        super.speak();  // Calls the Animal's speak method
    }
}

public class TestSuper {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.speak();
        dog.callSuperSpeak();
    }
}
```

**Failed Attempt:**  
I expected both `dog.speak()` and `dog.callSuperSpeak()` to print "The Dog barks" because both are instances of the `Dog` class.

**Mistake:**  
The issue is with the `name` field in both the `Animal` and `Dog` classes. The `name` field in `Dog` shadows the `name` field in `Animal`. When calling `dog.speak()`, the `name` field from the `Dog` class is used. However, inside the `callSuperSpeak()` method, `super.speak()` is used, which calls the `speak()` method from the `Animal` class, and it uses the `name` field from `Animal`.

**Correction:**  
The `super.speak()` call in `callSuperSpeak()` uses the `name` variable from the `Animal` class, which is why it prints "The Animal makes a sound."

```java
class Animal {
    String name = "Animal";

    public void speak() {
        System.out.println("The " + name + " makes a sound.");
    }
}

class Dog extends Animal {
    String name = "Dog";

    public void speak() {
        System.out.println("The " + name + " barks.");
    }

    public void callSuperSpeak() {
        super.speak();  // Calls the Animal's speak method
    }
}

public class TestSuper {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.speak();  // Output: The Dog barks.
        dog.callSuperSpeak();  // Output: The Animal makes a sound.
    }
}
```

---

## Future Topics to Work On

1. **Constructor Chaining**:
   - Practice how constructors work in an inheritance hierarchy, and use `super()` to call superclass constructors.

2. **Polymorphism**:
   - Practice method overriding and understanding how Java uses dynamic method dispatch to call the correct method based on the object type.

3. **Field Shadowing**:
   - Understand how subclass fields can shadow superclass fields, and how `super` can be used to access the superclass’s fields and methods.
