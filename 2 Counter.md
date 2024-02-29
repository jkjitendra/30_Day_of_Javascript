# Counter

## Problem Statement:

Given an integer `n`, return a `counter` function. This `counter` function initially returns `n` and then returns 1 more than the previous value every subsequent time it is called (`n`, `n + 1`, `n + 2`, etc).

**Example 1:**

<pre><strong>Input:</strong> 
n = 10 
["call","call","call"]
<strong>Output:</strong> [10,11,12]
<strong>Explanation: 
</strong>counter() = 10 // The first time counter() is called, it returns n.
counter() = 11 // Returns 1 more than the previous time.
counter() = 12 // Returns 1 more than the previous time.
</pre>

**Example 2:**

<pre><strong>Input:</strong> 
n = -2
["call","call","call","call","call"]
<strong>Output:</strong> [-2,-1,0,1,2]
<strong>Explanation:</strong> counter() initially returns -2. Then increases after each sebsequent call.
</pre>

**Constraints:**

* `-1000<sup> </sup><= n <= 1000`
* `0 <= calls.length <= 1000`
* `calls[i] === "call"`


## Solution:

```javascript
/**
 * @param {number} n
 * @return {Function} counter
 */
var createCounter = function(n) {
  
  return function() {
    return n++;
  };
};

/** 
 * const counter = createCounter(10)
 * counter() // 10
 * counter() // 11
 * counter() // 12
 */
```
