# Bubble Sort in JavaScript

Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order.

This version also includes:
- **Optimization using `swapped` flag** (early exit if array is already sorted)
- A `count` variable to track number of comparisons

---

## ✅ Bubble Sort Code (JavaScript)

```javascript
function bubbleSort(arr) {
  let count = 0;

  for (let i = 0; i < arr.length - 1; i++) {
    let swapped = false;

    for (let j = 0; j < arr.length - 1 - i; j++) {
      count++;

      if (arr[j] > arr[j + 1]) {
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
        swapped = true;
      }
    }

    // if no swaps in this pass => already sorted
    if (!swapped) break;
  }
  return arr;
}
