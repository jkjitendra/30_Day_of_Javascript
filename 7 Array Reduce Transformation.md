# Array Reduce Transformation

## Problem Statement:

Given an integer array `nums`, a reducer function `fn`, and an initial value `init`, return the final result obtained by executing the `fn` function on each element of the array, sequentially, passing in the return value from the calculation on the preceding element.

This result is achieved through the following operations: `val = fn(init, nums[0]), val = fn(val, nums[1]), val = fn(val, nums[2]), ...` until every element in the array has been processed. The ultimate value of `val` is then returned.

If the length of the array is 0, the function should return `init`.

Please solve it without using the built-in `Array.reduce` method.

**Example 1:**

<pre><strong>Input:</strong> 
nums = [1,2,3,4]
fn = function sum(accum, curr) { return accum + curr; }
init = 0
<strong>Output:</strong> 10
<strong>Explanation:</strong>
initially, the value is init=0.
(0) + nums[0] = 1
(1) + nums[1] = 3
(3) + nums[2] = 6
(6) + nums[3] = 10
The final answer is 10.
</pre>

**Example 2:**

<pre><strong>Input:</strong> 
nums = [1,2,3,4]
fn = function sum(accum, curr) { return accum + curr * curr; }
init = 100
<strong>Output:</strong> 130
<strong>Explanation:</strong>
initially, the value is init=100.
(100) + nums[0] * nums[0] = 101
(101) + nums[1] * nums[1] = 105
(105) + nums[2] * nums[2] = 114
(114) + nums[3] * nums[3] = 130
The final answer is 130.
</pre>

**Example 3:**

<pre><strong>Input:</strong> 
nums = []
fn = function sum(accum, curr) { return 0; }
init = 25
<strong>Output:</strong> 25
<strong>Explanation:</strong> For empty arrays, the answer is always init.
</pre>

**Constraints:**

* `0 <= nums.length <= 1000`
* `0 <= nums[i] <= 1000`
* `0 <= init <= 1000`


## Solution:

#### Method 1:

```javascript
/**
 * @param {number[]} nums
 * @param {Function} fn
 * @param {number} init
 * @return {number}
 */
var reduce = function(nums, fn, init) {
  for (let i = 0; i < nums.length; i++) {
    init = fn(init, nums[i]);
  }
  return init;
};
```
