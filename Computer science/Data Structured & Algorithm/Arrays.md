---
id: Arrays
aliases: []
tags: []
---

Source: [[Basic Data Structures]]
Useful Page: https://www.geeksforgeeks.org/array-data-structure-guide/

is an collection of data store progressively in memory,he as three parts

- index -> the current position of the element starting in 0
- element -> the value store in the array (any data type or unique datatype)
- Length -> the length of the array determinate of the number of items that contains

## Memory Representation

Arrays store contigous in memory this is useful for search based on index and get quick acces to elements

```javascript
const arr = ["pepe", "mary", "George"];
//              0      1        2  --> index in memory
```

why do we need arrays

imagine we have 5 child, each child pick up 10 numbers sequentially and we want to store for future use, we can create individual variables and store it there, but what happen when we evaluate 100 child the amount of variables growth too, instead we can initialize an array for each kid and store the data. the arrays are useful for store multiple relation data in one variable.

## Type of Arrays

### Base on size

#### fix length

arrays with fix length are useful when you want to retrieve only an amount of data in order to no use to much memory, you can decide the length of the array when you either declare or initialize

#### dynamic size

Arrays that growth with the elements you put in

### Base on Dimensions

You can nested arrays in elements that called `(N)Dimensional Arrays` who store more data nested in the elements

## Operations Array

### Traversal array

This is the most commons operations, we use the index and the values of the elements in order to make the operations sequentially.

#### Type of traversals

Linear: go through the array from the start to the end

- useful for:
- printing values
- searching
- performing calculations (like sum or average)

Reverse:

- useful for:
- evaluate variable from the end

### Insertion arrays

Is the operations where you want to add some elements while maintain the order in the array
he do:

- determinate where the element is shifting
- adjust the index of the other element is he need it
- add the element
- increment the length of the array

#### Type of insertions

1. Insertion at the Beginning (Index 0)

   Every element must shift one position right.
   This is the least efficient case for large arrays as it affects all elements.

2. Insertion at a Specific Index

   Elements after the index shift right.
   If the index is in the middle, half of the array moves.

3. Insertion at the End

   The simplest case since no shifting is required.
   Used in dynamic arrays where size increases automatically (e.g., Python lists, Java ArrayList).

### Delete arrays

use it to delete element of an arrays, we know that arrays are continuous in memory so if you delete an element the other shift to the left in order to keep the space, and reduce the length depending of the type

#### Type of DELETE

Types of Deletion

1. Deletion at the Beginning (Index 0)

   Every element shifts left by one position.
   This is the most expensive case as it affects all elements.

2. Deletion at a Specific Index

   Only elements after the index shift left.
   If the index is in the middle, half of the array moves.

3. Deletion at the End

   The simplest case since no shifting is required.
   The size of the array is reduced (in dynamic arrays).

## Searching Operation

Searching in an array refers to the process of finding a specific element in a given list of elements. The goal is to determine whether the element exists in the array and, if so, find its index (position).
Searching is a fundamental operation in programming, as it is used in data retrieval, filtering, and processing.

Types of Searching in an Array

There are two main types of searching techniques in an array:

1. Linear Search (Sequential Search)

   This is the simplest search algorithm.
   It traverses the array one element at a time and compares each element with the target value.
   If a match is found, it returns the index of the element.
   If the element is not found, the search continues until the end of the array.

2. Binary Search (Efficient Search for Sorted Arrays)

   Works only on sorted arrays (in increasing or decreasing order).
   Uses a divide and conquer approach.
   It repeatedly divides the search space in half until the target element is found.

How Binary Search Works?

    Find the middle element of the array.
    If the target is equal to the middle element, return its index.
    If the target is less than the middle element, search the left half.
    If the target is greater than the middle element, search the right half.
    Repeat until the element is found or the search space is empty.
