# Selection Sort in JavaScript

This repository contains an implementation of the **Selection Sort** algorithm in JavaScript.

## 📌 What is Selection Sort?

Selection Sort is a simple comparison-based sorting algorithm. It works by repeatedly selecting the smallest element from the unsorted portion of the array and placing it at the beginning.

---

## 🧠 Algorithm Steps

1. Start from the first element of the array.
2. Assume the current element is the minimum.
3. Compare it with the rest of the elements in the array.
4. Find the actual minimum element.
5. Swap it with the current position.
6. Move to the next position and repeat until the array is sorted.

---

## 💻 Code Implementation

```javascript
function selectionSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    let min = i;

    for (let j = i + 1; j < arr.length; j++) {
      if (arr[min] > arr[j]) {
        min = j;
      }
    }

    if (min !== i) {
      let temp = arr[i];
      arr[i] = arr[min];
      arr[min] = temp;
    }
  }

  return arr;
}

## ▶️ Example

```javascript
const input = [64, 25, 12, 22, 11];
const sorted = selectionSort(input);

console.log(sorted);
