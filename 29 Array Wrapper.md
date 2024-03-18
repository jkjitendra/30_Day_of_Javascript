# Array Wrapper

## Problem Statement:

Create a class `ArrayWrapper` that accepts an array of integers in its constructor. This class should have two features:

* When two instances of this class are added together with the `+` operator, the resulting value is the sum of all the elements in both arrays.
* When the `String()` function is called on the instance, it will return a comma separated string surrounded by brackets. For example, `[1,2,3]`.

**Example 1:**

<pre><strong>Input:</strong> nums = [[1,2],[3,4]], operation = "Add"
<strong>Output:</strong> 10
<strong>Explanation:</strong>
const obj1 = new ArrayWrapper([1,2]);
const obj2 = new ArrayWrapper([3,4]);
obj1 + obj2; // 10
</pre>

**Example 2:**

<pre><strong>Input:</strong> nums = [[23,98,42,70]], operation = "String"
<strong>Output:</strong> "[23,98,42,70]"
<strong>Explanation:</strong>
const obj = new ArrayWrapper([23,98,42,70]);
String(obj); // "[23,98,42,70]"
</pre>

**Example 3:**

<pre><strong>Input:</strong> nums = [[],[]], operation = "Add"
<strong>Output:</strong> 0
<strong>Explanation:</strong>
const obj1 = new ArrayWrapper([]);
const obj2 = new ArrayWrapper([]);
obj1 + obj2; // 0
</pre>

**Constraints:**

* `0 <= nums.length <= 1000`
* `0 <= nums[i] <= 1000`
* `Note: nums is the array passed to the constructor`

## Solution:

## Method 1:

```javascript
/**
 * @param {number[]} nums
 * @return {void}
 */
var ArrayWrapper = function(nums) {
  this.arrays = nums;
};

/**
 * @return {number}
 */
ArrayWrapper.prototype.valueOf = function() {
  let sumOfNums = 0;
  for (num of this.arrays) {
    sumOfNums += num;
  }
  return sumOfNums;
}

/**
 * @return {string}
 */
ArrayWrapper.prototype.toString = function() {
  return `[${this.arrays.join(',')}]`;
  // return JSON.stringify(this.arrays);
}

/**
 * const obj1 = new ArrayWrapper([1,2]);
 * const obj2 = new ArrayWrapper([3,4]);
 * obj1 + obj2; // 10
 * String(obj1); // "[1,2]"
 * String(obj2); // "[3,4]"
 */
```

#### Method 2:

```javascript
/**
 * @param {number[]} nums
 * @return {void}
 */
var ArrayWrapper = function(nums) {
  this.arrays = nums;
};

/**
 * @return {number}
 */
ArrayWrapper.prototype.valueOf = function() {
  return this.arrays.reduce((arr1, arr2) => arr1+arr2, 0);
}

/**
 * @return {string}
 */
ArrayWrapper.prototype.toString = function() {
  return `[${this.arrays.join(',')}]`;
  // return JSON.stringify(this.arrays);
}

/**
 * const obj1 = new ArrayWrapper([1,2]);
 * const obj2 = new ArrayWrapper([3,4]);
 * obj1 + obj2; // 10
 * String(obj1); // "[1,2]"
 * String(obj2); // "[3,4]"
 */
```
