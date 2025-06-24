# InsertionSort

**Concept Type**:: #javaScript
**Mastery Level**:: `🧠 Familiar `
**Date Started**:: 2025-06-24
**Last Revised**::
**Related**:: [[Algorithmic_Complexity]][[SortingAlgorithms]]
**Tags**:: #fundamentals #algorithm #SortingAlgorithms

## Core Concept

> _hold the values in a sorted part of the array and the other part is for the unsorted values._

## Core Mechanics

1. Take the first value from the unsorted part of the array.
2. Move the value into the correct place in the sorted part of the array.
3. Go through the unsorted part of the array again as many times as there are values.

```javaScript
function insertionSort(arr) {
  for (let i = 1; i <= arr.length - 1; i++) {
    let temp = arr[i];
    let j = i - 1;

    while (j >= 0 && temp < arr[j]) {
      arr[j + 1] = arr[j];
      j--
    }

    arr[j + 1] = temp;
  }

  return arr;
}

```

## Resources

1. [Official Documentation](https://www.geeksforgeeks.org/dsa/insertion-sort-algorithm/)
2. [Key Tutorial]()
3. [Deep Dive Article](https://www.hackerearth.com/practice/algorithms/sorting/insertion-sort/tutorial/)
4. [Practice Platform]()
