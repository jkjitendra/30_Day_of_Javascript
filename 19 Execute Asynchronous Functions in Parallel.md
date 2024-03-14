# Execute Asynchronous Functions in Parallel

## Problem Statement:

Given an array of asynchronous functions `functions`, return a new promise `promise`. Each function in the array accepts no arguments and returns a promise. All the promises should be executed in parallel.

`promise` resolves:

* When all the promises returned from `functions` were resolved successfully in parallel. The resolved value of `promise` should be an array of all the resolved values of promises in the same order as they were in the `functions`. The `promise` should resolve when all the asynchronous functions in the array have completed execution in parallel.

`promise` rejects:

* When any of the promises returned from `functions` were rejected. `promise` should also reject with the reason of the first rejection.

Please solve it without using the built-in `Promise.all` function.

**Example 1:**

<pre><strong>Input:</strong> functions = [
  () => new Promise(resolve => setTimeout(() => resolve(5), 200))
]
<strong>Output:</strong> {"t": 200, "resolved": [5]}
<strong>Explanation:</strong> 
promiseAll(functions).then(console.log); // [5]

The single function was resolved at 200ms with a value of 5.
</pre>

**Example 2:**

<pre><strong>Input:</strong> functions = [
    () => new Promise(resolve => setTimeout(() => resolve(1), 200)), 
    () => new Promise((resolve, reject) => setTimeout(() => reject("Error"), 100))
]
<strong>Output:</strong> {"t": 100, "rejected": "Error"}
<strong>Explanation:</strong> Since one of the promises rejected, the returned promise also rejected with the same error at the same time.
</pre>

**Example 3:**

<pre><strong>Input:</strong> functions = [
    () => new Promise(resolve => setTimeout(() => resolve(4), 50)), 
    () => new Promise(resolve => setTimeout(() => resolve(10), 150)), 
    () => new Promise(resolve => setTimeout(() => resolve(16), 100))
]
<strong>Output:</strong> {"t": 150, "resolved": [4, 10, 16]}
<strong>Explanation:</strong> All the promises resolved with a value. The returned promise resolved when the last promise resolved.
</pre>

**Constraints:**

* `functions` is an array of functions that returns promises
* `1 <= functions.length <= 10`


## Solution:

#### Method 1:

```javascript
/**
 * @param {Array<Function>} functions
 * @return {Promise<any>}
 */
var promiseAll = function(functions) {
  return new Promise((resolve, reject) => {

    const results = [];
    let resolvedCount = 0;
    let rejected = false;

    for (let i = 0; i < functions.length; i++) {
      functions[i]()
      .then(result => {
        if (!rejected) {
          results[i] = result;
          resolvedCount++;

          if (resolvedCount === functions.length) {
            resolve(results);
          }
        }
      })
      .catch(error => {
        if (!rejected) {
          rejected = true;
          reject(error);
        }
      });
    }
  });
};

/**
 * const promise = promiseAll([() => new Promise(res => res(42))])
 * promise.then(console.log); // [42]
 */
```

#### Method 2:

```javascript
/**
 * @param {Array<Function>} functions
 * @return {Promise<any>}
 */
var promiseAll = function(functions) {
  return new Promise((resolve, reject) => {

    let count = 0;
    const functionsPromiseResult = [];
    functions.forEach((fn, index) => {
      fn()
      .then((res) => {
        functionsPromiseResult[index] = res;
        count++;
        if(count === functions.length) resolve(functionsPromiseResult);
      })
      .catch((errorMessage) => reject(errorMessage));
    });
  });
};

/**
 * const promise = promiseAll([() => new Promise(res => res(42))])
 * promise.then(console.log); // [42]
 */
```