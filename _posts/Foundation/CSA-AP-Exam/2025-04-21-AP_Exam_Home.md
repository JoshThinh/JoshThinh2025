---
layout: post
title: AP CSA Exam Home
description: Home page to access all material for the AP CSA Final Exam
permalink: /CSA/Final/Exam/Home
type: collab
comment: true
---

## Units 1-10
<!-- Search Bar -->
<div class="mb-4">
  <input 
    type="text" 
    id="searchBar" 
    placeholder="Search subjects..." 
    class="w-full px-4 py-2 border border-gray-300 rounded"
    onkeyup="filterSubjects()"
  />
</div>

<!-- Scrollable Button Row -->
<div class="overflow-x-auto">
  <div class="flex flex-nowrap space-x-2 pb-2" id="subjectContainer">
    {% assign topics = "Primitive Types,Using Objects,Boolean Expressions and if Statements,Iteration,Writing Classes,Array,ArrayList,2D Array,Inheritance,Recursion" | split: "," %}
    {% assign links = "primitive-types,using-objects,boolean-expressions,iteration,writing-classes,array,arraylist,2d-array,inheritance,recursion" | split: "," %}
    {% for topic in topics %}
      <a 
        href="/JoshThinh2025/CSA/Final/Exam/{{ links[forloop.index0] }}/" 
        class="inline-flex bg-blue-500 hover:bg-blue-600 text-white font-semibold py-2 px-4 rounded subject-btn whitespace-nowrap"
      >
        {{ topic }}
      </a>
    {% endfor %}
  </div>
</div>

<script>
function filterSubjects() {
  const input = document.getElementById('searchBar').value.toLowerCase();
  const buttons = document.getElementsByClassName('subject-btn');
  for (let btn of buttons) {
    const text = btn.innerText.toLowerCase();
    btn.style.display = text.includes(input) ? 'inline-flex' : 'none';
  }
}
</script>

---

## AP CSA Study Plan (Burndown List)

### Study Strategy
- Study one topic per day
- Review and practice every 2–3 topics
- Take practice quizzes weekly
- Review mistakes and refine notes

---

## Burndown by Topic

### 1. Primitive Types
- [ ] Variables and data types
- [ ] Casting and overflow
- [ ] Arithmetic expressions
- [ ] Integer division vs float

### 2. Using Objects
- [ ] String methods
- [ ] Wrapper classes (Integer, Double)
- [ ] Constructors and method calls

### 3. Boolean Expressions and if Statements
- [ ] Logical operators (&&, ||, !)
- [ ] If/else, else-if logic
- [ ] De Morgan’s Law

### 4. Iteration
- [ ] for, while, do-while loops
- [ ] Nested loops
- [ ] Common loop errors

### 5. Writing Classes
- [ ] Instance variables
- [ ] Constructors
- [ ] Accessor and mutator methods
- [ ] Overloading methods

### 6. Array
- [ ] Declaring and initializing arrays
- [ ] Looping through arrays
- [ ] Common array algorithms

### 7. ArrayList
- [ ] ArrayList methods: add, get, remove, set
- [ ] Enhanced for loop
- [ ] Choosing ArrayList vs array

### 8. 2D Array
- [ ] Declaration and indexing
- [ ] Nested loops with 2D arrays
- [ ] Row sum, column sum, max/min

### 9. Inheritance
- [ ] extends and super keywords
- [ ] Method overriding
- [ ] Polymorphism basics
- [ ] Abstract classes

### 10. Recursion
- [ ] Base and recursive cases
- [ ] Tracing recursive calls
- [ ] Writing simple recursive methods
