---
layout: post
title: "Java Collections"
description: "Explore the Java Collections Framework, including Lists, Sets, and Deques, their key features, and example usages."
permalink: "/CSA/Final/Exam/collectibles-frq/"
type: post
comment: "A detailed overview of Java Collections with practice problems."
---

## Java Collections Overview

The **Java Collections Framework** provides a unified structure for working with groups of objects. At its core is the `Collection` interface, which defines common behaviors for all standard collections. Since `Collection` extends `Iterable`, all collections can be looped through using a for-each loop. 

### Key Benefits of Using Collections:
- **Dynamic sizing** (unlike arrays)
- Works with any **object type** using generics
- Common operations like `add()`, `remove()`, and `contains()`
- Allows flexible, reusable code through **interfaces**

### Core Java Collection Implementations:
- **ArrayList**: Implements `List` (which extends `Collection`)
  - Ordered, allows duplicates, fast random access
  - Example: `ArrayList`
  
- **HashSet**: Implements `Set` (which extends `Collection`)
  - Unordered, no duplicates, fast operations using hashing
  - Example: `HashSet`
  
- **LinkedList**: Implements `List`, `Deque`, and `Queue` (all extend `Collection`)
  - Ordered, allows duplicates, efficient insert/remove
  - Example: `LinkedList`

---

### 1. Lists - **Srini**
#### What is a List?
- **Ordered Collection**: Elements are stored in a specific sequence.
- **Indexed Access**: Elements can be accessed via their index.
- **Duplicates Allowed**: Lists can contain multiple instances of the same element.
- **Insertion Order Preserved**: The order of insertion is maintained.

#### Common Operations:
- `add(E e)`: Adds the element to the end of the list.
- `add(int index, E element)`: Inserts the element at the specified index.
- `get(int index)`: Retrieves the element at the specified index.
- `set(int index, E element)`: Replaces the element at the specified index.
- `remove(int index)`: Removes the element at the specified index.
- `indexOf(Object o)`: Finds the first occurrence of the specified element.
- `lastIndexOf(Object o)`: Finds the last occurrence of the specified element.
- `subList(int fromIndex, int toIndex)`: Returns a sublist from the specified range of indices.

#### Example: Basic List Operations
import java.util.ArrayList;
import java.util.List;

List<String> fruits = new ArrayList<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Orange");
fruits.add("Mango");

System.out.println("Fruits List: " + fruits);
String firstFruit = fruits.get(0);
System.out.println("First Fruit: " + firstFruit);

fruits.set(1, "Blueberry");
System.out.println("Updated List: " + fruits);

fruits.remove(2);
System.out.println("List After Removal: " + fruits);

int index = fruits.indexOf("Mango");
System.out.println("Index of Mango: " + index);

int size = fruits.size();
System.out.println("Size of List: " + size);

boolean hasApple = fruits.contains("Apple");
System.out.println("List contains Apple: " + hasApple);

List<String> sublist = fruits.subList(0, 2);
System.out.println("Sublist: " + sublist);

---

### 2. Sets
#### What is a Set?
- A **Collection** that cannot contain duplicate elements
- Models the mathematical set abstraction
- No guarantees concerning the order of elements

#### Key Operations:
- `add(E e)`: Adds element to the set if not already present.
- `remove(Object o)`: Removes specified element if present.
- `contains(Object o)`: Returns true if set contains the specified element.
- `isEmpty()`: Returns true if set contains no elements.
- `size()`: Returns the number of elements in the set.
- `clear()`: Removes all elements from the set.

#### Example: Basic Set Operations
import java.util.HashSet;
import java.util.Set;

Set<String> fruits = new HashSet<>();
fruits.add("Apple");
fruits.add("Banana");
fruits.add("Orange");
fruits.add("Apple");  // Duplicate, won't be added!

System.out.println("Set after adding elements: " + fruits);
fruits.remove("Banana");
System.out.println("Set after removing 'Banana': " + fruits);

boolean containsOrange = fruits.contains("Orange");
System.out.println("Set contains 'Orange': " + containsOrange);

System.out.println("Size of Set: " + fruits.size());
System.out.println("Is Set empty: " + fruits.isEmpty());

fruits.clear();
System.out.println("Set after clearing: " + fruits);
System.out.println("Is Set empty after clear: " + fruits.isEmpty());

---

### 3. Queues
#### What is a Queue?
- A collection designed for holding elements prior to processing.
- Follows the **First-In-First-Out (FIFO)** principle: the first element added is the first one to be removed.
- Useful in scenarios like scheduling, task processing, or handling events.

#### Key Operations:
- `add(E e)`: Adds an element to the queue.
- `remove()`: Removes and returns the head (first element) of the queue.
- `peek()`: Returns the head of the queue without removing it.
- `isEmpty()`: Returns true if the queue contains no elements.
- `size()`: Returns the number of elements in the queue.
- `clear()`: Removes all elements from the queue.

#### Example: Basic Queue Operations
import java.util.LinkedList;
import java.util.Queue;

Queue<String> queue = new LinkedList<>();
queue.add("Apple");
queue.add("Banana");
queue.add("Orange");

System.out.println("Queue after adding elements: " + queue);

String removedElement = queue.remove();
System.out.println("Removed element: " + removedElement);

String firstElement = queue.peek();
System.out.println("First element (peek): " + firstElement);

