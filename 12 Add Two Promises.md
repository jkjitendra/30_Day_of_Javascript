# Add Two Promises

## Problem Statement:

Given two promises `promise1` and `promise2`, return a new promise. `promise1` and `promise2` will both resolve with a number. The returned promise should resolve with the sum of the two numbers.

**Example 1:**

<pre><strong>Input:</strong> 
promise1 = new Promise(resolve => setTimeout(() => resolve(2), 20)), 
promise2 = new Promise(resolve => setTimeout(() => resolve(5), 60))
<strong>Output:</strong> 7
<strong>Explanation:</strong> The two input promises resolve with the values of 2 and 5 respectively. The returned promise should resolve with a value of 2 + 5 = 7. The time the returned promise resolves is not judged for this problem.
</pre>

**Example 2:**

<pre><strong>Input:</strong> 
promise1 = new Promise(resolve => setTimeout(() => resolve(10), 50)), 
promise2 = new Promise(resolve => setTimeout(() => resolve(-12), 30))
<strong>Output:</strong> -2
<strong>Explanation:</strong> The two input promises resolve with the values of 10 and -12 respectively. The returned promise should resolve with a value of 10 + -12 = -2.
</pre>

**Constraints:**

* `promise1` and `promise2` are promises that resolve with a number


## Solution:

#### Method 1:

```javascript
/**
 * @param {Promise} promise1
 * @param {Promise} promise2
 * @return {Promise}
 */
var addTwoPromises = async function(promise1, promise2) {
  let promiseSum = await promise1 + await promise2;
  return promiseSum;
};

/**
 * addTwoPromises(Promise.resolve(2), Promise.resolve(2))
 *   .then(console.log); // 4
 */
```
