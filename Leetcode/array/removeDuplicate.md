relational: [[Computer science]]
diagram: https://excalidraw.com/#json=guZWnNVQ9NaCm2dMsTA-i,BdhdAj_ABXK-3s1kJC_eSg 
Given an integer array nums sorted in non-decreasing order, remove the duplicates in-place such that each unique element appears only once.
The relative order of the elements should be kept the same. Then return the number of unique elements in nums.

Consider the number of unique elements of nums to be k, to get accepted, you need to do the following things:

Change the array nums such that the first k elements of nums contain the unique elements in the order they were present in nums initially. The remaining elements of nums are not important as well as the size of nums.
Return k.

## first try (brute Force)

```javascript
  let i = 0;
  const arr = [];
  const results = [];
  while (i <= nums.length - 1) {
    if (arr.includes(nums[i])) {
      results.push(i);
    } else {
      arr.push(nums[i]);
    }
    i++
  }

  let j = results.length - 1;

  while (j >= 0) {
    nums.splice(results[j],1)
    j--;
  }
  return nums.length;
```

### approach
intuition
- Get the index of the duplicates Values
- Iterate from the end and remove the duplicates values in-place

Explanation
- my approach is, take all the unique values in the input (arr) and 
and take the duplicates values in the input (results)
- iterate from the end to the beginning of the input and erase the duplicates values 
using the results array
- then retrieve the input array length with only unique values

## Second try (two pointers)

```javascript
function removeDuplicates(nums) {
let i = 1;
let j = 1;

  while (i < nums.length) {

    if (nums[i] !== nums[i - 1]) {
      nums[j] = nums[i]
      j++
    }
    i++
  }
  return j;
}
```

intuition
- use two pointers, one for iterate over the array and the other for replace the duplicates values
- start from 1 because the first value in the array always gonna be unique
- don't focus in the duplicates instead focus when they are different

Explanation
 -We have an array of number in ascending order with duplicates values, 
-we need to check and focus  when the values are different not when the values are duplicate
- create two pointer, one for iterate and one for make change when a value is different
- we need to:
    - initialize both pointers in one
    - check if the current values is not equal to the previous value
        - if its we want to make "j" the current value in "i" and increment "j"
	- increment "I" until we find all the unique values
    - then we retrieve the count in "j"