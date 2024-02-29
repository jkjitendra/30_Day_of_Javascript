# Create Hello World Function

## Problem Statement:

Write a function `createHelloWorld`. It should return a new function that always returns `"Hello World"`.

**Example 1:**

<pre><strong>Input:</strong> args = []
<strong>Output:</strong> "Hello World"
<strong>Explanation:</strong>
const f = createHelloWorld();
f(); // "Hello World"

The function returned by createHelloWorld should always return "Hello World".
</pre>

**Example 2:**

<pre><strong>Input:</strong> args = [{},null,42]
<strong>Output:</strong> "Hello World"
<strong>Explanation:</strong>
const f = createHelloWorld();
f({}, null, 42); // "Hello World"

Any arguments could be passed to the function but it should still always return "Hello World".
</pre>

**Constraints:**

* `0 <= args.length <= 10`


## Solution:

```javascript
/**
 * @return {Function}
 */
var createHelloWorld = function() {
  
  return function(...args) {
    return "Hello World";
  }
};

/**
 * const f = createHelloWorld();
 * f(); // "Hello World"
 */
```
