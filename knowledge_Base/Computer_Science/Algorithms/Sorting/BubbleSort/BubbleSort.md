# BubbleSort

**Concept Type**:: #javaScript
**Mastery Level**:: `🧠 Familiar `
**Date Started**:: 2025-06-22
**Last Revised**::
**Related**:: [[Algorithmic_Complexity]],[[SortingAlgorithms]]
**Tags**:: #fundamentals #SortingAlgorithms #algorithm

## Core Concept

> _is an algorithm that sorted the array or list from the lowest to the highest value_

## How It Works

1. Go through the array, one value at a time.
2. For each value, compare the value with the next value.
3. If the value is higher than the next one, swap the values so that the highest value comes last.
4. Go through the array as many times as there are values in the array.

## Core Mechanics

```javaScript
function bubbleSort(arr) {
  let i = 0;
  let j = 0;
  let temp;
  while (i <= arr.length - 1) {
    let sorted = false;
    while (j <= arr.length - 1) {
    if (arr[j] > arr[j + 1] && arr[j + 1] !== undefined) {
      temp = arr[j];
      arr[j] = arr[j + 1];
      arr[j + 1] =  temp
        sorted = true
    }
      j++
    }
    if (!sorted) return arr;
    j = 0
    i++;
    console.log(`run Number: ${i}`)
  }
  return arr;
}

console.log(bubbleSort([7,12,9,11,3]));
console.log(bubbleSort([100, 50, 75, 25, 1000, 1, 0, -1]));
console.log(bubbleSort([7, 3, 9, 12, 11]));
```

## Resources

1. [Official Documentation](https://www.w3schools.com/dsa/dsa_algo_bubblesort.php)
2. [Key Tutorial]()
3. [Deep Dive Article]()
4. [Practice Platform]()
