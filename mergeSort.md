# 📌 Merge Sort (JavaScript)

Merge Sort is a **divide and conquer** algorithm that divides the array into smaller parts, sorts them, and then merges them back together.

---

## 💻 Code Implementation

```javascript
function mergeSort(arr) {
  if (arr.length <= 1) return arr;

  let mid = Math.floor(arr.length / 2);

  let left = mergeSort(arr.slice(0, mid));
  let right = mergeSort(arr.slice(mid));

  return merge(left, right);
}

function merge(left, right) {
  let result = [];
  let i = 0, j = 0;

  while (i < left.length && j < right.length) {
    if (left[i] < right[j]) {
      result.push(left[i]);
      i++;
    } else {
      result.push(right[j]);
      j++;
    }
  }

  return [...result, ...left.slice(i), ...right.slice(j)];
}
const arr = [38, 27, 43, 3, 9, 82, 10];
const sorted = mergeSort(arr);

console.log(sorted);

How It Works
Divide array into halves recursively
Sort each half
Merge sorted halves

Example breakdown:

[5,2,4,6]
→ [5,2] [4,6]
→ [5] [2] [4] [6]
→ [2,5] [4,6]
→ [2,4,5,6]

| Case         | Time Complexity |
| ------------ | --------------- |
| Best Case    | O(n log n)      |
| Average Case | O(n log n)      |
| Worst Case   | O(n log n)      |


