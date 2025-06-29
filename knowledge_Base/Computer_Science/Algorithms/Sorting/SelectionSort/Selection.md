# Selection

**Concept Type**:: #javaScript
**Mastery Level**:: `🧠 Familiar`
**Date Started**:: 2025-06-23
**Last Revised**::
**Related**:: [[Algorithmic_Complexity]], [[SortingAlgorithms]]
**Tags**:: #fundamentals #SortingAlgorithms #algorithm

## Core Concept

> _Sorting algorithm who divide the arr of elements in two sorted and unsorted_

## How It Works

1. initially the sorted part is empty and the unsorted contains all the elements
2. the algorithm iterate through the unsorted list and store the minum value and put in in the end
   of the sorted list
3. the process continue until the sorted list have all the parts from the unsorted List.

## Core Mechanics

```javaScript
function selectionSort(arr) {

  for (let i = 0; i <= arr.length - 1;i++) {
    let ln = i;
    let temp;
    for (let j = i + 1; j< arr.length;j++) {

      if (arr[j] < arr[ln]) {
        ln = j;
      }
    }
    temp = arr[i];
    arr[i] = arr[ln];
    arr[ln] = temp;
  }
  console.log(arr);
}



selectionSort([7,12,9,11,3]);
selectionSort([64, 34, 25, 12, 22, 11, 90, 5]);
```

## Resources

1. [Official Documentation]()
2. [Key Tutorial]()
3. [Deep Dive Article]()
4. [Practice Platform]()
