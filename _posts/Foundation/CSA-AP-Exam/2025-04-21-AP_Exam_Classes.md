---
layout: post
title: Writing Classes - Practice Problems and Corrections
description: Practice problems with failed attempts and detailed corrections to help understand writing classes in Java.
permalink: /CSA/Final/Exam/writing-classes/
type: collab
comment: true
---

# Writing Classes - AP CSA Practice Problems

## Description

Writing classes is a fundamental aspect of object-oriented programming in Java. In this section, we will focus on creating custom classes, defining instance variables, constructors, methods, and the importance of using getters and setters. We'll also explore method overloading and how to instantiate objects.

---

## Practice Problem 1: Creating a Simple Class and Using Constructor

**Problem:**  
Create a class called `Book` with instance variables `title`, `author`, and `pages`. Implement a constructor to initialize these variables and display the book information.

```java
public class Book {
    String title;
    String author;
    int pages;

    // Constructor
    public Book(String title, String author, int pages) {
        title = title;
        author = author;
        pages = pages;
    }

    public void displayInfo() {
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
        System.out.println("Pages: " + pages);
    }

    public static void main(String[] args) {
        Book myBook = new Book("Java Programming", "John Doe", 350);
        myBook.displayInfo();
    }
}
```

**Failed Attempt:**  
I was trying to print the `title`, `author`, and `pages`, but when I ran the program, the output showed that the values were missing or null.

**Mistake:**  
The issue occurred because the constructor was not properly initializing the instance variables. In the constructor, the parameters `title`, `author`, and `pages` were assigned to themselves instead of the instance variables. This caused the instance variables to remain uninitialized (i.e., null for `String` and 0 for `int`).

**Correction:**  
The correct way to assign the parameter values to the instance variables is to use the `this` keyword to refer to the instance variables of the class. Here's the corrected code:

```java
public class Book {
    String title;
    String author;
    int pages;

    // Constructor
    public Book(String title, String author, int pages) {
        this.title = title;       // Use 'this' to refer to instance variables
        this.author = author;
        this.pages = pages;
    }

    public void displayInfo() {
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
        System.out.println("Pages: " + pages);
    }

    public static void main(String[] args) {
        Book myBook = new Book("Java Programming", "John Doe", 350);
        myBook.displayInfo();
    }
}
```

**Explanation:**  
- In the constructor, `this.title = title;` assigns the value of the `title` parameter to the `title` instance variable of the class. The same applies for `author` and `pages`.
- Now, when the program is run, the correct information for the `Book` instance is displayed.

---

## Practice Problem 2: Using Getters and Setters

**Problem:**  
Enhance the `Book` class to include getter and setter methods for all instance variables. Then, write a method to update the `pages` value and print the updated information.

```java
public class Book {
    private String title;
    private String author;
    private int pages;

    // Constructor
    public Book(String title, String author, int pages) {
        this.title = title;
        this.author = author;
        this.pages = pages;
    }

    // Getter methods
    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public int getPages() {
        return pages;
    }

    // Setter methods
    public void setTitle(String title) {
        this.title = title;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public void setPages(int pages) {
        this.pages = pages;
    }

    // Method to update pages
    public void updatePages(int newPages) {
        setPages(newPages);
        System.out.println("Updated Pages: " + getPages());
    }

    public void displayInfo() {
        System.out.println("Title: " + getTitle());
        System.out.println("Author: " + getAuthor());
        System.out.println("Pages: " + getPages());
    }

    public static void main(String[] args) {
        Book myBook = new Book("Java Programming", "John Doe", 350);
        myBook.displayInfo();
        
        // Update pages
        myBook.updatePages(400);
        myBook.displayInfo();
    }
}
```

**Failed Attempt:**  
I wrote the getter and setter methods correctly, but when I tried to update the pages with `myBook.setPages(400);`, I was not sure how to handle it when modifying an individual instance variable.

**Mistake:**  
While the setter method works, it’s good practice to encapsulate modifications in specialized methods that provide meaningful behavior. In this case, a `updatePages` method was missing to encapsulate the behavior of changing the number of pages and printing the result.

**Correction:**  
I created a new method `updatePages(int newPages)` that uses the setter method to update the `pages` variable, then prints the updated value. This ensures proper encapsulation and maintains good object-oriented design principles.

---

## Practice Problem 3: Method Overloading in Classes

**Problem:**  
Add method overloading to the `Book` class, where you provide two versions of the `displayInfo` method: one that displays full information (`title`, `author`, and `pages`) and another that only displays the `title` and `author`.

```java
public class Book {
    private String title;
    private String author;
    private int pages;

    // Constructor
    public Book(String title, String author, int pages) {
        this.title = title;
        this.author = author;
        this.pages = pages;
    }

    // Overloaded displayInfo method
    public void displayInfo() {
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
        System.out.println("Pages: " + pages);
    }

    // Overloaded displayInfo method
    public void displayInfo(boolean showPages) {
        System.out.println("Title: " + title);
        System.out.println("Author: " + author);
        if (showPages) {
            System.out.println("Pages: " + pages);
        }
    }

    public static void main(String[] args) {
        Book myBook = new Book("Java Programming", "John Doe", 350);
        
        // Display full info
        myBook.displayInfo();

        // Display only title and author
        myBook.displayInfo(false);
    }
}
```

**Failed Attempt:**  
I was unsure how to overload a method correctly. I thought I could simply give both methods the same name without any parameters, but Java requires method overloading to differ in their parameters.

**Mistake:**  
To overload a method, Java needs to differentiate the methods by their parameters, either in the number of parameters or their types. I tried to use the same method signature, but the compiler won't allow it.

**Correction:**  
I overloaded the `displayInfo` method by adding a boolean parameter. If `true`, it prints the number of pages; if `false`, it omits the pages from the output.

---

## Future Topics to Work On

1. **Constructor Overloading**:
   - Practice creating multiple constructors for the same class with different parameter lists.

2. **Instance Methods vs Static Methods**:
   - Understand the difference between instance methods (that operate on object data) and static methods (that operate on class-level data).

3. **Encapsulation and Abstraction**:
   - Focus on using access modifiers (`private`, `protected`, `public`) to encapsulate the class data and control access through getters and setters.

4. **Method Chaining**:
   - Explore the practice of method chaining in object-oriented classes, where multiple methods can be called in a single line using the return values of methods.

