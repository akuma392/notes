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

## Solution (JavaScript)

```javascript
function factorial(n) {
  if (n === 0 || n === 1) {
    return 1;
  }
  return n * factorial(n - 1);
}

console.log(factorial(3)); // 6

