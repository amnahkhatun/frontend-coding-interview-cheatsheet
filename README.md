# Frontend coding Interview cheatsheet

### Polyfill of map
```
const arr = [1,2,3,4];

Array.prototype.myMap = function(cb){
  let newArr = [];
  for(let arr of this){
    newArr.push(cb(arr))
  }
  return newArr;
}
arr.myMap((item) => console.log(item * 2)) // [2,4,6,8]

```
### Polyfill of reduce
```
const arr = [1,2,3,4];

Array.prototype.myReduce = function (cb,value){
  for(let arr of this){
    value = value !== undefined ? cb(value,arr) : arr;
  }
  return value
}

let x1 = arr.myReduce(function(a, b) {
return a + b;
});
console.log(x1);

```
### Find the unique number
```
const nums = [1, 4, 5, 1, 7, 8, 4, 9, 5, 9];

var uniqueNumber = function (nums) {
  let myMap = new Map();
  nums.forEach(num => {
    let count = myMap.get(num)
    if (myMap.has(num)) {
      myMap.set(num, count + 1)
    } else {
      myMap.set(num, 1)
    }
  })
  for (const [k, v] of myMap) {
    if (v === 1) {
      console.log(k)
    }
  }
  
  console.log(singleNumber(nums)) // 7,8
```
### Find the duplicate element
```
const nums = [1, 4, 5, 1, 7, 8, 4, 9, 5, 9];

var duplicateNumber = function (nums) {
  let myMap = new Map();
  nums.forEach(num => {
    let count = myMap.get(num)
    if (myMap.has(num)) {
      myMap.set(num, count + 1)
    } else {
      myMap.set(num, 1)
    }
  })
  for (const [k, v] of myMap) {
    if (v > 1) {
      console.log(k)
    }
  }
  
  console.log(duplicateNumber(nums)) // 1,4,5,9
```
### Delete the duplicate elements
```
Time complexity is O(n^2) --> Quadratic time
let arr = [1, 2, 2, 4, 5, 6, 6]

function removeDuplicates(arr) {
  for (let i = 0; i <= arr.length - 1; i++) {
    for (let j = i + 1; j <= arr.length; j++) {
      if (arr[i] === arr[j]) {
        arr.splice(i, 1)
      }
    }
  }
  return arr
}
console.log(removeDuplicates(arr)) // [ 1, 2, 4, 5, 6 ]

---
// Using Set

function removeDuplicates(arr) {
  return [...new Set(arr)];
}
console.log(removeDuplicates(arr));
```
### Buble sort
### Insertion sort
### Selection sort
### Merge sort
### Find the length of the longest substring
- https://leetcode.com/problems/longest-substring-without-repeating-characters/
```
const s = "babad";
var lengthOfLongestSubstring = function (s) {
    const set = new Set();
    let [i, j, max] = [0, 0, 0];
    while (j < s.length) {
        if (set.has(s[j])) {
            set.delete(s[i++]);
        } else {
            set.add(s[j++]);
            max = Math.max(max, set.size);
        }
    }
    console.log(set.values()) //{'b','a','d'}

    return max;
};
console.log(lengthOfLongestSubstring(s)) //3

```
### Reverse a string
```
let reverseString = str => {
  let s = str.split("");
  let left = 0;
  let right = s.length - 1;
  while (left < right) {
    [s[left++], s[right--]] = [s[right], s[left]];
  }
  return s.join("");
};
console.log(reverseString("hello amnah")); //hanma olleh

let reverseString2 = str => {
  let s = str.replace(/\W/g, "");
  return [...s].reverse().join("");
};
console.log(reverseString2("A car, a man, a maraca")); //acaramanamaracA
console.log(reverseString2("amnah")); //hanma

```
### Merge sorted array
```
let mergeSortedArray = (arr1, arr2) => {
  const mergedArray = [];
  let arr1Item = arr1[0];
  let arr2Item = arr2[0];
  let i = 1;
  let j = 1;

  if (arr1.length < 2) {
    return arr1;
  }
  if (arr2.length < 2) {
    return arr2;
  }

  while (arr1Item || arr2Item) {
    if (arr2Item === undefined || arr1Item < arr2Item) {
      mergedArray.push(arr1Item);
      arr1Item = arr1[i];
      i++;
    } else {
      mergedArray.push(arr2Item);
      arr2Item = arr2[j];
      j++;
    }
  }
  return mergedArray;
};
console.log(mergeSortedArray([0, 3, 4, 31], [3, 4, 6, 30])); // [
  0, 3,  3,  4,
  4, 6, 30, 31
]
console.log(mergeSortedArray([1, 2], [4, 5, 6])); //[ 1, 2, 4, 5, 6 ]

let merge = function (nums1,nums2) {
  nums1.splice(nums2.length, nums1.length, ...nums2)
  return nums1.sort((a, b) => a - b)
};
console.log(merge([1, 2], [4, 5, 6])) // [ 1, 2, 4, 5, 6 ]
```
### Find the target

### Find the maximum subarray

## Tree

### Invert the binary tree
### Maximum depth of the binary tree
### Diameter of the binary tree
