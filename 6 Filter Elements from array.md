# Filter Elements from array

## Problem Statement:


Given an integer array `arr` and a filtering function `fn`, return a filtered array `filteredArr`.

The `fn` function takes one or two arguments:

* `arr[i]` - number from the `arr`
* `i` - index of `arr[i]`

`filteredArr` should only contain the elements from the `arr` for which the expression `fn(arr[i], i)` evaluates to a **truthy** value. A **truthy** value is a value where `Boolean(value)` returns `true`.

Please solve it without the built-in `Array.filter` method.

**Example 1:**

<pre><strong>Input:</strong> arr = [0,10,20,30], fn = function greaterThan10(n) { return n > 10; }
<strong>Output:</strong> [20,30]
<strong>Explanation:</strong>
const newArray = filter(arr, fn); // [20, 30]
The function filters out values that are not greater than 10</pre>

**Example 2:**

<pre><strong>Input:</strong> arr = [1,2,3], fn = function firstIndex(n, i) { return i === 0; }
<strong>Output:</strong> [1]
<strong>Explanation:</strong>
fn can also accept the index of each element
In this case, the function removes elements not at index 0
</pre>

**Example 3:**

<pre><strong>Input:</strong> arr = [-2,-1,0,1,2], fn = function plusOne(n) { return n + 1 }
<strong>Output:</strong> [-2,0,1,2]
<strong>Explanation:</strong>
Falsey values such as 0 should be filtered out
</pre>

**Constraints:**

* 0 <= arr.length <= 1000
* -10<sup>9</sup> <= arr[i] <= 10<sup>9</sup>

## Solution:
#### Method 1:

```javascript
/**
 * @param {number[]} arr
 * @param {Function} fn
 * @return {number[]}
 */
var filter = function(arr, fn) {
  const filteredArray = [];
  for (let i = 0; i < arr.length; i++) {
    const val = fn(arr[i], i);
    if (val) {
      filteredArray.push(arr[i]);
    }
  }
  return filteredArray;
};
```