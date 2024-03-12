# Function Composition

## Problem Statement:


Given an array of functions `[f<span>1</span>, f<sub>2</sub>, f<sub>3</sub>, ..., f<sub>n</sub>]`, return a new function `fn` that is the **function composition** of the array of functions.

The **function composition** of `[f(x), g(x), h(x)]` is `fn(x) = f(g(h(x)))`.

The **function composition** of an empty list of functions is the **identity function** `f(x) = x`.

You may assume each function in the array accepts one integer as input and returns one integer as output.

**Example 1:**

<pre><strong>Input:</strong> functions = [x => x + 1, x => x * x, x => 2 * x], x = 4
<strong>Output:</strong> 65
<strong>Explanation:</strong>
Evaluating from right to left ...
Starting with x = 4.
2 * (4) = 8
(8) * (8) = 64
(64) + 1 = 65
</pre>

**Example 2:**

<pre><strong>Input:</strong> functions = [x => 10 * x, x => 10 * x, x => 10 * x], x = 1
<strong>Output:</strong> 1000
<strong>Explanation:</strong>
Evaluating from right to left ...
10 * (1) = 10
10 * (10) = 100
10 * (100) = 1000
</pre>

**Example 3:**

<pre><strong>Input:</strong> functions = [], x = 42
<strong>Output:</strong> 42
<strong>Explanation:</strong>
The composition of zero functions is the identity function</pre>

**Constraints:**

* `-1000 <= x <= 1000`
* `0 <= functions.length <= 1000`
* `all functions accept and return a single integer`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Function[]} functions
 * @return {Function}
 */
var compose = function(functions) {
  
  return function(x) {
    if (functions.length === 0) return x;
    let output = functions[functions.length - 1](x);
    for (var i = functions.length - 2; i >= 0; i--) {
    output = functions[i](output);
    }
    return output;
  }
};

/**
 * const fn = compose([x => x + 1, x => 2 * x])
 * fn(4) // 9
 */
```