System.out.println("Size of Queue: " + queue.size());
System.out.println("Is Queue empty: " + queue.isEmpty());

queue.clear();
System.out.println("Queue after clearing: " + queue);
System.out.println("Is Queue empty after clear: " + queue.isEmpty());

---

### 4. Deques
#### What is a Deque?
- A **double-ended queue** that allows insertion and removal of elements from both ends.
- Supports both **FIFO (queue)** and **LIFO (stack)** operations.

#### Key Operations:
- `addFirst(E e)`: Inserts element at the front.
- `addLast(E e)`: Inserts element at the back.
- `removeFirst()`: Removes and returns the front element.
- `removeLast()`: Removes and returns the back element.
- `peekFirst()`: Returns the front element without removing it.
- `peekLast()`: Returns the back element without removing it.
- `isEmpty()`: Returns true if the deque is empty.
- `size()`: Returns the number of elements.
- `clear()`: Removes all elements from the deque.

#### Example: Basic Deque Operations
import java.util.ArrayDeque;
import java.util.Deque;

Deque<String> deque = new ArrayDeque<>();
deque.addFirst("B");
deque.addLast("C");
deque.addFirst("A");
deque.addLast("D");

System.out.println(deque);

System.out.println(deque.removeFirst());
System.out.println(deque.removeLast());

System.out.println(deque.peekFirst());
System.out.println(deque.peekLast());

System.out.println(deque.isEmpty());
System.out.println(deque.size());

deque.clear();
System.out.println(deque.isEmpty());

---

## Java Collections Homework (due the Wednesday After Spring Break)
### Objectives:
- Practice using **List**, **Set**, and **Deque**.
- Understand when and why to use each collection type.
- Apply key methods from each collection type.
- Practice iteration and conditional logic with collections.

### Part 1: Working with Lists
**Task**: Create a method that takes a `List` and returns a new list containing only the **even numbers**, in the same order.
- **Requirements**: Use `ArrayList`, `add()`, `get()`, and `size()`. Use a loop (not streams).

### Part 2: Working with Sets
**Task**: Create a method that takes two `Set` objects and returns a new `Set` with only the **common elements** (i.e. the intersection).
- **Requirements**: Use `HashSet`, `contains()`, `add()`, and iteration. The final result should have no duplicates.

### Part 3: Working with Deques
**Task**: Simulate a line of customers using a `Deque`. Implement the following steps in order:
1. Add 3 customers to the end.
2. Add 1 customer to the front (VIP).
3. Remove the customer at the front.
4. Show the current front and back of the line.
5. Print the size of the line.

- **Requirements**: Use `ArrayDeque`, `addFirst()`, `addLast()`, `removeFirst()`, `peekFirst()`, `peekLast()`, and `size()`.

### Challenge Question (Bonus +0.01)
**Question**: You need to store a collection of student IDs where:
- Order doesn’t matter.
- You must prevent duplicates.
- You often need to check if an ID exists.
Which collection type would be most efficient to use and why?
## Part 2: Working with Sets
Task: Create a method that takes two Set objects and returns a new Set with only the common elements (i.e. the intersection).

Requirements: Use HashSet, contains(), add(), and iteration. The final result should have no duplicates.

Solution:
java
Copy
Edit
import java.util.HashSet;
import java.util.Set;

public class SetIntersection {
    public static Set<Integer> intersection(Set<Integer> set1, Set<Integer> set2) {
        Set<Integer> result = new HashSet<>();
        for (Integer num : set1) {
            if (set2.contains(num)) {
                result.add(num);
            }
        }
        return result;
    }

    public static void main(String[] args) {
        Set<Integer> set1 = new HashSet<>();
        set1.add(1);
        set1.add(2);
        set1.add(3);

        Set<Integer> set2 = new HashSet<>();
        set2.add(2);
        set2.add(3);
        set2.add(4);

        System.out.println(intersection(set1, set2));
    }
}
## Part 3: Working with Deques
Task: Simulate a line of customers using a Deque. Implement the following steps in order:

Add 3 customers to the end.

Add 1 customer to the front (VIP).

Remove the customer at the front.

Show the current front and back of the line.

Print the size of the line.

Solution:
java
Copy
Edit
import java.util.ArrayDeque;
import java.util.Deque;

public class CustomerLine {
    public static void main(String[] args) {
        Deque<String> line = new ArrayDeque<>();
        
        // Step 1: Add 3 customers to the end
        line.addLast("Customer1");
        line.addLast("Customer2");
        line.addLast("Customer3");
        
        // Step 2: Add a VIP customer to the front
        line.addFirst("VIP Customer");
        
        // Step 3: Remove customer at the front
        line.removeFirst();
        
        // Step 4: Show the current front and back of the line
        System.out.println("Front: " + line.peekFirst());
        System.out.println("Back: " + line.peekLast());
        
        // Step 5: Print the size of the line
        System.out.println("Line size: " + line.size());
    }
}
## Challenge Question (Bonus +0.01)
Question: You need to store a collection of student IDs where:

Order doesn’t matter.

You must prevent duplicates.

You often need to check if an ID exists. Which collection type would be most efficient to use and why?

Answer: A HashSet would be most efficient because:

It doesn't maintain any order.

It automatically prevents duplicates.

It provides fast access to check if an element (student ID) exists due to the use of hashing.