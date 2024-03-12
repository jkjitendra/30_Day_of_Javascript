# Return Length of Arguments Passed

## Problem Statement:


Write a function `argumentsLength` that returns the count of arguments passed to it.

**Example 1:**

<pre><strong>Input:</strong> args = [5]
<strong>Output:</strong> 1
<strong>Explanation:</strong>
argumentsLength(5); // 1

One value was passed to the function so it should return 1.
</pre>

**Example 2:**

<pre><strong>Input:</strong> args = [{}, null, "3"]
<strong>Output:</strong> 3
<strong>Explanation:</strong> 
argumentsLength({}, null, "3"); // 3

Three values were passed to the function so it should return 3.
</pre>

**Constraints:**

* `args` is a valid JSON array
* `0 <= args.length <= 100`

## Solution:

#### Method 1:

```javascript
/**
 * @param {...(null|boolean|number|string|Array|Object)} args
 * @return {number}
 */
var argumentsLength = function(...args) {
  return args.length;
};

/**
 * argumentsLength(1, 2, 3); // 3
 */
```