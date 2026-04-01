```javascript

# Power using Recursion

function power(n, pow) {
  if (pow === 0) {
    return 1;
  } else {
    return n * power(n, pow - 1);
  }
}
console.log(power(2, 2)); // 4

# Factorial using Recursion

## Problem
Write a function to calculate the **factorial of a number `n`** using recursion.

Factorial of a number is defined as:

n! = n × (n - 1) × (n - 2) × ... × 1

Example:
5! = 5 × 4 × 3 × 2 × 1 = 120

---

# Solution (JavaScript)

function factorial(n) {
  if (n === 0 || n === 1) {
    return 1;
  }
  return n * factorial(n - 1);
}

console.log(factorial(3)); // 6

# Product of Array using Recursion

## Problem
Write a function that returns the **product of all numbers in an array** using recursion.

Example:

Input:
[3, 4, 10, 100]

Output:
12000

---
## Solution 1

function productOfAnArray(arr) {
  if (arr.length === 1) {
    return arr[0];
  }

  return arr[arr.length - 1] * productOfAnArray(arr.slice(0, arr.length - 1));
}
console.log(productOfAnArray([3, 4, 10, 100])); // 12000

# shorter solutions 
function productOfAnArray(arr) {
  if (arr.length === 0) return 1;
  return arr[0] * productOfAnArray(arr.slice(1));
}

# Recursive Range (Sum of Numbers)

## Problem
Write a recursive function that returns the **sum of all numbers from `n` down to `0`**.

### Example

Input:
recursiveRange(6)

Output:
21

Explanation:
6 + 5 + 4 + 3 + 2 + 1 + 0 = 21

---

## Solution (JavaScript)

function recursiveRange(n){
  if(n === 0){
    return 0
  }
  return n + recursiveRange(n-1)
}

console.log(recursiveRange(6)) // 21

# Fibonacci Number using Recursion

## Problem
Write a recursive function that returns the **nth Fibonacci number**.

The Fibonacci sequence is defined as:

0, 1, 1, 2, 3, 5, 8, 13, ...

Where:
- fib(0) = 0  
- fib(1) = 1  
- fib(n) = fib(n-1) + fib(n-2)

---

## Solution (JavaScript)

```javascript
function fib(n){
  // add whatever parameters you deem necessary - good luck!
  if(n === 0 || n === 1) return n;
  return fib(n - 1) + fib(n - 2);
}



