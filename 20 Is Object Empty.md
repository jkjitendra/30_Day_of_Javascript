# Is Object Empty

## Problem Statement:

Given an object or an array, return if it is empty.

* An empty object contains no key-value pairs.
* An empty array contains no elements.

You may assume the object or array is the output of `JSON.parse`.

**Example 1:**

<pre><strong>Input:</strong> obj = {"x": 5, "y": 42}
<strong>Output:</strong> false
<strong>Explanation:</strong> The object has 2 key-value pairs so it is not empty.
</pre>

**Example 2:**

<pre><strong>Input:</strong> obj = {}
<strong>Output:</strong> true
<strong>Explanation:</strong> The object doesn't have any key-value pairs so it is empty.
</pre>

**Example 3:**

<pre><strong>Input:</strong> obj = [null, false, 0]
<strong>Output:</strong> false
<strong>Explanation:</strong> The array has 3 elements so it is not empty.
</pre>

**Constraints:**

* `obj` is a valid JSON object or array
* 2 <= JSON.stringify(obj).length <= 10`<sup>`5`</sup>`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Object|Array} obj
 * @return {boolean}
 */
var isEmpty = function(obj) {
  
  return Object.keys(obj).length === 0;
};
```
