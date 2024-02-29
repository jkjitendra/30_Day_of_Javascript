# To Be Or Not To Be

## Problem Statement:

Write a function `expect` that helps developers test their code. It should take in any value `val` and return an object with the following two functions.

* `toBe(val)` accepts another value and returns `true` if the two values `===` each other. If they are not equal, it should throw an error `"Not Equal"`.
* `notToBe(val)` accepts another value and returns `true` if the two values `!==` each other. If they are equal, it should throw an error `"Equal"`.

**Example 1:**

<pre><strong>Input:</strong> func = () => expect(5).toBe(5)
<strong>Output:</strong> {"value": true}
<strong>Explanation:</strong> 5 === 5 so this expression returns true.
</pre>

**Example 2:**

<pre><strong>Input:</strong> func = () => expect(5).toBe(null)
<strong>Output:</strong> {"error": "Not Equal"}
<strong>Explanation:</strong> 5 !== null so this expression throw the error "Not Equal".
</pre>

**Example 3:**

<pre><strong>Input:</strong> func = () => expect(5).notToBe(null)
<strong>Output:</strong> {"value": true}
<strong>Explanation:</strong> 5 !== null so this expression returns true.</pre>

## Solution:

#### Method 1:

```javascript
/**
 * @param {string} val
 * @return {Object}
 */
var expect = function(val) {
  let obj = {
    toBe: function(val1) {
      if (val === val1) return true;
      else throw new Error("Not Equal");
    },
    notToBe: function(val2) {
      if (val !== val2) return true;
      else throw new Error("Equal");
    }
  };
  return obj;
};

/**
 * expect(5).toBe(5); // true
 * expect(5).notToBe(5); // throws "Equal"
 */
```
