# TimevsSpaceComplexity

**Concept Type**:: #fundamentals #algorithm
**Mastery Level**:: `🧠 Familiar`
**Date Started**:: 2025-06-22
**Last Revised**::
**Related**:: [[Algorithmic_Complexity]]
**Tags**:: #core

## Core Concept

> _time complexity refers to how much computational time take the algorithm to run_

> _Space complexity refers to how much memory is using in the algorithm_

## Why Important?

- in order to make an algorithm faster, often is gonna take more memory
- in order to make an algorithm use less memory, often is gonna me slower

### how to calculate Complexity

The process of calculating algorithmic complexity, often referred to as Big O notation,
involves counting the operations or steps an algorithm takes in function of the size of its input.
The aim is to identify the worst-case, average-case, and best-case complexity. Generally,
the main focus is on the worst-case scenario which represents the maximum number of steps taken by
an algorithm. To calculate it, you consider the highest order of size (n) in your algorithm's steps.
For instance, if an algorithm performs a loop 5 times for 'n' items, and then does 3
unrelated steps, it has a complexity of O(n), because the linear steps grow faster than constant
ones as n increases. Other complexities include O(1) for constant complexity, O(n) for linear
complexity, O(n^2) for quadratic complexity, and so on, based on how the steps increase with size.

## Asymptotic Notation

Asymptotic notation is a way to describe the running time of an algorithm as the input size grows
towards infinity. It provides a high-level understanding of an algorithm's efficiency without
getting bogged down in implementation details or specific hardware.

### Common Asymptotic Notations:

- **Big O Notation ($O$):** Describes the **upper bound** or worst-case scenario of an
  algorithm's running time. It tells us that an algorithm will **at most**
  take a certain amount of time.
- Example: $O(n^2)$ means the running time grows no faster than a
  quadratic function of the input size $n$.
- **Omega Notation ($Omega$):** Describes the **lower bound** or best-case scenario.
  It tells us that an algorithm will **at least** take a certain amount of time.
  - Example: $Omega(n)$ means the running time will be at least linear with
    respect to the input size $n$.
- **Theta Notation ($Theta$):** Describes the **tight bound** or average-case scenario.
  It tells us that an algorithm's running time is both upper and lower bounded by the same
  function, meaning it grows at the same rate.
  - Example: $Theta(n log n)$ means the running time grows proportionally to $n log n$.

## Common Runtimes

Understanding these common runtimes is crucial for evaluating and comparing algorithm efficiency.

- **$O(1)$ - Constant Time:** The execution time remains constant, regardless of the input size.
  - Example: Accessing an element in an array by its index.
- **$O(log n)$ - Logarithmic Time:** The execution time grows logarithmically with the input size.
  This is very efficient, as the time required increases very slowly as the input grows.
  - Example: Binary search.
- **$O(n)$ - Linear Time:** The execution time grows linearly with the input size.
  If the input doubles, the time doubles.
  - Example: Iterating through an array to find a specific element.
- **$O(n log n)$ - Linearithmic Time:** The execution time grows proportionally to $n$ multiplied
  by the logarithm of $n$. This is common in efficient sorting algorithms.
  - Example: Merge Sort, Heap Sort.
- **$O(n^2)$ - Quadratic Time:** The execution time grows proportionally to the square of the
  input size. This often occurs when nested loops are used.
  - Example: Bubble Sort, insertion sort (worst case).
- **$O(2^n)$ - Exponential Time:** The execution time doubles with each additional element in
  the input. This is typically seen in algorithms that solve problems by brute-force searching
  through all possible subsets.
  - Example: Solving the Traveling Salesperson Problem using dynamic programming
    (for some formulations).
- **$O(n!)$ - Factorial Time:** The execution time grows very rapidly as the input size increases,
  proportional to the factorial of the input size. These algorithms are
  typically impractical for even small inputs.
  - Example: Brute-force solution to the Traveling Salesperson Problem.

## Resources

1.  [Official Documentation](https://www.google.com/search?q=)
2.  [Key Tutorial](https://www.google.com/search?q=)
3.  [Deep Dive Article](https://www.google.com/search?q=)
4.  [Practice Platform](https://www.google.com/search?q=)
