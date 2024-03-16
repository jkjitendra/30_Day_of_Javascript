# Compact Object

## Problem Statement:

Given an object or array `obj`, return a  **compact object** . A **compact object** is the same as the original object, except with keys containing **falsy** values removed. This operation applies to the object and any nested objects. Arrays are considered objects where the indices are keys. A value is considered **falsy** when `Boolean(value)` returns `false`.

You may assume the `obj` is the output of `JSON.parse`. In other words, it is valid JSON.

**Example 1:**

<pre><strong>Input:</strong> obj = [null, 0, false, 1]
<strong>Output:</strong> [1]
<strong>Explanation:</strong> All falsy values have been removed from the array.
</pre>

**Example 2:**

<pre><strong>Input:</strong> obj = {"a": null, "b": [false, 1]}
<strong>Output:</strong> {"b": [1]}
<strong>Explanation:</strong> obj["a"] and obj["b"][0] had falsy values and were removed.</pre>

**Example 3:**

<pre><strong>Input:</strong> obj = [null, 0, 5, [0], [false, 16]]
<strong>Output:</strong> [5, [], [16]]
<strong>Explanation:</strong> obj[0], obj[1], obj[3][0], and obj[4][0] were falsy and removed.
</pre>

**Constraints:**

* `obj` is a valid JSON object
* 2 <= JSON.stringify(obj).length <= 10`<sup>`6`</sup>`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Object|Array} obj
 * @return {Object|Array}
 */
var compactObject = function(obj) {
  if (obj === null) return null;
  if (Array.isArray(obj)) {
    return obj.filter(Boolean).map(compactObject);
  }
  if (typeof obj !== 'object') {
    return obj;
  }

  const compactObj = {};
  for (const key in obj) {
    const value = compactObject(obj[key]);
    if (Boolean(value)) {
      compactObj[key] = value;
    }
  }
  return compactObj;
};
```
