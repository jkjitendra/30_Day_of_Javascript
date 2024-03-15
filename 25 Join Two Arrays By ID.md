# Join Two Arrays By Id

## Problem Statement:

Given two arrays `arr1` and `arr2`, return a new array `joinedArray`. All the objects in each of the two inputs arrays will contain an `id` field that has an integer value. `joinedArray` is an array formed by merging `arr1` and `arr2` based on their `id` key. The length of `joinedArray` should be the length of unique values of `id`. The returned array should be sorted in **ascending** order based on the `id` key.

If a given `id` exists in one array but not the other, the single object with that `id` should be included in the result array without modification.

If two objects share an `id`, their properties should be merged into a single object:

* If a key only exists in one object, that single key-value pair should be included in the object.
* If a key is included in both objects, the value in the object from `arr2` should override the value from `arr1`.

**Example 1:**

<pre><strong>Input:</strong> 
arr1 = [
    {"id": 1, "x": 1},
    {"id": 2, "x": 9}
], 
arr2 = [
    {"id": 3, "x": 5}
]
<strong>Output:</strong> 
[
    {"id": 1, "x": 1},
    {"id": 2, "x": 9},
    {"id": 3, "x": 5}
]
<strong>Explanation:</strong> There are no duplicate ids so arr1 is simply concatenated with arr2.
</pre>

**Example 2:**

<pre><strong>Input:</strong> 
arr1 = [
    {"id": 1, "x": 2, "y": 3},
    {"id": 2, "x": 3, "y": 6}
], 
arr2 = [
    {"id": 2, "x": 10, "y": 20},
    {"id": 3, "x": 0, "y": 0}
]
<strong>Output:</strong> 
[
    {"id": 1, "x": 2, "y": 3},
    {"id": 2, "x": 10, "y": 20},
    {"id": 3, "x": 0, "y": 0}
]
<strong>Explanation:</strong> The two objects with id=1 and id=3 are included in the result array without modifiction. The two objects with id=2 are merged together. The keys from arr2 override the values in arr1.
</pre>

**Example 3:**

<pre><strong>Input:</strong> 
arr1 = [
    {"id": 1, "b": {"b": 94},"v": [4, 3], "y": 48}
]
arr2 = [
    {"id": 1, "b": {"c": 84}, "v": [1, 3]}
]
<strong>Output:</strong> [
    {"id": 1, "b": {"c": 84}, "v": [1, 3], "y": 48}
]
<strong>Explanation:</strong> The two objects with id=1 are merged together. For the keys "b" and "v" the values from arr2 are used. Since the key "y" only exists in arr1, that value is taken form arr1.</pre>

**Constraints:**

* `arr1` and `arr2` are valid JSON arrays
* Each object in `arr1` and `arr2` has a unique integer `id` key
* 2 <= JSON.stringify(arr1).length <= 10`<sup>`6`</sup>`
* 2 <= JSON.stringify(arr2).length <= 10`<sup>`6`</sup>`

## Solution:

#### Method 1:

```javascript
/**
 * @param {Array} arr1
 * @param {Array} arr2
 * @return {Array}
 */
var join = function(arr1, arr2) {
  let resultantArray = {};
  let joinedArray = [...arr1, ...arr2];
  for (let obj of joinedArray) {
    let id = obj.id;
    if (resultantArray[id]) {
      resultantArray[id] = {...resultantArray[id], ...obj};
    } else {
      resultantArray[id] = obj;
    }
  }
  return Object.values(resultantArray);
};
```

#### Method 2:

```javascript
/**
 * @param {Array} arr1
 * @param {Array} arr2
 * @return {Array}
 */
var join = function(arr1, arr2) {
  const resultantObject = {};

  for (let element of arr1) {
    resultantObject[element.id] = element;
  }
  for (let element of arr2) {
    let id = element.id;
    if (id in resultantObject) {
      resultantObject[id] = Object.assign(resultantObject[id], element);
    } else {
      resultantObject[id] = element;
    }
  }
  return Object.values(resultantObject);
};
```
