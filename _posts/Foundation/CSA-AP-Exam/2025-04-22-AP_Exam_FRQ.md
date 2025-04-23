---
layout: post
title: FRQ Overview
description: Corrections on the College Board FRQ
permalink: /CSA/Final/Exam/college-frq/
type: collab
comment: true
---

## 2020 FRQ Practice
### Question 1

```
// Part A
public static int hailstoneLength(int n) {
    int count = 1; // Start counting from the initial value
    while (n != 1) {
        if (n % 2 == 0) {
            n = n / 2;
        } else {
            n = 3 * n + 1;
        }
        count++;
    }
    return count;
}

// Part B
public static boolean isLongSequence(int n) {
    return hailstoneLength(n) > n;
}

// Part C
public static double propLong(int n) {
    int longCount = 0;
    for (int i = 1; i <= n; i++) {
        if (isLongSequence(i)) {
            longCount++;
        }
    }
    return (double) longCount / n;
}
```
### Key Takeaways
- This problem reinforces control flow using loops and conditionals.

- Using helper methods reduces repetition and increases code clarity.

- Be mindful of the return types, especially when working with proportions.

### Common Mistakes
- Forgetting to include the starting number in the count.

- Using integer division when a double result is required.

- Confusing the sequence termination condition.

### What I Learned
- You can reuse methods to build up more complex functionality.

- When dividing integers for a percentage or proportion, type casting is crucial.

- Simple algorithms like Hailstone can be powerful practice for logic and structure.

### Things to Look Out For
- Integer vs. double when calculating and returning a ratio.

- Make sure all loops eventually exit, especially recursive patterns.

- Watch for off-by-one errors when looping through a range.

### Tips
- Break down the problem into smaller parts to solve each step individually.

- Test your logic with known sequences (e.g., hailstone for 5 or 7).

- Use a helper method like isLongSequence inside loops to simplify main logic.

### Question 2
```
import java.util.Random;

public class GameSpinner {
    private int sectors;
    private int lastSpin;
    private int runLength;
    private Random rand;

    public GameSpinner(int numSectors) {
        sectors = numSectors;
        lastSpin = -1;
        runLength = 0;
        rand = new Random();
    }

    public int spin() {
        int result = rand.nextInt(sectors) + 1;
        if (result == lastSpin) {
            runLength++;
        } else {
            runLength = 1;
            lastSpin = result;
        }
        return result;
    }

    public int currentRun() {
        return runLength;
    }
}
```
## Key Takeaways
- Randomization combined with state tracking teaches important simulation patterns.

- Maintaining state across multiple method calls is a critical object-oriented skill.

## Common Mistakes
- Resetting the lastSpin or runLength incorrectly.

- Not initializing lastSpin to an invalid state (e.g., -1) initially.

- Off-by-one errors with the range of random numbers.

## What I Learned
- How to use instance variables to store state between method calls.

- Importance of updating and resetting values based on conditions.

- Creating classes that simulate real-world processes involves more than just one-time calculations.

## Things to Look Out For
- Random values must include all sectors, so remember to add 1 to the result of rand.nextInt().

- State logic must distinguish between the first spin and future spins.

- Avoid unnecessary changes to values outside of key conditions.

## Tips
- Use diagrams to visualize the state changes of the object.

- Test multiple spins in sequence to validate run tracking.

- Print debugging information to trace internal state during tests.

## Question 3
```
// Part A
public void addReview(ProductReview prodReview) {
    reviewList.add(prodReview);
    String name = prodReview.getName();
    if (!productList.contains(name)) {
        productList.add(name);
    }
}

// Part B
public int getNumGoodReviews(String prodName) {
    int count = 0;
    for (ProductReview review : reviewList) {
        if (review.getName().equals(prodName) && review.getReview().contains("best")) {
            count++;
        }
    }
    return count;
}
```
## Key Takeaways
- Good for learning about combining object references with list-based collections.

- Shows how string comparison and search can be used to process reviews.

## Common Mistakes
- Using == instead of .equals() when comparing strings.

- Not checking both name and review content properly.

- Failing to avoid duplicates in productList.

## What I Learned
- Always use .equals() when comparing objects like Strings.

- Looping through lists lets you apply filters or counters based on conditions.

- Dual list management (like a list of names and reviews) is a common structure in applications.

## Things to Look Out For
- Make sure both conditions in Part B are enforced (equals and contains).

- Keep list operations efficient by avoiding unnecessary duplicates.

- Handle empty list cases gracefully.

## Tips
- Start with small test cases with a single review to test functionality.

- Think of productList as a catalog and reviewList as the history — they serve different roles.

- Practice searching and filtering collections to gain fluency.

## Question 4
```
// Part A
public Theater(int seatsPerRow, int tier1Rows, int tier2Rows) {
    theaterSeats = new Seat[tier1Rows + tier2Rows][seatsPerRow];
    for (int row = 0; row < theaterSeats.length; row++) {
        int tier = (row < tier1Rows) ? 1 : 2;
        for (int col = 0; col < seatsPerRow; col++) {
            theaterSeats[row][col] = new Seat(true, tier);
        }
    }
}

// Part B
public boolean reassignSeat(int fromRow, int fromCol, int toRow, int toCol) {
    Seat from = theaterSeats[fromRow][fromCol];
    Seat to = theaterSeats[toRow][toCol];

    if (to.isAvailable() && to.getTier() >= from.getTier()) {
        from.setAvailability(true);
        to.setAvailability(false);
        return true;
    }
    return false;
}
```
## Key Takeaways
- A great example of how to initialize and manage 2D arrays of objects.

- Teaches how to encode domain rules into program logic (e.g., seat tiers).

## Common Mistakes
- Not checking all conditions when moving seats.

- Misusing row/column indices or confusing tier rules.

- Failing to initialize each seat correctly in the constructor.

## What I Learned
- How to create and initialize a 2D array of objects based on row-specific rules.

- How to enforce constraints in movement logic (e.g., can’t downgrade seats).

- Constructing logic with real-world inspiration (e.g., seat upgrades).

## Things to Look Out For
- Watch for logic errors in tier comparisons.

- Ensure availability is updated on both source and destination.

- All array cells must be filled — no nulls allowed!

## Tips
- Build a helper method for seat reassignment if conditions grow more complex.

- Always initialize 2D arrays row-by-row and column-by-column.

- Trace an example reassign scenario by hand to verify correctness.