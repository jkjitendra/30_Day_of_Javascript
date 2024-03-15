# Sort By

## Problem Statement:

Given an array `arr` and a function `fn`, return a sorted array `sortedArr`. You can assume `fn` only returns numbers and those numbers determine the sort order of `sortedArr`. `sortedArray` must be sorted in **ascending order** by `fn` output.

You may assume that `fn` will never duplicate numbers for a given array.

**Example 1:**

<pre><strong>Input:</strong> arr = [5, 4, 1, 2, 3], fn = (x) => x
<strong>Output:</strong> [1, 2, 3, 4, 5]
<strong>Explanation:</strong> fn simply returns the number passed to it so the array is sorted in ascending order.
</pre>

**Example 2:**

<pre><strong>Input:</strong> arr = [{"x": 1}, {"x": 0}, {"x": -1}], fn = (d) => d.x
<strong>Output:</strong> [{"x": -1}, {"x": 0}, {"x": 1}]
<strong>Explanation:</strong> fn returns the value for the "x" key. So the array is sorted based on that value.
</pre>

**Example 3:**

<pre><strong>Input:</strong> arr = [[3, 4], [5, 2], [10, 1]], fn = (x) => x[1]
<strong>Output:</strong> [[10, 1], [5, 2], [3, 4]]
<strong>Explanation:</strong> arr is sorted in ascending order by number at index=1. 
</pre>

**Constraints:**

* `arr` is a valid JSON array
* `fn` is a function that returns a number
* 1 <= arr.length <= 5 * 10`<sup>`5`</sup>`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Array} arr
 * @param {Function} fn
 * @return {Array}
 */
var sortBy = function(arr, fn) {
  const sortedArr = arr.sort((a, b) => fn(a) - fn(b));
  return sortedArr;
};
```
