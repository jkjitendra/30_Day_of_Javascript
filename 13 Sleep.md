# Sleep

## Problem Statement:

Given a positive integer `millis`, write an asynchronous function that sleeps for `millis` milliseconds. It can resolve any value.

**Example 1:**

<pre><strong>Input:</strong> millis = 100
<strong>Output:</strong> 100
<strong>Explanation:</strong> It should return a promise that resolves after 100ms.
let t = Date.now();
sleep(100).then(() => {
  console.log(Date.now() - t); // 100
});
</pre>

**Example 2:**

<pre><strong>Input:</strong> millis = 200
<strong>Output:</strong> 200
<strong>Explanation:</strong> It should return a promise that resolves after 200ms.
</pre>

**Constraints:**

* `1 <= millis <= 1000`

## Solution:

#### Method 1:

```javascript
/**
 * @param {number} millis
 * @return {Promise}
 */
async function sleep(millis) {
  return await new Promise((res) => setTimeout(res, millis)); 
}

/** 
 * let t = Date.now()
 * sleep(100).then(() => console.log(Date.now() - t)) // 100
 */
```
