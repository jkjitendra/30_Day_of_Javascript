# Flatten Deeply Nested Array

## Problem Statement:

Given a **multi-dimensional** array `arr` and a depth `n`, return a **flattened** version of that array.

A **multi-dimensional** array is a recursive data structure that contains integers or other **multi-dimensional** arrays.

A **flattened** array is a version of that array with some or all of the sub-arrays removed and replaced with the actual elements in that sub-array. This flattening operation should only be done if the current depth of nesting is less than `n`. The depth of the elements in the first array are considered to be `0`.

Please solve it without the built-in `Array.flat` method.

**Example 1:**

<pre><strong>Input</strong>
arr = [1, 2, 3, [4, 5, 6], [7, 8, [9, 10, 11], 12], [13, 14, 15]]
n = 0
<strong>Output</strong>
[1, 2, 3, [4, 5, 6], [7, 8, [9, 10, 11], 12], [13, 14, 15]]

<strong>Explanation</strong>
Passing a depth of n=0 will always result in the original array. This is because the smallest possible depth of a subarray (0) is not less than n=0. Thus, no subarray should be flattened. </pre>

**Example 2:**

<pre><strong>Input</strong>
arr = [1, 2, 3, [4, 5, 6], [7, 8, [9, 10, 11], 12], [13, 14, 15]]
n = 1
<strong>Output</strong>
[1, 2, 3, 4, 5, 6, 7, 8, [9, 10, 11], 12, 13, 14, 15]

<strong>Explanation</strong>
The subarrays starting with 4, 7, and 13 are all flattened. This is because their depth of 0 is less than 1. However [9, 10, 11] remains unflattened because its depth is 1.</pre>

**Example 3:**

<pre><strong>Input</strong>
arr = [[1, 2, 3], [4, 5, 6], [7, 8, [9, 10, 11], 12], [13, 14, 15]]
n = 2
<strong>Output</strong>
[1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15]

<strong>Explanation</strong>
The maximum depth of any subarray is 1. Thus, all of them are flattened.</pre>

**Constraints:**

* 0 <= count of numbers in arr <= 10`<sup>`5`</sup>`
* 0 <= count of subarrays in arr <= 10`<sup>`5`</sup>`
* `maxDepth <= 1000`
* `-1000 <= each number <= 1000`
* `0 <= n <= 1000`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Array} arr
 * @param {number} depth
 * @return {Array}
 */
var flat = function (arr, n) {
  if (n <= 0)
    return arr;
  let flattenedArray = [];
  for (element of arr) {
    if (Array.isArray(element)) {
      flattenedArray.push(...flat(element, n-1));
    } else {
      flattenedArray.push(element);
    }
  }
  return flattenedArray;
};

```
