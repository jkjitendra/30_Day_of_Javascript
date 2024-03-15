# Chunk Array

## Problem Statement:

Given an array `arr` and a chunk size `size`, return a **chunked** array. A **chunked** array contains the original elements in `arr`, but consists of subarrays each of length `size`. The length of the last subarray may be less than `size` if `arr.length` is not evenly divisible by `size`.

You may assume the array is the output of `JSON.parse`. In other words, it is valid JSON.

Please solve it without using lodash's `_.chunk` function.

**Example 1:**

<pre><strong>Input:</strong> arr = [1,2,3,4,5], size = 1
<strong>Output:</strong> [[1],[2],[3],[4],[5]]
<strong>Explanation:</strong> The arr has been split into subarrays each with 1 element.
</pre>

**Example 2:**

<pre><strong>Input:</strong> arr = [1,9,6,3,2], size = 3
<strong>Output:</strong> [[1,9,6],[3,2]]
<strong>Explanation:</strong> The arr has been split into subarrays with 3 elements. However, only two elements are left for the 2nd subarray.
</pre>

**Example 3:**

<pre><strong>Input:</strong> arr = [8,5,3,2,6], size = 6
<strong>Output:</strong> [[8,5,3,2,6]]
<strong>Explanation:</strong> Size is greater than arr.length thus all elements are in the first subarray.
</pre>

**Example 4:**

<pre><strong>Input:</strong> arr = [], size = 1
<strong>Output:</strong> []
<strong>Explanation:</strong> There are no elements to be chunked so an empty array is returned.</pre>

**Constraints:**

* `arr` is a valid JSON array
* 2 <= JSON.stringify(arr).length <= 10`<sup>`5`</sup>`
* `1 <= size <= arr.length + 1`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Array} arr
 * @param {number} size
 * @return {Array}
 */
var chunk = function(arr, size) {
  let chunked = [];
  for (let i = 0; i < arr.length; i+=size) {
    chunked.push(arr.slice(i, i+size));
  }
  return chunked;
};

```

#### Method 2:

```javascript
/**
 * @param {Array} arr
 * @param {number} size
 * @return {Array}
 */
var chunk = function(arr, size) {
  let chunked = [];

  for (let i = 0; i < arr.length; i++) {
    chunked.push(arr.splice(i, size, arr[i]));
  }
  return chunked;
};

```
