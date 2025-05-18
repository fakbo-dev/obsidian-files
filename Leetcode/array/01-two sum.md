Relation: [[Computer science]]

# Step to solve the problem

```javascript
//Given an array of integers nums and an integer target, return indices of the two numbers such that they add up to target.

//You may assume that each input would have exactly one solution, and you may not use the same element twice.

//You can return the answer in any order.


//example 1:

//input: nums = [2,7,11,15], target = 9
//output: [0,1]
//explanation: because nums[0] + nums[1] == 9, we return [0, 1].

//example 2:

//Input: nums = [3,2,4], target = 6
//Output: [1,2]
//Example 3:

//Input: nums = [3,3], target = 6
//Output: [0,1]


```

## Solution one: Brute Force
we need the index of the number his sum be equal to the target.
- we take the length of the array and store it in a variable
- we initialize an array name "result" in order to store the answer
- we use a nested loop, one iterate through the whole array starting for the first element (0)
- the nested loop iterate from (i + 1) and check every possible combination until he get the value
```javascript
function twoSum(nums,target) {

  const l = nums.length;
  let result = []
  for (let i = 0; i <= l - 1; i++) {

    for (let j = i + 1; j <=l - 1; j++) {
      if (nums[i] + nums[j] === target) {
        result.push(i);
        result.push(j);
      }

    }
  }
  return result;
}
console.log(twoSum([2,7,11,15], 9));

```

## Solution Two: Binary Search

