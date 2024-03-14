# Promise Time Limit

## Problem Statement:

Given an asynchronous function `fn` and a time `t` in milliseconds, return a new **time limited** version of the input function. `fn` takes arguments provided to the **time limited **function.

The **time limited** function should follow these rules:

* If the `fn` completes within the time limit of `t` milliseconds, the **time limited** function should resolve with the result.
* If the execution of the `fn` exceeds the time limit, the **time limited** function should reject with the string `"Time Limit Exceeded"`.

**Example 1:**

<pre><strong>Input:</strong> 
fn = async (n) => { 
  await new Promise(res => setTimeout(res, 100)); 
  return n * n; 
}
inputs = [5]
t = 50
<strong>Output:</strong> {"rejected":"Time Limit Exceeded","time":50}
<strong>Explanation:</strong>
const limited = timeLimit(fn, t)
const start = performance.now()
let result;
try {
   const res = await limited(...inputs)
   result = {"resolved": res, "time": Math.floor(performance.now() - start)};
} catch (err) {
   result = {"rejected": err, "time": Math.floor(performance.now() - start)};
}
console.log(result) // Output

The provided function is set to resolve after 100ms. However, the time limit is set to 50ms. It rejects at t=50ms because the time limit was reached.
</pre>

**Example 2:**

<pre><strong>Input:</strong> 
fn = async (n) => { 
  await new Promise(res => setTimeout(res, 100)); 
  return n * n; 
}
inputs = [5]
t = 150
<strong>Output:</strong> {"resolved":25,"time":100}
<strong>Explanation:</strong>
The function resolved 5 * 5 = 25 at t=100ms. The time limit is never reached.
</pre>

**Example 3:**

<pre><strong>Input:</strong> 
fn = async (a, b) => { 
  await new Promise(res => setTimeout(res, 120)); 
  return a + b; 
}
inputs = [5,10]
t = 150
<strong>Output:</strong> {"resolved":15,"time":120}
<strong>Explanation:</strong>
The function resolved 5 + 10 = 15 at t=120ms. The time limit is never reached.
</pre>

**Example 4:**

<pre><strong>Input:</strong> 
fn = async () => { 
  throw "Error";
}
inputs = []
t = 1000
<strong>Output:</strong> {"rejected":"Error","time":0}
<strong>Explanation:</strong>
The function immediately throws an error.</pre>

**Constraints:**

* `0 <= inputs.length <= 10`
* `0 <= t <= 1000`
* `fn` returns a promise

## Solution:

#### Method 1:

```javascript
/**
 * @param {Function} fn
 * @param {number} t
 * @return {Function}
 */
var timeLimit = function(fn, t) {
  
  return async function(...args) {
    return await new Promise((resolve, reject) => {
      let timeout = setTimeout(() => {
        reject("Time Limit Exceeded");
      }, t);

      fn(...args).then((res) => {
        clearTimeout(timeout);
        resolve(res);
      }).catch((err) => {
        clearTimeout(timeout);
        reject(err);
      });
      
    });
  }
};

/**
 * const limited = timeLimit((t) => new Promise(res => setTimeout(res, t)), 100);
 * limited(150).catch(console.log) // "Time Limit Exceeded" at t=100ms
 */
```

#### Method 2:

```javascript
/**
 * @param {Function} fn
 * @param {number} t
 * @return {Function}
 */
var timeLimit = function(fn, t) {
  
  return async function(...args) {
    const oldFn = fn(...args);
    const timeout = new Promise((resolve, reject) => {
      setTimeout(()=>{
        reject('Time Limit Exceeded');
      },t);
    })
    return Promise.race([oldFn,timeout]);
  }
};

/**
 * const limited = timeLimit((t) => new Promise(res => setTimeout(res, t)), 100);
 * limited(150).catch(console.log) // "Time Limit Exceeded" at t=100ms
 */
```