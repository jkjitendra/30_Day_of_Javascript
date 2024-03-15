# Array Prototype Last

## Problem Statement:

Write code that enhances all arrays such that you can call the `array.last()` method on any array and it will return the last element. If there are no elements in the array, it should return `-1`.

You may assume the array is the output of `JSON.parse`.

**Example 1:**

<pre><strong>Input:</strong> nums = [null, {}, 3]
<strong>Output:</strong> 3
<strong>Explanation:</strong> Calling nums.last() should return the last element: 3.
</pre>

**Example 2:**

<pre><strong>Input:</strong> nums = []
<strong>Output:</strong> -1
<strong>Explanation:</strong> Because there are no elements, return -1.
</pre>

**Constraints:**

* `arr` is a valid JSON array
* `0 <= arr.length <= 1000`

## Solution:

#### Method 1:

```javascript
/**
 * @return {null|boolean|number|string|Array|Object}
 */
Array.prototype.last = function() {
  return this.length === 0 ? -1 : this[this.length -1];
};

/**
 * const arr = [1, 2, 3];
 * arr.last(); // 3
 */
```
